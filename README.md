# PaddleOCR Fine-tune on US License Plate

By Lawrence Li (ll3598@columbia.edu) for COMS 4995 applied computer vision project

Spring 2023, Columbia University

## About the project
This project built an OCR model for US license plates by fine-tuning on pre-trained text recognition model (CRNN with MobileNetV3 backbone) from PaddleOCR. Given a US license plate image, the model will output the number of that license plate. 

## Dataset
The project uses OpenALPR benchmark dataset for fine-tuning and testing. The dataset is available here: https://github.com/openalpr/benchmarks

Note that this dataset contains only license plate text labels without bounding boxes annotations.

## Accuracy

| Evaluation Set | All 746 Images  | 146 Val Images |
| ----------- | ----------- | -------------- |
| DB+CRNN no fine-tuning      | 81.23%      | 82.88%         |
| CRNN no fine-tuning   | 49.06%      | 39.73%         |
| CRNN with fine-tuning   | 98.79%      | 93.84%         |

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

### Repository structure

* `fine_tuned_rec_model/rec`: contains the test results txt file from fine-tuned text recognition model for US license plate. My fine tuned model for US license plate `v3_en_mobile` is available here: https://drive.google.com/drive/folders/1JS5SEloMik3JdPrjR6t9q2rbKesfdICN?usp=sharing.
* `train_data`: contains US license plate image data from OpenALPR benchmark dataset, with `data_preprocess.ipynb` that can prepare the train test split ready for PaddleOCR fine-tuning process.
* Other files are jupyter notebook files that user can explore and run, see `Running` section below.
 
### Running

* Run `train_data/data_preprocess.ipynb` if you want to preprocess data into format accepted by PaddleOCR fine-tune training.
* Check out `fine_tune.ipynb` if you want to fine-tune the model.
* Check out and run `accuracy_evaluate.ipynb` for accuracy evaluation for fine-tuned text recognition model. Make sure to copy and run it under `PaddleOCR` directory after you cloned the github repository and completed the `train_data/data_preprocess.ipynb` and commands in `fine_tune.ipynb`.
* Run `main.ipynb` for DB+CRNN text detection and recognition model execution and performance evaluation. This model is not fine-tuned and return raw results from PaddleOCR built-in pre-trained models. 

