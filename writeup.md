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

#### 1.1 Gaussian blur
We apply Gaussian blur to the image in order to reduce noise and make the image more concise without the tedious details. Image you are driving a car. If you focus on too many irrelevant objects, it would keep your brain busy dealing too much information.

![blur image][image1]

#### 1.2 Color selection
The purpose of color selection is to filter out the pixels that are not related to the lane lines. In order to complete the task, we need to convert image from RGB space to HSV space. 

Representing color in HSV space makes the color selection more accurate and it’s widely used in the color tracking application. 

HSV stands for Hue, Saturation and Value. It allows the computer to pick the color even when the lane line is in the shadow.

![color selection][image2]

Debug tips:
I basically use an image color picker to get the HSV value for the lane line and then use color generator to get the range of the desired color.
Useful website:

[1. online image color picker](http://imagecolorpicker.com/)
[2. color generator](http://color.yafla.com/)

#### 1.3 Edge detection
We use Canny edge detection algorithm to convert a image into an edge images. There’re two parameters that we care about when using the canny function. The algorithm uses the “high_threshold” to detect strong pixels and extends the pixels that both exceed the “low_threshold” and connect to the strong pixels. Canny himself recommends 1:2 or 1:3 for the low/high ratio.

![edge detection][image3]

#### 1.4 Region of Interest
We want to define a region of interest now. Assume the camera is mounted in the front of the car and pointing ahead, the region of interest is always at the lower half of the image.

![ROI][image4]

#### 1.5 Hough Transform
We then use “Hough Transform” to detect lines in the image. The basic idea of Hough Transform is to convert points in the Cartesian coordinate to polar coordinate in Hough space. Each point in Cartesian space now becomes a sine curve in Hough space. The algorithm then calculates the numbers of intersections of the sine curves and pick the high vote ones. 

![Hough Transform][image5]

#### 1.6 Draw lane lines
Finally, we need to draw the detected lane lines on the road. In order to gain a smooth, stable lane line, we need to follow these steps:
Filter out horizontal and vertical line segments.
a. _Group line segments together and assign each one to either left or right lane lines_
b. _Calculate average slope and intersection for left/right lanes_
c. _Draw it on the image._

![Final output][image6]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
