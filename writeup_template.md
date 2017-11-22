**Vehicle Detection Project**
-----------------------------

The goals / steps of this project are the following:

-   Perform a Histogram of Oriented Gradients (HOG) feature extraction on a
    labeled training set of images and train a classifier Linear SVM classifier

-   Optionally, you can also apply a color transform and append binned color
    features, as well as histograms of color, to your HOG feature vector.

-   Note: for those first two steps don't forget to normalize your features and
    randomize a selection for training and testing.

-   Implement a sliding-window technique and use your trained classifier to
    search for vehicles in images.

-   Run your pipeline on a video stream (start with the test_video.mp4 and later
    implement on full project_video.mp4) and create a heat map of recurring
    detections frame by frame to reject outliers and follow detected vehicles.

-   Estimate a bounding box for vehicles detected.

[Rubric](https://review.udacity.com/#!/rubrics/513/view) Points
---------------------------------------------------------------

### Video Implementation

#### 1. Provide a link to your final video output. Your pipeline should perform reasonably well on the entire project video (somewhat wobbly or unstable bounding boxes are ok as long as you are identifying the vehicles most of the time with minimal false positives.)

Here's a [link to my video result](./project_video.mp4)

#### 2. Describe how (and identify where in your code) you implemented some kind of filter for false positives and some method for combining overlapping bounding boxes.

I recorded the positions of positive detections in each frame of the video. From
the positive detections I created a heatmap and then thresholded that map to
identify vehicle positions. I then used `scipy.ndimage.measurements.label()` to
identify individual blobs in the heatmap. I then assumed each blob corresponded
to a vehicle. I constructed bounding boxes to cover the area of each blob
detected.

Here's an example result showing the heatmap from a series of frames of video,
the result of `scipy.ndimage.measurements.label()` and the bounding boxes then
overlaid on the last frame of video:

### Here are six frames and their corresponding heatmaps:

![alt text](./examples/bboxes_and_heat.png)

### Here is the output of `scipy.ndimage.measurements.label()` on the integrated heatmap from all six frames:

![alt text](./examples/labels_map.png)

### Here the resulting bounding boxes are drawn onto the last frame in the series:

![alt text](./examples/output_bboxes.png)

### Discussion

#### 1. Briefly discuss any problems / issues you faced in your implementation of this project. Where will your pipeline likely fail? What could you do to make it more robust?

Here I'll talk about the approach I took, what techniques I used, what worked
and why, where the pipeline might fail and how I might improve it if I were
going to pursue this project further.
