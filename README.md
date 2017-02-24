#**Finding Lane Lines on the Road** 


<img src="./pipeline_pictures/Final_image.jpg" width="480"  />

Overview
---

When we drive, we use our eyes to decide where to go.  The lines on the road that show us where the lanes are act as our constant reference for where to steer the vehicle.  Naturally, one of the first things we would like to do in developing a self-driving car is to automatically detect lane lines using an algorithm.



The Project
---


**Step 1:** Focus on potintial areas using color segmentation

Mainly most of lanes are white or yellow so as initial step filter these colors. 
Transforming image to HSV space and filter only yellow and white colored pixel and mask the rest of picture.
For this step we define range of possible yellow and white values in HSV space and using "inrange" function from opencv lib. to filter out the rest of colors.

<img src="./pipeline_pictures/yellow_white_masking.jpg" width="480"/>


**Step 2:** closing the gaps

Filter the image and connect any missy areas will inhance our edge detection algorithm. for this we used morphological "closing" operator from opencv lib. 

<img src="./pipeline_pictures/closing_operator.jpg" width="480"/>


**Step 3:** Edge Detection  

for edge detection, canny edge operater is used. good tunning minimum and maximum thershold parameters of canny operator will inhance outputed edges.

<img src="./pipeline_pictures/canny_operator.jpg" width="480"/>

**Step 4:** Focus on lanes` edges 

By croping only a Region of Interset where lanes of Ego car is moving in, while reduce any potintial noise data for lane lines detection

<img src="./pipeline_pictures/ROI.jpg" width="480"  />

Cropped Edges 

<img src="./pipeline_pictures/masked_canny_edges.jpg" width="480"  />

**Step 5:** Line Segments Detection
Using Hough Transform of edges outputed from Canny operator will results in finding most suitable line segmants in image. 

<img src="./pipeline_pictures/Hough_Lines.jpg" width="480"  />

**Step 6:** Connecting Lane Lines


<img src="./pipeline_pictures/Final_image.jpg" width="480" />

Final Output of Lane Finding Pipeline
---

![](./pipeline_pictures/yellow.gif)
