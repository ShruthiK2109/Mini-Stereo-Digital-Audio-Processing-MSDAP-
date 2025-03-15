# Mini-Stereo-Digital-Audio-Processing-MSDAP-
The Mini Stereo Digital Audio Processor (MSDAP) is a specialized, low-power digital audio processing chip designed for high-efficiency stereo Finite Impulse Response (FIR) filtering. Unlike conventional general-purpose DSP chips, MSDAP is optimized exclusively for linear convolution-based FIR filtering, enabling significantly lower cost, reduced power consumption, and streamlined hardware complexity.

How MSDAP Differs from Conventional Processors:

I. Application-Specific Design – Unlike general DSPs that handle multiple signal processing tasks, MSDAP is purpose-built for FIR filtering, reducing unnecessary computational overhead.

II. Power-Efficient Architecture – Consumes 5-10x less power than general DSP chips by eliminating redundant hardware components.

III. Cost-Effective – Achieves up to 10x cost reduction, making it ideal for portable and embedded audio systems.

IV. Optimized Computation – Implements Power-of-Two (POT) coefficient encoding, replacing multiplications with fast shift-and-add operations, boosting efficiency without sacrificing precision.

Key Features:

Dual-Channel Processing – Supports real-time stereo FIR filtering for high-fidelity audio applications.

Compact Memory Footprint – Integrates optimized data and program RAMs for seamless storage and execution.

Scalability – Handles FIR filters with order up to 255 while maintaining high performance.

Adaptive Clocking – Operates at variable system clock rates (up to 24.58 MHz) to match industry-standard audio sampling rates (32 kHz, 44.1 kHz, 48 kHz).

Low Latency – Implements a streamlined data flow with minimal computational delays, ensuring real-time audio processing.

MSDAP is an innovative alternative to power-hungry DSP chips, offering high-performance digital audio processing while minimizing hardware complexity and power consumption. 

Key Deliverables:

1. MSDAP Algorithm implementation in C++:
   
This gives the implementation of a Fixed-Point FIR (Finite Impulse Response) Filter using C/C++. It was developed as part of the Application-Specific Integrated Circuit (ASIC) Design course at The University of Texas at Dallas (EEDG 6306).

Overview:

The goal is to implement the MSDAP linear convolution operation for a 256-tap FIR filter using fixed-point arithmetic. The implementation is optimized for hardware design considerations, avoiding floating-point operations and standard multiplication. Instead, all computations rely on bitwise shifts, additions, and subtractions.

Key Features:

Implements a 256-tap FIR filter using power-of-two (POT) coefficients.

Reads filter coefficients from coeff.in and input data from data1.in or data2.in.

Processes 1000 input samples with fixed-point arithmetic.

Outputs 40-bit fixed-point results in hexadecimal format (output.out).


2.MSDAP FSM Implementation in Verilog:

The goal of this part of the project is to design and implement a Finite State Machine (FSM) for the Mini Stereo Digital Audio Processing (MSDAP) chip. This FSM controls the flow of audio data through different stages, including initialization, data reception, processing, and output generation, ensuring precise synchronization and efficient power management.

Implementation of MSDAP FSM:
The Finite State Machine (FSM) is implemented using Verilog for the Mini Stereo Digital Audio Processing (MSDAP) chip. The implementation follows these steps:

FSM Design:

Defined 9 states to control the flow of audio data, handling initialization, data input, processing, and power management.

Hardware Implementation:

Registers and Memory: Store Rj values, coefficients, and audio samples.

Clock Synchronization: Uses Sclk (26.88 MHz) and Dclk (768 kHz) for precise timing.

Data Processing Flow:

Reads 16-bit input samples, extends them to 40-bit, and sends processed output via OutputL.

Power Management:

The FSM enters sleep mode when detecting 800 consecutive zeroes, reducing power consumption.

Testbench & Verification:

A testbench generates input signals, drives FSM state transitions, and verifies output using simulation waveforms.

3. MSDAP Architecture design:
   
This part of the project explains the architecture of MSDAP. 

Key Functional Blocks Implemented:

1. MSDAP Control Unit
Manages FSM state transitions and overall system control.
Handles clock synchronization (Sclk, Dclk).
Controls sleep mode activation when 800 zeroes are detected.

3. Memory Banks (Rj, Coefficients, and Data Memory)
Rj Memory: Stores reference values (Rj), required for computations.
Coefficient Memory: Holds 512 locations of filter coefficients for processing.
Data Memory: Implements a circular buffer for input storage (256 locations).

5. Serial In Parallel Out (SIPO) Unit
Converts incoming serial 16-bit input data into parallel form.
Captures input data on the rising edge of Dclk.
Signals readiness to write data to memory.

7. Zero Detector Unit
Monitors consecutive zeroes in input data.
Triggers sleep mode when 800 zeroes are detected.

9. Arithmetic Logic Unit (ALU) Control Block
Executes addition/subtraction based on coefficient values.
Controls shifting and accumulation of processed data.

11. Adder and Shift-Accumulate Unit
Performs 40-bit addition/subtraction for each input sample.
Implements bit-wise shift and accumulate operations.

13. Parallel In Serial Out (PISO) Unit
Converts processed parallel 40-bit data back into serial format.
Ensures proper synchronization before output transmission.

4. MSDAP Final Design:

Key goals of the final design:

1. RTL Verilog code for MSDAP was written and tested using testbench.
Each functional block of the MSDAP was designed in RTL Verilog and the functionality was verified using a testbench in ModelSim.

2. Logic Synthesis using Synopsys Design Compiler - Design Vision.
Synthesis was done successfully for the complete MSDAP design and various design reports (area, power, timing and cell) was generated.

3. Timing report was generated and slack was MET.

4. ASIC Design flow of MSDAP is successfully done.

Summary of Results:

Total Cell area = 2166284.7934

Total cells = 16

Total Dynamic power = 45.88 mW

Cell Leakage Power = 76.1606 uW

Sclk frequency = 39.03ns 

Dclk frequency = 1302.35ns

Slack = MET (0.28)

