# PaddleOCR Fine-tune on US License Plate

By Lawrence Li (ll3598@columbia.edu) for COMS 4995 applied computer vision project

Spring 2023, Columbia University

## About the project
This project built an OCR model for US license plates by fine-tuning on pre-trained text recognition model (CRNN with MobileNetV3 backbone) from PaddleOCR. Given a US license plate image, the model will output the number of that license plate. 

## Dataset
The project uses OpenALPR benchmark dataset for fine-tuning and testing. The dataset is available here: https://github.com/openalpr/benchmarks

Note that this dataset contains only license plate text labels without bounding boxes annotations.

## Accuracy

* Without fine-tuning: 81.50%
* With fine-tuning: 84.18%

## About the Repository

This repository contains pre-trained model that is fine-tuned for US license plate images under `us_fine_tune_rec` folder.
The OpenALPR benchmark dataset is also included under `train_data` folder. 

## Instructions

The following instructions are based on Linux and MacOS system. Not suitable for Windows.

### Requirements

* `Python 3.7`
* `PaddleOCR`, install instructions here: https://github.com/PaddlePaddle/PaddleOCR/blob/release/2.6/doc/doc_en/quickstart_en.md. Make sure to install the package and clone the source code. Supports CUDA 10.1 / CUDA 10.2 for NVIDIA gpu.
* `numpy`
* `matplotlib`

### Running

* Run `train_data/data_preprocess.ipynb` if you want to preprocess data into format accepted by PaddleOCR fine-tune training.
* Check out `fine_tune.ipynb` if you want to fine-tune the model.
* Run `main.ipynb` for model execution and performance evaluation.

