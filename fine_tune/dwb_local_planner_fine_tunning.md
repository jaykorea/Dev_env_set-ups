# if the roobt keeps rotating near obstacle
When the robot rotates in place instead of moving towards the goal point, it is likely that the robot's path is being blocked by an obstacle, and the local planner is trying to find a way around it. This behavior is known as oscillation, and it can occur when the planner cannot find a clear path to the goal.

There are a few ways to deal with oscillation in DWB local planner:

Increase the oscillation_reset_dist parameter in the Oscillation critic. This parameter determines the distance the robot must travel before the oscillation counter is reset. Increasing this parameter can help the planner recover from oscillation more quickly.

Increase the xy_goal_tolerance parameter to allow for more tolerance in the goal position. This parameter determines the radius around the goal position that is considered acceptable. Increasing it may help the planner find a clearer path to the goal.

Adjust the obstacle inflation parameters to allow for more clearance around obstacles. This can be done by adjusting the scale parameter in the BaseObstacle critic or by using the ObstacleFootprint critic to specify a larger robot footprint.

Reduce the max_vel_theta and min_vel_theta parameters to limit the robot's rotation speed. This can help the planner avoid overshooting the goal and getting stuck in an oscillation loop.

Increase the sim_time parameter to allow for longer trajectories to be generated. This can help the planner find a clearer path to the goal by exploring more potential trajectories.

It may also be helpful to visualize the planner's output and observe its behavior as it navigates around obstacles. You can do this by enabling the publish_cost_grid_pc, publish_local_plan, and publish_global_plan parameters and visualizing the corresponding topics in RViz. This can help you diagnose any issues with the planner's behavior and identify areas where it may need further tuning.
