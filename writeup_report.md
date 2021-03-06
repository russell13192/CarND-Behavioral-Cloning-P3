# **Behavioral Cloning** 

---

**Behavioral Cloning Project**

The goals / steps of this project are the following:
* Use the simulator to collect data of good driving behavior
* Build, a convolution neural network in Keras that predicts steering angles from images
* Train and validate the model with a training and validation set
* Test that the model successfully drives around track one without leaving the road
* Summarize the results with a written report


[//]: # (Image References)


[image1]: images/network_architecture.png "Network Architecture"
[image2]: images/left.jpg "Left Camera"
[image3]: images/center.jpg "Center Camera"
[image4]: images/right.jpg "Right Camera"
## Rubric Points
### Here I will consider the [rubric points](https://review.udacity.com/#!/rubrics/432/view) individually and describe how I addressed each point in my implementation.  

---
### Files Submitted & Code Quality

#### 1. Submission includes all required files and can be used to run the simulator in autonomous mode`

My project includes the following files:
* model.py containing the script to create and train the model
* drive.py for driving the car in autonomous mode
* model.h5 containing a trained convolution neural network 
* writeup_report.md or writeup_report.pdf summarizing the results

#### 2. Submission includes functional code
Using the Udacity provided simulator and my drive.py file, the car can be driven autonomously around the track by executing 
```sh
python drive.py model.h5
```


#### 3. Submission code is usable and readable

The model.py file contains the code for training and saving the convolution neural network. The file shows the pipeline I used for training and validating the model, and it contains comments to explain how the code works.

### Model Architecture and Training Strategy

#### 1. An appropriate model architecture has been employed

I elected to implement the Convolutional Neural Network as described in Nvidia's "End To End Learning For Self-Driving Cars" research paper [here](https://arxiv.org/pdf/1604.07316.pdf). I feed the network in an input shape of (160,320,3) and the entire network architecture is a 9 layer network that consists of 9 layers with 5 Convolutional Layers and 3 Fully Connected Layers.

#### 2. Attempts to reduce overfitting in the model

I initially had a dropout of 0.5 in my model, but after some experimentation I elected to not implement dropout as I found the results of eliminating dropout to be more stable.

The model was trained and validated on different data sets to ensure that the model was not overfitting. The model was tested by running it through the simulator and ensuring that the vehicle could stay on the track.

#### 3. Model parameter tuning


* I used an Adam optimizer with a default learning rate

#### 4. Appropriate training data

Training data was chosen to keep the vehicle driving on the road. I used a combination of center lane driving, recovering from the left and right sides of the road to train the model in recovery behavior.

For details about how I created the training data, see the next section. 

### Model Architecture and Training Strategy

#### 1. Solution Design Approach

The overall strategy for deriving a model architecture was to 

My first step was to use a convolution neural network model similar to the ... I thought this model might be appropriate because ...

In order to gauge how well the model was working, I split my image and steering angle data into a training and validation set. I found that my first model had a low mean squared error on the training set but a high mean squared error on the validation set. This implied that the model was overfitting. 

To combat the overfitting, I modified the model so that ...

Then I ... 

After training the model for ten epochs, I ran the model using the provided drive.py script, with a sligh modification of setting the Max Speed to 25 (as opposed to the default of 9) to try and see the overall stability of my model and its ability to react to real-time conditions.

At the end of the process, the vehicle is able to drive autonomously around the track without leaving the road.

#### 2. Final Model Architecture

The final model architecture (model.py lines 18-24) consisted of a convolution neural network with the following layers and layer sizes ...

Here is a visualization of the architecture 

![alt text][image1]

#### 3. Creation of the Training Set & Training Process

In capturing training data I tried to maintain the vehicle in the center of the lane as much as possible. In addition I also captured recovery data, in moving the vehicle from both the far right and far left to the center of the lane. This proved to be critical as there was an area of the track that confused the network and caused it to veer off on several occassions. 

![alt text][image2] ![alt text][image3]![alt text][image4]

After the collection process, I had X number of data points. I then preprocessed this data by ...


I finally randomly shuffled the data set and put Y% of the data into a validation set. 

I used this training data for training the model. The validation set helped determine if the model was over or under fitting. The ideal number of epochs was Z as evidenced by ... I used an adam optimizer so that manually training the learning rate wasn't necessary.
