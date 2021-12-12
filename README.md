**A brief description of Flexible Automation Simulation**

The goal of the assignment is to design and develop a manufacturing cell in which a robot segregates mixed items from an intake conveyor to three output conveyors.

**Problem Statement**

You can also find here the problem statement :
[FlexibleAutomation_SimulationAssignment_Questions_UniGe_2021.pdf](https://github.com/Farzinsvi/FlexibleAutomation_Simulation/files/7699222/FlexibleAutomation_SimulationAssignment_Questions_UniGe_2021.pdf)

**Plant Layout Design and Simulation**

For each of the three meshes of the desired object to work with a convex approximation has been generated using **HACD** (for CamFhaft_Engine) and **V-HACD** (for FuelPump_Engine and OilTray_Engine pieces, due to the inability of the former algorithm to model it in a satisfying way). As a naming convention the convex shape has been named _dynamic whilst the visual mesh _visual: the latter has been set to non-respondable and non-dynamic, and placed in the hierarchy as the child of the convex shape.

Note that, in order to reduce the computational burden, convex shape have been set as non-renderable (among the special properties), whilst the visual shape as been set exclusively as renderable. This in order to have camera based system detect the actual visual shape of the object, which is instead not a priority in the other detection systems.

To all three shaped was appllied a material, in order to more accurately model their dynamic properties.

**Materials**

![Untitled](https://user-images.githubusercontent.com/74813983/145723072-90c5ee0a-9b1c-425d-bb67-8bb082dfcf53.png)

**Spawn system**

A dummy object (SpawnPoint, child of ConveyorIn) is responsible to spawn the items via its child script(by using **Proximity sensor spawner** as child of SpawnPoint). The delay between each spawn is, currently, hardcoded as 20 seconds +- 4 seconds of random variability added on purpose. To each model spawned is added a reasonable random rotation component to model variability in the incoming items orientation.

**Robot Mechanism**

Since the load/unload task does not require fine manipulation of the conveyed objects, a Cartesian (PRR) mechanism has been chosen as the body of the robot. It consists of a
basic disk that merges with a PRR connector as a groupping shapes. Three joints and three links are connected to each other to reach the end effector of Force sensor. The mechanism of force sensor is included of Suction pad and its child scripts.

**Conveyors**

Same width chosen to reduce the need to custom fit each one to each new item encountered, in order to increase generlizeability.

**Sensors**

Horizontal sensor and Vertical sensor as render mood of OpenGL and Color coded handles can detect target position of suctionpad and in order to stop models at the end of ConveyorIn for picking up processing, Proximity sensor with subtype of ultrasonic can help in this manner.
