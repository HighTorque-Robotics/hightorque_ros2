# HighTorque ROS2 Workspace

This repository serves as a **meta-repository** for organizing the HighTorque humanoid robot ROS2 workspace. You **do not need to clone this repository** — only the `hightorque.repos` file is required to set up the workspace.

## Quick Start

### 1. Install vcstool

`vcstool` is a VCS/SCM Python source control library for svn, git, hg, and bzr:

```bash
sudo apt install python3-vcstool
```

### 2. Create Workspace

```bash
mkdir -p ~/colcon_ws
cd ~/colcon_ws
```

### 3. Download Repository Manifest

```bash
wget https://raw.githubusercontent.com/HighTorque-Robotics/hightorque_ros2/refs/heads/main/hightorque.repos
```

### 4. Import All Repositories

```bash
vcs import ./ < hightorque.repos
```

This command will clone all required repositories into your workspace according to the manifest.

### 5. Build the Workspace

```bash
source /opt/ros/foxy/setup.bash
colcon build
```

## Launching the Robot

The actual launch files are located in the [hightorque_bringup](https://github.com/HighTorque-Robotics/hightorque_bringup) repository.

For detailed launch instructions, please refer to the README in that repository.

## What is hightorque.repos?

The `hightorque.repos` file is a YAML manifest that defines all repositories in the HighTorque ROS2 workspace, including:

- Package names
- Repository URLs
- Target branches
- Relative paths in the workspace

By using `vcs import`, you can set up the entire workspace with a single command, ensuring all developers work with the same repository structure and versions.

## Workspace Structure

After running `vcs import`, your workspace will contain:

```
~/colcon_ws/
├── hightorque.repos
├── hightorque_bringup/
├── hightorque_controller/
├── hightorque_midware/
├── hightorque_msgs/
├── hightorque_robot/
├── humanoid_driver/
└── ... (other packages)
```

## Why Not Clone This Repository?

This repository exists primarily to host the `hightorque.repos` manifest file. Cloning the entire repository is unnecessary — you only need the manifest file to bootstrap your workspace. This approach:

- Reduces redundant data transfer
- Keeps your workspace clean
- Follows the standard ROS2 workspace setup pattern with vcstool

## Additional Resources

- [vcstool documentation](https://github.com/dirk-thomas/vcstool)
- [ROS2 workspace tutorials](https://docs.ros.org/en/foxy/Tutorials.html)
