#!/usr/bin/env pybricks-micropython

from pybricks import ev3brick as brick
from pybricks.ev3devices import (Motor, TouchSensor, ColorSensor,
                                 InfraredSensor, UltrasonicSensor, GyroSensor)
from pybricks.parameters import (Port, Stop, Direction, Button, Color,
                                 SoundFile, ImageFile, Align)
from pybricks.tools import print, wait, StopWatch
from pybricks.robotics import DriveBase

# Write your program here
motor1 = Motor(Port.A)
motor2 = Motor(Port.D)
sensor = GyroSensor(Port.S4, direction = Direction.CLOCKWISE)
robot = DriveBase(motor1, motor2, 54, 155)

sensor.mode = 'GYRO-RATE'

while True:
    while sensor.speed() + 20 > 50:
        robot.drive(200, 0)
        print(sensor.speed())
    while sensor.speed() + 20 < -50:
        robot.drive(-200, 0)
        print(sensor.speed())
    robot.stop(stop_type = Stop.COAST)
    print(sensor.speed())
