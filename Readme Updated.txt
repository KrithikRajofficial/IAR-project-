- Webots Crazyflie Swarm – Execution Guide

This project demonstrates a Crazyflie drone swarm in Webots using a leader–follower architecture.  
The default Webots Crazyflie controller is used for the initial takeoff, after which custom controllers are executed for swarm behaviour and perception.

---

- Controllers Used

- Default Webots Controller  
  - Used only for initial takeoff and stabilization  
  - Ensures all drones reach a safe hover state before custom control begins  

- Custom Controllers  
  - my_crazytest.py – Leader drone (waypoint navigation and MQTT broadcasting)  
  - my_controller_test1.py – Left follower drone (leader tracking without vision)  
  - my_controller_test2.py – Right follower drone (leader tracking with YOLO-based object detection)  

---

- Execution Steps

- Step 1: Initial Takeoff Using Default Controller  
  1. Open the Webots world file.  
  2. Assign the default Crazyflie controller to all drones.  
  3. Run the simulation.  
  4. Wait until all drones take off and reach a stable hover.  

  This step is required to ensure proper initialization before switching to custom controllers.

---

- Step 2: Stop the Simulation  
  1. Stop the simulation after takeoff is complete.  
  2. Do not reset the world.  

---

- Step 3: Assign Custom Controllers  

  | Drone Role | Controller File |
  |-----------|-----------------|
  | Leader | my_crazytest.py |
  | Left Follower | my_controller_test1.py |
  | Right Follower | my_controller_test2.py |

---

- Step 4: Run Custom Swarm Behaviour  
  1. Start the simulation again.  
  2. The leader drone begins waypoint-based navigation.  
  3. The leader publishes its position using MQTT on the topic `crazyflie/swarm`.  
  4. The follower drones track the leader using predefined position offsets.  
  5. The right follower performs real-time object detection using YOLO and its onboard camera.