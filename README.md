# FlightGoggles

## Environment
- Ubuntu 20.04 Desktop
- Nvidia GeForce RTX 3090

## Install 
### FlightGoggles Renderer
- Download the latest binary from [Releases](https://github.com/mit-fast/FlightGoggles/releases) and extract the files.


### FlightGoggles Client
```bash
# Setup catkin workspace
mkdir -p ~/flightgoggles_ws/src
cd ~/flightgoggles_ws/
catkin init
echo 'source ~/flightgoggles_ws/devel/setup.bash' >> ~/.bashrc

# Install FlightGoggles nodes and deps from rosinstall file
cd src
wstool init
wstool merge https://raw.githubusercontent.com/donghun-han/FlightGoggles/master/flightgoggles.rosinstall
wstool update

# Install required libraries.
cd ../
rosdep install --from-paths src --ignore-src --rosdistro noetic -y
# Install external libraries for flightgoggles_ros_bridge
sudo apt install -y libzmqpp-dev libeigen3-dev
# Install dependencies for flightgoggles renderer
sudo apt install -y libvulkan1 vulkan-utils gdb

# Build nodes and download FlightGoggles renderer binary
# NOTE: to avoid downloading the FlightGoggles renderer binary, use the following build command:
catkin build --cmake-args -DFLIGHTGOGGLES_DOWNLOAD_BINARY=OFF

# Refresh workspace. 
source ~/.bashrc
```

---
<details>
<summary>Original README</summary>
<div markdown="1">

## Documentation, Installation, & Usage Instructions
Please refer to the [project website](https://flightgoggles.mit.edu) for project information and our [code documentation](https://mit-aera.github.io/FlightGoggles-Documentation/index.html) for installation and usage instructions. 

## Description

A framework for photorealistic hardware-in-the-loop agile flight simulation using Unity3D and ROS.

[![Video Link](Images/stata_ground_floor.png)](https://youtu.be/qoUlbSAiRko)

## Citation
If you find this work useful for your research, please cite:
```bibtex
@misc{1905.11377,
  Title = {FlightGoggles: Photorealistic Sensor Simulation for Perception-driven Robotics using Photogrammetry and Virtual Reality},
  Author = {Winter Guerra and Ezra Tal and Varun Murali and Gilhyun Ryou and Sertac Karaman},
  Year = {2019},
  Eprint = {arXiv:1905.11377},
}
```
FlightGoggles: [Paper](https://arxiv.org/abs/1905.11377), [Website](http://flightgoggles.mit.edu)

## Papers using this work

```bibtex
@inproceedings{antonini2018blackbird,
  title={The Blackbird Dataset: A large-scale dataset for UAV perception in aggressive flight},
  author={Antonini, Amado and Guerra, Winter and Murali, Varun and Sayre-McCord, Thomas and Karaman, Sertac},
  booktitle={International Symposium on Experimental Robotics, {ISER} 2018, Buenos Aires,
               Argentina, November 5-8, 2018.},
  year={2018}
}

@article{antonini202IJRR,
author = {Amado Antonini and Winter Guerra and Varun Murali and Thomas Sayre-McCord and Sertac Karaman},
title ={The Blackbird UAV dataset},
journal = {The International Journal of Robotics Research},
volume = {39},
number = {10-11},
pages = {1346-1364},
year = {2020},
doi = {10.1177/0278364920908331},
}

@inproceedings{sayremccord2018visual,
  title={Visual-inertial navigation algorithm development using photorealistic camera simulation in the loop},
  author={Sayre-McCord, Thomas and
  Guerra, Winter and
  Antonini, Amado and
  Arneberg, Jasper and
  Brown, Austin and
  Cavalheiro, Guilherme and
  Fang, Yajun and
  Gorodetsky, Alex and
  McCoy, Dave and
  Quilter, Sebastian and
  Riether, Fabian and
  Tal, Ezra and
  Terzioglu, Yunus and
  Carlone, Luca and
  Karaman, Sertac},
  booktitle={2018 IEEE International Conference on Robotics and Automation (ICRA)},
  year={2018}
}
```
Blackbird Dataset: [Paper](https://arxiv.org/abs/1810.01987), [Website](https://github.com/mit-fast/Blackbird-Dataset)

Visual-inertial navigation algorithm development using photorealistic camera simulation in the loop: [Paper](https://doi.org/10.1109/icra.2018.8460692)

## Core Contributers

```
Winter Guerra
Ezra Tal
Varun Murali
Gilhyun Ryou
Sertac Karaman
```


</div>
</details>
