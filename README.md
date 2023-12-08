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
| Output | 1 | T | --- | --- | --- |
| Output | 2 | T | --- | --- | --- |
| Data Capturing | 3 | T | --- | --- | --- |
| ^ | 4 | T | --- | --- | --- |
| Control | 5 | T | --- | --- | --- |
| Control | 6 | T | --- | --- | --- |
| Weight/Dimensions | 7 | T | --- | --- | --- |
| Power | 9 | T | --- | --- | --- |
| Power | 10 | T | --- | --- | --- |
        
