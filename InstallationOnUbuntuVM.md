## Configuring ROS2 on Ubuntu Virtual Machine

1. **Download VirtualBox:**
   - Visit [VirtualBox website](https://www.virtualbox.org/).
   - Download and install VirtualBox according to your operating system.

2. **Download Ubuntu 22.04.4 ISO:**
   - Navigate to [Ubuntu download page](https://ubuntu.com/download/desktop).
   - Download the Ubuntu 22.04.4 ISO file.

3. **Configure Virtual Machine with Ubuntu:**
   - Open VirtualBox and create a new virtual machine.
   - Select Ubuntu ISO file as the installation media.
   - Configure virtual machine settings and proceed with Ubuntu installation.

4. **Check ROS2 Official Documentation:**
   - Visit [ROS2 official documentation](https://docs.ros.org/en/humble/index.html).

5. **Set Locale:**
   - Open a terminal in the Ubuntu virtual machine.
   - Execute the following commands:
     ```bash
     locale  # Check for UTF-8
     sudo apt update && sudo apt install locales
     sudo locale-gen en_US en_US.UTF-8
     sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
     export LANG=en_US.UTF-8
     locale  # Verify settings
     ```

6. **Set up ROS 2 Apt Repository:**
   - Execute the following commands in the terminal:
     ```bash
     sudo apt install software-properties-common
     sudo add-apt-repository universe
     sudo apt update && sudo apt install curl -y
     sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg
     echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
     ```

7. **Install ROS2 Packages:**
   - Execute the following commands:
     ```bash
     sudo apt update -y && apt full-upgrade -y && apt autoremove
     sudo apt install ros-humble-desktop
     ```

8. **Environment Setup:**
   - Source the setup script by executing:
     ```bash
     source /opt/ros/humble/setup.bash
     ```

9. **Verify Installation:**
   - Open a terminal and execute:
     ```bash
     source /opt/ros/humble/setup.bash
     ros2 run demo_nodes_cpp talker
     ```
   - In another terminal, execute:
     ```bash
     source /opt/ros/humble/setup.bash
     ros2 run demo_nodes_py listener
     ```
   - Verify that the talker is publishing messages and the listener is receiving them.

By following these steps, you should have successfully configured ROS2 on your Ubuntu virtual machine.
