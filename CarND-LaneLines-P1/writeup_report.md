# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./test_images_output/grayscale.jpg "Grayscale"
[image2]: ./test_images_output/blur_gray_image.jpg "Blur_gray"
[image3]: ./test_images_output/edges.jpg "edges"
[image4]: ./test_images_output/masked_edges.jpg "masked_edges"
[image5]: ./test_images_output/line_image.jpg "line_image"
[image6]: ./test_images_output/testouput.jpg "testoutput_image"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. First, I converted the images to grayscale.

![alt text][image1]

Then, I applied the Gaussian Blur to the image with Kernal size of 5.

![alt text][image2]


Thirdly, I apply the canny edge detection to the image with low_threshold=30 and high_threshold=200.

![alt text][image3]

After that, the masked image is created by applying a defined region of interest in the frame.
![alt text][image4]


Then, I apply the hough transform to the masked image.
![alt text][image5]

Lastly, I draw the lines on the orginal image.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by adding a calculation for the slopes and intercept values for all lines in the image. All lines are classified to left and right lane by the slope values. The slopes and intercepts are averaged by left and right separtely. The top and bottom points of two lines are calculated by their slopes and intercepts accordingly.

![alt text][image6]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming could be that there might be some frames in the video where the detected lines on one side are very limited or even not availabe, thus add some instablitlity to the lanes position 

Another shortcoming could be that the lane detection can be wrong when there are more shades and darkness in the picutre, just as the optional challenge video shows.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to convert or normolized the color map of the orginal image.

Another potential improvement could be to add some connections between video frames to make their changes more continous. 
