# Data Modeling with Postgres Project Starter Code

The objective of this project is to apply data modeling with Postgres and build an ETL pipeline using Python.

<!--more-->

[//]: # (Image References)

[image1]: ./images/HS_Launch1.jpg "./Launch.sh"
[image2]: ./images/HS_Launch2.jpg "./Launch.sh"
[image3]: ./misc_images/HS_Gazebo.jpg "gazebo MyWorld.world"
[image4]: ./misc_images/HS_Test_Slam1.jpg "./test_slam.sh"
[image5]: ./misc_images/HS_Test_Slam2.jpg "./test_slam.sh"
[image6]: ./misc_images/HS_Wall_Follower1.jpg "./wall_follower.sh"
[image7]: ./misc_images/HS_Wall_Follower2.jpg "./wall_follower.sh"
[image8]: ./misc_images/HS_Test_Navigation1.jpg "./test_navigation.sh"
[image9]: ./misc_images/HS_Test_Navigation2.jpg "./test_navigation.sh"
[image10]: ./misc_images/HS_Test_Navigation3.jpg "./test_navigation.sh"
[image11]: ./misc_images/HS_Pick_Objects1.jpg "./pick_objects.sh"
[image12]: ./misc_images/HS_Pick_Objects2.jpg "./pick_objects.sh"
[image13]: ./misc_images/HS_Add_Markers1.jpg "./add_markers.sh"
[image14]: ./misc_images/HS_Add_Markers2.jpg "./add_markers.sh"
[image15]: ./misc_images/HS_Home_Service1.jpg "./home_service.sh"
[image16]: ./misc_images/HS_Home_Service2.jpg "./home_service.sh"


---


#### How to run the program with your own code

Go to Desktop and open a terminal.

For the execution of your own code, we head to the Project Workspace.

```bash
  python create_tables.py
```

If you do not have an active workspace, you can create one. You can launch it by running the following commands first.
```bash
  cd /home/workspace/
  mkdir -p catkin_ws/
```

Clone the required repositories to the `/home/workspace/catkin_ws/` folder
```bash
  cd /home/workspace/catkin_ws/
  git clone https://github.com/Abhaycl/RoboND-Home-Service-Robot-2P5.git src
```

Clone the required repositories to the ~/catkin_ws/src folder. Note that this repository already includes official ROS packages compatible with this repository: [gmapping](https://github.com/ros-perception/slam_gmapping), [turtlebot_teleop](http://wiki.ros.org/turtlebot_teleop), [turtlebot_rviz_launchers](https://github.com/turtlebot/turtlebot_interactions), and [turtlebot_gazebo](https://github.com/turtlebot/turtlebot_simulator). Their dependencies must be installed to succesfully use this repository.

(Optional)
- https://github.com/turtlebot/turtlebot_apps.git
* This repository contains the turtlebot_navigation package which is a turtlebot dependency.
* This will give you some room to tweak navigation and some SLAM behaviors.

Add required ROS packages as git submodules.
```bash
  cd ~/catkin_ws/src
  git submodule add https://github.com/ros-perception/slam_gmapping.git
  git submodule add https://github.com/turtlebot/turtlebot.git
  git submodule add https://github.com/turtlebot/turtlebot_interactions.git
  git submodule add https://github.com/turtlebot/turtlebot_simulator.git
```

Install ROS packages dependancies.
```bash
  cd ~/catkin_ws/src
  sudo rosdep -i install gmapping -y
  sudo rosdep -i install turtlebot_teleop -y
  sudo rosdep -i install turtlebot_rviz_launchers -y
  sudo rosdep -i install turtlebot_gazebo -y
```

Once copied everything, it's important to give permissions, reading and/or execution to the files necessary for the proper functioning.

Build the project:
```bash
  cd /home/workspace/catkin_ws
  catkin_make
  source devel/setup.bash
```

#### Catkin Workspace Structure
Should look something like this:
```
catkin_ws/src
    |-- add_markers
        |-- src
        |-- ...
    |-- misc_images
        |-- ...
    |-- pick_objects
        |-- src
        |-- ...
    |-- RvizConfig
        |-- ...
    |-- ShellScripts
        |-- ...
    |-- slam_gmapping
        |-- gmapping
        |-- slam_gmapping
        |-- ...
    |-- turtlebot
        |-- turtlebot
        |-- turtlebot_bringup
        |-- turtlebot_capabilities
        |-- turtlebot_description
        |-- turtlebot_teleop
        |-- ...
    |-- turtlebot_apps
        |-- turtlebot_navigation
        |-- ...
    |-- turtlebot_interactions
        |-- turtlebot_dashboard
        |-- turtlebot_interactions
        |-- turtlebot_interactive_markers
        |-- turtlebot_rviz_launchers
        |-- ...
    |-- turtlebot_simulator
        |-- turtlebot_gazebo
        |-- turtlebot_simulator
        |-- turtlebot_stage
        |-- turtlebot_stdr
        |-- ...
    |-- wall_follower
        |-- src
        |-- ...
    |-- World
        |-- ...
```


---

The summary of the files and folders within repo is provided in the table below:

| File/Folder              | Definition                                                                                                   |
| :----------------------- | :----------------------------------------------------------------------------------------------------------- |
| data/*                   | Folder that contains all the json files with the data used in this project.                                  |
| images/*                 | Folder containing the images of the project.                                                                 |
|                          |                                                                                                              |
| test.ipynb               | Displays the first few rows of each table to let check the database.                                         |
| create_tables.py         | Drops and creates the tables. This file is to reset the tables before each time that run the ETL scripts.    |
| etl.ipynb                | Reads and processes a single file from song_data and log_data and loads the data into the tables. This notebook contains detailed instructions on the ETL process for each of the tables. |
| etl.py                   | Reads and processes files from song_data and log_data and loads them into the tables.                        |
| sql_queries.py           | Contains all the sql queries, and is imported into the last three files above.                               |
|                          |                                                                                                              |
| README.md                | Contains the project documentation.                                                                          |
| README.pdf               | Contains the project documentation in PDF format.                                                            |


---

**Steps to complete the project:**  

1. Define fact and dimension tables for a star schema for a particular analytic focus.
2. Write an ETL pipeline that transfers data from files in two local directories into these tables in Postgres using Python and SQL.


## [Rubric Points](https://review.udacity.com/#!/rubrics/2500/view)
### Here I will consider the rubric points individually and describe how I addressed each point in my implementation.  

---
## Execution of the different shellscripts.

For run **launch.sh** open a terminal:

```bash
  cd /home/workspace/catkin_ws/src/ShellScripts
  ./launch.sh
```

![alt text][image1]
![alt text][image2]

---

For create **my world** open a terminal:

```bash
  cd /home/workspace/catkin_ws/src/World
  gazebo MyWorld.world
```

Design your environment.

* Open a terminal and launch Gazebo.
* Click Edit and launch `Building Editor`.
* Design a simple environment.
* Apply textures or color.
* Save the building editor environment and go back to Gazebo.
* Save the Gazebo environment to the `World` directory under your `~/catkin_ws/src`.

![alt text][image3]

---

For run **test_slam.sh** open a terminal:

```bash
  cd /home/workspace/catkin_ws/src/ShellScripts
  ./test_slam.sh
```

![alt text][image4]
![alt text][image5]

---

For run **wall_follower.sh** open a terminal:

```bash
  cd /home/workspace/catkin_ws/src/ShellScripts
  ./wall_follower.sh
```

![alt text][image6]
![alt text][image7]

---

For run **test_navigation.sh** open a terminal:

```bash
  cd /home/workspace/catkin_ws/src/ShellScripts
  ./test_navigation.sh
```

![alt text][image8]
![alt text][image9]
![alt text][image10]

---

For run **pick_objects.sh** open a terminal:

```bash
  cd /home/workspace/catkin_ws/src/ShellScripts
  ./pick_objects.sh
```

![alt text][image11]
![alt text][image12]

---

For run **add_markers.sh** open a terminal:

```bash
  cd /home/workspace/catkin_ws/src/ShellScripts
  ./add_markers.sh
```

![alt text][image13]
![alt text][image14]

---

For run the project **home_service.sh** open a terminal:

```bash
  cd /home/workspace/catkin_ws/src/ShellScripts
  ./home_service.sh
```

![alt text][image15]
![alt text][image16]
