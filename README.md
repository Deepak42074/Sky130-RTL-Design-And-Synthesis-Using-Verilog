# Sky130-RTL-Design-And-Synthesis-Using-Verilog

This repository shows the contents  and labs covered in the [RTL Desing using Verilog with Sky130 Technology](https://www.vlsisystemdesign.com/rtl-design-using-verilog-with-sky130-technology/) workshop.

![](https://github.com/Deepak42074/Sky130-RTL-Design-And-Synthesis-Using-Verilog/blob/main/DAY_1/VSD_Workshop_Detail.png)



# Table of Contents

1. [Introduction](#introduction)
2. [Day1 - Introduction to Verilog RTL Design and Synthesis](#[Day1 - Introduction to Verilog RTL Design and Synthesis)
   1. [Introduction to iverilog, Design and Test Bench](##Introduction to iverilog, Design and Test Bench)
   2. [Design and Test Bench setup](##Design and Test Bench setup)
   3. [Synthesis with Yosys](#synthesis-with-yosys)

8. [Acknowledgements](#acknowledgements)
9. [References](#references)


# 1. Introduction :
Tools used:   
* Icarus Verilog: It is a verilog simulation and synthesis tool. It operates as a compiler, compiling source code written in Verilog (IEEE-1364) 	       			  into some target format.Icarus Verilog is an open source Verilog compiler that supports the IEEE-1364 Verilog HDL including IEEE1364-				  2005 plus.
* GTKwave	: GTKWave is a VCD waveform viewer based on the GTK library. This viewer support VCD and LXT formats for signal dumps.It also reads LXT, LXT2, VZT, 		      FST, and GHW files as well as standard Verilog VCD/EVCD files and allows their viewing.
* Yosys 	: Yosys is a framework for Verilog RTL synthesis. It currently has extensive Verilog-2005 support and provides a basic set of synthesis algorithms 			for various application domains.
Technology used: Sky130 technology.   
	
# 2. Day1 - Introduction to Verilog RTL Design and Synthesis
The first day of the workshop covers the brief description of iverilog simulator, Test Bench setup, iverilog simulation flow  and lab using iverilog, gtkwave, yosys tools.
## 2.1 Introduction to iverilog, Design and Test Bench	
* RTL Design : It is the actual verilog code or set of verilog codes which has intended functionality to meet with the required specifications.
		Register Transfer Level (RTL) is an abstraction for defining the digital portions of a design. It is the principle abstraction used for 			defining electronic systems today and often serves as the golden model in the design and verification flow. The RTL design is usually 				captured using a hardware description language (HDL) such as Verilog or VHDL.
	
* Test Bench : It is the setup to apply stimulus(test_vectors) to the design to check its functionality. So to ensure that our design is obeying the 		  		required specification, we apply stimulus to the design ,observe its output and match it with respect to the specification.
	
	
## 2.2 Simulating the Designs with iverilog
* Simulation : Simulation is the process by which the design model coded in the HDL gets executed (after a successful compilation and elaboration) based on a given 		   execution model.It is done by using a simulation software (simulator) to verify the functional correctness of a digital design that is modeled using 	      a HDL (hardware description language) like VHDL,Verilog. It is the process of checking whether the design is adhering to the given specs.
		
* Simulator : It is the tool used for simulating the design.The simulator used here is "iverilog". The RTL design is the implementation of the required 	   		specification and the functionality of the specs needs to be verified by simualting the design using simulator.
	
* How does a simulator work ?
   Simulator works by continuously monitoring the changes in the inputs. Upon a change in any one of the inputs, the output is re-evaluated. If there is no 	     	change in input, the ouput will not be evaluated. Simulator dumps the change to the ouput to a file according to the change in input.
    
 ## 2.3 Design and Test Bench setup
 * The RTL design written in verilog code has some primary inputs and primary outputs. It may have one or more than one primary inputs and one or more 	    	      than one primary outputs.
 * We need to give stimulus to all the primary inputs and need to observe the primary outputs. Thus we need stimulus generator at the input and stimulus 	observer at the output.
 * For giving stimulus we write the test bench, for that the design(module) is instantiated in the test bench, then stimulus is applied.
 * It is important to note that the test bench doesn't have any primary input and primary output.
 <dl>
  <dd>Below image shows the test bench set : </dd>
</dl>
 
	![](https://github.com/Deepak42074/Sky130-RTL-Design-And-Synthesis-Using-Verilog/blob/main/DAY_1/Test_bench_setup.png)
 	
## 2.4 iverilog Simulation Flow
* Inputs to the simulator :  
    The iverilog simulator accepts two main inputs.  
	1. RTL Design    : This is the behavioral description of the specs in some HDL language(verilog here).  
        2. Test Bench    : The testbench is the setup to apply stimulus or test vectors to the design to check its functionality and correctness.
        		   Test bench instantiate the verilog module of design and give stimulus to the input ports of the RTL design.
	
* Output of the simulator :  
 The iverilog simulator outputs a value chage dump (.vcd) file as output.This vcd file can be viewed using the GTKWave viewer tool.  
<dl>
  <dd>Below image shows the complete iverilog simulation flow : </dd>
</dl>	 
 
	![](DAY_1/iverilog_sim_flow.png )
        

## 2.5 Setting Up the Lab.
*  
<dl>
  <dd>Login to your lab instance and in our home directory create a directory named VLSI.: </dd>
</dl>

``` 
cd /home/deepak074.verma/
mkdir VLSI
```
![](https://github.com/Deepak42074/Sky130-RTL-Design-And-Synthesis-Using-Verilog/blob/main/DAY_1/LAB_setup1.1.png)
      
*
 Clone the github repository into the VLSI directory.
	      ``` 
	      cd VLSI
	      git clone https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git
	      ```
      ![](https://github.com/Deepak42074/Sky130-RTL-Design-And-Synthesis-Using-Verilog/blob/main/DAY_1/LAB_setup1.2.png)
      
 * Check the contents of sky130RTLDesignAndSynthesisWorkshop directory
	      ``` 
	      cd sky130RTLDesignAndSynthesisWorkshop
	      ls -ltr
	      cd my_lib 
	      cd lib                       : Contains sky130 standard cell library
	      cd ..
	      cd verilog_model 		   : Contains verilog model of standard cells in lib directory
	      ```
      ![](https://github.com/Deepak42074/Sky130-RTL-Design-And-Synthesis-Using-Verilog/blob/main/DAY_1/LAB_setup1.3.png)
      
 * Check the contents of verilog_files directory which contains working files for this workshop
	     ```
	     cd sky130RTLDesignAndSynthesisWorkshop
	     ls -ltr
	     cd verilog_files
	     ```
     ![](https://github.com/Deepak42074/Sky130-RTL-Design-And-Synthesis-Using-Verilog/blob/main/DAY_1/LAB_setup1.4.png)

  ## 2.6 Iverilog Simulation of Multiplexer(MUX)
  Iverilog simulation is done as per below steps:
		*  Iverilog takes RTL design and test bench as input and generates a executable file " a.out".
		*  On executing "a.out" ,it dumps the simulation in value change dump format(.vcd file).
		*  Then GTKWave takes the .vcd file and display the simulation waveform.
  The above steps are shown below: 
      1. Run iverilog with the design verilog file and the testbench as inputs. This will create an executable named a.out.
        	```
		cd sky130RTLDesignAndSynthesisWorkshop
		ls -ltr
		cd verilog_files 
		iverilog good_mux.v tb_good_mux.v
		```
      2. Execute the file a.out. This will generate the value change dump (.vcd) file.
         	 ```
		 ./a.out
		 ```
      3. Now run GTKwave with the vcd file as input to view the simulation waveform.
		 ```
		 gtkwave tb_good_mux.vcd
		 ```
      4. To view the signal on the wave window click and drag them to the signal column.
  		
     
## 2.7 Synthesis with Yosys
Synthesis : Synthesis is the process during which RTL design actually gets converted into a circuit. There are special programing languages called Hardware 		      Description Languages (HDLs) which are used to describe the hardware of a circuit and then the computer makes the circuit based on the program 	
 	      written. After synthesis we obtain something known as a “Gate Level Netlist”. This netlist is how our circuit will look.
	      The tool used here to do synthesis is Yosys.
### 2.7.1 Yosys Synthesis Flow setup
The synthesis tool takes the RTL design and the liberty file(.lib) as inputs and synthesize the RTL design into netlist which is the gate level representation of the RTL design.

   Below image shows the Yosys synthesis flow setup: 
   ![](DAY_1/Yosys_setup.png)  
   
   Below are the steps to synthesize the multiplexer design(good_mux.v):
   	1. To invoke Yosys:   
           ```
           cd verilog_files 
	   yosys
           ```
	   Below image show the yosys synthesis suite:
	   ![](DAY_1/yosys_invoke.png)
       2. Reading sky130 standard library :
           ```
           read_liberty -lib ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib  
           ```
	   read_liberty : It read cells from liberty file as modules into current design.
	   		  The option "-lib"  only create empty blackbox modules.
        3. Reading the RTL design(verilog file) :
           ```
           read_verilog good_mux.v  
           ```
	   read_verilog : This command is used to read the verilog desgin file. It load modules from a Verilog file to the current design.
	   Below image show the yosys synthesis suite:
	   ![](DAY_1/Yosys_setup_2.png)
        4. Synthesize the top level module  : Below command is used to synthesize the module
           ```
           synth -top good_mux  
           ```
	   synth : This command runs the default synthesis script. This command does not operate on partly selected designs.
	   -top <module> : This option use the specified module as top module (default='top'). Here we have module name "good_mux" for our example.
            ![](DAY_1/Yosys_setup_3.png)
        
        5. Mapping to the standard library 
           ```
           abc -liberty ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
           ```
	abc : This pass uses the ABC tool for technology mapping of yosys's internal gate library to a target architecture. This command converts RTL code into 		gates,cells which is taken from the sky130_fd_sc_hd__tt_025C_1v80.lib file.
	-liberty <file> : It generate netlists for the specified cell library (using the liberty file format).
	![](DAY_1/Yosys_setup_4.png)
        6. To view the result as a grapviz use below command
           ```
           show
           ``` 
	Show : It creates  graphviz DOT file for the selected part of the design and compile it to a graphics file (usually SVG or PostScript).It is used to show 
		the logic realized from the verilog code after synthesis.
          ![](DAY_1/Yosys_setup_5.png)
        7. To write the  netlist to a file use below command which  will output the netlist to a file in the current directory.
           ```
           write_verilog -noattr good_mux_netlist.v
           ```
	write_verilog : It write the current design to a Verilog file.
	-noattr :By using this option no attributes are included in the output
	good_mux_netlist.v : File name to which we want to write the netlist.It can be any name.
          ![](/DAY_1/Yosys_setup_6.png)
### 2.7.2 Verifying the Synthesis output netlist:
	The netlist is written as a verilog code in terms of standard cell from sky130_fd_sc_hd__tt_025C_1v80.lib. As the netlist is the true representation of the 	    RTL design ,it needs to be simulated to verify ,if tool has synthesized our design correctly.
	To simulate the generated netlist follow the same iverlog simulation flow done above. The only change in the input of iverilog is the netlist file is used 	   in place of RTL design.
	The set of primary inputs & ouputs will remain same for RTL design and synthesized netlist.Thus same test bench can be used.
	

    
# Acknowledgements

* Kunal Gosh, Co-Founder (VSD Corp. Pvt Ltd)
* Shon Taware, Teaching Assistant (VSD Corp. Pvt Ltd)


