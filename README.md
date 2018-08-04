# Semantic-Segmentation
Udacity Self-Driving NanoDegree Term 3 Project on Semantic Segmentation

## Project: Semantic-Segmentation [![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)

Overview
---
  This project implements semantic segmentation for Udacity's Self Driving Car Nanodegree using a fully convolutional neural network. The network comprises of an encoder based on VGG-16 model, and a decoder based on transposed convolutions, 1x1 convolutions and skip-layer connections.

Code changes
---
For this project I made the following changes to the starter code.

__*main.py*__

1. I modified the _load_vgg_ method to return the tensors associated with the input image, and the outputs of layer 3, 4 and 7.
2. I modified the _layers_ method to implement the decoder for the fully convolutional network. The topology of the full network is shown below.

![Network Graph](https://github.com/calvinhobbes119/Semantic-Segmentation/blob/master/Network_Graph.png)

3. I implemented the _optimize_ method to compute the total loss which comprises of both the cross-entropy loss and L2 regularization loss. The training operation is performed by an Adam Optimizer with a tuning hyperparameter of 0.0001.
4. Finally, I implemented the _train_nn_ method to initalize a TensorFlow session, and perform SGD using a minibatch size of 5 samples, and 50 training epochs. I also experimented with 10 and 25 epochs, but settled on 50 epochs based on performance. The total loss for the final selection of minibatch size and epochs is shown below.

![Network Loss](https://github.com/calvinhobbes119/Semantic-Segmentation/blob/master/Network_Loss.png)

__*Results*__

The results of the Path Planning project demonstrating the car moving in autonomous mode around the Unity simulator track are shown below. As shown in the video, the path planner satisfies the following criteria:

1. The ego car drives 4.32 miles without incidents involving exceeding acceleration/jerk/speed, collision, or driving outside of the lanes.
2. The car drives below the speed limit and also the car isn't driving much slower than speed limit unless obstructed by traffic.
3. The car does not exceed a total acceleration of 3 m/s^2 and a jerk of 3 m/s^3.
4. The car performs smooth lane changes within 3 seconds and the vehicle stays within the 3 lanes on the right hand side of the road.
5. The car is able to smoothly change lanes when it makes sense to do so, such as when behind a slower moving car and an adjacent lane is clear of other traffic.

[![Path_Planning_Project](https://github.com/calvinhobbes119/Path-Planning-Project/blob/master/Untitled.png)](https://youtu.be/6ydnQEybQac)
