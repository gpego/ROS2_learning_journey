# ROS2_learning_journey
Notes about a beginners ROS2 guide.
## Before getting started
This is not intended to be a full fledged ROS2 guide. I'm nowhere enough good to write one.
It is just of a collection of the notes I'm taking while getting into the magical world if ROS2, alongside the articles/tutorials I'm reading.
Because of how this material came to be (is coming to be), hereafter information will be displayed in the most concise way possible. I acknowledge from now that it might be too concise.
Specifically the notes revolve around this [Getting Started with ROS2](https://medium.com/spinor/getting-started-with-ros2-an-introduction-a36e21ff5feb) Series.
## Initial setup
Installing ROS2 inside a Docker container in WSL2: [guide](https://medium.com/@oelmofty/ros2-in-docker-why-and-how-b72b3880dc97).
Basic commands to interact with the container (IMPORTANT: if you use Docker Desktop make sure it is running before typing anything on the shell):
```bash
# Start and open a terminal inside the container
docker start <container_name_or_id> # Example name: ros2_container
docker exec -it <container_name_or_id> bash

# Stop the container
docker stop base_ros2_container
```
Useful basic configuration:
```bash
# Installing basic utilities
# Assunming you already have root access
apt-get update && apt-get install -y \
nano \ 
python3-pip \ 
wget \ 
curl \ 
software-properties-common \ 
&& rm -rf /var/lib/apt/lists/*

apt-get update && apt-get upgrade -y
```
Furthermore it is required to source the setup file each time you start the container, with:
```bash
source /opt/ros/humble/setup.bash
```
You can skip this tedious process by sourcing it once and for all:
```bash
# Register the bash file
# Open or create .bashrc file
nano ~/.bashrc

# Add this line at the end of the file (adjust the path to match your ROS distribution)
source /opt/ros/humble/setup.bash

# Save and exit (Ctrl+X, then Y, then Enter) # Reload the .bashrc
source ~/.bashrc
```
## Guide chapters
### Part 3
[Link](https://medium.com/spinor/getting-started-with-ros2-install-and-setup-ros2-humble-on-ubuntu-22-04-lts-ad718d4a3ac2). A first trivial example can be found at Point 5.
### Part 5
[Link](https://medium.com/spinor/getting-started-with-ros2-create-and-set-up-a-workspace-f60a6c52328c). Introduction to workspaces.
#### Structure
- `src`
- `install`
- `build`
- `log`
#### Setting up colcon
The command:
```bash
colcon --version
```
Instead use:
```bash
colcon version-check
```
#### Creating a workspace
Create a directory containing the `src` folder.
Run:
```bash
colcon build
```
Now source the `<your_workspace_dir>/install/setup.bash` file:
```bash
source ~/ros2_ws/install/setup.bash
```
This can be automated by adding:
```bash
echo "source <your_workspace_dir>/install/setup.bash" >> ~/.bashrc
# e.g. echo "source ~/ros2_ws/install/setup.bash" >> ~/.bashrc
```
to your `.bashrc` file. Then run:
```bash
source ~./bashrc
```
to refresh the shell configuration.
### Part 6
