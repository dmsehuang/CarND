# **Finding Lane Lines on the Road** 

---
The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image0]: ./write_up_images/0_original_image.jpg "Original image"
[image1]: ./write_up_images/1_blur_image.jpg "Blur image"
[image2]: ./write_up_images/2_color_selection.jpg "Color selection"
[image3]: ./write_up_images/3_canny_edge.jpg "Canny edge"
[image4]: ./write_up_images/4_ROI.jpg "ROI"
[image5]: ./write_up_images/5_hough_transform.jpg "Hough Transform"
[image6]: ./write_up_images/6_final_output.jpg "Final output"

---

### Reflection

### 1. Pipeline 
My pipeline consists of 5 steps:
1. Apply Gaussian blur to the image
2. Color selection
3. Edge detection
4. Get Region of Interest
5. Use Hough Transform to detect lines
6. Draw lines

This is the original image:
![original image][image0]

#### 1. Gaussian blur
We apply Gaussian blur to the image in order to reduce noise and make the image more concise without the tedious details. Image you are driving a car. If you focus on too many irrelevant objects, it would keep your brain busy dealing too much information.

![blur image][image1]

#### 2. Color selection
The purpose of color selection is to filter out the pixels that are not related to the lane lines. In order to complete the task, we need to convert image from RGB space to HSV space. 

Representing color in HSV space makes the color selection more accurate and it’s widely used in the color tracking application. 

HSV stands for Hue, Saturation and Value. It allows the computer to pick the color even when the lane line is in the shadow.

![color selection][image2]

Debug tips:
I basically use an image color picker to get the HSV value for the lane line and then use color generator to get the range of the desired color.
Useful website:

[1. online image color picker](http://imagecolorpicker.com/)

[2. color generator](http://color.yafla.com/)


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
