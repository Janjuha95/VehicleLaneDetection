# VehicleLaneDetection
Vehicle Detection and Lane Segmentation using Deep Learning

Step 1 - Identify Lanes : 

1. Issues : lane lines colors can vary , lighting conditions vary
2. Methodology :  develop software pipeline for series of images. after testing on images employ
model for lane detection in video stream.

pipeline consists of 5 major steps excluding reading and writing the image


Load image
convert to grayscale from RBG
gaussian blur ( to remove noise or gradients )
canny edge detection and binary image produced
extract lanes and remove irrelevant edges
merge identified lane lines image with original image
merged lines not continuous ; so modify drawlines() function to make lines continous
left lane - positive slope
right lane - negative slope
Flat lines having slope below absolute value of 0.5 are discarded.

store points for respective left and right lanes, a linear curve fit (degree 1) using polyfit() function done
to obtain the slope and intercept of left and right lanes. 

x coordinates are found for respective y top and btm coordinates (user defined) using the lane equations for both lanes. 
we now have starting and ending coordinates for both left and right lane. 

now lines drawn using cv2.line() function to connect these points and the image is merged with the original image as before 

improvement  : 

identify lanes using perspective transformations 
sliding window approach se lines ko fit kr skte h after perspective transformations
map.color se lines ke beech mei color fill se better lane identification kr skte h



Step 2 - Vehicle Detection and Tracking


Perform a Histogram of Oriented Gradients (HOG) feature extraction on a labeled training set of images
train a classifier Linear SVM classifier

sliding-window technique and trained classifier to search for vehicles in images.

Run pipeline on a video stream and create a heat map of recurring detections frame by frame to reject outliers and follow detected vehicles.

Estimate a bounding box for vehicles detected.
