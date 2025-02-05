Name: YESUPOGU PAPAIAH

Company: CODTECH IT SOLUTIONS

ID: CT08KOK

Domain: VLSI

Duration: JAN 10th TO FEB 10th 2025.

Mentor: NEELA SANTHOSH KUMAR 



## Overview of the Project

### Project: DIGITAL-FILTER-DESIGN


FIR Filter Design and Simulation in Verilog
This project involves the design and simulation of a Finite Impulse Response (FIR) filter using Verilog. The aim was to implement a simple 3-tap FIR filter that processes an 8-bit input signal and produces a 16-bit output signal. The filter was simulated using Icarus Verilog on EDA Playground. This report outlines the design, simulation, and performance analysis of the FIR filter.

1. FIR Filter Design
A FIR filter is a type of digital filter whose output is based on a weighted sum of current and past input values. The output 
𝑦
[
𝑛
]
y[n] of an FIR filter is given by:

𝑦
[
𝑛
]
=
∑
𝑘
=
0
𝑀
−
1
ℎ
[
𝑘
]
⋅
𝑥
[
𝑛
−
𝑘
]
y[n]= 
k=0
∑
M−1
​
 h[k]⋅x[n−k]
Where:

𝑥
[
𝑛
]
x[n] is the input signal,
ℎ
[
𝑘
]
h[k] are the filter coefficients,
𝑦
[
𝑛
]
y[n] is the output signal.
For this project, a 3-tap FIR filter was used with coefficients:

ℎ
[
0
]
=
1
h[0]=1,
ℎ
[
1
]
=
2
h[1]=2,
ℎ
[
2
]
=
1
h[2]=1.
These coefficients resulted in a simple filter that uses the current input and the two previous inputs to compute the output. This type of filter is commonly used in real-time signal processing tasks like audio processing.

2. Verilog Implementation
The FIR filter was implemented as a synchronous Verilog module that processes the input signal on each clock cycle. The module consists of the following:

Registers for storing input values: The previous two input samples are stored in x_reg[0], x_reg[1], and x_reg[2].
Filter computation: At every positive clock edge, the filter computes the output 
𝑦
y by multiplying the stored input values by the corresponding filter coefficients and summing them.
The filter's implementation in Verilog is straightforward, and it is designed to reset its outputs and registers when the reset signal is asserted.

3. Testbench Design
The testbench for the FIR filter includes:

Clock generation: The clock is toggled every 5 time units.
Reset signal: A reset is applied initially to initialize the filter.
Input stimulus: A series of 8-bit input values (x) are applied to the filter.
Waveform generation: The $dumpfile and $dumpvars commands were added to generate a VCD file, enabling visualization of the signal transitions.
The testbench applies a variety of input values (from 1 to 5) and observes the output (y). The output was monitored in both the console and the VCD waveform.

4. Simulation and Results
The simulation was run on EDA Playground using Icarus Verilog. The results confirmed the correct operation of the FIR filter. In the console, the input and output values were printed at each simulation step, showing the weighted sum of the current and previous inputs. The VCD file, generated during the simulation, was downloaded and visualized using a waveform viewer like EPWave.

The simulation confirmed that the filter processed the input values and generated the expected output values. The input signal values were shifted through the registers, and the output was computed as the sum of the weighted inputs.

5. Performance Analysis
The FIR filter demonstrated the following:

Correct output behavior: The output matched the expected weighted sum of inputs, confirming proper filter functionality.
Efficiency: The filter operates in linear time relative to the number of taps, making it efficient for small-scale applications.
Hardware utilization: While not explicitly measured, the filter design is minimal in terms of logic resources, with the complexity primarily determined by the number of taps.
The use of a 3-tap filter allowed for quick simulation and easy observation of the filter’s behavior.

6. Conclusion
This project successfully demonstrated the design and simulation of a 3-tap FIR filter using Verilog. The filter processed the input signal correctly, and the results were validated through both console output and VCD waveform visualization. The project highlights the practicality of implementing FIR filters in hardware description languages like Verilog and serves as a foundation for more complex signal processing tasks. Future improvements could involve expanding the number of taps or modifying the filter coefficients for specific applications.



### Output: 
![output](https://github.com/yesupogupapaiah/DIGITAL-FILTER-DESIGN/blob/main/task4.png)
