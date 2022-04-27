# Sky130-RTL-Design-And-Synthesis-Using-Verilog

This repository shows the contents  and labs covered in the [RTL Desing using Verilog with Sky130 Technology](https://www.vlsisystemdesign.com/rtl-design-using-verilog-with-sky130-technology/) workshop.

![](https://github.com/Deepak42074/Sky130-RTL-Design-And-Synthesis-Using-Verilog/blob/main/DAY_1/VSD_Workshop_Detail.png)



# Table of Contents

1. [Introduction](#introduction)
   1. [What is logic synthesis](#what-is-logic-synthesis-)
   2. [Synthesis Steps](#synthesis-steps)
   3. [Inputs To The Synthesis Process](#inputs-to-the-synthesis-process)
   4. [Output Of The Synthesis Process](#output-of-the-synthesis-process)
2. [Day1 - Introduction to Verilog RTL Design and Synthesis](#day1---introduction-to-verilog-rtl-design-and-synthesis)
   1. [Setting Up the Lab](#setting-up-the-lab)
   2. [Simulating the Designs with iverilog](#simulating-the-designs-with-iverilog)
   3. [Synthesis with Yosys](#synthesis-with-yosys)

8. [Acknowledgements](#acknowledgements)
9. [References](#references)


* Register Tranfer level:

# Day1 - Introduction to Verilog RTL Design and Synthesis
The first day of the workshop covers the brief description of iverilog simulator, Test Bench setup, iverilog simulation flow  and lab using iverilog, gtkwave, yosys tools.
1. ## Introduction to iverilog, Design and Test Bench
	* Icarus Verilog (iverilog) : It is a verilog simulation and synthesis tool. It operates as a compiler, compiling source code written in Verilog (IEEE-1364) 	       into some target format.Icarus Verilog is an open source Verilog compiler that supports the IEEE-1364 Verilog HDL including IEEE1364-2005 plus.
	
	* RTL Design : It is the actual verilog code or set of verilog codes which has intended functionality to meet with the required specifications.
	
	* Test Bench : It is the setup to apply stimulus(test_vectors) to the design to check its functionality. So to ensure that our design is obeying the 		  required specification, we apply stimulus to the design ,observe its output and match it with respect to the specification.
	
	
 2. ## Simulating the Designs with iverilog
	* Simulation : It is the process of using a simulation software (simulator) to verify the functional correctness of a digital design that is modeled using a  		HDL (hardware description language) like VHDL,Verilog. It is the process of checking whether the design is adhering to the given specs.
	
	* Simulator : It is the tool used for simulating the desing. The simulator used here is "iverilog". The RTL design is the implementation of the required 	   specification and the functionality of the specs needs to be verified by simualting the design using simulator.
	
	* How does a simulator work ?
   	  Simulator works by continuously monitoring the changes in the inputs. Upon a change in any one of the inputs, the output is re-evaluated. If there is no 	     change in input, the ouput will not be evaluated. Simulator dumps the change to the ouput to a file accoridng to the change in input.
    
 3. ## Design and Test Bench setup
 	* The RTL design written in verilog code has some primary inputs and primary outputs. It may have one or more than one primary inputs and one or more 	    	      than one primary outputs.
 	* We need to give stimulus to all the primary inputs and need to observe the primary outputs. Thus we need stimulus generator at the input and stimulus 	observer at the output.
 	* For giving stimulus we write the test bench, for that the design(module) is instantiated in the test bench, then stimulus is applied.
 	* It is important to note that the test bench doesn't have any primary input and primary output.
 	
 	Below image shows the test bench set :
	![](https://github.com/Deepak42074/Sky130-RTL-Design-And-Synthesis-Using-Verilog/blob/main/DAY_1/Test_bench_setup.png)
 	
4. ##  iverilog Simulation Flow
	* Inputs to the simulator :
    	  The iverilog simulator accepts two main inputs.
        	1. RTL Design    : This is the behavioral description of the specs in some HDL language(verilog here).
        	2. Testbench     : The testbench is the setup to apply stimulus or test vectors to the design to check its functionality and correctness.
	
	* Output of the simulator :
	 The iverilog simulator outputs a value chage dump (.vcd) file as output.
	 
	 This vcd file can be viewed using the GTKWave viewer tool.
	 
	 Below image shows the complete iverilog simulation flow :
	![](         )
        

4.   ### Setting Up the Lab.
    - Login to your lab instance and in our home directory create a directory named VLSI.
      ``` 
      cd /home/deepak074.verma/
      mkdir VLSI
      ```
      ![](https://github.com/Deepak42074/Sky130-RTL-Design-And-Synthesis-Using-Verilog/blob/main/DAY_1/LAB_setup1.1.png)
      
      - Clone the github repository into the VLSI directory.
      ``` 
      cd VLSI
      git clone https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git
      ```
      ![](https://github.com/Deepak42074/Sky130-RTL-Design-And-Synthesis-Using-Verilog/blob/main/DAY_1/LAB_setup1.2.png)
      
    - Check the contents of sky130RTLDesignAndSynthesisWorkshop directory
      ``` 
      cd sky130RTLDesignAndSynthesisWorkshop
      ls -ltr
      cd my_lib 
      cd lib                       : Contains sky130 standard cell library
      cd ..
      cd verilog_model 		   : Contains verilog model of standard cells in lib directory
      ```
      ![](https://github.com/Deepak42074/Sky130-RTL-Design-And-Synthesis-Using-Verilog/blob/main/DAY_1/LAB_setup1.3.png)
      
      - Check the contents of verilog_files directory which contains working files for this workshop
     ```
     cd sky130RTLDesignAndSynthesisWorkshop
     ls -ltr
     cd verilog_files
     ```
     ![](https://github.com/Deepak42074/Sky130-RTL-Design-And-Synthesis-Using-Verilog/blob/main/DAY_1/LAB_setup1.4.png)

    4. **iverilog Simulation Flow**

     ![](/src/img/iverilogn.png)
      1. Run iverilog with the design verilog file and the testbench as inputs. This will create an executable named a.out.
         ![](/src/img/iverilog1.png)
         ```
         iverilog good_mux.v tb_good_mux.v
         ```
      2. Execute the file a.out. This will generate the value change dump (.vcd) file.
         ![](/src/img/iverilog2.png)
         ```
         ./a.out
         ```
      3. Now run gtkwave with the vcd file as input to view the timing diagram.
         ![](/src/img/iverilog3.png)
         ```
         gtkwave tb_good_mux.vcd
         ```
      4. To view the signal on the wave window click and drag them to the signal column.
         ![](/src/gif/iverilog44.gif)
      5. To zoom in, click on the area that you want to zoom in and then click on the [+] button.
         ![](/src/gif/iverilog5.gif)
3. ### Synthesis with Yosys
    1. **What is yosys.!?**\
       Yosys is free software framework for RTL synthesis licensed under the ISC license. It currently has extensive Verilog-2005 support and provides a basic set of synthesis algorithms for various application domains. Yosys  reads a design  from the verilog file, synthesizes it to a gate-level netlist using the cell library in the given Liberty file  and writes the synthesized results as Verilog netlist to output.
    2. **The Standard Library File**\
       The standard library file is a collection of logical modules. It can include basic gates like not, and , or etc and macrocells like flops and muxes. Further many flavors of the same gate might be present like slow, medium, fast as well as multiple input options like 2 inputs , 3 inputs etc..
    3. **Why different flavors of gates**\
       The combinational delay in the logic path between two flops determine the maximum frequency of operation. The delay should be such that the data produced by the source flop reaches the input of the destination flop Tsetup time before the capturing clock edge, to avoid setup violations. Slower the delay, faster we can operate the circuit without failing this condition. So are only fast gates sufficient..!?. Its seems that we have to ensure a minimum delay on the path too. This ensure thats the data launched by a flop is captured by the other flop only in the next clock cycle and not the current cycle. Cases where this conditions are not met are called hold violations. So we need a mix of fast and slow gates for a proper working design.
    4. **Selection of cell**\
       The synthesizer selects the best cell from the standard library based on the inputs given to it called constraints. Constraints are the designers guide to the synthesis tool on what to optimize the design for, like power, performance or area. For high performance, the tool might choose faster gates which would indeed result in high power and more area. If slower gates are used to minimize power, the performance of the design will be impacted.
    5. **Yosys flow**
        1. start yosys.
           ![](/src/img/yosys1.png)
           ```
           yosys
           ```
        2. load the sky130 standard library.
           ![](/src/img/yosys2.png)
           ```
           read_liberty -lib ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
           ```
        3. Read the design files
           ![](/src/img/yosys3.png)
           ```
           read_verilog good_mux.v
           ```
        4. Synthesize the top level module
           ![](/src/img/yosys4.png)
           ```
           synth -top good_mux
           ```
           ![](/src/img/yosys5.png)
        
        5. Map to the standard library
           ![](/src/img/yosys6.png)
           ```
           abc -liberty ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
           ```
           ![](/src/img/yosys7.png)
        6. Two view the result as a graphich use the show command.
           ```
           show
           ```
           ![](/src/img/yosys8.png)
        7. To write the result netlist to a file use the write_veriog command. This will output the netlist to a file in the current directory.
           ```
           write_verilog -noattr synth_result.v
           ```
           ![](/src/img/yosys9.png)

# Day2 - Timing libs, hierarchical vs flat synthesis and efficient flop coding styles 
1. ## The standard cell library
   1. A standard cell library is a collection of characterized logic gates that can be used to implement digital circuits. This is usually part of set of file created by the foundry called the PDK(Process Development Kit). The designers use the PDK to design, simulate, draw and verify the design before handing the design back to the foundry to produce chips.\
   The standard library contains.
      1. Behavioral Views\
         HDL Descriptions of the cells that can be used for simulation and logic equivalence checking.
      2. Physical View\
         Contains layout of cells(GDSII) and abstract of cells(LEF)
      3. Transistor Level View\
         Can be used for spice simulations.
      4. Timing/Power
         Liberty files with characterization of timing and power.\
         etc...
   2. ### The SkyWater Open Source PDK
      The SkyWater Open Source PDK is a collaboration between Google and SkyWater Technology Foundry to provide a fully open source Process Design Kit and related resources, which can be used to create manufacturable designs at SkyWater’s facility. In this workshop we will be targeting this foundry and hence will be using the library file from this pdk for synthesis.
   3. ### Library naming convention
      The SkyWater Foundry Provides multiple Standard Cell Libraries. For this workshop we will be using the "sky130_fd_sc_hd". The sky130_fd_sc_hd library is designed for high density. This library enables higher routed gated density, lower dynamic power consumption, and comparable timing and leakage power. As a trade-off it has lower drive strength. Specifically this workshop uses the library "sky130_fd_sc_hd__tt_025C_1v80".
     ![](/src/img/libname.png)
   4. ### The .lib(liberty) File contents
      The timing data of standard cells is provided in the liberty format. Every .lib file will provide timing, power, noise, area information for a single corner ie process,voltage, temperature etc.
      1. Library\
         general information common to all cells in the library.
      2. Cell\
         specific information about each standard cell.
      3. Pin\
         Timing, power, capacitance, leakage functionality etc characteristics for each pin in each cell.
      ![](/src/img/lib1.png)
      ![](/src/img/lib2.png)
      ![](/src/img/lib3.png)
2. ## Hierarchical and Flat synthesis
   - When you do synth -top 'topmodulename' in yosys, it does an hierarchical synthesis. ie the different hierarchies between modules are preserved.
     ![](/src/img/hier1.png)
   - The yosys command flatten can be used to "flatten" the hierarchy and produce a single module. In the resulting netlist the hierarchies will not be preserved.
     ![](/src/img/hier2.png)
     ```
     flatten
     ```
   - ### submodule Level Synthesis
     Why submodule level synthesis.!?
     - case 1 :  **Top module with multiple instantiations of the same component.**\
       In this case, the submodule can be just synthesized once and then later stitched together in the top module.
     - case 2 : **High design complexity.**\
       Due to the size of the design, the synthesis tool is not to properly operate. In such cases we can deploy a divide and conquer strategy wherein the design can be synthesized at a submodule level and then latter stitched together in the top module.
     - To synthesize a sub module use the command "synth -top" with the submodule name instead of the the top module name.
       ![](/src/img/hier3.png)
3. ## Glitches
      Consider any combinational circuit. Each gate in it has an associated delay. Any change in its input take some finite amount of time to propagate to its output. A combinational circuit with gates whose delays are unbalanced might result in unwanted transitions in the outputs for changes in the input. These are called glitches
      For example consider the logic a + a'. From boolean algebra we know that the output of this should always be 1. But, in reality this may not be the case. See the timing diagram below.
      ![](/src/img/glitch.png)
      We can clearly see that, though our output is supposed to be always at one, due to the imbalance in delays, it goes low for some time. These can be bad for circuit operation. Further, if more and more combinational circuits are cascaded together, we might reach a situation where the output never settles.
4. ## Avoiding glitches = FlipFlops.
      Flipflops are storage elements. Their outputs only reflect the input on a clock edge. Between edges, the output is completely isolated from the inputs. So if we add flops between our combinational paths, we can prevent glitches from chaining up and causing unstable outputs. They act as barriers at the input of the combinational circuit, giving its output time to settle after a change in the inputs.
5. ## Flops initial state.
      Its important to control the initial states of the flops. Since the output of the flops are input to a combinational circuit, if the initial state is unknown, this may result in the combinational logic evaluating to some garbage value. To avoid this we should be able to control the initial values of the flop. For the designer, usually two ways are available. One is to reset the clock, which would set its output to 0 and the other is to set the flop which would set its output to 1. Both can be done asynchronously or synchronous with respect to the clock.
6. ## Flops with asynchronous reset/set.
      Asynchronous means, the output of the flop is set/reset as soon as the set/reset line is asserted. It does not wait for the clock.
      ![](/src/img/async.png)
7. ## Flops with synchronous reset/set.
      Synchronous means, the output not set/reset as soon as the reset/set pin is asserted. Instead, it waits for the next clock edge. Synchronous set/reset are always added to the datapath. ie they add extra logic to the input of the flop.
      ![](/src/img/syncrst1.png)

# Day3 - Combinational and Sequential optimizations.
  The synthesis tool can adopt various techniques to the most optimized design for power, area or performance. This section tries to cover some of those techniques.
  1. ## Combinational Logic Optimizations.
     Some of the common techniques used for optimizing combinational logic are constant propagation and boolean logic minimization. These are covered in detail below.
     1.  **Constant Propagation**\
         In this technique, constant inputs to the logic are propagate to the output which results in a minimized expression implementing the same logic. For example consider the case y=((ab)+c)' when b is tied to 0.
         ![](/src/img/opt1.png)
         We can see that the whole expression can be reduced to just an inverter. The input a does not affect the input as well.
     2. **Boolean logic optimization**\
         This is the good old techniques of minimizing large boolean expression using laws of boolean algebra. Consider the below expression for an example.
         ```
         assign y=a?(b?c:(c?a:0)):(!c)
         ```
         If we write the expanded form, it would look something like below
         ```
         y = a(bc + b'(ca + c'0)) + a'c'
           = abc + ab'c + a'c'
           = ac(b+b') + a'c'
           = ac = a'c'
           = a xnor c
         ```
         We can see that the long expression got minimized to a single xnor gate. 
         
     3.  **Optimization with Yosys**\
           In yosys  use the command otp_clean to optimize the design and remove unwanted components after running synth command.
           ```
           opt_clean -purge
           ```
           Yoysys synthesis does the same optimization for the above mentioned logic as seen in the below image.
           ![](/src/img/opt2.png)
     4. **Optimizing designs with multiple modules**\
          For designs with multiple modules, after synthesis flatten the design before running opt_clean -purge.
          ![](/src/img/opt31.png)

  2. ## Sequential Logic Optimizations
     1. **Sequential constant propagation.**\
        To understand sequential constant propagation, check out the below verilog code.
        ```
         module dff_prop(clk,d,q,rst);
            input clk,rst,d;
            output reg q;

            always @(posedge clk or posedge rst)
               begin
                  if(rst)
                     q<=1'b0;
                  else
                     q<=1'b0;
               end
         endmodule
         ```
         If you look carefully, we can see that the output q would always be 0, irrespective of clk,d or reset. ie the flop can be optimized away. Lets see what yosys thinks.
         ![](/src/img/opt4.png)
         We can see that the entire circuit gets optimized to just a single wire. This is sequential constant propagation.
     2. **Cases when Sequential constant propagation do not apply**\
         A constant connected to the input of a flop does not mean that we can always optimize it out. To understand better, see the code below.
         ```
         module dff_no_prop(clk,d,q,set);
            input clk,rst,d;
            output reg q;

            always @(posedge clk or posedge set)
               begin
                  if(rst)
                     q<=1'b1;
                  else
                     q<=1'b0;
               end
         endmodule
         ```
         We might be compelled to think that we can optimize out the flop. The output seems like following the set pin. ie when set is asserted the output is high and when its is de asserted its low. In other words, q<=set. lets look at the timing diagram once.
         ![](/src/img/opt5.png)
         We can clearly see that the flop cannot be optimized out in this case.
         ![](/src/img/opt6.png)
         Yosys also thinks the same and is retaining the flop after synthesis. The point is **not all constant input flops can be optimized out**.

  3. ## Sequential optimizations for unused outputs
        To understand this technique better, consider the below code.
        ```
        module counter_opt (input clk , input reset , output q);
            reg [2:0] count;
            assign q = (count == 3'b101);
            always @(posedge clk ,posedge reset)
               begin
                  if(reset)
                     count <= 3'b101);
                  else
                     count <= count + 3'h4;
               end
        endmodule
        ```
        At first glance, we might be tempted to think that the design would contain 3 flops after synthesis. After all the counter is a 3 bit one. But think again. If we look closely, after a reset the value of count just toggles between 101 and 001(101+100). Output q is high when count = 101 or in this case simply when count[2] is 1. In other word q<=count[2]. So we just need one flop that toggles count[2] every clock cycle. Also the reset would be connected to the set of an async set flop. Lets see what yosys thinks.
        ![](/src/img/opt7.png)
        We can clearly see that yosys has inferred just a single flop and the entire circuit is exactly like what we imagined it to be. Long story short, **any logic that does not affect the primary outputs will be optimized out.**
   4. ## Some other optimization techniques.
      1. **state optimization**
      2. **cloning**
      3. **retiming**

# Day4 - GLS, blocking vs non-blocking and Synthesis-Simulation mismatch.
   1. ## Gate Level Simulation(GLS).
      Gate level simulation is running the testbench against the output netlist after synthesis. Originally the RTL code was the design under test. Netlist should be logically same as the rtl code with the same set of inputs and outputs. So we can use the same testbench used for rtl simulation in gate level simulation also.
      1. **Why GLS**
         GLS is required to check the correctness of the design after synthesis. After all the netlist is produced by an automated algorithm which can easily go wrong. So its imperative that we compare and test the resultant netlist against the original specification and make sure that its indeed the same. It can also be used to check whether the design meets the timing constraints. For this the gate level models of the standard cell libraries should be delay annotated.
      2. **GLS with iverilog**
         The GLS flow with iverilog is exactly same as that done during rtl simulation. Instead of using the rtl design as input, we will be using the netlist generated after synthesis as the input to iverilog. Additionally, we also have to pass the gate level veriog models of the standard cell library also to iverilog so that the tool knows the functionality of various gates that where mapped during synthesis. If the verilog models of the standard cell library is delay annotated, it can be used to check if the design meets the timing constraints as well.
         ![](/src/img/gls1.png)
   2. ## Synthesis Simulations Mismatches.
      Situations may arise when the rtl simulation and the gate level simulation yields different results. This clearly indicates that the netlist after synthesis might not match with the requirements in hand. This is called synthesis simulation mismatch. In this section, we look into details some common reason for simulation synthesis mismatches.
      1. **Missing signals in sensitivity list**\
         This issue is mainly due to how the simulator works. An always block is executed only when any of the signals in its sensitivity list changes. So for any logic, all the value that are read by that block should be in the sensitivity list. If some of them is missed, then the block may not be run for changes to that signals. But since the logic written inside the block might itself be correct, the synthesis tool might infer the correct logic. This would then lead to a mismatch between the rtl and gls simulation. Lets understand it better with an example. Consider the below simple code snippet
         ```
         module and_vm(a,b,y);
            input a,b;
            output reg y;
            always @(a) 
               y=a&b;
         endmodule;
         ```
         Lets simulates this and see what happens.
         ![](/src/img/mismatch1.png)
         Clearly we are not getting an and gate. But what about gls after synthesis.?
         ![](/src/img/mismatch2.png)
         The timing is now that of an and gate. This is not because the synthesis tool in intelligent enough to figure out what the designers intend was, but due to the fact that the logic inside the block was correct to start with. In other word, you cannot makee an and gate that only responds to 1 input, though such a thing can be written in verilog and simulated.\
         Also note the command used to do gls with iverilog.
         ```
         iverilog test_net.v tbvm.v ../my_lib/verilog_model/primitives.v ../my_lib/verilog_model/sky130_fd_sc_hd.v
         ```
         apart from the synthesized netlist(test_net.v) and the testbench(tbvm.v), it also has the verilog models of the sky130 standard library as inputs. Rest all is same as rtl simulation.
      2. **Blocking and Nonblocking statements.**\
         Both blocking and nonblocking statements are procedural statements that can only come inside an always( or initial ) block. The main difference between them is that blocking statements are evaluated in the order they are written while all non blocking statements execute concurrently. These difference can cause synthesis simulation mismatches due to the order in which the blocking statements are written. As an example see the below code.
         ```
         module(a,b,c,d);
            input a,b,c;
            output reg y;
            reg x;
            always @(*)
               begin
                  d=c&x;
                  x=a|b;
               end
         endmodule
         ```
         We are trying to implement the logic (a|b)&c. Lets simulate and see the result.
         ![](/src/img/mismatch3.png)
         The output is clearly wrong. Why!?..Because since we are using blocking statements, the order matters. If you look closely, we are calculating d first and then x. ie d will be evaluated with the previous value of x. The simulation will look like there is a delay on x. To correct this we can reverse the order of the statements in the always block. Correct order or wrong order, both get synthesized to correct hardware.
         ![](/src/img/mismatch4.png)
         So this will again cause a simulation synthesis mismatch.\
         **As a rule of thumb always use blocking statements for combinational logic and non blocking for sequential logic**

# Day5 - If, case, for loop and for generate
   1. ## IF statement.
      If statement can infer a mux or priority logic based on how its coded. Also if written badly, if statements can infer latches. Main reason for inferred latches is incomplete if statements. Take a look at the code below.
      ```
      module incomp_if (input i0 , input i1 , input i2 , output reg y);
         always @ (*)
         begin
	         if(i0)
		         y <= i1;
         end
      endmodule
      ```
      We can see that the if statement is not complete. When i0 is 1 y is i1, but what about when i0 is not 1. Its not defined in the code clearly. So the synthesis tool will assume that if i0 is not 1 y should retain its previous value or in another words, a latch is inferred. This is bad because we did not intend a latch but a latch is inferred in the circuit. Moreover we were designing a combinational circuit, but due the bad coding style, have inferred a sequential element in it.
      ![](/src/img/mismatch5.png)

      if..else if chain can also be used to implement priority logic. Interesting things can happen if the chain is incomplete. Check the below code.
      ```
      module incomp_if2 (input i0 , input i1 , input i2 , input i3, output reg y);
         always @ (*)
            begin
	            if(i0)
		            y <= i1;
	            else if (i2)
		            y <= i3;

            end
      endmodule
      ```
      The if statements are clearly incomplete. Lets see how yosys synthesizes this code.
      ![](/src/img/mismatch6.png)
      clearly a latch has been inferred. The logic goes like this. If i0 is high y is i1, else i3. now if either of i0 or i2 is high the latch is enabled and correspondingly i1 or i3 is fed to output. if both i0 and i2 are low, output retains its last value.
      Said that, there may be case where an inferred latch is intended. Take for example the below code for a counter.
      ```
      module counter (input clk , input reset, input en, output q[2:0]);
         reg [2:0] count;
         assign q = count;
         always @(posedge clk, posedge reset)
            begin
               if(reset)
                  count <= 3'b000;
               else if(en)
                  count <= count+1;
               end
      endmodule
      ```
      The above also has an incomplete if statement so surely will infer latches. But in this case, its is actually intended. en is used to control whether the counter will count or not. If en is high count will increment on every clock. Otherwise since we have not specified the case, it would latch on to the current value of the count. This is just like a pause functionality.
   2. ## Case statement.
      The case statements are usually inferred as muxes. Like if statements, incomplete case statements can lead to inferred latches. An example is given below.
      ```
      module incomp_case (input i0 , input i1 , input i2 , input [1:0] sel, output reg y);
         always @ (*)
            begin
	            case(sel)
		            2'b00 : y = i0;
		            2'b01 : y = i1;
	            endcase
            end
      endmodule
      ```
      The sel line is a 2 bit signal. so it has total 4 possibilities. But in the case we have added only two of them. What about when sel is one of the other two values. Like incomplete if , the synthesizer would infer that in such cases the value of y should retain its previous value and insert latches. Let us see the output of yosys.
      ![](/src/img/mismatch7.png)
      With case statements, an easy way to avoid such latches is to add a default. The default would match for all the conditions of the sel line which are not explicitly coded in the case. The modified code looks like below.
      ```
      module incomp_case (input i0 , input i1 , input i2 , input [1:0] sel, output reg y);
         always @ (*)
            begin
	            case(sel)
		            2'b00   : y = i0;
		            2'b01   : y = i1;
                  default : y = 1'b0;
	            endcase
            end
      endmodule
      ```
      ![](/src/img/mismatch8.png)
      No more latches.\
      But, just adding the default clause might not be enough to avoid latches in certain cases. This is case where you are driving multiple outputs from each leg of the case. In such case, each leg of the case should have each of the output defined. if any one is missed, it will result in inferring a latch along the path for that particular output. Lets see with an example.
      ```
      module incomp_case (input i0 , input i1 , input i2 , input [1:0] sel, output reg x,y);
         always @ (*)
            begin
	            case(sel)
		            2'b00   : begin x = i0; y = i0; end
		            2'b01   : x = i1;
                  default : begin x =1'b0; y = 1'b0; end
	            endcase
            end
      endmodule
      ```
      Here for the case 2'b01 only output x is defined and y is not defined. Let us synthesize the above code and see.
      ![](/src/img/mismatch8.png)
      clearly a latch is inferred and its on the path of output y.
   3. ## For loop
      For loop are used inside procedural blocks. They are used to evaluate expressions. They are not for instantiating modules.
      The following code uses for loop to generate a 4X1 mux.
      ```
      module mux_generate (input i0 , input i1, input i2 , input i3 , input [1:0] sel  , output reg y);
         wire [3:0] i_int;
         assign i_int = {i3,i2,i1,i0};
         integer k;
         always @ (*)
            begin
               for(k = 0; k < 4; k=k+1) begin
	               if(k == sel)
		               y = i_int[k];
               end
            end
      endmodule
      ```
      The main advantage of such a coding style is scalability. To convert this code to generate 128X1 mux would just mean, changing the loop condition( and of course the inputs and select also should be scaled accordingly.).
   4. ## For Generate
      For Generate loops are used to multiple instantiations of modules. They are not to be used inside a procedural block. An example is shown below.
      ```
      module and_8(a,b,y);
         input [7:0] a,b;
         output [7:0] y;
         genvar i;
         generate
            for(i=0;i<8;i=i+1)
               and g(y[i],a[i],b[i]);
         endgenerate
      endmodule
      ```
      The above will instantiate 8 and gates and make connections accordingly. Much more scalable than writing all the individual instantiations separately. Yosys output is given below.
      ![](/src/img/genloop.png)
# FAQs
1.  What is the significance of -lib while importing liberty file in yosys
    -   the -lib option creates like a library/list of all the cells present in the .lib file with only IO ports and not the internal structure.

2. yosys produces different implementations for the same circuit and standard library file
    - This would mostly be because of difference in the versions of yosys that you are running. Different versions might be optimized for different areas of optimizations like power, performance or area. Also later version might have improvements in algorithms that might help it to choose a better standard cell for the same design. Same technique can be used to generate n bit ripple carry adders from full adders.
    
# Acknowledgements

* Kunal Gosh, Co-Founder (VSD Corp. Pvt Ltd)
* Shon Taware, Teaching Assistant (VSD Corp. Pvt Ltd)

# References
1. https://www.vlsisystemdesign.com/rtl-design-using-verilog-with-sky130-technology/
2. https://www.eng.biu.ac.il/temanad/files/2017/02/Lecture-4-Standard-Cell-Libraries.pdf
3. https://skywater-pdk.readthedocs.io/en/latest/
4. http://www.clifford.at/yosys/
