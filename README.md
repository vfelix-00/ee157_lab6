# Lab 6: Servo Control Lab 

Vanessa Felix

Lab Partner: Vivian Auduong, Jaden Redhair 

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

## Submission Items

1. In figure 3, the carrier waveform is set to 15 kHz. Why do you think this frequency was chosen? What are the factors to consider when selecting a PWM frequency for a motor driver bridge?

I think the frequency 15 kHz was chosen since it is a realtively low frequency. This allows the opamps to keep up. It is also in the mid-range for op amp operation. Factors to consider in a PWM are probably the shape, switching frequency, and duty cycle.



