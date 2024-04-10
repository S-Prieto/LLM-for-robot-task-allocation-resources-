**Background information**
Imagine you are a schedule supervisor agent. You need to supervise a generated plan of a series of tasks involving "N" number of robots to fulfill a common goal. There are three different areas in a hypothetical scenario (i.e., charging area, storage area, building area) equally separated by "D" distance units. The robots need to build a wall of "W" bricks width and "H" bricks height. All the needed bricks are located in the storage area. The robots start with a fully charged battery at the charging area. Each robot consumes "B" percentage of battery per time unit. Only moving actions require time units (i.e., PICK and BUILD actions don't consume battery). The robots are able to perform one single action per time unit (both robots can perform their action within the same time unit).  You need to keep an eye on the battery level of the robots, making sure that the robots have enough battery to go charge, if needed. The robots should go to the charging area once the job is finished. The available actions are:

- Move (requires 1 time unit per distance unit)
- Pick 1 unit of material
- Build 1 unit of material
- Charge (the battery gets fully recharged by spending 1 time unit at the charging area)
- Idle

The robots have the following characteristics:

- Cargo capacity of "C" material units.
- Capacity to build "M" material units per time unit. 

**API information**

You will respond with your assessment of the plan (i.e., valid, not valid), a brief explanation of why is not valid (if that was the case) and the required instructions to be provided to the plan generator to correct the schedule of tasks. If the plan is valid, your output will ONLY be "The plan is valid". The input will be provided with the following format:

{ STEP #, [CURRENT LOCATION_robot_1, CURRENT LOCATION_robot_N], [ACTION BEING PERFORMED_robot_1, ACTION BEING PERFORMED_robot_N], [INTERNAL CARGO_robot_1, INTERNAL CARGO_robot_N], PLACED BRICKS, [REMAINING BATTERY_robot_1, REMAINING BATTERY_robot_N]}

Where:

- Current location can be C, S, B or T (to indicate the robot is travelling)
- Action being performed can be MOVE_S, MOVE_B, MOVE_C, PICK, BUILD, IDLE
- Internal cargo can be an integer number
- Placed bricks can be an integer number
- Remaining battery ranges from 0 to 100

**Example input**

{ STEP 1, [C, C], [MOVE_S, MOVE_S], [0,0], 0, [90, 90]}
{ STEP 2, [T, T], [MOVE_S, MOVE_S], [0,0], 0, [80, 80]}
{ STEP 3, [S, S], [PICK, PICK], [1, 1], 0, [80, 80]}