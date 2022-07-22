rtabmap
=======

[![RTAB-Map Logo](https://raw.githubusercontent.com/introlab/rtabmap/master/guilib/src/images/RTAB-Map100.png)](http://introlab.github.io/rtabmap)

[![Release][release-image]][releases]
[![License][license-image]][license]

 * Linux: [![Build Status](https://github.com/introlab/rtabmap/actions/workflows/cmake.yml/badge.svg)](https://github.com/introlab/rtabmap/actions/workflows/cmake.yml) [![Build Status](https://github.com/introlab/rtabmap/actions/workflows/cmake-ros.yml/badge.svg)](https://github.com/introlab/rtabmap/actions/workflows/cmake-ros.yml) [![docker](https://github.com/introlab/rtabmap/actions/workflows/docker.yml/badge.svg)](https://github.com/introlab/rtabmap/actions/workflows/docker.yml) 
 * Windows: [![Build status](https://ci.appveyor.com/api/projects/status/hr73xspix9oqa26h/branch/master?svg=true)](https://ci.appveyor.com/project/matlabbe/rtabmap/branch/master)

[release-image]: https://img.shields.io/badge/release-0.20.16-green.svg?style=flat
[releases]: https://github.com/introlab/rtabmap/releases

[license-image]: https://img.shields.io/badge/license-BSD-green.svg?style=flat
[license]: https://github.com/introlab/rtabmap/blob/master/LICENSE

RTAB-Map library and standalone application.

For more information, visit the [RTAB-Map's home page](http://introlab.github.io/rtabmap) or the [RTAB-Map's wiki](https://github.com/introlab/rtabmap/wiki).

To use RTAB-Map under ROS, visit the [rtabmap](http://wiki.ros.org/rtabmap) page on the ROS wiki.

### Acknowledgements
This project is supported by [IntRoLab - Intelligent / Interactive / Integrated / Interdisciplinary Robot Lab](https://introlab.3it.usherbrooke.ca/), Sherbrooke, Québec, Canada.

<a href="https://introlab.3it.usherbrooke.ca/">
<img src="https://github.com/introlab/16SoundsUSB/blob/master/images/IntRoLab.png" alt="IntRoLab" height="100">
</a>

## OCCAM Lab Usage Instructions
### Usage Overview
This repository was used in Summer of 2022 by Ayush Chakraborty, Rucha Dave, and Richard Li in order to obtain Ground Truth Data to benchmark the backend code of Invisible Map. In order to generate .g2o files from a RTABMap scan that Invisible Map can process to a ground truth dataset, follow the instructions below. The format of the .g2o file is TAG_ORIENTATION_TYPE (rpy (roll pitch yaw) as default) APRIL_TAG_ID TAG_X TAG_Y TAG_Z TAG_Q_X TAG_Q_Y TAG_Q_Z TAG_Q_W separated by spaces. 

### Instructions
1. Download rtabmap iOS build to a LiDAR device (can be downloaded either from the App Store or built through XCode found in //app/ios/RTABMap.xcodeproj).
2. Scan the desired space using the built app. This can either be done all in one scan, or as multiple sessions.
 *Note: The app tends to crash due to intensive memory demand to generate the point cloud during scanning. If the app crashes, it can be recovered by re-opening the app and hitting "Start Camera", which prompts you to restore a previous session. From there, you can either append to the restored scan, or save the recovered file.*
3. Save and export all scans to your local computer (these should be as .db files).
4. Follow this [link](https://github.com/introlab/rtabmap/wiki/Installation) in order to build the RTABMap onto your native machine. *Note: In order to ensure that the desktop app can properly optimize the database, the app must be built with g2o.*
5. Follow this [link](https://github.com/introlab/rtabmap/wiki/Multi-Session-Mapping-with-RTAB-Map-Tango)  in order to re-run your scan on your native machine (can be done with one or multiple database files).
6. Once the app has finished iterating through the data, close the database and export the scan as a .g2o file (File > Export Poses > g2o (*.g2o)). This will prompt you to save the .g2o file. From there, it can be inputted into Invisible Map and processed into a ground truth dataset.

Tip: Generate a thorough scan of the formula car - very satisfying to the eye.