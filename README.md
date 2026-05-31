# Image Classification & Segmentation 🧠
* **Course:** CMSC426
* **Author:** Arik Gershman

## Viewing This Project
The Jupyter notebook contains embedded output and visualizations, which makes it too large to render directly on GitHub. For the best experience:
* 📄 **[View the PDF](CMSC426_Assignment5_sp26.pdf)** — recommended for a quick look at the code and results
* 📓 **[View the notebook on nbviewer](https://nbviewer.org/github/arikgershman/cifar10-cnn-classifier/blob/main/CMSC426_Assignment5_sp26.ipynb)** — for interactive notebook rendering
* 💾 Download the `.ipynb` file to run it locally

## Project Overview
This project focuses on two core computer vision tasks: image classification and image segmentation. I built and trained a Convolutional Neural Network (CNN) to classify images into 10 categories from the CIFAR-10 dataset, and utilized the Segment Anything Model (SAM) for advanced image segmentation.

## Running the Code & Custom Images
The custom test images used in this project (including `airplane.jpg`, `bird.jpg`, and others) are located in the `data/` directory of this repository. 

**Important:** To run the notebook successfully (especially in environments like Google Colab), you must upload these individual image files directly to your active working directory. 

## Methodology
The pipeline is broken down into several main components:

**1. Data Loading & Preprocessing**
* Loaded the CIFAR-10 dataset (50,000 training images, 10,000 test images) using the `datasets` library.
* Preprocessed the images by applying PyTorch transformations (resizing, converting to tensors, and normalizing the RGB channels to a [-1, 1] range).

**2. Network Architecture**
* Designed a lightweight CNN using `torch.nn`.
* The architecture consists of:
  * Conv2D (3 input channels $\rightarrow$ 32 output channels) $\rightarrow$ ReLU $\rightarrow$ MaxPool2D
  * Conv2D (32 input channels $\rightarrow$ 64 output channels) $\rightarrow$ ReLU $\rightarrow$ MaxPool2D
  * Flattening operation
  * Fully Connected (Linear) Layer (1600 $\rightarrow$ 256) $\rightarrow$ ReLU
  * Fully Connected Layer (256 $\rightarrow$ 128) $\rightarrow$ ReLU
  * Output Linear Layer (128 $\rightarrow$ 10 classes)

**3. Training & Evaluation**
* Used Cross-Entropy Loss and the Adam optimizer.
* Trained the network for 5 epochs over the dataset.
* Tracked the average training loss and evaluated the test accuracy, calculating both overall accuracy and individual per-class accuracy distributions.

**4. Segmentation**
* Implemented image segmentation workflows utilizing the Segment Anything Model (SAM) to isolate subjects in custom test images.

## Technologies Used
* **Language:** Python
* **Environment:** Jupyter Notebook, Google Colab
* **Libraries:** PyTorch (`torch`, `torch.nn`, `torch.optim`), TorchVision, Hugging Face Datasets, NumPy, Matplotlib
