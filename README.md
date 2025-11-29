# ROS2 Dev Container Templates (Humble, Iron, Rolling)

A set of `.devcontainer` templates for running ROS2 inside Docker with VS Code.  
These templates let you quickly create isolated development environments for different ROS2 distros without polluting your host system.

Supported distros:
- **ROS2 Humble**
- **ROS2 Iron**
- **ROS2 Rolling**

Each template includes:
- A `devcontainer.json` with correct volume mounts, GUI support, DDS settings, and extensions
- A matching `Dockerfile` (or base image) for the specific ROS2 version
- Automatic `rosdep` setup on container creation
- X11 forwarding for RViz2 and Gazebo
- Reasonable defaults for ROS_DOMAIN_ID, discovery range, etc.

---

## Why use this?

ROS2 requires specific versions of Python, Qt, DDS, and system libraries.  
Running it on the host often leads to conflicts with:

- different ROS2 distros,
- local Python/conda/pyenv environments,
- snap GLIBC mismatches,
- system libraries and drivers,
- conflicting Gazebo/RViz installs.

These dev containers isolate all of that and make sure each ROS2 project runs in a clean, reproducible environment.

---

## How to Use

### 1. Create a new ROS2 project
```bash
mkdir -p ~/workspaces/my_project/src
cd ~/workspaces/my_project
```

### 2. Copy a template
Example for Humble:
```bash
cp -r ~/devcontainer-templates/ros2-humble/.devcontainer .
```

### 3. Open the folder in VS Code
```
Press: Ctrl + Shift + P → Dev Containers: Reopen in Container
```
VS Code will build the container and mount your project located at:
```
/workspaces/<your-project>
```
You can now run:
```bash
colcon build
source install/setup.bash
rviz2
ros2 run ...
```
directly inside the container.


---

## Folder Structure
```
devcontainer-templates/
  ros2-humble/
    .devcontainer/
      devcontainer.json
      Dockerfile
  ros2-iron/
    .devcontainer/
      devcontainer.json
      Dockerfile
  ros2-rolling/
    .devcontainer/
      devcontainer.json
      Dockerfile
```
