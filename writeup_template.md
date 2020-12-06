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

[image2]: ./test_images_output/segment_solidWhiteCurve.jpg "segment_solidWhiteCurve_result"

[image3]: ./test_images_output/solidWhiteCurve.jpg "solidWhiteCurve_result"

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

Depending on the angle and the location of the lines in the image, the new function, draw_lanes(), classifies the line as part of left or right lane. A weighted average is then applied to all the lines in the respective lane. The longer the line, the higher the weight. The averaged left and right line is then extrapolated to the edge of the detection area to form the left and right lanes

![alt text][image3]


### 2. Identify potential shortcomings with your current pipeline

The current pipeline have the following shortcomings:

- The `draw_lanes()` function cannot detect vertical lines as the function uses Cartesian coordinates to compute slope of the line. If the line is vertical, the function cannot compute its slope and classify whether the line is part of left or right lane.

- In order to detect lane markings further down the road, `max_line_length` of Hough Transform algorithm needs to be tuned to a lower value. This also allows noises that are not part of a lane to be picked up by the algorithm.

- The `draw_lanes()` function extrapolates straight lanes based on averages of lines. If the lane markings are not aligned on the road, there will be substantial oscillation in the lateral position and the angle of the detected lanes. 

- The `draw_lanes()` function extrapolates straight lanes to the edge of the detection area. If the vehicle path curvature increases, the extrapolated lanes would project poorly onto the actual lane, as evident in the attempt of applying the pipeline on the optional challenge video.

- Also evident in the optional challenge video is that the pipeline cannot detect lane markings that have little contrast against the road. Since Canny Edge Detection functions by highlighting gradient in the image. If there is too little gradient (e.g. faded lane marking) or too much variation in gradient (e.g. shades from trees), the pipeline will either detect nothing or pick up too much noises.


### 3. Suggest possible improvements to your pipeline

The current pipeline can benefit from the following improvements:

- The `draw_lanes()` function can be modified to detect vertical lines using Polar coordinates.

- Filtering techniques can be applied to video stream to filter out noises picked up by the Hough Transform algorithm.

- Instead of extrapolating straight lanes, the `draw_lanes()` function can be expanded to draw curved lanes using higher order polynomials to piece together the line segments from Hough Transform algorithm.

- In addition to using Canny Edge Detection algorithm, the pipeline can also include detection of other features (e.g. Color gradient) in order to improve robustness of lane markings in different lighting or contrast condition.