# Sky130-RTL-Design-And-Synthesis-Using-Verilog

This repository shows the contents  and labs covered in the [RTL Desing using Verilog with Sky130 Technology](https://www.vlsisystemdesign.com/rtl-design-using-verilog-with-sky130-technology/) workshop.

![](https://github.com/Deepak42074/Sky130-RTL-Design-And-Synthesis-Using-Verilog/blob/main/DAY_1/VSD_Workshop_Detail.png)



# Table of Contents

1. [Introduction](#introduction)
2. [Day1 - Introduction to Verilog RTL Design and Synthesis](#Day1---introduction-to-verilog-rtl-design-and-synthesis)
   1. [Introduction to iverilog, Design and Test Bench](##Introduction to iverilog, Design and Test Bench)
   2. [Design and Test Bench setup](##Design and Test Bench setup)
   3. [Synthesis with Yosys](#synthesis-with-yosys)

8. [Acknowledgements](#acknowledgements)
9. [References](#references)


# Introduction -   
	Tools used:   iVerilog(for Simulation), GTKWave(for waveform view), Yosys(for Synthesis)  
	Technology used: Sky130 technology.   
	
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
        

5. ## Setting Up the Lab.
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

     ![]()
      1. Run iverilog with the design verilog file and the testbench as inputs. This will create an executable named a.out.
         ![](g)
         ```
         iverilog good_mux.v tb_good_mux.v
         ```
      2. Execute the file a.out. This will generate the value change dump (.vcd) file.
         ![]()
         ```
         ./a.out
         ```
      3. Now run gtkwave with the vcd file as input to view the timing diagram.
         ![]()
         ```
         gtkwave tb_good_mux.vcd
         ```
      4. To view the signal on the wave window click and drag them to the signal column.
         ![]()
      5. To zoom in, click on the area that you want to zoom in and then click on the [+] button.
         ![]()
3. ### Synthesis with Yosys
    
    
      
     **Yosys working flow**
        1. start yosys. 
           ![]()  
           ```
           yosys 
           ```
        2. load the sky130 standard library.  
           ![]()
           ```
           read_liberty -lib ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib  
           ```
        3. Read the design files  
           ![]() 
           ```
           read_verilog good_mux.v  
           ```
        4. Synthesize the top level module  
           ![]()  
           ```
           synth -top good_mux  
           ```
           ![]()
        
        5. Map to the standard library  
           ![]()
           ```
           abc -liberty ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
           ```
           ![]()
        6. Two view the result as a graphich use the show command.  
           ```
           show
           ``` 
           ![](g)
        7. To write the result netlist to a file use the write_veriog command. This will output the netlist to a file in the current directory.
           ```
           write_verilog -noattr synth_result.v
           ```
           ![]()


    
# Acknowledgements

* Kunal Gosh, Co-Founder (VSD Corp. Pvt Ltd)
* Shon Taware, Teaching Assistant (VSD Corp. Pvt Ltd)


