# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./test_images/solidWhiteCurve.jpg "solidWhiteCurve"
[image2]: ./test_images_output/segment_solidWhiteCurve.png "segment_solidWhiteCurve"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of the following steps. 

1. Images are converted to grayscale

2. Resulting grayscale image is smoothed through Gaussian smoothing / blurring with a kernel size of 5

3. Canny Edge Detector algorithm is applied on the blurred image with threshold of [90, 180]

4. A mask is applied on the resulting image to detect edges in the region of interest

5. Hough Transform algorithm is applied on the masked image to extract lines from the image

Below is the before and after an image is processed by the pipeline

**Before**
![alt text][image1]

**After**
![alt text][image2]

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
