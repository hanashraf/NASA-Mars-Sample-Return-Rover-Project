# NASA-Mars-Sample-Return-Rover-Project
In this project, we’ll do computer vision for robotics. We are going to build a Sample &amp; Return Rover in simulation. Mainly, we’ll control the robot from images streamed from a camera mounted on the robot. The project aims to do autonomous mapping and navigation given an initial map of the environment.

## The steps of this project are the following: 
1) Define source and destination points for perspective transform
2) Apply perspective transform
3) Apply color threshold to identify navigable terrain/obstacles/rock samples
4) Update Rover.vision_image (this will be displayed on left side of screen)
5) Convert map image pixel values to rover-centric coords
6) Convert rover-centric pixel values to world coordinates
7) Update Rover worldmap (to be displayed on right side of screen)
8) Convert rover-centric pixel positions to polar coordinates



