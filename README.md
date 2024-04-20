# Issac SIM ROS2 ZED Camera Setup
This will use Issac SIM ROS2 which has Zed driver and SDK already.
Use there scripts to create the docker container.

https://nvidia-isaac-ros.github.io/getting_started/hardware_setup/sensors/zed_setup.html


# Build and Launch Docker Container
```bash
cd ${ISAAC_ROS_WS}
./src/isaac_ros_common/scripts/run_dev.sh ${ISAAC_ROS_WS}
```

# Start ZED Camera 
Within the docker container, start the zed camera
```bash
source install/setup.bash
source /opt/ros/humble/setup.bash
ros2 launch zed_wrapper zed_camera.launch.py camera_model:=zedm
```

Replace `<camera_model>` with the model of the camera that you are using: `'zed'`, `'zedm'`, `'zed2'`, `'zed2i'`, `'zedx'`, `'zedxm'`.

# Install Issac ROS2 Sim Docker Image Utility and ZED ROS2 Wrapper
```bash
export ISAAC_ROS_WS=~/Documents/ros && \
mkdir -p ${ISAAC_ROS_WS}/src && \
cd ${ISAAC_ROS_WS}/src && \
git clone https://github.com/NVIDIA-ISAAC-ROS/isaac_ros_common.git && \
git clone --recurse-submodules https://github.com/stereolabs/zed-ros2-wrapper
```

Include ZED in docker container
```bash
cd ${ISAAC_ROS_WS}/src/isaac_ros_common/scripts && \
touch .isaac_ros_common-config && \
echo CONFIG_IMAGE_KEY=ros2_humble.user.zed >> .isaac_ros_common-config
```