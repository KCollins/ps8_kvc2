# ps8_kvc2
This package is based on the package example_sensor_guided_motion, from the cwru_baxter repository. The original code takes selected points in RViz, computes the centroid and positions Baxter's tool coordinate frame such that the origin is coincident with the table top and the tool frame Z axis is pointing into the table top, normal to the surface; i.e., Baxter's hand is above the table at the selected spot. This version adds code for Baxter to move his hand back and forth, as though wiping the table. Apart from name changes, only the .cpp file has been modified, as marked by comments blocking off the modified section in the code.


## Example usage in simulation
`roslaunch cwru_baxter_sim baxter_world.launch`. Wait for the "Gravity compensation turned off" message.
`roslaunch ps8_kvc2  ps8_kvc2_baxter_sensor_guided_motion.launch`

In the RViz sidebar, set the PCL2 cloud to display kinect/depth/points.
Select points by clicking the "Publish Selected Points" button (this is a plugin, so make sure you have it downloaded), then clicking and dragging to select points on the table, then hitting "Select." Baxter's arm will then move from prepose and swab the table. 


Watch out for the following; kinect transform is different for Gazebo vs real Baxter
`roslaunch cwru_baxter_sim kinect_xform.launch`


 ## Future work   
A possible extension: Have the program look at the selected points and determine the width of the sweep and number of repetitions based on the standard deviation. For a large region, Baxter could execute a few wide sweeps. For a small selected region, Baxter could scrub an area with many repetitions of small strokes. 
