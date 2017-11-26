Vehicle Detection
=================

<http://www.udacity.com/drive>

In this project, your goal is to write a software pipeline to detect vehicles in
a video

**project_video_output.mp4** is the output of the project.

Check also the detailed **writeup.md** of the project.

 

### **Project highlights**

-   **Histogram of Oriented Gradients (HOG)** feature extraction on a labeled
    training set of images and train a classifier Linear SVM classifier

-   **Binned color features**, as well as **histograms of color**, appended to
    HOG feature vector.

-   Classifier used : SVM, Neural Network

-   Optionally i used also a **Convolutional Neural Network** instead of the
    **Histogram of Oriented Gradients**

-   **Sliding-window technique **and use your trained classifier to search for
    vehicles in images.

Estimate a bounding box for vehicles detected.

 

The training data used to train the classifiers,  for
[vehicle](https://s3.amazonaws.com/udacity-sdc/Vehicle_Tracking/vehicles.zip)
and
[non-vehicle](https://s3.amazonaws.com/udacity-sdc/Vehicle_Tracking/non-vehicles.zip)
:

[GTI vehicle image
database](http://www.gti.ssr.upm.es/data/Vehicle_database.html)

[KITTI vision benchmark suite](http://www.cvlibs.net/datasets/kitti/)

 

### **Folders list:**

**output_images**  images obtained applying the Pipeline on single test images

**test_images**      some test images provided by Udacity

**test_images2    **test images extracted frm the test_video.mp4

**test_images_project**  test images extracted from project_video_output.mp4

**train_data ** car and non-car training images

**write_md_images** images for the writeup.md

 

### **Files list**

**car_detection_classifier.pkl **SVM classifier saved to disk

**keras_model.h5 ** Neural Network saved to disk

**kerasCNN_model.h5** Convolutional Neural Network saved to disk

**cars_detection.ipynb ** iPython Notebook containing the program

 

**project_video_output.mp4** the processed video

**project_video.mp4** project video provided by Udacity

**test_video.mp4 **test video provided by udacity

 

**writeup.md ** containing the explanation of the pipeline used

**X_scaler.pkl ** the scaler used for the HOG features  ( also color and spatial
) scaling.

 

 

 

 

 
