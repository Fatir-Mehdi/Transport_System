# Transport_System

**Transport system with DC drive project is demonstrated to understand PLC programming for automation, including using function blocks and creating control sequences according to IEC 61131.**

![image](https://github.com/user-attachments/assets/c973cc73-2334-4e88-afbe-a34cd604c605)


## Methodology

The documents provide a structured, IEC 61131-based approach to designing control systems for transport automation.


System Requirements: Overview of components (DC motor, sensors, PLC) and task objectives.

Hardware Setup: Connection diagrams, I/O mappings, and symbol table usage for clarity.

Control Design: Starts with verbal plans, then develops function plans using FBD, ST, or GRAPH.

Programming: Implements functions (FCs) and function blocks (FBs) in main program (OB1).

## Tools Required:

PLC Programming Software: Primarily SIMATIC Step 7 and CODESYS, supporting IEC 61131 languages (FBD, ST, GRAPH) for designing and testing control programs.

Key Hardware Components:

DC Motor: Drives the conveyor belt, controlled via PLC for speed and direction.

Conveyor Belt: Transports workpieces, with control for precise movement.

Sensors: Include limit switches, pulse sensors, optical, inductive, capacitive, and magnetic sensors for detecting positions, objects, or materials.

Actuators: Magnetic valves and stop cylinders for controlling workpiece movement and positioning.

SUB-D Cables/Connectors: Ensures signal transmission and compatibility between PLC and hardware.

## Description

**The project covers several project which includes:**


Conveyor Belt Control Experiments: These experiments introduce practical application of PLC programming to control the conveyor belt.

Inching Mode: This experiment focuses on controlling the conveyor belt's movement in both directions using buttons. The conveyor belt moves as long as the button is pressed and stops when released.

Inching Mode with Deactivation at Limits: This builds upon inching mode, adding limit switches to stop the conveyor belt automatically at the predefined end positions.

Inching Mode with Reversal: This experiment involves programming the conveyor belt to automatically reverse direction when it reaches a limit switch, effectively making it move back and forth between the two end positions.

Position Measurement/Speed Control: This experiment utilizes the pulse sensor to accurately measure the position of the workpiece carrier on the conveyor belt. It also involves programming the PLC to control the speed of the conveyor belt based on its position, for example, moving at full speed until reaching a midpoint, then slowing down to a creep speed.

Function Blocks: Function blocks are reusable code modules that encapsulate specific functionalities.

Flashing Module: This involves creating a function block that controls a flashing lamp. This function block could be used for various purposes, like indicating a system status or an alarm condition.

Speed Monitor: This experiment focuses on designing a function block to continuously monitor the conveyor belt's speed. If the speed drops below a predefined threshold, this function block triggers an alarm, potentially indicating a fault or problem with the conveyor system

**For more detail go to:** [Description](Description.md)


## Skills Acquired with Transport System Files

- **Control Technology Basics**:
  - Logical operations (AND, OR, NOT)
  - Flip-flops, timers, and counters
  - Sequencers and function plans

- **PLC Programming**:
  - Proficiency in FBD and exposure to ST, GRAPH, and SCL
  - Understanding Program Organization Units (POUs)

- **Hardware Integration**:
  - Sensor and actuator interfacing
  - System behavior analysis
  - Basic PLC communication/networking

- **Troubleshooting**:
  - Analyzing program logic with VAT
  - Debugging techniques
  - Hardware verification

 ## Importance of the Project

This project, focused on developing a programmable control system for an automated transport system, highlights the essential skills required in modern industrial automation. By integrating PLC programming with hardware components such as conveyor belts, DC motors, and various sensors and actuators, the project provides a hands-on understanding of real-world control technology. It emphasizes the use of advanced tools like SIMATIC Step 7 and CODESYS, and programming methodologies in accordance with the IEC 61131 standards. This structured approach to automation fosters proficiency in designing, testing, and implementing control logic, which is vital in industries where precision and reliability are key.

Through this project, I have gained essential skills in organizing code into function blocks (FBs) for reusability, interfacing multiple sensors and actuators with the PLC, and creating complex sequences for automated operations. The project’s emphasis on modularity, clarity, and structured design closely aligns with industry standards, making it an invaluable exercise in preparing for real-world automation challenges.

## Conclusion

Completing this project has provided a comprehensive foundation in PLC programming, system integration, and troubleshooting, giving me practical experience in building and testing automated control systems. By designing control sequences and implementing logic plans, I have developed skills that are directly applicable to industrial settings, reinforcing the importance of standardized practices and modular design. This project has not only solidified my technical abilities but has also enhanced my understanding of the systematic approach needed to develop robust, scalable, and maintainable control systems in modern automation.
