#Autonomous Cleaning Robot Simulation

A virtual cleaning robot built in CoppeliaSim that autonomously navigates through a home environment, plans a 2D path using the Potential Field Method, avoids obstacles with a proximity sensor, and performs cleaning tasks before returning to its charging dock.

#Features

Real-time 2D Path Planning using the Potential Field Method

Obstacle Detection & Avoidance via a proximity sensor

Live Visualization of planned paths and sensor feedback

Simulation Environment: Full house layout including rooms, walls, furniture, plants, and (optional) people

#Requirements

CoppeliaSim (version compatible with simOMPL plugin)

OMPL library integrated with CoppeliaSim

Lua 5.3 (built into CoppeliaSim)

#Project Structure

/scene
  cleaning_robot.ttt        # CoppeliaSim scene file
/lua
  robot_control_script.lua  # Main control and planning script
/README.md                  # This documentation

#Setup & Usage

- Open the Scene

Launch CoppeliaSim and open cleaning_robot.ttt from the /scene folder.

- Load OMPL Plugin

Ensure the OMPL plugin is enabled in the model browser (Tools → Plugin).

- Start Simulation

-Press Play. The robot will:

Begin at its charging dock (predetermined start point).

Plan a path to the target room using the Potential Field Method.

Use its proximity sensor to detect and avoid obstacles in real-time.

Visualize the planned path and free-space nodes on-screen.

Perform its cleaning routine in the target room.

Return to the docking station when finished.

#How It Works

- Initialization (sysCall_init):

Handle retrieval (robot base, joints, collision volume).

Obstacle collection setup and planner parameter configuration.

Coroutine creation for the main control loop.

Control Loop (sysCall_actuation):

Resumes the coroutine each simulation step.

After reaching a goal, increments target index and continues.

Collision Correction:

Backs the robot out of any initial collisions before planning.

Path Planning & Execution (gotoTarget):

Adjusts goal if it’s out of range or colliding.

Configures and solves an OMPL task with collision pairs.

Simplifies and visualizes the resulting path.

Drives the robot along the path with differential drive velocities.

Customization

Change House Layout: Edit the scene file to add/remove walls, furniture, or obstacles.

Swap Robot Model: Replace the differential-drive robot with another compatible model.

Tweak Planning: Adjust searchRange, searchDuration, or switch OMPL algorithms.

Contributing

Fork this repository.

Create a new branch (git checkout -b feature/YourFeature).

Commit your changes (git commit -m 'Add new feature').

Push to your branch (git push origin feature/YourFeature).

Open a Pull Request.

License

This project is licensed under the MIT License. See the LICENSE file for details.
