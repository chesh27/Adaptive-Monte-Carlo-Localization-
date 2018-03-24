# Adaptive-Monte-Carlo-Localization-
## Abstract

Two different mobile robot models are described and evaluated for performance in a simulated environment. Both simulations are run using Gazebo and RViz. The robots use Adaptive Monte Carlo Localization and the move-base plug in for navigation to successfully arrive at a goal that was either pre-determined or user-defined in real time.

[image_1]: ./images/overview.png
![alt text][image_1]

## Introduction

One of the most integral, yet challenging components of a mobile robot is the ability to navigate through space. In order to successfully navigate, a robot must accomplish 4 sequential tasks. It must first perceive the world around it using sensors and then interpret sensor data to draw meaningful information. Second, the robot must be able to efficiently localize itself, or determine its position and pose within a mapped environment. The third and fourth tasks are cognition and and motor control – the robot must decide its next action and ultimately actuate movement in the desired direction.

In this paper, both Kalman Filters and the Monte Carlo Localization algorithms are explored, and ultimately the Adaptive MCL is implemented to localize two different mobile robots in simulation. Through experimentation, the various parameters of the algorithm are tuned to optimize localization. The images below show the benchmark model, the personal model and the maze they both navigated. 

[image_2]: ./images/benchmark.png
![alt text][image_2]

[image_3]: ./images/personal.png
![alt text][image_3]

[image_4]: ./images/maze.png
![alt text][image_4]

## Simulations 

Simulations were carried out in a Gazebo environment with the use of RViz for visualization of different aspects of the mobile robot and world. The following sections will discuss the performance of each robot individually, in addition to a description of the robot model design, packages used, and the parameters chosen for the robot to properly localize itself. The performance of the robots is evaluated through simulations, run using Gazebo and Rviz.

The project was conducted on an Ubuntu Virtual Machine with ROS installed. The code below uses 3 separate terminals to launch the simulation and navigate to the goal:

```
# Benchmark Model
$ roslaunch udacity_bot udacity_world.launch
$ roslaunch udacity_bot amcl.launch
$ rosrun udacity_bot navigation_goal
```

```
# Personal Model
$ roslaunch chesh_bot chesh_world.launch
$ roslaunch chesh_bot amcl.launch
$ rosrun chesh_bot navigation_goal
```

## Results 
### Benchmark Model - udacity_bot
The benchmark model was able to successfully reach the goal position in about 24 minutes without any major deviations from the global path. Notably, the particle filter converges within the first minute and remains fairly consistent throughout the robot's path. The images below display the progress that udacity\_bot made and the path it took to get to the navigation goal. 

[image_5]: ./images/b1.png
![alt text][image_5]

[image_6]: ./images/b2.png
![alt text][image_6]

[image_7]: ./images/b3.png
![alt text][image_7]

### Personal Model - chesh_bot
Chesh_bot reached the navigation goal in about minutes. During the course of navigation. Similar to udacity bot, it was fairly accurate in following the global path while it was in the confined zone, but once it got to a more open area it deviated from the global path. Particle filters here also converged within the first minute. The images below display the progress that chesh_bot made and the path it took to get to the navigation goal.

[image_8]: ./images/p1.png
![alt text][image_8]

[image_9]: ./images/p2.png
![alt text][image_9]

[image_10]: ./images/p3.png
![alt text][image_10]

[image_11]: ./images/p4.png
![alt text][image_11]

## Discussion

While both robots reached the navigation goal, the bench- mark model clearly took a more direct path and achieved the goal in the time. Given that chesh bot is heavier than udacity bot, the slower motion and greater deviation from the path was expected.
The placement of the laser rangefinder likely had an effect on the performance of chesh bot, perhaps because it did not provide enough accurate information for localization. However, this is yet to be tested rigorously. One can tune the position of the Hokuyo holding all else constant in order to test this.

## Conclusion / Future Work

The localization results are reasonable for both models. The benchmark model as well as the personal model show convergence of the particle filters within the first half minute of localization, and remain clustered throughout the path, indicating that AMCL is working effectively. The bench- mark model reaches the goal in about 26 minutes while the personal model takes about 35 minutes. The benchmark model follows a fairly smooth path throughout its journey. The personal model follows a smooth path when bounded by walls, but deviates considerably in open space.
The project achieved its goals. However, there is great scope.

for improvement. One could tune the parameters further for the personal model to ensure it reaches the goal in a more straightforward manner. It would also be very inter- esting to deploy the models on hardware and apply it to a range of commercial products. For example, medical nano- robots could exploit localization and navigation tools to efficiently navigate the bloodstream and provide life-saving medication. The possibilities for future work in this field are virtually endless.
