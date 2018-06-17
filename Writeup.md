# **Traffic Sign Recognition** 
## Writeup
**Build a Traffic Sign Recognition Project**
The goals / steps of this project are the following:
* Load the data set (see below for links to the project data set)
* Explore, summarize and visualize the data set
* Design, train and test a model architecture
* Use the model to make predictions on new images
* Analyze the softmax probabilities of the new images
* Summarize the results with a written report

### Data Set Summary & Exploration
#### 1. Provide a basic summary of the data set. In the code, the analysis should be done using python, numpy and/or pandas methods rather than hardcoding results manually.
I used the pandas library to calculate summary statistics of the traffic
signs data set:
* The size of training set is (39209, 32, 32, 3)
* The size of test set is (12630, 32, 32, 3)
* The shape of a traffic sign image is (32, 32, 3)
* The number of unique classes/labels in the data set is 43.
#### 2. Include an exploratory visualization of the dataset.
The exploratory visualization of the data set has been shown in the code. 

### Design and Test a Model Architecture
#### 1. Describe how you preprocessed the image data. What techniques were chosen and why did you choose these techniques? Consider including images showing the output of each preprocessing technique. Pre-processing refers to techniques such as converting to grayscale, normalization, etc. (OPTIONAL: As described in the "Stand Out Suggestions" part of the rubric, if you generated additional data for training, describe why you decided to generate additional data, how you generated the data, and provide example images of the additional data. Then describe the characteristics of the augmented training set like number of images in the set, number of images for each class, etc.)
* Converting to grayscale.
* Normalizing the data to the range (-1,1) - This was done using the line of code X_train_normalized = (X_train - 128)/128. The resulting dataset mean wasn't exactly zero, but it was reduced from around 82 to roughly -0.35. I chose to do this mostly because it was suggested in the lessons and it was fairly easy to do.
#### 2. Describe what your final model architecture looks like including model type, layers, layer sizes, connectivity, etc.) Consider including a diagram and/or table describing the final model.
Rumor has it that data augmentation is the single best method to increase accuracy of the model. Because several classes in the data have far fewer samples than others the model will tend to be biased toward those classes with more samples. I implemented augmentation by creating copies of each sample for a class (sometimes several copies) in order to boost the number of samples for the class to 800 (if that class didn't already have at least 800 samples). Each copy is fed into a "jitter" pipeline that randomly translates, scales, warps, and brightness adjusts the image. I sought to keep the parameters for these transformations relatively conservative and keep the sign in the image recognizable. This was by far the most laborious part of the project, and it takes quite some time to run the code。
#### 3. Describe how you trained your model. The discussion can include the type of optimizer, the batch size, number of epochs and any hyperparameters such as learning rate.
There are various aspects to consider when thinking about this problem:
* Neural network architecture
* Play around preprocessing techniques (normalization, rgb to grayscale, etc)
* Number of examples per label (some have more than others).
* Generate fake data.

### Test a Model on New Images
#### 1. Choose five German traffic signs found on the web and provide them in the report. For each image, discuss what quality or qualities might be difficult to classify.
I picked images from the orginal set. All those images includes no border. The images are picked ramdomly.
#### 2. Discuss the model's predictions on these new traffic signs and compare the results to predicting on the test set. At a minimum, discuss what the predictions were, the accuracy on these new predictions, and compare the accuracy to the accuracy on the test set.
The accuracy on thoese new predictions is about 75%. Compared to the accuracy on the test set, this is too low. It looks like the trained model is not good at recognizing numbes.
#### 3. Describe how certain the model is when predicting on each of the five new images by looking at the softmax probabilities for each prediction. Provide the top 5 softmax probabilities for each image along with the sign type of each probability.
From the plots we can find that the prediction of number 50 and 30 are completely wrong. And this can because of the preprocessed data lost too much information when dealing with numbers.






