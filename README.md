# Franka-Omega Teleoperation in Rviz

## original github project

- [Gavin1129/franka_haptic_teleoperate: Franka research 3 robot arm teleoperated by sigma 7 Haptic device](https://github.com/Gavin1129/franka_haptic_teleoperate)

## software requirement

- Unbuntu 22.04 LTS

  - [Ubuntu 22.04.5 LTS (Jammy Jellyfish)](https://releases.ubuntu.com/jammy/)

- ROS2 humble

  - [ROS 2 Documentation — ROS 2 Documentation: Humble documentation](https://docs.ros.org/en/humble/index.html)

- libfranka (version >=0.15.0)

  - [frankarobotics/libfranka: C++ client library to control Franka robots in real-time](https://github.com/frankarobotics/libfranka)

- franka_ros2

  - [frankarobotics/franka_ros2: ROS 2 integration for Franka research robots](https://github.com/frankarobotics/franka_ros2)

- Omega 7 force feedback device SDK

  - [南大云盘 NJU Box (SDK3.17.6.rar)](https://box.nju.edu.cn/library/12272c5e-94b3-40c4-936f-cbd8a28d69b9/Omega%207%20force%20feedback%20device%20SDK/)


## hardware requirement

- Omega 7/Sigma 7 force feedback device
- Franka Research 3 robotic arm (with gripper)



## Omega 7 SDK installation steps

1. create a workspace and open a terminal in it, follwing the steps below: 

   ````
   sudo tar -zxvf sdk-3.17.6.0-linux-x86_64-gcc.tar.gz
   ````

   ````
   sudo apt-get update
   ````

   ````
   sudo apt-get install libusb-1.0
   ````

   ````
   sudo apt-get install libqt5widgets5
   ````

   ````
   sudo apt-get install libglfw3-dev
   ````


2. restart the computer and open the terminal, following the steps below:

   ````
   cd sdk-3.17.3/bin
   ````

   ````
   sudo ./HapticDesk
   ````
3. you will see the real-time force feedback interface: 

    <img width="940" height="785" alt="实时力反馈可视化" src="https://github.com/user-attachments/assets/d92a1e9a-d234-48c4-9189-02e1b121c3e7" />

    <img width="937" height="784" alt="实时力反馈界面" src="https://github.com/user-attachments/assets/c922af43-5a58-4b09-8777-0b16ef8af939" />




## franka-omega communication and control schematic diagram


## how to run franka-omega7 in Rviz


1. create a workspace and build from source
   ````
   colcon build
   ````
2. turn omega7 and run main code
   ````
   ros2 run sigma7 sigma_main
   ````
    <img width="730" height="186" alt="step1-run omega" src="https://github.com/user-attachments/assets/6521b420-1108-4c35-a47b-101822ba36cc" />

3. launch Rviz
   ````
   ros2 launch franka_pose_control rviz.launch.py
   ````
    <img width="730" height="174" alt="step2-run rviz" src="https://github.com/user-attachments/assets/4deb0ac9-826e-4ff9-ae53-ebdf3728bdab" />

    <img width="1410" height="1422" alt="Rviz" src="https://github.com/user-attachments/assets/d6a19d65-5b29-4f3d-bbde-57906b958dbb" />

4. run pose publisher
   ````
   ros2 run franka_pose_control franka_targetPose_publisher
   ````
  <img width="730" height="183" alt="step3-run omega publisher" src="https://github.com/user-attachments/assets/fa859358-b193-4cff-9842-b88153a6e244" />

5. run franka controller to plan tragectory
   ````
   ros2 run franka_pose_control franka_pose
   ````
    <img width="727" height="171" alt="step4-run franka controller" src="https://github.com/user-attachments/assets/ff148389-0827-4294-96a5-09b604424b79" />

6. finally, you can get:

    ![最终效果](https://github.com/user-attachments/assets/fedd683c-be64-4e16-8097-26457c709e08)
