# LibCarla Wrapped Up As a ROS Package
This package provides [LibCarla (CARLA C++ API)](https://github.com/carla-simulator/carla/tree/master/LibCarla) as a ROS Package. The LibCarla libraries were compiled using gcc-7.

**CARLA Version: 0.9.10.1**

## How to Build CARLA C++ API (LibCarla)
LibCarla can be built by the following command:
```bash
cd ${CARLA_SRC_ROOT_DIR}/Examples/CppClient
make run
```
Then reorganize the generated folder `libcarla-install` as a ROS package.

## Document of Debug Progress
1. How to solve header file includes in other ROS packages: https://answers.ros.org/question/93266/how-to-export-non-standard-include-directories-in-catkin/?answer=93281?answer=93281#post-id-93281
```bash
Errors     << cpp_client_demo:make /mnt/ssd1/repos/carla-ros-bridge/catkin_ws/logs/cpp_client_demo/build.make.004.log  
In file included from /mnt/ssd1/repos/carla-ros-bridge/catkin_ws/install/share/libcarla/cmake/../../../include/libcarla/carla/rpc/ActorAttribute.h:9,
                 from /mnt/ssd1/repos/carla-ros-bridge/catkin_ws/install/share/libcarla/cmake/../../../include/libcarla/carla/client/ActorAttribute.h:9,
                 from /mnt/ssd1/repos/carla-ros-bridge/catkin_ws/install/include/libcarla/carla/client/ActorBlueprint.h:11,
                 from /mnt/ssd1/repos/carla-ros-bridge/catkin_ws/src/carla_playground/cpp_client_demo/src/demo_main.cpp:3:
/mnt/ssd1/repos/carla-ros-bridge/catkin_ws/install/share/libcarla/cmake/../../../include/libcarla/carla/MsgPack.h:11:10: fatal error: rpc/msgpack.hpp: No such file or directory
   11 | #include <rpc/msgpack.hpp>
      |          ^~~~~~~~~~~~~~~~~
compilation terminated.
make[2]: *** [CMakeFiles/cpp_client_demo.dir/build.make:63: CMakeFiles/cpp_client_demo.dir/src/demo_main.cpp.o] Error 1
make[1]: *** [CMakeFiles/Makefile2:563: CMakeFiles/cpp_client_demo.dir/all] Error 2
make: *** [Makefile:141: all] Error 2
cd /mnt/ssd1/repos/carla-ros-bridge/catkin_ws/build/cpp_client_demo; catkin build --get-env cpp_client_demo | catkin env -si  /usr/bin/make --jobserver-auth=3,4; cd -
```