# ✍️ Handwritten Character Recognition using Air-Writing  

## 🌐 Project Overview  
This project focuses on **recognizing handwritten characters written in the air** using a camera and **Mediapipe hand tracking**. The system allows users to draw digits and letters in the air with their index finger, and the gestures are converted into **images** and classified using a **Convolutional Neural Network (CNN)**.  

The model can recognize:  
* **Digits (0–9)**
* **Uppercase Letters (A–Z)**  
* **Lowercase Letters (_a–_z)**
  
This work combines **computer vision** and **deep learning** to explore a natural human–computer interaction method.  

---

## 🔎 Problem Statement  
Traditional handwriting recognition requires pen and paper or stylus input. However, in many scenarios (AR/VR, gesture interfaces, touchless devices), users may want to **write in the air** without a physical surface.  

The challenge is to build a system that can:  
* Track finger movements in real-time  
* Convert trajectories into structured input (images/CSV)  
* Train a classifier to recognize characters accurately  
* Support both uppercase and lowercase recognition  

---

## 📁 Dataset Overview  
The dataset was **self-created using Mediapipe**.  
 <img src="https://th.bing.com/th/id/OIP.mKuBD4cYR9Y-jqWpuw9cWAHaEc?w=245&h=180&c=7&r=0&o=7&pid=1.7&rm=3" alt="omnicron_image" width="300" style="margin-right: 20px;">

* **Classes**:  
  - Digits: 0–9  
  - Uppercase: A–Z  
  - Lowercase: _a–_z (underscore prefix keeps case-sensitive folder names)  

* **Format**:  
  - Gesture trajectories stored as CSV (`gesture_trajectories_dataset.csv`)  
  - Augmented dataset (`augmented_gesture_motion_dataset.csv`) for robustness  
  - Converted to **64x64 grayscale images** for CNN training  

* **Dataset File**: [`group_33_dataset.zip`](./group_33_dataset.zip)  

---

## 🧹 Data Preparation  
The dataset creation involved:  
<img src="https://www.mdpi.com/electronics/electronics-12-00995/article_deploy/html/images/electronics-12-00995-g002.png" alt="omnicron_image" width="300" style="margin-right: 20px;">
* **Hand Landmark Tracking** → Using Mediapipe to detect the index finger tip path  
* **Normalization** → Scaling trajectories for consistency  
* **Data Augmentation** → Rotations, shifts, scaling to improve generalization  
* **Image Conversion** → Converting trajectories into 64×64 grayscale images  

---

## 🏗️ Model Architecture  
A **CNN model** was built with the following architecture:  

* Input: 64×64 grayscale image  
* Conv Layer 1 → 32 filters  
* Conv Layer 2 → 64 filters  
* Conv Layer 3 → 128 filters  
* Dense Layer → 256 units  
* Dropout layers for regularization  
* Softmax output for 62 classes (digits + uppercase + lowercase)  

Training details:  
* Loss Function: Categorical Crossentropy  
* Optimizer: Adam  
* Early Stopping to avoid overfitting  

---

## 📊 Evaluation Metrics  
The model was evaluated using:  
* ✅ Accuracy → Proportion of correctly predicted characters  
* 📉 Precision, Recall, F1-Score → For class-wise performance  
* 🔄 Confusion Matrix → Breakdown of predictions vs actual labels  

---

## 🌐 Visualizations  
* Gesture trajectories (raw finger movements)  
* Training & validation accuracy/loss curves  
* Confusion matrix heatmaps  

---

## 🚀 Usage  

### 1. Dataset Creation  
Run `dataset creation.ipynb` to generate and augment the dataset.  
<img src="https://github.com/Sayanb087/my_collage_project/blob/main/sample_7.jpg" alt="omnicron_image" width="300" style="margin-right: 20px;">
### 2. Model Training  
Open `group_33_final_project.ipynb` and run all cells to:  
* Load dataset  
* Train CNN model  
* Evaluate test accuracy  

### 3. Inference  
Use the trained model for recognizing new air-writing gestures.  
<img src="https://github.com/Sayanb087/my_collage_project/blob/main/lowercase.png" alt="omnicron_image" width="300" style="margin-right: 20px;">


---

## 🧪 Experiments  
The project experimented with:  
* Different augmentation strategies  
* Varying convolutional filter sizes  
* Dropout tuning for generalization  
* Testing uppercase vs lowercase recognition separately  

---

## 📝 Summary  
This project demonstrates an end-to-end pipeline for **air-writing recognition**, from **dataset creation** to **CNN model training** and **evaluation**. It shows how deep learning can enable **touchless handwriting recognition**, with potential applications in **AR/VR, gesture-based UIs, and assistive technologies**.  

Future directions include:  
* Multi-character word/sentence recognition  
* Real-time segmentation with **CRAFT algorithm**  
* Deployment as a web or mobile application  

---

✨ Built with passion by **Group 33**  
