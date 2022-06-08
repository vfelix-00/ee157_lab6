# Lab 6: Servo Control Lab 

Vanessa Felix

Lab Partner: Jaden Redhair 

## Overview 

In this lab, we took a hobby servo with the control board removed and designed our own
analog PID controller and PWM generator with an H-bridge driver IC. The hobby servos
were modified so that we would have access to the three potentiometer terminals, as well as the
two terminals of the brushed DC motor. 

The objectives of this lab were:
- Learn about pulse width modulation (PWM) and create a circuit that generates PWM signals that control the voltage on a brushed DC motor. 
- Learn about and create a closed-loop position control for a servo drive using an analog PID controller.
-  Experiment with and understand the practical considerations when designed position controllers for servo applications.

## Procedure summary

This lab required putting together a relatively complex circuit. Debugging circuits like this can be difficult, so we tested and verified smaller components as we built it. We practiced making neat breadboard circuits, keeping our components close to the board and minimizing large loops for signal wires. Once we confirmed that the small parts of the circuit were working, we trimmed all the wires and components down to keep things neat and double checked if it still worked. Whenever we encountered a bug, we measured signals at all stages of our circuit.


This is the summary of the circuit components we put together:

- Analog PWM generator using the Analog Discover 2 to generate a triangle wave, and making comparators with the MCP600x op-amps.
- PWM-based voltage source based on the L9110 H-bridge that will drive the brushed DC motor inside the hobby servo.
- Error amplifier using position measurement from the rotary potentiometer in the hobby servo.
- Feedback control loop. This will include a summing amplifier that adds together the signals of the proportional, integral, and derivative gain amplifiers. The output of our PID terms are going to be ”fed back” and set the PWM duty cycle of our H-bridge.

## Circuit Diagram


![EE157_Lab_6_Lab_Handout](https://user-images.githubusercontent.com/71578472/172559406-f0c509db-db40-4d37-994d-fe43b16dd870.jpeg)


## Submission Items

1. In figure 3, the carrier waveform is set to 15 kHz. Why do you think this frequency was chosen? What are the factors to consider when selecting a PWM frequency for a motor driver bridge?

I think the frequency 15 kHz was chosen since it is a realtively low frequency. This allows the opamps to keep up. It is also in the mid-range for op amp operation. Factors to consider in a PWM are probably the shape, switching frequency, and duty cycle. This frequency may also balance the switching losses associated with turning transistors on and off. 

2. Estimate the friction torque of the gearbox. Please refer to the motor specsheet in the pre-lab handout. (Hint, you may want to measure the resistance of the motor coils to estimate the current). Show your reasoning.

We observed that the motor overcame friction at 300 mV and it had a coil resitance of 5 ohms. So, the current supplied was 0.06 Amps. This means that the power output was 18 mW, making the friction about 18 mNm.

3. Find the gain and period of oscillation when the system begins sustained self-oscillation. Use these values to calculate some initial guesses for the Kp, Ki, and Kd coefficient using the “some overshoot” Ziegler-Nichols method.

We were able to find that a gain of 120 allowed a sustained oscillation. We then calculated Kp = 0.00276, Ki = 0.1083, and Kd = 4.745e-5.

<img width="982" alt="lab6_q3" src="https://user-images.githubusercontent.com/71578472/172556883-60a8b2ed-fea7-4be8-8580-d38b049be240.png">

4. Now reduce the gain to just below threshold where oscillations are sustained. Give the system a step command voltage. Show a scope capture including the command voltage and position feedback voltage for a 1V step command. If you are using a square wave position command, make sure period is long enough for the position to settle.

<img width="986" alt="lab6_q4" src="https://user-images.githubusercontent.com/71578472/172557177-cd91bfee-1f02-484c-a189-47d6cf400741.png">

5. Describe what you see. Is there overshoot? Is there steady state error?

We saw that there is overshoot. 

6. Now reduce the proportional gain even further (to about 1/4 of the previous value). Show a scope capture of the step response and compare the results.

<img width="977" alt="lab6_q6" src="https://user-images.githubusercontent.com/71578472/172557531-65f4e378-68ee-415f-9f2b-907564279176.png">

12. Do you think the Ziegler-Nichols method was appropriate for this servo? What are the non-idealities of our servo that might give the Ziegler-Nichols method trouble?

I don't think so. Since, the back-EMF is not linear, Ziegler-Nicols method was not appropriate because of non-idealities/non-linearities that the servo system introduces. 

## Motor Oscillating 







