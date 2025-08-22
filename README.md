# Low-Cost-Driver-Monitoring-System-Using-Machine-Learning

import cv2
import winsound
import os
from datetime import datetime

# Create folder to save captured images
save_dir = "captured_alerts"
os.makedirs(save_dir, exist_ok=True)

face_cascade = cv2.CascadeClassifier(cv2.data.haarcascades + 'haarcascade_frontalface_default.xml')
eye_cascade = cv2.CascadeClassifier(cv2.data.haarcascades + 'haarcascade_eye.xml')

cap = cv2.VideoCapture(0, cv2.CAP_DSHOW)
cap.set(3, 640)
cap.set(4, 480)

eye_closed_frames = 0
EYE_CLOSED_THRESHOLD = 15
ALERT_ON = False

try:
    while True:
        ret, frame = cap.read()
        if not ret:
            break

        gray = cv2.cvtColor(frame, cv2.COLOR_BGR2GRAY)
        faces = face_cascade.detectMultiScale(gray, 1.2, 5)

        if len(faces) > 0:
            eyes_detected = False
            for (x, y, w, h) in faces:
                roi_gray = gray[y:y+h, x:x+w]
                roi_color = frame[y:y+h, x:x+w]

                eyes = eye_cascade.detectMultiScale(roi_gray, 1.1, 3, minSize=(30, 30))
                if len(eyes) > 0:
                    eyes_detected = True
                    for (ex, ey, ew, eh) in eyes:
                        cv2.rectangle(roi_color, (ex, ey), (ex+ew, ey+eh), (0,255,0), 2)

            if eyes_detected:
                if eye_closed_frames > 0:
                    eye_closed_frames -= 1
            else:
                eye_closed_frames += 1
                print(f"Eyes possibly closed - frame count: {eye_closed_frames}")

            if eye_closed_frames >= EYE_CLOSED_THRESHOLD:
                if not ALERT_ON:
                    print("⚠️ ALERT: Driver might be sleeping!")
                    winsound.Beep(1000, 1000)  # 1 sec beep
                    ALERT_ON = True

                    # ---- SAVE PHOTO ----
                    timestamp = datetime.now().strftime("%Y%m%d_%H%M%S")
                    filename = os.path.join(save_dir, f"alert_{timestamp}.jpg")
                    cv2.imwrite(filename, frame)
                    print(f"📷 Photo captured: {filename}")

            else:
                ALERT_ON = False

        cv2.imshow("Drowsiness Detection", frame)

        if cv2.waitKey(1) & 0xFF == ord('q'):
            break

except KeyboardInterrupt:
    print("Program interrupted manually!")

cap.release()
cv2.destroyAllWindows()
