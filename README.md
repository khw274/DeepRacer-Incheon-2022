# deepracer
# AWS DeepRacer Championship
# 베스트 모델

import math
def reward_function(params):
    all_wheels_on_track=params['all_wheels_on_track']
    if all_wheels_on_track :
        reward1 = 2
    else:
        reward1 = 1e-3
    speed = params['speed']
    
    if speed > 2 :
        reward2 = 1
    elif speed > 1 :
        reward2 = 0.5
    else:
        reward2 = 1e-3
    distance_from_center = params['distance_from_center']
    track_width = params['track_width']
  
    if distance_from_center < 0.3 * track_width :
        reward3 = 1
    else:
        reward3 = 1e-3
   
    abs_steering = abs(params['steering_angle'])
    waypoints = params['waypoints']
    closest_waypoints = params['closest_waypoints']
    heading = params['heading']
    next_point = waypoints[closest_waypoints[1]]
    prev_point = waypoints[closest_waypoints[0]]
    speed=params['speed']
    track_direction = math.atan2(next_point[1] - prev_point[1], next_point[0] - prev_point[0])
    track_direction = math.degrees(track_direction)  
    steering_angle=params['steering_angle']
  
    if track_direction>heading:
        if steering_angle==True:
            reward4=1
        else:
            reward4=1e-3   
    else:
        if steering_angle==False:
            reward4=1e-3
        else:
            reward4=1
    direction_diff = abs(track_direction - heading)
    if direction_diff > 180:
        direction_diff = 360 - direction_diff
    reward5=1-0.05*direction_diff
    reward = reward1 + reward2 + reward3 + reward4 + reward5
    
  
    
    return float(reward)





Environment simulation
The 2019 DeepRacer Championship Cup

Gradient descent batch size	64
Entropy	0.01
Discount factor	0.999
Loss type	Huber
Learning rate	0.0003
Number of experience episodes between each policy-updating iteration	20
Number of epochs	10

Action space type
Continuous
Action space
Speed: [ 1.5 : 3 ] m/s
Steering angle: [ -10 : 30 ] °
