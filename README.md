# Staubli

[![Build Status: Ubuntu Bionic (Actions)](https://github.com/ros-industrial/staubli/workflows/CI%20-%20Ubuntu%20Bionic/badge.svg?branch=indigo-devel)](https://github.com/ros-industrial/staubli/actions?query=workflow%3A%22CI+-+Ubuntu+Bionic%22)
[![Build Status: Ubuntu Focal (Actions)](https://github.com/ros-industrial/staubli/workflows/CI%20-%20Ubuntu%20Focal/badge.svg?branch=indigo-devel)](https://github.com/ros-industrial/staubli/actions?query=workflow%3A%22CI+-+Ubuntu+Focal%22)
[![Github Issues](https://img.shields.io/github/issues/ros-industrial/staubli.svg)](http://github.com/ros-industrial/staubli/issues)

[![license - apache 2.0](https://img.shields.io/:license-Apache%202.0-yellowgreen.svg)](https://opensource.org/licenses/Apache-2.0)

[![support level: community](https://img.shields.io/badge/support%20level-community-lightgray.svg)](http://rosindustrial.org/news/2016/10/7/better-supporting-a-growing-ros-industrial-software-platform)

[ROS-Industrial][] Staubli meta-package. See the [ROS wiki][] page for more information.

The [staubli_experimental][] repository contains additional packages.


## Contents

Branch naming follows the ROS distribution they are compatible with. `-devel` branches may be unstable. Releases are made from distribution branches (`hydro`, `indigo`, `kinetic`).


## Building

### On newer (or older) versions of ROS

Building the packages on newer (or older) versions of ROS is in most cases possible and supported. For example: building the packages in this repository on Ubuntu Xenial/ROS Kinetic or Ubuntu Bionic/ROS Melodic systems is supported. This will require creating a Catkin workspace, cloning this repository, installing all required dependencies and finally building the workspace.

### Catkin tools

It is recommended to use [catkin_tools][] instead of the default [catkin][] when building ROS workspaces. `catkin_tools` provides a number of benefits over regular `catkin_make` and will be used in the instructions below. All packages can be built using `catkin_make` however: use `catkin_make` in place of `catkin build` where appropriate.

### Building the packages

The following instructions assume that a [Catkin workspace][] has been created at `$HOME/catkin_ws` and that the *source space* is at `$HOME/catkin_ws/src`. Update paths appropriately if they are different on the build machine.

These instructions build the `indigo-devel` branch on a ROS Kinetic system:

```bash
# change to the root of the Catkin workspace
$ cd $HOME/catkin_ws

# retrieve the latest development version of staubli.
$ git clone -b indigo-devel https://github.com/ros-industrial/staubli.git src/staubli

# check build dependencies. Note: this may install additional packages,
# depending on the software installed on the machine
$ rosdep update

# be sure to change 'kinetic' to whichever ROS release you are using
$ rosdep install --from-paths src/ --ignore-src --rosdistro kinetic

# build the workspace (using catkin_tools)
$ catkin build
```

### Activating the workspace

Finally, activate the workspace to get access to the packages just built:

```bash
$ source $HOME/catkin_ws/devel/setup.bash
```

At this point all packages should be usable (ie: `roslaunch` should be able to auto-complete package names starting with `staubli_..`). In case the workspace contains additional packages (ie: not from this repository), those should also still be available.


## Installation and usage

Refer to [Working With ROS-Industrial Robot Support Packages][] for information on how to use the files provided by the robot support and MoveIt configuration packages. See also the other pages on the [ROS wiki][].


## Disclaimer

The author(s) of these packages is (are) not affiliated with Stäubli International AG in any way.
All trademarks and registered trademarks are property of their respective owners, and company, product and service names mentioned in this readme or appearing in source code or other artefacts in this repository are used for identification purposes only.
Use of these names does not imply endorsement by Stäubli International AG.



[ROS-Industrial]: http://wiki.ros.org/Industrial
[ROS wiki]: http://wiki.ros.org/staubli
[staubli_experimental]: https://github.com/ros-industrial/staubli_experimental
[Catkin workspace]: http://wiki.ros.org/catkin/Tutorials/create_a_workspace
[catkin]: http://wiki.ros.org/catkin
[catkin_tools]: https://catkin-tools.readthedocs.io/en/latest
[Working With ROS-Industrial Robot Support Packages]: http://wiki.ros.org/Industrial/Tutorials/WorkingWithRosIndustrialRobotSupportPackages
