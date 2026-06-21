# 🎵 Image-Based Deep Learning Song Recommender

A deep learning-based framework that analyzes the scene and mood of an image to recommend the perfect soundtrack. The system classifies the environment type using a Convolutional Neural Network (CNN) and performs a pixel-level brightness analysis to match the visual atmosphere with a curated song database.

---

## 🚀 Overview & Key Features

*   **Scene Classification**: Utilizes a deep learning model to categorize input images into 6 distinct environmental landscapes (Buildings, Forest, Glacier, Mountain, Sea, Street).
*   **Atmosphere/Brightness Analysis**: Converts the image into the HSV color space to calculate the average value (V channel), categorizing the scene into either **"Bright"** or **"Dark"** moods.
*   **Curated Music Mapping**: Queries a predefined database (`songs.csv`) to randomly select a song matching both the predicted location and its specific lighting condition.
*   **Interactive Notebook Display**: Seamlessly renders the tested image alongside an embedded interactive YouTube video player for instant playback within the environment.

---

## 🛠️ Tech Stack

*   **Language**: Python
*   **Deep Learning Framework**: TensorFlow / Keras (CNN / VGG16 Transfer Learning)
*   **Computer Vision & Image Processing**: OpenCV (OpenCV-Python), PIL (Pillow)
*   **Data Manipulation**: Pandas, NumPy
*   **Visualization & Multimedia**: Matplotlib, Seaborn, IPython.display (YouTubeVideo)

---

## 📊 Dataset & Database Structure

### 1. Training Dataset: Intel Image Classification
The core classification model is trained on the widely recognized **Intel Image Classification Dataset**, which contains thousands of natural scene images across 6 classes:
*   `buildings` | `forest` | `glacier` | `mountain` | `sea` | `street`

### 2. Song Database (`songs.csv`)
Songs are pre-classified and structured inside a CSV file based on location and lighting conditions. 
*   **Columns**:
    *   `place`: Matches the 6 predicted labels from the Intel dataset.
    *   `bright`: Curated tracklists/YouTube links suited for daytime or well-lit scenes.
    *   `dark`: Curated tracklists/YouTube links suited for nighttime, overcast, or dimly lit scenes.

---

## ⚙️ How It Works (Pipeline)

```text
[ Input Image ] ──> [ Preprocessing / Resizing ]
                          │
                          ├──> [ Deep Learning Model ] ──> Predicts: Place Label
                          └──> [ HSV Color Extraction ] ──> Predicts: Bright / Dark
                                                                 │
[ Output Display ] <── [ Play Random YouTube Track ] <── [ Query songs.csv ]
```

1. **Image Ingestion**: An image from the test environment or user input is loaded.
2. **Dual-Track Analysis**:
    *   The CNN model predicts the geographical category (`predicted_label`).
    *   The system extracts the V-channel (Value/Brightness) to compute the mean value, establishing a `brightness_category` (`bright` vs. `dark`).
3. **Database Querying**: The script filters rows in `songs.csv` where the location aligns with the prediction and slices the precise YouTube video token.
4. **Result Generation**: Outputs the predicted metadata, displays the original image, and embeds a localized YouTube widget.

---

## 📋 Installation & Getting Started

### Prerequisites
Make sure you have Google Colab or a local Python environment configured with a GPU for optimal model performance.

### Running the Project
1. Clone this repository:
```bash
   git clone [https://github.com/jeongwonbahk/deep-learning-song-recommender.git](https://github.com/jeongwonbahk/deep-learning-song-recommender.git)
   ```
2. Ensure `songs.csv` and your Intel Dataset paths are correctly mapped within the environment script.
3. Execute the cells inside `코드.ipynb` to train/load the weights and test your custom images.
