# Base
## Overview
- Ubuntu 14.04
- CUDA 8.0 + Cudnn v7
- ROS-Indigo

## Setup
- Install NVIDIA Graphic driver. Check graphic driver of your local host (System Settings&rarr;Softwar & Updates&rarr;
Additional Drivers&rarr;NVIDIA binary driver XXX), e.g. mine is nvidia-384. 
Download runfile from [here](http://www.nvidia.com/object/linux-amd64-display-archive.html). 
```
$ wget ${DOWNLOAD_LINK_TO_RUNFILE}
$ chmod u+x NVIDIA-Linux-XXX-XXX.run
$ ./NVIDIA-Linux-XXX-XXX.run -a -N --ui=none --no-kernel-module
$ # Choose "Continue installation"
```
- Manually download Gazebo models from [here](https://bitbucket.org/osrf/gazebo_models/downloads/).
```
$ cd ~/.gazebo # if you don't have ~/.gazebo, just create one yourself
$ mkdir models && cd models
$ apt-get install unzip
$ unzip ${DOWNLOAD_LINK}
$ mv ${UNZIPPED_DIR}/* .
$ # remove .zip file and the empty unzipped directory
```

## Test If Everything goes well
- Check NVIDIA.
```
$ nvidia-smi
$ nvcc --version # CUDA
```
- Check Python path.
```
$ python -c "import os; print(os.environ['PYTHONPATH'].split(os.pathsep))"
$ # it should be ['/opt/ros/indigo/lib/python2.7/dist-packages']
```
- Check gazebo. You need to wait a bit if your are opening gazebo for the first time.
```
$ roslaunch gazebo_ros empty_world.launch
```

## FAQ
- If you didn't install NVIDIA Graphic driver in your docker, you will encounter the following error while opening Gazebo, 
([Reference](https://github.com/NVIDIA-Jetson/redtail/issues/24))
```
libGL error: failed to load driver: swrast
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Value in failed request:  0x0
  Serial number of failed request:  30
  Current serial number in output stream:  31
```
- There is some problems in [Gazebo database](http://gazebosim.org/models/). Download models manually. 
([Reference](https://answers.ros.org/question/199401/problem-with-indigo-and-gazebo-22/))
```
Warning [ModelDatabase.cc:334] Getting models from[http://gazebosim.org/models/]. This may take a few seconds.
Warning [gazebo.cc:215] Waited 1seconds for namespaces.
...
Error [gazebo.cc:220] Waited 11 seconds for namespaces. Giving up.
```
