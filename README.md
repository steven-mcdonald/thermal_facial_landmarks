# Thermal Facial Landmark Annotation

## A Framework for Transferring Facial Landmarks from Visible Spectrum to Thermal Spectrum Images

- [Overview](#overview)
- [Objectives](#objectives)
- [Key Stages](#key-stages)
- [Summary and Conclusions](#summary-and-conclusions)
- [Possible Extensions](#possible-extensions) 

------

### Overview
This project contains selected code and outputs from my UCL MSc Data Science and Machine Learning thesis.

<br/>

The ability to accurately identify landmark locations on thermal facial images is key to a number of facial analysis problems. Annotation on thermal images using models trained on visible spectrum images are unreliable. Current approaches therefore rely on time consuming manual annotation or are limited to facial images in constrained situations. This project is a framework for annotating thermal facial images in situations where thermal and visible images capture the same scene with cameras that may not be co-located or time- synchronised. The framework requires minimal manual annotation and does not require constrained head poses or expressions. The framework makes use of solutions to the Perspective-n-Point (PnP) pose problem to transfer 3D landmarks annotated on visible images to 2D landmarks on corresponding thermal images.

Example 1

![Example1](https://github.com/steven-mcdonald/thermal_facial_landmarks/blob/main/videos/p10_lmarks_compare_pix.gif)

The short clip above compares three videos of the same passenger sitting in a car. On the left we see footage from a thermal camera with facial landmark locations annotated using the Face Alignment Network (FAN) mode developed by Bulat et al. [github link](https://github.com/1adrianb/face-alignment). The FAN model was trained to work on RGB facial images and works robustly on 'in-the-wild' images. We can clearly see however that the model is unable to generate reliable landmarks on the thermal images. In the middle we see the same scene captured from a different viewpoint using an RGB camera. (Note: The video has been pixelated to protect the participants identity). In this case the FAN model aplies accurate annotation as expected. On the right we see the thermal footage again but this time with landmarks transferred from the RGB video using the framework outlined in this project. We can clearly see the improvement between the annotation on the thermal image on the left and on the right.

![Example2](https://github.com/steven-mcdonald/thermal_facial_landmarks/blob/main/videos/p06_lmarks_compare_pix.gif)



