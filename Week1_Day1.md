Week 1 — Day 1: Introduction to Verilog RTL Design & Synthesis

Welcome to **Day 1** of the RTL Workshop!  
Today, we embark on the journey into digital design by learning **Verilog**, open-source simulation with **Icarus Verilog (iverilog)**, and the basics of logic synthesis using **Yosys**.  
This guide contains essential concepts, practical labs, and explanations to help build a strong foundation in RTL design.


## Table of Contents
1. # 1-what-is-a-simulator-design-and-testbench
2. # 2-getting-started-with-iverilog
3. # 3-lab-simulating-a-2-to-1-multiplexer
4. # 4-verilog-code-analysis
5. # 5-introduction-to-yosys--gate-libraries
6. # 6-synthesis-lab-with-yosys
7. # 7-summary


## 1. What is a Simulator, Design, and Testbench?

**Simulator**  
A simulator is a software tool that checks your digital circuit’s functionality by applying test inputs and viewing outputs. This helps verify the design before actual hardware implementation.

**Design**  
The design is your Verilog code describing the intended logic functionality.

**Testbench**  
A testbench is a simulation environment that applies various inputs to your design and checks if the outputs are correct.


## 2. Getting Started with iverilog

`iverilog` is an open-source simulator for Verilog.  
Here’s the typical simulation flow:

1️ Both the **design** and **testbench** are provided as input to iverilog.  
2️ The simulator produces a `.vcd` file which can be viewed using **GTKWave**.


## 3. Lab: Simulating a 2-to-1 Multiplexer

Let's simulate a simple 2-to-1 multiplexer using iverilog.

### 🪜 Step 1: Clone the Workshop Repository
```bash
git clone https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git
cd sky130RTLDesignAndSynthesisWorkshop/verilog_files
# Compile the design and testbench
iverilog good_mux.v tb_good_mux.v
module good_mux (input i0, input i1, input sel, output reg y);
always @ (*)
begin
    if(sel)
        y <= i1;
    else 
        y <= i0;
end
endmodule
Inputs: i0, i1 (data), sel (select line)

Output: y (registered output)

Logic: If sel = 1, then y = i1; if sel = 0, then y = i0.


# Run the simulation
./a.out

# View the waveform
gtkwave tb_good_mux.vcd
exit



