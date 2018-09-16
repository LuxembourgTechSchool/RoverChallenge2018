# LTS - Space Resources Challenge 2018

This repository contains documentation for the LTS - Space Resources Challenge 2018 using the Erle Rover.

Sponsor by [SpaceResources.lu Initiative](https://spaceresources.public.lu/en.html)

# Requirements & Links

We have prepared a virtual machine for you to work with.
This is the easiest way to get started with the simulation environment.

To run the virutal machine you will need:

- [VirtualBox](www.virtualbox.org)
- [LTS Virtual Machine Image (4.6 GB)](https://www.dropbox.com/s/zcvwiraq3kspj0o/LTS_Rover_Lubuntu.ova?dl=0) (Password of the default user is "lts")

Link to the youtube tutorials is [here](https://www.youtube.com/playlist?list=PLya9cR8AUBydU-pzImClcrSf0GKgXXg89).

The Virtual Machine contains:

- Python 2
- ROS Indigo
- Gazebo (Simulator)
- [Erle Rover](https://erlerobotics.com/blog/erle-rover/) ([Official Documentation](http://docs.erlerobotics.com/simulation))

# Getting Started

The main working directory is: `~/simulation/`

## 1. Proxy

To run the simulation, we have to launch the proxies first.

### Proxy Setup

Open the terminal and type the following commands:

	source ~/simulation/ros_catkin_ws/devel/setup.bash 
	cd ~/simulation/ardupilot/APMrover2
	../Tools/autotest/sim_vehicle.sh -j 4 -f Gazebo
	param load ~/Tools/Frame_params/3DR_Rover.param

### Proxy Mode

The proxy has multiple modes for the rover controller.
We are interested in 2 modes.

To control the rover **manually** via the terminal run: `param set SYSID_MYGCS 255`

To control the rover **remotely** via the ROS Messages run: `param set SYSID_MYGCS 1`

## 2. Launch the simulator

Once the proxy is running, we can launch the simulation.
Open a new terminal window/tab and run the following commands:

	source ~/simulation/ros_catkin_ws/devel/setup.bash
	roslaunch ardupilot_sitl_gazebo_plugin rover_spawn.launch

## 3. Run a Python Program

The proxy is running and the simulation is open. Now you can run a rover controller.

Open a third terminal window/tab and run the following command:

	source ~/simulation/ros_catkin_ws/devel/setup.bash

After that, you are ready to run a controller.

There are a few examples in this virtual machine that you can run.
They are located at:

	~/simulation/ros_catkin_ws/src/gazebo_python_examples/erle_rover_explorer/scripts

Then, just run for example:

	python rover_obstacle_avoidance.py

## 2. Stop the simulation

Stopping is easy: `CTRL+C` until it stops.

## 3. Reset the simulation

If you want to reset the rover and the simulation to his initial state, you will have to:

1. Cancel the process in the second terminal tab where the Gazebo simulator is running using `CTRL+C`
2. Run again `roslaunch ardupilot_sitl_gazebo_plugin rover_spawn.launch`

# How to write your own code

The easiest way to code your own controller is to create a new `*.py` file in the scripts folder:

	~/simulation/ros_catkin_ws/src/gazebo_python_examples/erle_rover_explorer/scripts

# Submissions not later than 31st October 2018

Send your python code solution with your contact info to challenge@techschool.lu

# More about the Erle Rover

For more infor and support about the Erle Rover simulation visit the Erle Robotics [forum at](http://forum.erlerobotics.com/c/robots/erle-rover)

# Sponsors

- [SpaceResources.lu Initiative](https://spaceresources.public.lu/en.html)
- [Digital Luxembourg](https://digital-luxembourg.public.lu)
- [SCRIPT](https://portal.education.lu/script/)
- [CGIE](https://portal.education.lu/cgie/)
- [FNR](https://www.fnr.lu)
