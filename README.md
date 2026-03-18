# Vision_Proctor
This VisionProctor system successfully bridges the gap between deep learning research and practical application. By combining a lightweight CNN architecture with robust real-time logic, it achieves high-fidelity gaze tracking capable of running on standard consumer hardware (8GB RAM) without the need for specialized eye-tracking sensors.
![Model Output for violation](https://github.com/Ashis153/Vision_Proctor/blob/main/AI%20Proctor%20Resume%20Demo%2015-03-2026%2018_29_25.png)
![Model Output for safe](https://github.com/Ashis153/Vision_Proctor/blob/main/AI%20Proctor%20Resume%20Demo%2015-03-2026%2018_29_36.png)

# Key Features

* **Memory-Efficient Training:** Optimized to train on the 13GB MPIIGaze dataset using only 8GB of RAM through chunked serialization and manual garbage collection.
* **3D to 2D Mathematical Transformation:** Converts 3D unit gaze vectors into spherical coordinates (Pitch and Yaw) to reduce model complexity while maintaining accuracy.
* **Real-Time Inference Pipeline:** Uses a Cascade-CNN Hybrid approach (Haar Cascades + CNN) for person-agnostic eye tracking.
* **Auto-Calibration Layer:** Includes a real-time calibration step (stare-at-center) to establish a baseline for different environments and users.
* **Violation Detection:** Implements a status buffer logic to detect and flag gaze deviations (potential proctoring violations) in real-time.time.
