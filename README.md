# MobileRobot-Openloopcontrol
## Aim:

To develop a python control code to move the mobilerobot along the predefined path.

## Equipments Required:
1. RoboMaster EP core
2. Python 3.7

## Procedure

Step1:

Use from robomaster import robot.

Step2:

Choose the x,y,z - axis movement distance(meters).

Step3:

Give ep_chassis.move to move straight.

Step4:

Give time.sleep() for a break.

Step5:

Give ep_chassis.drive_speed to have a circular movement.

## Program
```
from robomaster import robot
import time
from robomaster import camera

if _name_ == '_main_':
    ep_robot = robot.Robot()
    ep_robot.initialize(conn_type="ap")

    ep_chassis = ep_robot.chassis
    ep_led = ep_robot.led
    ep_camera = ep_robot.camera
          
    print("Video streaming started.....")
    ep_camera.start_video_stream(display=True, resolution = camera.STREAM_360P)
    ''' 
    x = x-axis movement distance,( meters) [-5,5]
    y = y-axis movement distance,( meters) [-5,5] 
    z = rotation about z axis ( degree)[-180,180]
    xy_speed = xy axis movement speed,( unit meter/second)  [0.5,2]

    '''
    ep_chassis.move(x=2, y=0, z=0, xy_speed=1).wait_for_completed()
    ep_led.set_led(comp="all",r=255,g=100,b=0,effect="on")  
    ep_chassis.move(x=0, y=0, z=-90, xy_speed=1).wait_for_completed()
    ep_led.set_led(comp="all",r=255,g=0,b=0,effect="on")  
    time.sleep(2)
    ep_chassis.move(x=2, y=0, z=0,xy_speed=1).wait_for_completed()
    ep_led.set_led(comp="all",r=255,g=255,b=0,effect="on")  
    ep_chassis.move(x=0, y=0, z=-90, xy_speed=1).wait_for_completed()
    ep_led.set_led(comp="all",r=0,g=255,b=255,effect="on")  
    time.sleep(2)
    ep_chassis.move(x=2, y=0, z=0, xy_speed=1).wait_for_completed()
    ep_led.set_led(comp="all",r=255,g=102,b=0,effect="on")  
    ep_chassis.move(x=0, y=0, z=-90, xy_speed=1).wait_for_completed()
    ep_led.set_led(comp="all",r=255,g=153,b=204,effect="on")  
    time.sleep(2)
    ep_chassis.move(x=2, y=0, z=0, xy_speed=1).wait_for_completed()
    ep_led.set_led(comp="all",r=153,g=204,b=0,effect="on")  

    ep_camera.stop_video_stream()
    print("Stopped video streaming.....")

    ep_robot.close()

```
## circular_movement.py
```
from robomaster import robot
import time

if _name_ == '_main_':
    ep_robot = robot.Robot()
    ep_robot.initialize(conn_type="ap")

    ep_chassis = ep_robot.chassis

    '''
    x = speed in x direction( meter/second) [-3.5,3.5]
    y = speed in y direction( meter/second) [-3.5,3.5]
    z = rotation about z axis ( degree/second)[-600,600]
    '''
    ep_chassis.drive_speed(x=0,y=0.2,z=15)
    time.sleep(20)
    ep_chassis.drive_speed(x=0,y=0,z=0)

    ep_robot.close()
```

## led_blink.py
```
rom robomaster import robot
import time


if _name_ == '_main_':
    ep_robot = robot.Robot()
    ep_robot.initialize(conn_type="ap")

    ep_led = ep_robot.led
    '''
    comp – enum: (“all”, “top_all”, “top_right”, “top_left”, “bottom_all”, “bottom_front”, “bottom_back”, “bottom_left”, “bottom_right”) lighting parts, all: all armor lights ;top_all: all armored lights of the gimbal; top_right: armored lights on the right side of the gimbal; top_left: armored lights on the left of the gimbal; bottom_all: all armored lights on the chassis; bottom_front: front armored lights; bottom_back: rear armored lights; bottom_left: left armored lights light; bottom_right: right armor light
    r – int: [0~255], RGB red component value
    g – int: [0~255], RGB green component value
    b – int: [0~255], RGB blue component value
    effect – enum: (“on”, “off”, “flash”, “breath”, “scrolling”) lighting effect type, on: always on; off: always off; flash: blinking; breath: breathing; scrolling: horse racing Lamp (only valid for PTZ lamp)
    '''
    for i in range(2):
        ep_led.set_led(comp="all",r=255,g=215,b=0,effect="on")   
        time.sleep(2)
        ep_led.set_led(comp="all",r=255,g=69,b=0,effect="on")
        time.sleep(2)
        ep_led.set_led(comp="all",r=255,g=105,b=180,effect="on")
        time.sleep(2)        
    
    print("Completed...")
    ep_robot.close()
```

## linear_movement.py
```
if _name_ == '_main_':
    ep_robot = robot.Robot()
    ep_robot.initialize(conn_type="ap")

    ep_chassis = ep_robot.chassis

    '''
    x = x-axis movement distance,( meters) [-5,5]
    y = y-axis movement distance,( meters) [-5,5]
    z = rotation about z axis ( degree)[-180,180]
    xy_speed = xy axis movement speed,( unit meter/second) [0.5,2]
    '''
    ep_chassis.move(x=2, y=0, z=0, xy_speed=0.75).wait_for_completed()

    ep_chassis.move(x=0, y=0, z=55, xy_speed=1).wait_for_completed()

    ep_chassis.move(x=1.6, y=0, z=0, xy_speed=0.75).wait_for_completed()

    ep_chassis.move(x=0, y=0, z= -95, xy_speed=0.75).wait_for_completed()

    ep_chassis.move(x=1.5, y=0, z=0, xy_speed=0.75).wait_for_completed()


    ep_robot.close()
```

## MobileRobot Movement Image:

![image](https://github.com/DHARINIPV/mobilerobot-openloopcontrol/assets/119400845/25e4bea5-9b70-4771-9a45-cce7f1d9f3a2)

![image](https://github.com/DHARINIPV/mobilerobot-openloopcontrol/assets/119400845/58d3bb38-c4ef-44e1-b03e-f55596acb643)


## MobileRobot Movement Video:

Youtube Link : (https://youtu.be/AfWMcAk0HtY)

## Result:
Thus the python program code is developed to move the mobilerobot in the predefined path.

```
Mobile Robotics Laboratory
Department of Artificial Intelligence and Data Science/ Machine Learning
Saveetha Engineering College
```
