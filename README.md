# MechatronicsProject
Project Description: Hip Exoskeleton Final Project for Introduction to Mechatronics

This project can be implemented on a hip exoskeleton to conduct state estimation and positional control.
This project takes in sensor values and calculates the hip angular displacement, velocity and checks for heel strikes.
Based on the hip joint angles in each stride, the machine will change states between Level Walking, Incline and Decline.
It will also provide positional control to a thigh strut using the hip joint angles.

    Sensors: Gyroscope PMOD - Placed directly on the leg using a Sensor Mount
                            - Used to obtain gyroscope data which is used to calculate hip angular displacement and velocity
                            
             Accelerometer PMOD - Placed on the strut mounted on the motor
                                - Used to obtain accelerometer data which is used to calculate IMU spikes in the vertical direction
                                
    Actors: Pololu S03TXF STD Servo Motor - Attached to the hip actuator mount with a Motor Mount, has a thigh strut attached to it
                                          - Positional control is used to keep the thigh strut aligned with the leg
                                          
            LEDs - Attached on the breadboard on top of the myRio controller
                 - Displays the current state (Level-walking, Incline, Decline)

File Descriptions:

    Filename: Final_Project_HipExo.lvproj
        This should be used to begin/open the Final Project

    Filename: HipExo.vi
        This is the main file containing majority of the code and coordination required to conduct state estimation and positional control.

    Filename: GYRO_Read_Plot.vi
        This SubVI configures the Gyroscope PMOD, reads and plots the output data.

    Filename: Interrupts.vi
        This SubVI looks out for any interrupts inputted by the various Pmods.

    Filename: ACL_Read_Plot.vi
        This SubVI configures the Accelerometer PMOD, reads and plots the output data.

    Filename: state_typedef.ctl
        This is the type def variable used to control the changing states

CAD Descriptions:

    Filename: pololumotormount.SLDPRT
        This part is used to mount the motor to the Actuator Mount

    Filename: ActuatorMount_SweepBased_YM_v3.SLDPRT
        This part curves around the waist and holds the actuator

    Filename: LowerBackInterface_withCurvature_MW.SLDPRT
        This part connects the Actuator Mount on each side
        
    Filename: thighstrut.SLDPRT
        This part is mounted on the actuator and also holds the accelerometer

    Filename: IMU with curved handles.SLDPRT
        This part is mounted on the leg with a velcro-strap and holds the GYRO PMOD

Requirements:

| Category | No. | Threshold/Objective | Requirement | Value | Unit |
| --- | --- | --- | --- | --- | --- |
| Output | 1 | T | Motor outputs positions commanded by MyRio | T/F | |
| Output | 2 | T | LEDs indicate when the ambulation mode is changed | T/F | |
| Data Capturing | 3 | T | System will read Accelerometer values every 5ms | 5 | ms |
| Data Capturing | 4 | T | System will read Gyroscope values every 5ms | 5 | ms |
| Control | 5 | T | System can classify different modes of ambulation | 3 | modes |
| Control | 6 | O | System outputs position based on the classified ambulation mode | T/F | |
| Weight/Dimensions | 7 | T | Prototype Weight (+/-) | 3 | Kgs |
| Power | 9 | T | Prototype shall operate for 30 minutes without the need to change batteries | 30 | minutes |
| Power | 10 | O | Prototype shall operate for 2 hours without the need to change batteries | 2 | hours |

We chose the following requirements to acheive our goal of creating an hip exoskeleton which conducts
state estimation and positional control. For this we needed the motor to change positions based on the commands
and the LEDs to change colors when the ambulation mode was changed. Secondly, we needed both our sensors to
read values atleat every 5 ms to reduce the delay in movement. The exoskeleton should also be able to classify
a altitude increasing and decreasing motion along with a maintaining altitude. Therefore we set the threshold as
3 states (Level walking, Incline and Decline). We needed the system to output appropriate position based on the states
to ensure that the thigh strut can successfully follow the leg. Lastly, we wanted to have a prototype weight which is 
lower than 3 Kgs and run for atleast 30 minutes as any higher weight or lower battery time would cause a hinderance to
the wearer.

The designs for the various parts used for this project are saved as .SLDPRT files in the CAD folder of the Github Repository.
The video demonstrations for this project are placed in the Media Folder of the Github Repository.

Challenges Encountered:

- Configuring the motor to reduce the delay and provide positional control.
- The Accelerometer gets thrown off by the other foot's heel strikes.
- The joint angle values are derived from the gyroscope values and thrus slowly accumulate error.
- The motor is too weak to provide meaningful support to a human leg

Conclusion and next steps:

Our completed project met all the requirements described in our table. We are able to reliably estimate state based
on the collected sensor data and provide positional control to our actuators.

Next steps should include using a motor with a motor encoder instead of relying on a Gyroscope PMOD. Secondly
the motor can provide torque control support instead of positional control. A battery can also be used to power
the myRio controller and the motor.



