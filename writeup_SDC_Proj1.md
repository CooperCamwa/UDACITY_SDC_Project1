# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/Writeup_pics/GrayScale.jpg "Grayscale"
[image2]: ./examples/Writeup_pics/CannyEdge.jpg "CannyEdge"
[image2]: ./examples/Writeup_pics/mask.jpg "mask"
[image2]: ./examples/Writeup_pics/road_example_1.jpg "road_example_1"
[image2]: ./examples/Writeup_pics/road_example_2.jpg "road_example_2"
[image2]: ./examples/Writeup_pics/road_example_3.jpg "road_example_3"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My program consisted of 2 main steps, my_pipeline and post_process_lines.

in my_pipeline the following steps are implemented:
    1- creating the gray scale image from original image
    [image1]: ./examples/Writeup_pics/GrayScale.jpg "Grayscale"
    2- defining the kernel size, it must be odd, starting with 5 or more, because gradient for whole image,
        here the selected kernel size is 5
    3- Guassian blur for gray scale image based on kernel size
    4- defining the threshold for canny edge detection (120, 220)
    [image2]: ./examples/Writeup_pics/CannyEdge.jpg "CannyEdge"
    5- defining the borders for creating and adding the mask
    [image2]: ./examples/Writeup_pics/mask.jpg "mask"
    6- defining the Hough transformation, starting with small values

in post_process_lines the following steps are implemented:
    1- reading the lines and detecting if in the left side (upward) or on the right side (downward)
    2- for every side choosing the longest line, one for left and one for right
    3- extending the selected lines to bottom of image
    4- using weighted_img function for drawing the line on image
   


If you'd like to include images to show how the pipeline works, here is how to include an image: 

[image2]: ./examples/Writeup_pics/road_example_1.jpg "road_example_1"
[image2]: ./examples/Writeup_pics/road_example_2.jpg "road_example_2"


### 2. Identify potential shortcomings with your current pipeline

Here a simple use case of line detecting is presented, just straight lines.
More challenging could be the following situation (just some exaples, the list could be longer):
1- curve lanes
2- lanes with different colors in road structures
3- in bad wetter condition and road condition such as rainy day and wet surface
4- under varying degrees of daylight and shadow
5- old roads with bad road lane
6- city roads are too much more challenging


### 3. Suggest possible improvements to your pipeline

my program is not really stable for video and doesn't detect very well, for example sometimes (especially in yellow one) the right lane jump to other lane of road, which are not relevant for this one. For the challenging video it is relly bad I've tried to tune the parameters for canny edge, mask border and Hough transformation, but unfortunately I couldn't improve it more.

[image2]: ./examples/Writeup_pics/road_example_3.jpg "road_example_3"


maybe using HSL or HSV images is better than RGB!