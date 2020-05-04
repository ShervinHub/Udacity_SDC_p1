# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)



---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of several steps. Grayscale the image, blur it using gaussian blur, binarize using canny and hough transform to find the lines and categorize them to left and right side lines base on slope. Then get the middle of each line in each group and find the best fitting lines that go through all of the points (regression), and draw these lines. 

I did not modify draw_lines. Instead added a helper function avg_lines() to categorize the lines, and fit the best line.

Results on the provided still images:

[image1]: ./test_images_output/solidWhiteCurve.jpg 

### 2. Identify potential shortcomings with your current pipeline


When there is only one line for each side of the lane returned by hough transfor, then there is an infinite number of best fitting lines (I know in a computer there is no such a thing as infinite - in theory I mean). Similar when no lines returned at all (due to bad tunning, etc.). 

It could be slower than avergaing the lines(not sure) but probably more robust.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to add a scene categorization code every few second to determine whether the car moving in a straight line, the position of the car on the road, etc, and then based on each follow a different strategy, or tuning of parameters.

Another potential improvement could be to allow curved lane lines, though with a little higher overload, it can produce better results.
