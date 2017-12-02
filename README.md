# Self-Drive

A Stimulated and User Data Dependent, Car Stimulation, Where Used Tranning Data is used to Train Model.

## Overview
###  How to Make a Self-Driving Car

Udacity recently open sourced their self driving car simulator originally built for SDND students.And I've Used it here to built it.

![Alt text](https://github.com/vedicnis/Self-Drive/blob/master/sim_image.png "Optional Title")

* built in Unity (free game making engine https://unity3d.com/)
* add new tracks, change prebuilt scripts like gravity acceleration easily

``` 
[Code](https://github.com/udacity/self-driving-car-sim ) - The Udacity recently open sourced self driving car simulator.

```

## Data Generation 

- records images from center, left, and right cameras w/ associated steering angle, speed, throttle and brake. 
- saves to CSV

## Training Mode - Behavioral cloning

We use a 9 layer convolutional network, based off of Nvidia's
end-to-end learning for self driving car paper. 72 hours of driving data was collected in all sorts of conditions from human drivers


#### Hardware design:

![alt text](https://github.com/vedicnis/Self-Drive/blob/master/data-collection-system.png "Logo Title Text 1")

- 3 cameras
-  The steering command is obtained by tapping into the vehicle’s Controller Area Network (CAN) bus.
- Nvidia's Drive PX onboard computer with GPUs

In order to make the system independent of the car geometry, the steering command is 1/r, where r is the turning radius in meters.  1/r was used instead of r to prevent a singularity when driving straight (the turning radius for driving straight is infinity). 1/r smoothly transitions through zero from left turns (negative values) to right turns (positive values).


#### Software Design (supervised learning!) :

![alt text](https://github.com/vedicnis/Self-Drive/blob/master/training.png "Logo Title Text 1")

Images are fed into a CNN that then computes a proposed steering command. The proposed command is compared to the desired command for that image, and the weights of the CNN are adjusted to bring the CNN output closer to the desired output. The weight adjustment is accomplished using back propagation

Eventually, it generated steering commands using just a single camera

![alt text](https://github.com/vedicnis/Self-Drive/blob/master/inference.png "Logo Title Text 1")

## Testing mode

We will just run autonomous mode, then run our model and the car will start driving

## Dependencies

``` 
* [numpy](http://www.numpy.org/ ) - NumPy is the fundamental package for scientific computing with Python.
* [matplotlib](https://matplotlib.org/ ) - Matplotlib is a Python 2D plotting library which produces publication quality figures.
* [scikit-learn](http://scikit-learn.org/stable/ ) - Simple and efficient tools for data mining and data analysis.



