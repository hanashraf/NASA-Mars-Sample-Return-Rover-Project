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

### 1) Define source and destination points for perspective transform
-Define calibration box in source (actual) and destination (desired) coordinates
-These source and destination points are defined to warp the image to a grid where each 10x10 pixel square represents 1 square meter
-The destination box will be 2*dst_size on each side
-Set a bottom offset to account for the fact that the bottom of the image
### 2) Apply perspective transform
-This is done though the perspect_transform function
### 3) Apply color threshold to identify navigable terrain/obstacles/rock samples
-Ignore half of the image as bad data
-Navigable[0:int(navigable.shape[0]/2), :] = 0
-Obstacles are simply navigable inverted
-Ignore half of the image as bad data
-Obstacles[0:int(obstacles.shape[0]/2),:] = 0
-Identify the rock
-Convert BGR to HSV
-Threshold the HSV image to get only upper_yellow colors
### 4) Update Rover.vision_image (this will be displayed on left side of screen)
-Example: Rover.vision_image[:,:,0] = obstacle color-thresholded binary image
     Rover.vision_image[:,:,1] = rock_sample color-thresholded binary image
     Rover.vision_image[:,:,2] = navigable terrain color-thresholded binary image
### 5) Convert map image pixel values to rover-centric coords
-Navigable_x_world, navigablerover_coords(binary_img)
### 6) Convert rover-centric pixel values to world coordinates
### 7) Update Rover worldmap (to be displayed on right side of screen)
-Example: Rover.worldmap[obstacle_y_world, obstacle_x_world, 0] += 1 <br />
     Rover.worldmap[rock_y_world, rock_x_world, 1] += 1 <br />
     Rover.worldmap[navigable_y_world, navigable_x_world, 2] += 1
### 8) Convert rover-centric pixel positions to polar coordinates
-Update Rover pixel distances and angles
     Rover.nav_dists = rover_centric_pixel_distances
     Rover.nav_angles = rover_centric_angles


