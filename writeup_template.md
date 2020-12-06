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

[image2]: ./test_images_output/segment_solidWhiteCurve.jpg "segment_solidWhiteCurve"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of the following steps. 

1. Images are converted to grayscale

2. Resulting grayscale image is smoothed through Gaussian smoothing / blurring

3. Canny Edge Detector algorithm is applied on the blurred image

4. A mask is applied on the resulting image to detect edges in the region of interest

5. Hough Transform algorithm is applied on the masked image to extract lines from the image

Below is the before and after an image is processed by the pipeline

**Before**

![alt text][image1]

**After**

![alt text][image2]

In order to draw a single line on the left and right lanes, draw_lines() function was modified to perform averaging of the slopes and the positions of the lines extracted by Hough Transform algorithm. However, the average is easily affected by smaller lines that are detected but are not part of the lane. Therefore, a weighted average is performed instead.

Depending on the slope and the location of the lines in the image, the new function, draw_lanes(), will classify the line as part of left or right lane. A weighted average is then applied to all the lines in the respective lane. The longer the line, the higher the weight. The averaged left and right line is then extrapolated to the edge of the detection area to form the left and right lanes


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
