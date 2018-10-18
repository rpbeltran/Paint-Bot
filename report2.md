# Inverse Kinematics Implementation
Our project determines the joint angles necessary to position the paintbrush (end-effector) by iterating over the joint space for each joint (that is, the possible locations each joint can be positioned to). 
To perform this task, basic forward kinematics are performed to check the location of each potential position. All solutions found are ranked based on which one requires the least movement from the robot's current position. 

In order to reduce the complexity of checking each possible joint position, solutions are checked repeatedly, starting with a coarse step size and gradually becoming smaller. 

The *inverse_kinematics(x,y)* method takes a desired end-effector position as an argument and returns the best solution (three joint angles), if one is found. If no valid solution is found, the method returns the robot's current joint angles.  
