# CarPartDetection: Detect Five Car Parts using YOLOv3 [![license](https://img.shields.io/github/license/mashape/apistatus.svg)](LICENSE)

This repo is to detect car parts using the state-of-the-art [YOLOv3](https://pjreddie.com/darknet/yolo/) computer vision algorithm. For a short write up check out this [medium post](https://medium.com/@muehle/how-to-train-your-own-yolov3-detector-from-scratch-224d10e55de2). 

This Project is to detect Five Parts of the car:
1. Light(Front and Back Light)
2. Glass(Front and Back Glass)
3. SideGlass
4. Door
5. Wheel

Checkout this inputs and outputs,

<img src="/Utils/Images/00234.jpg" width="400"/> <img src="/Utils/Images/00234_car_.jpg" width="400"/> 
<img src="/Utils/Images/00233.jpg" width="400"/> <img src="/Utils/Images/00233_car_.jpg" width="400"/> 
<img src="/Utils/Images/00232.jpg" width="400"/> <img src="/Utils/Images/00232_car_.jpg" width="400"/> 

### Pipeline Overview

To build and test your object detection algorithm follow the below steps:

 1. [Image Annotation](/1_Image_Annotation/)
	 - Install Microsoft's Visual Object Tagging Tool (VoTT)
	 - Annotate images
 2. [Training](/2_Training/)
 	- Download pre-trained weights
 	- Train your custom YOLO model on annotated images 
 3. [Inference](/3_Inference/)
 	- Detect objects in new images and videos

## Repo structure
+ [`1_Image_Annotation`](/1_Image_Annotation/): Scripts and instructions on annotating images
+ [`2_Training`](/2_Training/): Scripts and instructions on training your YOLOv3 model
+ [`3_Inference`](/3_Inference/): Scripts and instructions on testing your trained YOLO model on new images and videos
+ [`Data`](/Data/): Input Data, Output Data, Model Weights and Results
+ [`Utils`](/Utils/): Utility scripts used by main scripts

## Getting Started

### NEW: Google Colab Tutorial <a href="https://colab.research.google.com/github/AntonMu/TrainYourOwnYOLO/blob/master/TrainYourOwnYOLO.ipynb" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>
With Google Colab you can skip most of the set up steps and start training your own model right away. 

### Requisites
The only hard requirement is a running version of python 3.3 or newer. To install the latest python 3.x version go to 
- [python.org/downloads](https://www.python.org/downloads/) 

and follow the installation instructions. 

To speed up training, it is recommended to use a **GPU with CUDA** support. For example on [AWS](/2_Training/AWS/) you can use a `p2.xlarge` instance (Tesla K80 GPU with 12GB memory). Inference is very fast even on a CPU with approximately ~2 images per second. 


### Installation

#### 1a. Setting up Virtual Environment [Linux or Mac]

Clone this repo with:
```
git clone https://github.com/bhadreshpsavani/CarPartsDetectionChallenge
cd CarPartsDetectionChallenge/
```
Create Virtual **(Linux/Mac)** Environment (requires [venv](https://packaging.python.org/guides/installing-using-pip-and-virtual-environments/) which is included in the standard library of Python 3.3 or newer):
```
python3 -m venv env
source env/bin/activate
```
Make sure that, from now on, you **run all commands from within your virtual environment**.

#### 1b. Setting up Virtual Environment [Windows]
Use the [Github Desktop GUI](https://desktop.github.com/) to clone this repo to your local machine. Navigate to the `CarPartsDetectionChallenge` project folder and open a power shell window by pressing **Shift + Right Click** and selecting `Open PowerShell window here` in the drop-down menu.

Create Virtual **(Windows)** Environment (requires [venv](https://packaging.python.org/guides/installing-using-pip-and-virtual-environments/) which is included in the standard library of Python 3.3 or newer):

```
py -m venv env
.\env\Scripts\activate
```
![VSCode Command Prompt](/Utils/Screenshots/VSCode.png)
Make sure that, from now on, you **run all commands from within your virtual environment**.

#### 2. Install Required Packages [Windows, Mac or Linux]
Install all required packages with:

```
pip install -r requirements.txt
```
If this fails, you may have to upgrade your pip version first with `pip install pip --upgrade`. If your system has working CUDA drivers, it will use your GPU automatically for training and inference.

## Quick Start (Inference only)
To test the cat face detector on test images located in [`CarPartsDetectionChallenge/Data/Source_Images/Test_Images`](/Data/Source_Images/Test_Images) run the `Minimal_Example.py` script in the root folder with:

```
python Minimal_Example.py
```

The outputs are saved in [`CarPartsDetectionChallenge/Data/Source_Images/Test_Image_Detection_Results`](/Data/Source_Images/Test_Image_Detection_Results). This includes:
 - Cat pictures with bounding boxes around faces with confidence scores and
 - [`Detection_Results.csv`](/Data/Source_Images/Test_Image_Detection_Results/Detection_Results.csv) file with file names and locations of bounding boxes.

 If you want to detect car parts in your own pictures, replace the cat images in [`Data/Source_Images/Test_Images`](/Data/Source_Images/Test_Images) with your own images.

## Full Start (Training and Inference)

To train your own custom YOLO object detector please follow the instructions detailed in the three numbered subfolders of this repo:
- [`1_Image_Annotation`](/1_Image_Annotation/),
- [`2_Training`](/2_Training/) and
- [`3_Inference`](/3_Inference/).
 
**To make everything run smoothly it is highly recommended to keep the original folder structure of this repo!**

Each `*.py` script has various command line options that help tweak performance and change things such as input and output directories. All scripts are initialized with good default values that help accomplish all tasks as long as the original folder structure is preserved. To learn more about available command line options of a python script `<script_name.py>` run:

```
python <script_name.py> -h
```

## License

Unless explicitly stated otherwise at the top of a file, all code is licensed under the MIT license. 
This repo is the fork of [**TrainYourOwnYOLO**](https://github.com/AntonMu/TrainYourOwnYOLO) which is to train YOLOv3 algorithm cat detection. This repo makes use of [**ilmonteux/logohunter**](https://github.com/ilmonteux/logohunter) which itself is inspired by [**qqwweee/keras-yolo3**](https://github.com/qqwweee/keras-yolo3).

## Acknowledgements
I would like to thank [Anton Muelemann](https://github.com/AntonMu) for creating [**TrainYourOwnYOLO**](https://github.com/AntonMu/TrainYourOwnYOLO) repository which really helped me to create this custom object detector.

## Troubleshooting

0. If you encounter any error, please make sure you follow the instructions **exactly** (word by word). Once you are familiar with the code, you're welcome to modify it as needed but in order to minimize error, I encourage you to not deviate from the instructions above.  

1. If you are using [pipenv](https://github.com/pypa/pipenv) and are having trouble running `python3 -m venv env`, try:
    ```
    pipenv shell
    ```

2. If you are having trouble getting cv2 to run, try:

    ```
    apt-get update
    apt-get install -y libsm6 libxext6 libxrender-dev
    pip install opencv-python
    ```

3. If you are a Linux user and having trouble installing `*.snap` package files try:
    ```
    snap install --dangerous vott-2.1.0-linux.snap
    ```
    See [Snap Tutorial](https://tutorials.ubuntu.com/tutorial/advanced-snap-usage#2) for more information.

## Resources and Links:
* [AUG 23, 2021] -> If you have an object detection model, you can now use it with [OpenAI's](https://blog.roboflow.com/zero-shot-object-tracking/) zero shot object tracking repository to do object tracking - no additional modeling required. 


## Stay Up-to-Date

- ⭐ **star** this repo to get notifications on future improvements and
- 🍴 **fork** this repo if you like to use it as part of your own project.
