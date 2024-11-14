## Description
### Transport system with DC drive

![image](https://github.com/user-attachments/assets/53596982-4d8c-4cf6-b0fb-dbb9d32bd62d)


**Technical Data**

![image](https://github.com/user-attachments/assets/78f17382-22d0-42e3-890f-64a8396e24f3)

**Interface Assignment**
*PLC Inputs*

![image](https://github.com/user-attachments/assets/9fad33ff-1467-42cc-a884-e13584c06139)

*PLC Outputs*

![image](https://github.com/user-attachments/assets/3d16098e-185c-44a7-a2ad-93b0ac1dc20b)

**System Components**

![image](https://github.com/user-attachments/assets/7eb69de4-5d38-4ee2-b442-5fe3f3c3a258)

realized by means of two relays mutually interlocked at the hardware level (binary outputs
QR, QS).
1 relay for creeping motion in each direction of travel (binary output QS).
1 removable workpiece carrier (pallet).
2 limit sensors (reed contacts) for the workpiece carrier (binary outputs IL, IR).
1 pulse sensor for measuring the workpiece carrier's position and/or speed
(binary input IMP).
1 SUB-D plug for connecting the transport system via a SUB-D cable to the basic
configuration.

## Experiment descriptions

Inching mode for a conveyor belt

Inching mode with deactivation at limits

Inching mode with reversal

Position measurement/speed control

Function block for flashing

Function block for speed monitoring

*All projects are programmed in the FBD (Function Block Diagram) language
for SIMATIC Step 7.*

### Project 01 | Inching mode

*Showing simple inching mode for the conveyor belt's leftward and
rightward travel.*

Create a control routine for the conveyor belt incorporating the functions listed next.

Pressing button I_IMS1_TL causes the conveyor belt to move leftward until the button is
released (inching mode).

Pressing button I_IMS1_TR causes the conveyor belt to move rightward until the button is
released.

No deactivation takes place at limit sensors 1 and 2.

**Preparing a simple function plan for inching mode comprising the basic logical operators AND and
NOT.**

![image](https://github.com/user-attachments/assets/fb2fdf44-d194-4362-afe1-69adacf4ebce)

![image](https://github.com/user-attachments/assets/cb1860bc-cf31-4526-9df6-7554abf04418)


->Integrate FC1 into the OB1 organizational block.

->Test the control routine.

### Project 02 | Inching mode with deactivation at limits

*In this project, we will realize leftward and rightward movement for the conveyor belt, including
deactivation at its limits.*

Brief actuation of button I_IMS1_TL moves the conveyor belt leftward until limit sensor 2
is reached.

Brief actuation of button I_IMS1_TR moves the conveyor belt rightward until limit sensor 1
is reached.

A brief actuation of switch I_IMS1_ST stops the conveyor belt.

Both directions of travel are to be mutually interlocked at the software level.

Essential differences with respect to the simple inching mode:

The leftward and rightward buttons don't need to be held down.

There is a stop switch.

The belt is deactivated on attainment of either limit sensor.

Note: The limit sensors issue a 1-signal when triggered.

**Preparing a function plan for the inching mode with deactivation at limits.**

![image](https://github.com/user-attachments/assets/2f82650c-3297-44db-b0e0-391f5bcdaebd)

![image](https://github.com/user-attachments/assets/7dc3747b-f744-4b86-bbd5-4f3cefda2e23)

->Integrate FC2 into the OB1 organizational block.

->Test the control routine.

### Project 03 | Inching mode with reversal

*In this project, we will realize leftward and rightward travel including deactivation at limits and
automatic reversal.*

Create a control routine for the conveyor belt incorporating the functions listed next.

Brief actuation of button I_IMS1_TL moves the workpiece carrier left until attainment of
limit sensor 2. After 2 seconds, the workpiece carrier moves back automatically toward
the right limit.

Brief actuation of button I_IMS1_TR moves the workpiece carrier right until attainment of
limit sensor 1. After 2 seconds, the workpiece carrier moves back automatically toward
the left limit.

Brief actuation of button I_IMS1_ST stops the conveyor belt.

Both directions of travel are to be mutually interlocked at the software level.

Essential differences with respect to the inching mode without reversal:

The workpiece carrier moves back toward the other limit after 2 seconds.

Note: For realization of automatic reversal, it is advisable to use a turn-on delay in each
direction (i.e. two elements in total).

*Preparing a function plan for the inching mode with a reversal.*

![image](https://github.com/user-attachments/assets/84a76dc6-7ba8-448e-98fc-b74b5773235f)

![image](https://github.com/user-attachments/assets/57f5085d-319e-4d0a-ae2a-9ec9dbdafe6f)

->Integrate FC3 into the OB1 organizational block.

->Test the control routine.

### Project 04 | Position measurement / speed control

*Similar functions are performed on a number of technical installations possessing incremental
measurement systems, e.g. machine tools, robots etc.
The experiment on position measurement / speed control is divided into the progressive subexercises
described next.*

Sub-project 1 – position measurement: The actual position of the workpiece on the conveyor belt
in each direction of travel is to be measured by means of pulses from the pulse generator. A pulse
corresponds to a defined distance.

Sub-project 2 – speed control: In a progression of sub-exercise 1, the workpiece carrier is to
travel to the middle at full speed and then continue to the limit switch at creep speed.

**Position measurement**

Since the pulse generator is an incremental distance measuring system, the workpiece carrier must
be located at a defined reference point to start with. Let us select the left limit for this purpose. Before
starting the belt, you must therefore position the workpiece carrier manually so that the left-hand limit
sensor (2) is triggered.

The position control module must meet the requirements listed next.

If the workpiece carrier is moved right by means of button I_IMS1_TR, the pulse count
should increase. When the button is released, the motor should stop.

If the workpiece carrier is moved left by means of button I_IMS1_TL, the pulse count
should decrease. 

When the button is released, the motor should stop.

The motor should be switched off when it attains either of the limit sensors.

To save space, the prefixes I_IMS1_ and Q_IMS1_ for binary inputs and outputs have been left out
of the diagrams below.

![image](https://github.com/user-attachments/assets/fef8f35c-a6e6-4809-bfe7-ec63614b7e52)


![image](https://github.com/user-attachments/assets/d3b4ad01-6ea1-4583-be5f-2d50e349bfd9)


->Integrate FC4 into organizational block OB1.

->Test the control routine.

**Speed control**

Let us assume that the workpiece carrier is located somewhere between left-hand limit
sensor 2 (I_IMS1_IL) and the middle of the transport system, and that position
measurement from sub-exercise 1 is active.

If button TR is pushed briefly, the workpiece carrier should first move right at full speed
until it reaches the middle, and then proceed at creep speed to right-hand limit sensor 1
(I_IMS1_IR).

On attainment of this point, the motor should stop automatically.

If button I_IMS1_TL is pushed, the workpiece carrier should move left at full speed for as
long as the button is held down. Left limit sensor 2 should stop the motor.

The directions of travel should be mutually interlocked.

Note: To determine the conveyor belt's middle point, move the workpiece carrier once from
the left limit and divide the total number pulses counted over the carrier's travel by 2.

![image](https://github.com/user-attachments/assets/e2c55ffb-3722-4ebe-a2f7-98183e0fbfe5)

![image](https://github.com/user-attachments/assets/6ca608f0-b3d2-435d-9219-1a634e00806d)

### Project 05 | Flashing module

Steps and Considerations

1. Function Plan Design: The experiment starts with designing a function plan using graphical symbols to represent the logic of the FLASH function block. The plan shows the timers, their connections, and the inversion operation.

2. Function Block Realization: The function plan is then implemented in the PLC programming environment (e.g., Step 7) using the chosen programming language (e.g., FBD).

3. Integration and Testing: The FLASH function block is integrated into the main program (e.g., organizational block OB1) and tested with specific values for TI and TA.

4. Timer Type Analysis: The experiment explores the effects of using different timer types (TON, TOF, TP) on the function block's behavior.

Key Concepts

Modularity and Reusability: The experiment emphasizes the importance of creating modular code that can be reused across different applications, promoting efficiency and consistency.

Timer Functionality: It demonstrates how timers can be used to control time-based events and create specific time sequences.

Logical Operations: The use of logical operations, particularly inversion, is crucial in creating the alternating on-off pattern of the flashing signal.

Function Block Interface: The experiment defines the input and output variables of the FLASH function block, highlighting the concept of a well-defined interface for reusable software modules.

*One task detailed as part of many applications is to periodically control an alarm lamp with a
definable turn-on time TI and definable turn-off time TA (see the illustration below).*

![image](https://github.com/user-attachments/assets/4aaa484b-1866-40ba-bfd7-510d6dc92f46)

*We will write a FLASH function block whose output exhibits the time response mentioned above. The
FLASH function plan is illustrated below.*

![image](https://github.com/user-attachments/assets/95ce705a-7e24-4246-974b-928dc3b4e4e9)

This function block operates continuously.


Its input variables are:

TIMER1(TIMER): Timer address (must be defined externally for Step 7)

TA (S5TIME): Turn-on time

TIMER2 (TIMER): Timer address (must be defined externally for Step 7)

TI (S5TIME): Turn-off time

Its output variable is:

QB (BOOL): Flash signal

![image](https://github.com/user-attachments/assets/47cd4904-14b8-40ed-8184-323b42e10677)

![image](https://github.com/user-attachments/assets/efd012a2-2b7a-4468-ba5d-cbc178f2c9d6)

### Project 06 | Speed monitoring

*Conveyor equipment often requires monitoring for a minimum speed level to permit detection of
excessive friction or breakage of the drive shaft, for instance. If a diagnosis proves positive, the
conveyor belt and connected units can be de-energized to avoid blockage, and alarm lamps can be
activated.*

In this experiment, a pulse sensor is used to achieve this type of monitoring in a function block
designated "MONSPEED" (monitoring speed). If a certain time interval between pulses is exceeded,
MONSPEED recognizes that a defined minimum speed has been undershot, switches off the motor
and generates an alarm signal which must be acknowledged. The function block also accounts for
the fact that the motor is started at speed zero, and bypasses the monitoring routine accordingly
during this phase.

![image](https://github.com/user-attachments/assets/b91a99c0-dd02-4d0c-802c-c18050df1fce)

Input variables:


INIT (BOOL): Control signal for the conveyor belt's motor

IMP (BOOL): Pulse sensor signal

ACK (BOOL): Acknowledgement button

TIMER1 (TIMER): Timer address; to be specified externally for Step 7

TMON (S5TIME): Monitoring time

TIMER2 (TIMER): Timer address; to be specified externally for Step 7

TSTART (S5TIME): Speed monitor bypass time during start-up

Output variables

MOTOR (BOOL): Direct control of the conveyor belt's motor

ALARM (BOOL): Alarm signal

The function block's internal logic must meet the requirements listed next.

INIT is a signal for controlling the conveyor belt's motor; this signal is processed further by
the function block.

MOTOR is a signal used to directly control the motor via a dedicated binary output. If the
monitoring system is OK, MOTOR is equivalent to INIT. If the monitoring system
malfunctions, i.e. ALARM is issued (see below), MOTOR is always zero.
When the MOTOR signal changes from 0 to 1, the speed monitor is to remain disabled in
an initial TSTART phase to allow for the fact that the motor always starts at speed 0.

If the TSTART phase is over and the time interval between any 2 pulses from the IMP
sensor exceeds the monitoring time TMON, the MOTOR signal is to be set to zero, and
ALARM set to one. At the same time, the elapsed starting time is to be reset so that the
motor can be restarted after the alarm signal has been acknowledged.

ACK is used to reset to ALARM signal.

![image](https://github.com/user-attachments/assets/e693fad8-a62f-473d-a4c8-575a0699a6eb)

![image](https://github.com/user-attachments/assets/3a0ebbf0-a43d-485c-877b-6d9afb4eb4ab)

