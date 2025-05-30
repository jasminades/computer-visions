# Computer Vision Projects

This repository contains a collection of computer vision projects developed as part of the **Foundations of Intelligent Systems Vision** course at *University of Cordoba*. Each project demonstrates a key concept in image processing or computer vision, implemented in **C++ using OpenCV**. Below are detailed descriptions, usage instructions, and techniques used in each project.

---

## 1. Camera Calibration

### Objective

Estimate the **intrinsic** and **extrinsic** parameters of a camera using chessboard images and apply **image undistortion** based on the results.

### Techniques Used

* Chessboard corner detection
* `cv::calibrateCamera()` for calibration
* `cv::undistort()` for rectifying images

### Input/Output

* **Input:** Multiple chessboard images (e.g. `calib1.png`, `calib2.png`, ...)
* **Output:**

  * `calibration.yml`: Calibration parameters
  * Undistorted versions of images

### Run Instructions

```bash
./calibrate calib1.png calib2.png ... calibration.yml
./undistort calibration.yml input.png output.png
```

---

## 2. CBG Process (Color By Gray)

### Objective

Create stylized versions of images where the grayscale intensity controls the coloring effect.

### Techniques Used

* RGB to Grayscale conversion
* Channel manipulation
* Color masking based on intensity

### Run Instructions

```bash
./cbg_process input.png output.png
```

---

## 3. Chromakey (Green Screen Removal)

### Objective

Remove a green screen background and replace it with a custom image.

### Techniques Used

* Convert to HSV color space
* Create masks for green background
* Composite two images using the mask

### Input/Output

* **Input:** Green screen subject image and a background image
* **Output:** Composited image with background replaced

### Run Instructions

```bash
./chromakey subject.png background.jpg output.png
```

---

## 4. Image Equalization

### Objective

Improve image contrast using histogram equalization.

### Techniques Used

* Convert to grayscale
* Apply `cv::equalizeHist()`
* Visualize histogram before/after

### Input/Output

* **Input:** Grayscale or color image
* **Output:** Contrast-enhanced image

### Run Instructions

```bash
./img_equalization input.jpg output_equalized.jpg
```

---

## 5. Pollen Grain Classification

### Objective

Train and evaluate a machine learning model to classify 15 types of pollen grains.

### Techniques Used

#### Feature Extraction:

* \[0,1] normalized grayscale features
* Mean-stddev normalization

#### Classifiers:

* K-Nearest Neighbors (KNN)
* Support Vector Machines (SVM)
* Random Trees (RTrees)

#### Evaluation:

* Confusion matrix computation
* Recognition rate per class
* Overall accuracy and mean recognition rate

### Dataset

* Images in `data/train/`, `data/test/`, `data/valid/`
* Labels provided via corresponding `.csv` files

### Run Instructions

```bash
# train a model
./train_clf data/train knn_model.xml knn 5

# test the model
./test_clf data/test knn_model.xml predictions_test.csv
```

---

## 6. Sharpening and USM Enhance

### Objective

Apply sharpening filters to enhance image details and edges.

### Techniques Used

#### Sharpening:

* Laplacian kernel convolution
* Subtracting Laplacian result from original image

#### USM (Unsharp Masking):

* Apply Gaussian blur
* Subtract blurred version from original
* Add weighted mask back to the original

### Input/Output

* **Input:** Raw image
* **Output:** Sharpened and USM-enhanced versions

### Run Instructions

```bash
./sharpen input.jpg output_sharp.jpg
./usm_enhance input.jpg output_usm.jpg
```

---
