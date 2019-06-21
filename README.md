# Module 4 Image Classification
----------------
## Implementation of a YOLO v3 Object Detector

### Hussein Sajid & Taeho Jeon

[Jupyter Notebook](https://github.com/hussein073/Mod_4_Image_Classification/blob/master/Image_Detect_Yolov3.ipynb)

[Slides](https://docs.google.com/presentation/d/14-GSsqBWwYikHM0EngZw_1xe--rDP0knILt_I6ecBhA/edit?usp=sharing)

**Project Goal**

The goal of this project is to test our ability to gather information from a real-world and use our knowledge of statistical analysis, classification and transfer learning to solve a problem that would be difficult or impossible to solve directly using traditional ML methods. 

## Requirements
* Python 3.5
* OpenCV

## Detection Example

<img class="size-full wp-image-8990" src="https://www.pyimagesearch.com/wp-content/uploads/2018/11/yolo_baggage_claim_output.jpg" alt="" width="600" height="510" srcset="https://www.pyimagesearch.com/wp-content/uploads/2018/11/yolo_baggage_claim_output.jpg 600w, https://www.pyimagesearch.com/wp-content/uploads/2018/11/yolo_baggage_claim_output-300x255.jpg 300w" sizes="(max-width: 600px) 100vw, 600px">

## Dataset: 
The COCO dataset consists of 80 labels, including, but not limited to:

* People
* Bicycles
* Cars and trucks
* Airplanes
* Stop signs and fire hydrants
* Animals, including cats, dogs, birds, horses, cows, and sheep, to name a few
* Kitchen and dining objects, such as wine glasses, cups, forks, knives, spoons, etc.
…and much more!

## Project Structure

Our project mainly consists of directories and Python scripts.
The directories (in order of importance) are:
* yolo-coco/ : The YOLOv3 object detector pre-trained (on the COCO dataset) model files. These were trained by the Darknet team.
* images/ : This folder contains four static images which we’ll perform object detection on for testing and evaluation purposes.
* videos/ : After performing object detection with YOLO on images, we’ll process videos in real time. This directory contains four sample videos for you to test with.
* output/ : Output videos that have been processed by YOLO and annotated with bounding boxes and class names can go in this folder.

We are reviewing two Python scripts — yolo.py  and yolo_video.py . The first script is for images and then we’ll take what we learn and apply it to video in the second script.

**YOLO object detection in images**

Let’s get started applying the YOLO object detector to images!

All you need installed for this script OpenCV 3.4.2+ with Python bindings. You can find <a href="https://www.pyimagesearch.com/opencv-tutorials-resources-guides/" target="_blank" rel="noopener">OpenCV installation tutorials here</a>, just keep in mind that OpenCV 4 is in beta right now — you may run into issues installing or running certain scripts since it’s not an official release. For the time being I recommend going for OpenCV 3.4.2+. You can actually be up and running in less than 5 minutes <a href="https://www.pyimagesearch.com/2018/09/19/pip-install-opencv/" target="_blank" rel="noopener">with pip</a> as well.

First, we import our required packages — as long as OpenCV and NumPy are installed, your interpreter will breeze past these lines.
Following are the command line arguments include:

* --image : The path to the input image. We’ll detect objects in this image using YOLO.
* --yolo : The base path to the YOLO directory. Our script will then load the required YOLO files in order to perform object detection on the image.
* --confidence : Minimum probability to filter weak detections. I’ve given this a default value of 50% ( 0.5 ), but you should feel free to experiment with this value.
* --threshold : This is our non-maxima suppression threshold with a default value of 0.3 . You can read more about non-maxima suppression here.

Our args variable is a dictionary containing the key-value pairs values. 

**YOLO object detection in video streams**

<img class="size-full" src="https://s3-us-west-2.amazonaws.com/static.pyimagesearch.com/opencv-yolo/yolo_overpass_output.gif" width="600">
