**Vehicle Detection Project**
-----------------------------

 

### **Project highlights**

-   **Histogram of Oriented Gradients (HOG)** feature extraction on a labeled
    training set of images and train a classifier Linear SVM classifier

-   **Binned color features**, as well as **histograms of color**, appended to
    HOG feature vector.

-   Classifier used : SVM, Neural Network

-   Optionally i used also a **Convolutional Neural Network** instead of the
    **Histogram of Oriented Gradients**

-   **Sliding-window technique** and use your trained classifier to search for
    vehicles in images.

-   Estimate a bounding box for vehicles detected.

 

### **Output Video:**

**Here's a link to my video result ./project_video_output.mp4**

 

### **My implementation**

I used three different methodology in order to recognize the cars in the images.

 

1 - **Support Vector Machine**

As in the project lessons, I used a combinations of HOG features, Colors
histograms , and binned color features.

Then with a LinearSVC Support Vector machine, I have trained the classifier. The
classifier precision is on the paper 98% but when used on real “sliding windows”
, **there are lot of false positives** .

 

Keep in mind that the train images has not been augmented, and they contain the
entire object, while in the video using sliding windows, we are getting often
cropped parts of cars.

For example the yellow line on the asphalt sometimes get recognize as “car"

 

2 - **Neural Network**

As before for the feature recognition, but for the classifier I have used a
Neural Network.

The performance in this case is very good , there are not false positive, **but
the classifier precision is not as good as the Support Vector Machine**

 

3 - Convolutional Neural Network

The feature extraction is done in this case but the Network itself.

**Its much faster on the prediction , but obiously is very slow to train .**

The data are augmented with the Keras Image Processing library, using shifts,
zooms, and this meant that this network is **much better** at recognizing parts
of car , and not only the entire car\*\* as a car.\*\*

 

### Sliding windows.

Now, having a classifier that tells if in a portion of image there is or not a
car, we need do slide windows of **different dimensions** on the image:

 

![](write_md_images/Screen%20Shot%202017-11-26%20at%2020.12.35%20copy%202.png)

Having these list of windows, for each one i am applying the classifier to
recognize if the windows contains of not a part of a car

 

![](write_md_images/Screen%20Shot%202017-11-26%20at%2020.12.56%20copy.png)

I recorded the positions of positive detections in each frame of the video. From
the positive detections I created a heatmap and then thresholded that map to
identify vehicle positions. I then used `scipy.ndimage.measurements.label()` to
identify individual blobs in the heatmap. I then assumed each blob corresponded
to a vehicle. I constructed bounding boxes to cover the area of each blob
detected.

### Some example here

![](write_md_images/Screen%20Shot%202017-11-26%20at%2020.07.08.png)

### **FALSE POSITIVES**

I have implemented two further techniques:

1 - the averaging on the 3- previous frames, and discard of the boxes that are
**“ too much different"**

![](write_md_images/Screen%20Shot%202017-11-26%20at%2020.41.06.png)

 

2 - calculating the proportions of the width/height and discard all the boxes
that are not likely to contain a car

 

![](write_md_images/Screen%20Shot%202017-11-26%20at%2020.38.25%20copy.png)

### **Comparison between the 3 different classifier:**

**Support Vector Machine**

Lot of false positive

![](write_md_images/Screen%20Shot%202017-11-26%20at%2020.12.56%20copy.png)

But excluding the false positive the right boxes **are well centered:**

![](write_md_images/classifier%20SVM.png)

 

**Convolutional Neural Network**

In the Conv Net there are no false positive, but the centering is not the best:

![](write_md_images/CNN%20boxes%20copy.png)

![](write_md_images/classifier%20CNN.png)

**Neural Network**

This network is the worse.

On the paper the accuracy is good, BUT ONLY ON THE PAPER:

![](write_md_images/neural%20network%20accuracy%20copy.png)

Mainly because it has overfitted the trainin set, and now is able to recognize
only window containing the entire car, and not able to recognize part of the
car.**\*\* One solution can be to augment the training set, introducing shifs.
zoom, little rotations, and so on...but I haven’t done it\*\***

![](write_md_images/neural%20network%20copy.png)

 

**Test images with the 3 different classifier:**
------------------------------------------------

 

**CNN image 1**

![](output_images_cnn/test1.jpg)

**CNN image 2**

![](output_images_cnn/test2.jpg)

**CNN image 3**

![](output_images_cnn/test3.jpg)

**CNN image 4**

![](output_images_cnn/test4.jpg)

**CNN image 5**

![](output_images_cnn/test5.jpg)

 

**SVM image1**

![](output_images_svm/test1.jpg)

**SVM image2**

![](output_images_svm/test2.jpg)

**SVM image3**

![](output_images_svm/test3.jpg)

**SVM image4**

![](output_images_svm/test4.jpg)

**SVM image5**

![](output_images_svm/test5.jpg)

 

**HOG+ NN image1**

![](output_images_hog_nn/test1.jpg)

**HOG+ NN image2**

![](output_images_hog_nn/test2.jpg)

**HOG+ NN image3**

![](output_images_hog_nn/test3.jpg)

**HOG+ NN image4**

![](output_images_hog_nn/test4.jpg)

**HOG+ NN image5**

![](output_images_hog_nn/test5.jpg)

 

**Discussion**
--------------

I have experimented different classifiers.

I have expected the **CNN** to be the best, but sometimes happens something like
this:

![](write_md_images/Screen%20Shot%202017-11-26%20at%2020.00.00.png)

While is quite good but it **is not perfect.**

One thing to note is that the **Convolutional Neural Network** is able to say “
its a car” , **having a cropped image window with only some parts of the car**.

But this gives too many boxes recognized as correct around the car, and the
heatmap is making a box a little bit **too bigger**

I have experimented different thresholds in the heatmap, and I have ended
calculating the average of the non-zero elements , and moltiplying this result
for 0.7
