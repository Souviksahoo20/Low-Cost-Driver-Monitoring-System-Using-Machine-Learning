----------------------------------------------------------------------------------------------------------------------------
A Driver Monitoring System (DMS) is an in-vehicle safety technology that uses cameras and sensors
to track the driver's eye movements, head position, and behavior. It detects signs of drowsiness,
distraction, or inattention and alerts the driver to stay focused, enhancing overall road safety and accident
prevention.
A Driver Monitoring System is needed to enhance road safety by reducing accidents caused by
driver fatigue, distraction, or inattention—common factors in traffic crashes. It helps ensure drivers stay
alert, especially during long trips or in semi-autonomous vehicles. By providing timely alerts or taking
corrective actions, DMS can prevent dangerous situations, protect passengers and pedestrians, and
support compliance with growing vehicle safety regulations worldwide.
Low-cost Driver Monitoring Systems are important to make advanced safety features accessible in
a wider range of vehicles, including budget models. This increases overall road safety by enabling more
drivers to benefit from the technology, supporting broader adoption, regulatory compliance, and reducing
traffic accidents across all income levels.
IoT (Internet of Things) is needed to enable seamless connectivity and communication between
devices, allowing real-time data collection, monitoring, and control. In transportation, IoT enhances
vehicle safety, efficiency, and maintenance by linking systems like Driver Monitoring, GPS, and diagnostics.
It supports smarter decision-making, remote access, and predictive analytics, leading to improved
performance, reduced downtime, and a better driving experience. IoT also plays a key role in smart city
and mobility solutions.
Machine Learning (ML) can be used to improve accuracy and adaptability in systems like Driver
Monitoring by learning patterns from vast data. It enables real-time detection of drowsiness, distraction,
or risky behavior with high precision. ML models continuously evolve, enhancing performance over time.
In broader IoT applications, ML supports predictive maintenance, anomaly detection, and intelligent
decision-making, making systems smarter, more efficient, and responsive to changing environments and
user behavior.
 The paper titled “Low-Cost Driver Monitoring System Using Deep Learning” proposes an affordable
and efficient driver drowsiness detection system using deep learning and IoT hardware. The main objective
is to identify signs of fatigue in drivers—specifically yawning and eye closure—in real time using a
Raspberry Pi-based setup.[3]
Two datasets were used in the study. For yawning detection, a custom dataset was created using
videos of 15 volunteers. Around 500 images were manually labeled and later expanded to 1,020 images
through data augmentation. For eye state detection, the authors used the Kaggle Eye State Dataset, which
includes 1,500 images, later augmented to 3,000 images.[2]
The models were based on a modified LeNet-5 convolutional neural network, chosen for its
simplicity and efficiency on low-power devices. The system was implemented on a Raspberry Pi 3 Model
B+, with a Pi Camera Module V2 for image capture and a buzzer/display module for alerting the driver.The
models achieved 96% accuracy for yawning detection and 97.5% for eye state classification, performing
reliably in real-time.[1]
 The existing method relies on limited features—eye state and yawning—for drowsiness detection,
which may miss other indicators like gaze direction or head tilting. The small dataset and single-camera
setup reduce accuracy under varied conditions. To improve the system, we can use larger, more diverse
datasets, integrate additional sensors like infrared or gyroscope and adopt lightweight, more robust deep
learning models for better real-time performance.
-------------------------------------------------------------------------------------------------------------------------------------
