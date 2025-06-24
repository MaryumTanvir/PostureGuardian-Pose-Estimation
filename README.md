Here is your **cleanly formatted Markdown**, with absolutely **no changes to the text** — only fixed indentation, backticks, and block consistency to make it render properly:

```markdown
# Real-Time Posture Classification Using MediaPipe and Random Forest

This project classifies human posture in **real-time** using a webcam. It uses **MediaPipe Pose** to extract body landmarks and a **Random Forest** model to classify the posture as either **Correct** or **Incorrect**.

---

## Project Structure

```

├── dataset/                   # Raw videos (Correct/Incorrect folders)
├── split\_dataset/            # Sampled videos split into train/val/test
├── landmark\_data/            # Pose landmarks extracted and saved as .npy files
├── posture\_model.pkl         # Trained Random Forest model
├── train\_model.py            # Script to extract data and train the model
├── realtime\_predict.py       # Run this for live classification via webcam
├── README.md                 # You're reading this

````

---

## How to Run the Project

### 1. Install Requirements

```bash
pip install opencv-python mediapipe scikit-learn joblib numpy
````

---

### 2. Prepare the Dataset

* Put your videos in `dataset/` inside two folders:

  * `Arm Raise Correct/`
  * `Arm Raise Incorrect/`

### 3. Split and Sample the Dataset

Use the provided script to sample a fixed number of videos and split into train, val, and test sets.

---

### 4. Extract Landmarks & Train the Model

Run the training script:

```bash
python train_model.py
```

This will:

* Extract pose landmarks from each video
* Convert them into fixed-size feature vectors
* Train a Random Forest classifier
* Save it as `posture_model.pkl`

---

### 5. Run Real-Time Pose Classification

```bash
python realtime_predict.py
```

This will:

* Open your webcam
* Detect your pose using MediaPipe
* Predict posture correctness live on screen

---

## Explanation

### How the Dataset Was Used

* Two classes: `Arm Raise Correct` and `Arm Raise Incorrect`
* Videos were split into `train`, `val`, and `test` sets
* MediaPipe extracted 33 pose landmarks per frame
* Each video was represented by a **99-dimensional feature vector** (mean of x, y, z values)
* Used for training a Random Forest classifier

---

### Exercise Selected

* **Arm Raise** exercise
* Model classifies whether the user raised their arms correctly

---

### Classifier Accuracy & Performance

* **Validation Accuracy**: 93.5%
* **Test Accuracy**: 93.9% (may vary slightly depending on data sampling)
* Real-time performance: \~15–20 FPS depending on hardware

---

### Challenges Faced

* **Overfitting** on small datasets (fixed by limiting tree depth)
* Model sometimes failed in real-time due to:

  * Low lighting
  * Fast motion
  * Irregular framing or partial visibility
* MediaPipe sometimes misses pose when joints are out of frame

---

## Future Improvements

* Add frame-by-frame training instead of using video-level averages
* Use temporal features (e.g., joint velocity)
* Add more exercises (e.g., squats, lunges)
* Improve robustness by using smoothing or ensemble predictions over time

---

```


```
