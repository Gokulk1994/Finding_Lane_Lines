# Finding_Lane_Lines
This project identifies straight lane lines in a highway

**Objective:**

The main aim of the project is to identify the left and right lanes in a video. The identified lanes shall be averaged and extrapolated and a final solid line shall be drawn over the actual image.

**Pipeline:**

1. Change the Image from RGB to HSV.
2. Choose the colour selection based on the lane colour in HSV mode. Choose yellow and white colour and mask it with the actual image.
3. The noise was removed and image was smoothened using Gaussian blur function.
4. The edges in the images was detected using Canny edge detection.
5. The region in which lanes are present are masked using a polygon mask.
6. The Lines inside the masked region are identified using Hough Transform function.
7. Slope and Intercept was calculated for each line and Left and right lanes are separated using the slope value. If slope is negative it is considered left lane and vice versa.
8. The Identified lines are then averaged and a final slope and intercept was calculated separately for left and right lanes.
9. With the help of slope, intercept and older data, the lines were extrapolated and final points to draw lanes are identified.
10. The identified lanes are added with the actual images in the video. 

**Output:**

**Potential Shortcomings:**

1. The slope and intercept for the final lanes are obtained from averaging all the slopes and intercepts from all detected lines using Hough transform, as well as from last slope and intercept. When there is a huge difference in the slopes of lines, the average may deviate to a reasonable extent which could create jitter in the lanes due to variance in slope of successive frames from the video
2. The tuning was done with respect to the current frames and lighting conditions, it may have an impact with different types of roads

**Improvements:**

1. The region of interest was made as constant for different size of the images. This algorithm shall be improved to detect the region by itself using methods such as sliding window method, so that the pipline shall be used for all type of roads and camera angles.
2. The jitter in the displayed lanes can be reduced by taking into account of the all previous lane points instead of only the slope and intercept.
3. Tuning of Hough transform function plays a major role in detecting the lanes. Executing trial and error method takes huge time and effort. We may even fail to identify a best fit and would have satisfied with a near fit. Hence Tuning process shall be automated using Machine learning algorithms.
