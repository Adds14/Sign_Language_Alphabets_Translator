# 🤟 Real-Time American Sign Language (ASL) Alphabet Translator

[![Python 3.8+](https://img.shields.io/badge/Python-3.8%2B-blue)](https://www.python.org/)
[![Status](https://img.shields.io/badge/Status-Complete-success.svg)](https://github.com/Adds14/Sign_Language_Alphabets_Translator)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)

A computer vision project that uses **OpenCV**, **cvzone**, and a trained **Keras/TensorFlow** model to translate hand gestures into their corresponding American Sign Language (ASL) alphabet characters in real-time via a webcam.

## 📋 Table of Contents

* [Key Features](#key-features)
* [Installation & Setup](#installation--setup)
* [Usage](#usage)
    * [1. Real-Time Recognition](#1-real-time-recognition-mainpy)
    * [2. Data Collection](#2-data-collection-datacollectionpy)
* [Project Structure](#project-structure)
* [Dependencies](#dependencies)
* [Contributing](#contributing)
* [License](#license)

***

## ✨ Key Features

* **Real-time Hand Detection:** Utilizes `cvzone.HandDetector` to accurately locate and track a single hand in the webcam feed.
* **Intelligent Image Pre-processing:**
    * Crops the hand region with a consistent `offset` (30 pixels).
    * Resizes the cropped image to a uniform `300x300` pixel white canvas, maintaining the aspect ratio of the hand to prevent distortion.
* **High-Accuracy Classification:** Loads a pre-trained Keras model (`keras_model.h5`) to classify the processed hand image into one of the ASL alphabet labels (A, B, C, D, etc.).
* **Visual Feedback:** Draws a bounding box and displays the predicted alphabet character directly onto the webcam stream.

***

## 🛠️ Installation & Setup

### Prerequisites

1.  A Python environment (Python 3.8+ recommended).
2.  A working webcam.

### Step-by-Step Installation

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/Adds14/Sign_Language_Alphabets_Translator.git](https://github.com/Adds14/Sign_Language_Alphabets_Translator.git)
    cd Sign_Language_Alphabets_Translator
    ```

2.  **Create and activate a virtual environment** (Highly Recommended):
    ```bash
    python -m venv venv
    source venv/bin/activate  # macOS/Linux
    # venv\Scripts\activate   # Windows
    ```

3.  **Install the required libraries:**
    ```bash
    pip install -r requirements.txt
    ```
    *(Note: The `requirements.txt` should contain `opencv-python`, `numpy`, `cvzone`, and `tensorflow`)*

4.  **Model Files:** Ensure your trained model files (`keras_model.h5` and `labels.txt`) are placed in the `Model/` directory before running `MAIN.py`.

***

## 🚀 Usage

### 1. Real-Time Recognition (`MAIN.py`)

This is the main application file used for live inference. It loads the trained model and starts classification from your webcam.

1.  Make sure your webcam is connected and the model files are in place.
2.  Run the main script:
    ```bash
    python MAIN.py
    ```
3.  The webcam window will open. Place your hand in the frame and hold an ASL sign. The predicted letter will appear above the hand's bounding box.

### 2. Data Collection (`DataCollection.py`)

This script is used to gather a new dataset for training your own custom classifier.

1.  **Set up data folders:** Update the `folder` variable in `DataCollection.py` (e.g., `folder = "Data/J"`) to the specific sign you want to capture. Create the corresponding folder (e.g., `Data/J`).
2.  Run the data collection script:
    ```bash
    python DataCollection.py
    ```
3.  With the webcam open, hold the desired sign and press the **'s'** key. The script will save the processed 300x300 white-background image to your target folder, logging the counter in the terminal.

***

## 📂 Project Structure
Sign_Language_Alphabets_Translator/
|
├── Data/              # 📥 Training Data Repository

|   ├── A/             # Sub-folders for each ASL sign

|   ├── B/             # All captured images are saved here (300x300, white background)

|   └── I/

|
├── Model/             # 🧠 Machine Learning Assets

|   ├── keras_model.h5 # The core pre-trained Keras model weights.

|   └── labels.txt     # A text file containing the class labels (e.g., A, B, C, ...).

|

├── MAIN.py            # ▶️ Real-Time Recognition Script (The main application file)

├── DataCollection.py  # 📸 Data Collection Script (Used to build the dataset)

├── .gitignore         # Defines files and folders to exclude from version control.

└── requirements.txt   # Lists all Python dependencies needed to run the project.

***

## ✍️ Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

## 📄 License

This project is licensed under the **MIT License**. See the `LICENSE` file for details.
