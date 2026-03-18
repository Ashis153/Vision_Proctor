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


## 🏗️ Technical Architecture

### 1. Data Engineering (Phase A)
* **Dataset:** MPIIGaze (213,659 images from 15 subjects).
* **Preprocessing:** Histogram equalization, resizing (64x64), and normalization.
* **Serialization:** Data is stored in binary `.npy` format using `uint8` to save 75% more disk space compared to floating-point storage.

### 2. Model Development (Phase B)
The system utilizes a **Sequential CNN** architecture optimized for regression:

* **Convolutional Layers:** 3 layers (32, 64, and 128 filters) with `Batch Normalization` and `Max Pooling`.
* **Fully Connected Layers:** Dense layers (128 and 64 units) with `Dropout` (0.3) for regularization.
* **Loss Function:** **Mean Squared Error (MSE)** for predicting continuous pitch and yaw coordinates.

### 3. Live Deployment (Phase C)
* **Detection:** `cv2.CascadeClassifier` for rapid eye region localization.
* **Inference:** TensorFlow/Keras model processing **ROI** (Region of Interest) at a $0.0005$ learning rate.
* **Visualization:** Real-time gaze vector projection and status flagging (`SAFE` vs. `VIOLATION`).


## 📊 Performance

* **Total Parameters:** `3,451,080`
* **Trainable Parameters:** `1,150,210`
* **Model Convergence:** Successfully converged to an average epoch loss of ~`0.0044` across 10 epochs.
