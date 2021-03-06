# CarND-Path-Capstone-Project

[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)



<p align="center">
<img src="mygif.gif" width = "600" />
</p>


Overview
---


In this project vehicle drives in a simulation environment autonomously without human intervention. Plus, the vehicle has to stop on the traffic signals. The fundamental codes used in this project is based on Capstone project walkthrough at Udacity Self Driving Cars online course.


Pipeline
---


*The overall pipeline along with the results will be described here!*

<br>

I. Base of the source code that I've used for this project is inspired by the walkthrough session hosted by Aaron and Steven.


</br>


II. The main source codes are inside```CarND-CapStone/ros/src/``` folder. Most of the blocks and parts have been provided by Udacity and we just had to fill up specific functionalities and make sure that the car can go around route and stop at the traffic signals. The codes that has been modified and added in this project incude: 
- ```CarND-CapStone/ros/src/waypoint_updater/waypoint_updater.py```
- ```CarND-CapStone/ros/src/twist_controller/twist_controller.py```
- ```CarND-CapStone/ros/src/tl_detector/tl_detector.py```
- ```CarND-CapStone/ros/src/tl_detector/light_classification/tl_classifier.py```
- ```CarND-CapStone/train.py```


</br>


III. Here I try to talk about some of the codes and explain their purpose.

- ```CarND-CapStone/ros/src/waypoint_updater/waypoint_updater.py``` the waypoint_updater subscribes to topics ```/base_waypoints``` , ```/current_pose``` and publishes a list of waypoints ```/final_waypoints```.

- ```CarND-CapStone/ros/src/twist_controller/dbw_node.py``` Drive by wire node which subscribes to ```/twist_cmd``` and uses throttle, brake, and steering commands proportionately. 

- ```CarND-CapStone/ros/src/tl_detector/tl_detector.py``` This nodes subscribes to nodes such as ```/base_waypoints```, ```current_pose```, ```/image_color```, ```/vehicle/traffic_lights``` and publishes indexes of the waypoints for nearest upcoming red light's stop line to a single topic ```/traffic_waypoint```.

- ```CarND-CapStone/train.py``` was used in order to train the traffic light classifier. This code is provide by tensorflow objection detection <a href="https://github.com/tensorflow/models/tree/master/research/object_detection">API</a>. I used the data from <a href="https://github.com/alex-lechner/Traffic-Light-Classification">here</a>, in order to train the traffic light classifier. I used Amazon AWS in order to train the model. The output model was saved as ```frozen_inference_graph.pb``` in order to be used in the ```tl_classifier.py``` for the prediction purpose.


IV. Make sure include the ```dbw_mkz_msgs``` folder inside ```src``` folder when you are running the code. It is provided by Udacity as part of the project.

V. Lastly, be sure for your system to have at least a 5 core cpu and a good GPU specially when you turn on the camera on the simulator. The car runs smoothly around the block in autonomous mode without camera turned on. But when you turn on the camera, the car might steer off the road if you're system hardware are not strong enough.  

</br>
<br></br>