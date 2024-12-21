
# Object Detection Robot

## Overview

This project implements an autonomous robot with object detection and avoidance capabilities using an ultrasonic sensor, servo motor, and DC motors. The robot detects objects in its path, determines the optimal direction to turn, and navigates around obstacles.

## Features

- Detects objects within a specified distance using an ultrasonic sensor.
- Dynamically adjusts motor speeds to navigate and avoid obstacles.
- Uses a servo motor to scan the environment and identify the best path forward.
- Supports real-time distance monitoring via serial output for debugging.

## Hardware Requirements

1. Arduino board (e.g., Arduino Uno)
2. Ultrasonic sensor (e.g., HC-SR04)
3. Servo motor
4. Two DC motors with motor driver (e.g., L298N or equivalent)
5. Power supply for motors and Arduino
6. Chassis and wheels for the robot

## Pin Configuration

- **Servo Motor:**
  - Control Pin: Pin 3
- **Ultrasonic Sensor:**
  - Trigger Pin: Pin 11
  - Echo Pin: Pin 12
- **Right Motor:**
  - Enable Pin: Pin 5
  - Control Pins: Pins 7, 8
- **Left Motor:**
  - Enable Pin: Pin 6
  - Control Pins: Pins 9, 10

## Software Requirements

- Arduino IDE

## How It Works

1. The robot uses an ultrasonic sensor to measure the distance to objects in its path.
2. If an object is detected within 30 cm:
   - The robot stops and reverses slightly.
   - The servo motor rotates to scan the left and right sides for obstacles.
   - The robot compares distances on both sides and turns toward the side with more free space.
3. If no object is detected, the robot moves forward.
4. Distance measurements and movements are logged to the serial monitor for debugging purposes.

## Code Explanation

The provided code is structured into the following parts:

1. **Setup Function:**
   - Initializes pins, servo position, and serial communication.
2. **Loop Function:**
   - Continuously checks the distance to obstacles and adjusts motor actions accordingly.
3. **Motor Control:**
   - The `rotateMotor` function controls the speed and direction of the motors.
4. **Object Detection Logic:**
   - The robot uses the ultrasonic sensor to determine distances and decide its movement.

## How to Use

1. Assemble the hardware components as per the pin configuration.
2. Install the Arduino IDE and add the required libraries (`Servo.h` and `NewPing.h`).
3. Upload the provided code to the Arduino board.
4. Place the robot on a flat surface and power it on.
5. Monitor the serial output for real-time distance readings and movement logs.

## Libraries Used

- **Servo.h:** For controlling the servo motor.
- **NewPing.h:** For efficient ultrasonic sensor measurements.

## Customization

- **Adjust Distance Threshold:** Modify the `DISTANCE_TO_CHECK` constant to change the object detection range.
- **Motor Speeds:** Adjust `MAX_REGULAR_MOTOR_SPEED` and `MAX_MOTOR_ADJUST_SPEED` to control motor behavior.

## Troubleshooting

1. **Robot Not Moving:**
   - Check motor connections and ensure the motor driver is powered.
2. **Distance Not Detected:**
   - Verify the ultrasonic sensor connections and orientation.
3. **Inconsistent Behavior:**
   - Ensure the servo motor is correctly centered at 90° during initialization.

## Future Improvements

- Add IR sensors for improved obstacle detection.
- Implement advanced algorithms like SLAM (Simultaneous Localization and Mapping) for navigation.
- Integrate a camera for visual object recognition.

## Author

This project is developed as a learning exercise in robotics and embedded systems. Feel free to customize and expand upon the design!
