# **Finding Lane Lines on the Road** 

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/result.png "Result of the pipeline"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I applied a gaussian blur to the output of grayscale.
Then I  convert this image into edges with Canny function. I created a mask to get only the region of interest of Canny output. To detect the lines from Canny with mask, I applied hough transformation with tuned parameters. Finaly I return the lines (in red) on the original image.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by computing linear extrapolation between a virtual lane (could be done with a mask for example) and the bottom of the image. The thickness have been up and mixed with alpha filter to looks like the exemple video. Left and right lanes are separated by using they slope signs (negative or positive).

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when the road is curving because the pipeline is not adaped to this case (as we can see for the challenge video).

Another shortcoming could be a change of the resolution or another point of view of the camera.

I wonder what could happen with city roads with intersections and other subtleties.

### 3. Suggest possible improvements to your pipeline

A possible improvement would be to use cubic extrapolation to draw lines to be adapted to every situations of curve road.

Another potential improvement could be to go further and use a deep neural network to recognize lanes.
