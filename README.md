# 🧠 Image Classifier with Unsplash + CNN

An end-to-end image classification pipeline built in Google Colab. It automatically **downloads images from Unsplash**, **preprocesses them**, and **trains a custom CNN** to classify them into categories like cats, dogs, people, birds, and tables.

---

## 📌 Features

- 🔍 Auto-downloads 300 images per class from the Unsplash API
- 🧹 Preprocesses images (resize, blur, rename) using OpenCV
- 🤖 Trains a custom Convolutional Neural Network (CNN) with TensorFlow/Keras
- 📊 Uses data augmentation to improve model generalization
- 🖼️ Supports real-time prediction via image upload in Colab
- ⏱️ EarlyStopping to prevent overfitting

---

## 🗂️ Project Structure

```
image-classifier-unsplash-cnn/
│
├── image_classifier.ipynb     # Main Colab notebook
├── current_batch/             # Raw downloaded images (auto-created)
│   ├── cat/
│   ├── dog/
│   ├── person/
│   ├── birds/
│   └── table/
├── cleaned_batch/             # Preprocessed images (auto-created)
│   ├── cat/
│   ├── dog/
│   ├── person/
│   ├── birds/
│   └── table/
└── README.md
```

---

## 🚀 Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/image-classifier-unsplash-cnn.git
```

### 2. Open in Google Colab

Upload `image_classifier.ipynb` to [Google Colab](https://colab.research.google.com/) or open it directly from GitHub.

### 3. Get an Unsplash API Key

1. Go to [https://unsplash.com/developers](https://unsplash.com/developers)
2. Create a free developer account and a new application
3. Copy your **Access Key**
4. Replace it in the notebook:

```python
access_key = "YOUR_UNSPLASH_ACCESS_KEY"
```

> ⚠️ Never commit your API key to a public repository.

### 4. Run All Cells

Run the notebook top to bottom. It will:
1. Create folders for each class
2. Download 300 images per class from Unsplash
3. Preprocess and clean images
4. Train the CNN
5. Let you upload an image for prediction

---

## 🧰 Requirements

| Library         | Purpose                           |
|-----------------|-----------------------------------|
| `requests`      | Download images from Unsplash API |
| `opencv-python` | Image preprocessing               |
| `tensorflow`    | CNN model training & prediction   |
| `numpy`         | Array operations                  |
| `matplotlib`    | Visualizing uploaded images       |

All are available in Google Colab by default.

For local use:

```bash
pip install requests opencv-python tensorflow numpy matplotlib
```

---

## 🏗️ Pipeline Overview

```
Unsplash API
    ↓
Download 300 images × 5 classes
    ↓
Preprocess with OpenCV
  → Resize to 224×224
  → Gaussian Blur
  → Rename & save
    ↓
Data Augmentation (rotation, zoom, flip)
    ↓
Train CNN (80% train / 20% val)
    ↓
Predict on new image
```

---

## 🧬 Model Architecture

```
Input (224×224×3)
    ↓
Conv2D(32) → MaxPooling
    ↓
Conv2D(64) → MaxPooling
    ↓
Conv2D(128) → MaxPooling
    ↓
Flatten → Dense(128) → Dropout(0.5)
    ↓
Softmax Output (5 classes)
```

- **Optimizer:** Adam  
- **Loss:** Categorical Crossentropy  
- **EarlyStopping:** patience = 2

---

## 🏷️ Classes

| Label  |
|--------|
| cat    |
| dog    |
| person |
| birds  |
| table  |

---

## 📈 Sample Prediction Output

```
Prediction: dog
Confidence: 49.32%
```

---

## 🔒 Security Note

Your Unsplash **Access Key** is visible in the shared notebook. It's recommended to:
- Regenerate the key from the Unsplash developer dashboard
- Use Colab Secrets to store keys safely:

```python
from google.colab import userdata
access_key = userdata.get("UNSPLASH_KEY")
```

---

## 📄 License

This project is open-source and available under the [MIT License](LICENSE).

---

## 🙌 Acknowledgements

- [Unsplash API](https://unsplash.com/developers) — free photo search  
- [TensorFlow/Keras](https://www.tensorflow.org/) — model training  
- [OpenCV](https://opencv.org/) — image preprocessing  
- [Google Colab](https://colab.research.google.com/) — free GPU environment
