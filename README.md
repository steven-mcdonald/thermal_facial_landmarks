# Thermal Facial Landmark Annotation

## A Framework for Transferring Facial Landmarks from Visible Spectrum to Thermal Spectrum Images

- [Overview](#overview)
- [Objective](#overview)
- [Key Stages](#key-stages)
- [Summary](#summary-and-conclusions)

------

### Overview
This project contains selected code and outputs from my UCL MSc Data Science and Machine Learning thesis. 

<br/>

The ability to accurately identify landmark locations on thermal facial images is key to a number of facial analysis problems. Annotation on thermal images using models trained on visible spectrum images are unreliable. Current approaches therefore rely on time consuming manual annotation or are limited to facial images in constrained situations. This project is a framework for annotating thermal facial images in situations where thermal and visible images capture the same scene with cameras that may not be co-located or time- synchronised. The framework requires minimal manual annotation and does not require constrained head poses or expressions. The framework makes use of solutions to the Perspective-n-Point (PnP) pose problem to transfer 3D landmarks annotated on visible images to 2D landmarks on corresponding thermal images.

#### Example

![Example1](https://github.com/steven-mcdonald/thermal_facial_landmarks/blob/main/videos/p10_lmarks_compare_pix.gif)

The short clip above compares three videos of the same passenger sitting in a car. On the left we see footage from a thermal camera with facial landmark locations annotated using the Face Alignment Network (FAN) mode developed by Bulat et al. [github link](https://github.com/1adrianb/face-alignment). The FAN model was trained to work on RGB facial images and works robustly on 'in-the-wild' images. We can clearly see however that the model is unable to generate reliable landmarks on the thermal images. In the middle we see the same scene captured from a different viewpoint using an RGB camera. (Note: The video has been pixelated to protect the participants identity). In this case the FAN model aplies accurate annotation as expected. On the right we see the thermal footage again but this time with landmarks transferred from the RGB video using the framework outlined in this project. We can clearly see the improvement between the annotation on the thermal image on the left and on the right.

### Objective

Given images or video footage from an RGB camera and a thermal camera, the aim is to annotate facial landmarks on the RGB images and then transfer those landmarks to the equivalent thermal images. If the cameras are not co-located then the challenge is to transform the coordinates correctly. 

### Key Stages

#### 1. Time Alignment

If the RGB and thermal cameras are not genlocked or lack reliable time stamp information, the first step is to align the frame numbering from each camera as precisely as possible on events in the scene. Note thats if the frame rates of the videos are different, the RGB may need to be resampled in order to have matching frames for each thermal image.

#### 2. Initial Landmarks

The majority of facial landmark detection work has focused on 2D landmarks. The 3D FAN model has been trained to annotate 3D facial landmarks by fitting a 3D morphable model through minimizing the difference between the image and the model appearance. This 3D FAN model is used to annotate each frame of the RGB video with 3D facial landmarks.

We can transfer these 3D landmarks to the 2D image plane of the thermal camera by finding a solution to the Perspective-n-Point (PnP) pose problem [wikipedia](https://en.wikipedia.org/wiki/Perspective-n-Point). This is the problem of estimating the pose of a camera given a set of 3D points in the world and their corresponding 2D projections on an image. Once the camera pose is found then other 3D points from the world can be projected onto the image. From the FAN model applied to RGB images we have 3D points in the world. We can get the 2D projections by manually annotating a few of these landmarks on the equivalent thermal images using software such as labelme [github](https://github.com/wkentaro/labelme). 

#### 3. Camera Pose Estimation

The camera pose information can then be estimated using four or more automatically annotated 3D points from an RGB image and and the corresponding manually annotated points on the corresponding thermal image. This pose information is valid provided both camera positions remain fixed. 

#### 4. Transfer Landmarks

Using the pose information it is then straightforward to project 3D landmarks on an RGB frame directly onto the corresponding thermal frame. This can be done for each frame without any further manual annotation allowing large numbers of thermal images to be accurately annotaed with facial landmarks

### Summary

This framework can be used to annotate thousands of frames of thermal video with only  four or more manually annotated points. If the video feeds are gen-locked then the process can be set up with little further intervention. Otherwise, time-aligning the two video feeds requires some initial manual checking. 








