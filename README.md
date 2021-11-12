# thermal_facial_landmarks

### A Framework for Transferring Facial Landmarks from Visible Spectrum to Thermal Spectrum Images

<br/>

### Overview
This project contains selected code and outputs from my UCL MSc Data Science and Machine Learning thesis.

<br/>

The ability to accurately identify landmark locations on thermal facial images is key to a number of facial analysis problems. Annotation on thermal images using models trained on visible spectrum images are unreliable. Current approaches therefore rely on time consuming manual annotation or are limited to facial images in constrained situations. This project is a framework for annotating thermal facial images in situations where thermal and visible images capture the same scene with cameras that may not be co-located or time- synchronised. The framework requires minimal manual annotation and does not require constrained head poses or expressions. The framework makes use of solutions to the Perspective-n-Point (PnP) pose problem to transfer 3D landmarks annotated on visible images to 2D landmarks on corresponding thermal images.

Example

![Example](https://github.com/steven-mcdonald/thermal_facial_landmarks/blob/main/videos/p06_lmarks_compare_pix.gif)



