Vehicle Detection
=================

<http://www.udacity.com/drive>

In this project, your goal is to write a software pipeline to detect vehicles in
a video

Project output:

-   **project_video_output_cnn.mp4** using Conv Net

-   **project_video_output_hog_nn.mp4** using Neural Network

-   **project_video_output_svm.mp4** using Support Vector Machine

 

Check also the detailed **writeup.md** of the project.

 

### **Project highlights**

-   **Histogram of Oriented Gradients (HOG)** feature extraction on a labeled
    training set of images and train a classifier Linear SVM classifier

-   **Binned color features**, as well as **histograms of color**, appended to
    HOG feature vector.

-   Classifier used : SVM, Neural Network

-   Experimental use of  **Convolutional Neural Network** instead of the
    **Histogram of Oriented Gradients**

-   **Sliding-window technique** and use your trained classifier to search for
    vehicles in images.

-   Estimate a bounding box for vehicles detection.

 

The training data used to train the classifiers, for
[vehicle](https://s3.amazonaws.com/udacity-sdc/Vehicle_Tracking/vehicles.zip)
and
[non-vehicle](https://s3.amazonaws.com/udacity-sdc/Vehicle_Tracking/non-vehicles.zip)
comes from:

[GTI vehicle image
database](http://www.gti.ssr.upm.es/data/Vehicle_database.html)

[KITTI vision benchmark suite](http://www.cvlibs.net/datasets/kitti/)

 

### **Dependencies**

**Anaconda environment:**

-   [CarND Term1 Starter
    Kit](https://github.com/udacity/CarND-Term1-Starter-Kit)

    The lab enviroment can be created with CarND Term1 Starter Kit.
    Click [here](https://github.com/udacity/CarND-Term1-Starter-Kit/blob/master/README.md) for
    the details.

     

**shapely** - pip install shapely

 

### **Folders list:**

**output_images_cnn** images obtained applying the **Pipeline and CNN
classifier** on single test images

**output_images_hog_nn** images obtained applying the **Pipeline and Hog+ Neural
Network classifier** on single test images

**output_images_svm** images obtained applying the **Pipeline and CNN
classifier** on single test images

 

**test_images** some test images provided by Udacity

**test_images2** test images extracted frm the test_video.mp4

**test_images_project** test images extracted from project_video_output.mp4

**train_data** car and non-car training images

**write_md_images** images for the writeup.md

 

### **Files list**

**car_detection_classifier.pkl** SVM classifier saved to disk

**keras_model.h5** Neural Network saved to disk

**kerasCNN_model.h5** Convolutional Neural Network saved to disk

**cars_detection.ipynb** iPython Notebook containing the program

 

**project_video_output_cnn.mp4** the processed video ( **CNN** as classifier )

**project_video_output_hog_nn.mp4** the processed video using Neural Network (
**Hog** as features extractor )

**project_video_output_svm.mp4** the processed video using **SVM** classifier

 

**project_video.mp4** project video provided by Udacity

**test_video.mp4** test video provided by udacity

 

**writeup.md** containing the explanation of the pipeline used

**X_scaler.pkl** the scaler used for the HOG features ( also color and spatial )
scaling.

 

 

 

 

 
