# IIITB_VLSI

This github repository summarizes the progress made in the VSD-HDP tapeout program. Quick links:

[Day 0 : Open Source Labs installation](#day-0)

[Day 1 : Introduction to Verilog RTL design and Synthesis](#day-1)

[Day 2 : Timing libs,hierarchical,flat synthesis,efficient flop coding styles](#day-2)

[Day 3](#day-3)

[Day 4](#day-4)

## Day 0

<details>
 <summary> Summary </summary>
 
	
I installed the needed tools.

</details>	
	
 <details>
 <summary> Yosys </summary>


 I installed Yosys using the following commands:
```bash
git clone https://github.com/YosysHQ/yosys.git
cd yosys-master 
sudo apt install make 
sudo apt-get install build-essential clang bison flex \
    libreadline-dev gawk tcl-dev libffi-dev git \
    graphviz xdot pkg-config python3 libboost-system-dev \
    libboost-python-dev libboost-filesystem-dev zlib1g-dev
make 
sudo make install
```
Below is the screenshot showing sucessful installation:

![yosys](https://github.com/mavi62/IIITB_VLSI/assets/57127783/24dea86f-6bba-4835-bcf8-db0da6101ace)

</details>

<details>
 <summary> OpenSTA </summary>


 I installed and built OpenSTA (including the needed packages) using the following commands:
 ```bash
sudo apt-get install cmake clang gcctcl swig bison flex
git clone https://github.com/The-OpenROAD-Project/OpenSTA.git
cd OpenSTA
mkdir build
cd build
cmake ..
make
```
Below is the screenshot showing sucessful installation:

![OpenSTA](https://github.com/mavi62/IIITB_VLSI/assets/57127783/b5ffd733-4801-4dde-b01d-48b8de5eecc5)

</details>
 <details>
 <summary> ngspice </summary>


 I downloaded the tarball from https://sourceforge.net/projects/ngspice/files/ to a local directory and unpacked it using the following commands:
 ```bash
tar -zxvf ngspice-37.tar.gz
cd ngspice-37
mkdir release
cd release
../configure  --with-x --with-readline=yes --disable-debug
make
sudo make install
 ```
Below is the screenshot showing sucessful installation:

![ngSpice](https://github.com/mavi62/IIITB_VLSI/assets/57127783/ab066be0-b6c2-48c3-985f-887f47338059)

</details>
 <details>
 <summary> iverilog </summary>


 I installed iverilog using the following command:
  ```bash
sudo apt-get install iverilog
 ```
 Below is the screenshot showing sucessful installation:
 
 ![iverilog](https://github.com/mavi62/IIITB_VLSI/assets/57127783/41852158-c140-4b1e-a90e-688e6ac710b5)

 </details>
 <details>
 <summary> gtkwave </summary>


 I installed gtkwave using the following command:
  ```bash
sudo apt-get install gtkwave
 ```
 Below is the screenshot showing sucessful installation:
 
 ![gtkwave](https://github.com/mavi62/IIITB_VLSI/assets/57127783/9bbc4ae9-0774-433e-afa0-cb34ce4d50cc)

 </details>
 <details>
 <summary> magic </summary>


 I installed magic using the following commands:
  ```bash
sudo apt-get install m4
sudo apt-get install tcsh
sudo apt-get install csh
sudo apt-get install libx11-dev
sudo apt-get install tcl-dev tk-dev
sudo apt-get install libcairo2-dev
sudo apt-get install mesa-common-dev libglu1-mesa-dev
sudo apt-get install libncurses-dev
 ```
 Below is the screenshot showing sucessful installation:
 
 ![magic](https://github.com/mavi62/IIITB_VLSI/assets/57127783/22ed2199-8a03-4481-9905-0b6a307715cc)

 </details>


 <details>
 <summary> OpenLane & Docker </summary>


 I installed OpenLane & Docker using the following commands:
sudo apt-get update
sudo apt-get upgrade
sudo apt install -y build-essential python3 python3-venv python3-pip make git

sudo apt install apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt update

sudo apt install docker-ce docker-ce-cli containerd.io

sudo docker run hello-world

sudo groupadd docker
sudo usermod -aG docker $USER
sudo reboot 

docker run hello-world

Below is the screenshot showing sucessful launch:

![docker](https://github.com/mavi62/IIITB_VLSI/assets/57127783/72a85660-7514-4282-b9e2-aa92126c378a)

</details>

## Day 1

<details>
  <summary>Summary</summary>
  
  **Simulator:** It is a tool for checking the design written in HDL. RTL design is checked for the the adherence to to spexifaction of required circuit.
 
  **Design:** It is the verilog code to create the circuit that meets the required specificaations. It involves using HDL to specify behaviour and structure of the circuit.
	
 **RTL design outline:**

	module module_name (port_list);
		//declarations;
		//initializations;
		//continuos concurrent assigments;
		//procedural blocks;
	endmodule
 
  **Testbench:** It is used to apply stimulus to the design to check the working of the circuit and ensure that it's functionality meets the required specifications. 

![p1](https://github.com/mavi62/IIITB_VLSI/assets/57127783/2a176771-f7b2-47de-b3e9-42308b1e5524)

**iverilog:** iverilog stands for Icarus Verilog. Icarus Verilog is an implementation of the Verilog hardware description language.

**GTKwave:** GTKWave is a fully featured GTK+ based wave viewer for Unix, Win32, and Mac OSX which reads LXT, LXT2, VZT, FST, and GHW files as well as standard Verilog VCD/EVCD files and allows their viewing. 

![p2](https://github.com/mavi62/IIITB_VLSI/assets/57127783/2367bacd-ed16-4bb0-93e9-e8de0eeac236)


### Lab examples using iverilog and GTKwave

In this lab session we were made familiar with the linux operating system as well as GTKwave along with codes in iverilog. We cloned sky130RTLDesign library from github using command: **git clone**. and worked on good_mux file.

![git clone](https://github.com/mavi62/IIITB_VLSI/assets/57127783/893b1f88-e520-4186-b01e-e023c0067ef3)


![clone 2](https://github.com/mavi62/IIITB_VLSI/assets/57127783/e11d5ca5-c523-481f-afe3-d72fb69d8eed)

</details>

<details>
<summary> Simulation: iverilog and gtkwave </summary>
 
 I used the following commands to simulate and view the plots of the RTL design:
	
 ```bash
 iverilog <name verilog: good_mux.v> <name testbench: tb_good_mux.v>
 ./a.out
 gtkwave tb_good_mux.vcd
 ```
	
 Below is the screenshot of the gtkwave plots:

![clone3](https://github.com/mavi62/IIITB_VLSI/assets/57127783/a9b0b71b-903e-4a2b-9ee2-a5c3e122fac1)


Here is the code used in todays lab :<br />

	module good_mux (input i0 , input i1 , input sel , output reg y); 
		always @ (*)
		begin
			if(sel)
			y <= i1;
			else 
			y <= i0;
		end
	endmodule


	`timescale 1ns / 1ps
	module tb_good_mux;
	// Inputs
	reg i0,i1,sel;
	// Outputs
	wire y;
      		// Instantiate the Unit Under Test (UUT), name based instantiation
		good_mux uut (.sel(sel),.i0(i0),.i1(i1),.y(y));
		//good_mux uut (sel,i0,i1,y);  //order based instantiation
	initial begin
		$dumpfile("tb_good_mux.vcd");
		$dumpvars(0,tb_good_mux);
		// Initialize Inputs
		sel = 0;
		i0 = 0;
		i1 = 0;
		#300 $finish;
	end
	always #75 sel = ~sel;
	always #10 i0 = ~i0;
	always #55 i1 = ~i1;
	endmodule

</details>  

<details>
 <summary> Synthesis </summary>
 

 **Synthesizer:** It is a tool used to convert RTL design to gate level netlist. The Synthesis tool used in this lab is yosys.
 
 **Netlist:** It is representation of RTL design in for of standard cells i.e. It is a properly implemented chip design in terms of logic gates.
 
![1](https://github.com/mavi62/IIITB_VLSI/assets/57127783/54557e87-29dd-4f4a-a8e3-36a50c61b8ee)


 Synthesis takes place in following steps:
- Converting RTL into simple logic gates.
- Mapping those gates to actual technology-dependent logic gates available in the technology libraries.
- Optimizing the mapped netlist keeping the constraints set by the designer intact.

- **Verification of Synthesized design**: In order to make sure that there are no errors in the netlist, we need to verify the synthesized circuit. The netlist verification flow can be seen in the below image:

![2](https://github.com/mavi62/IIITB_VLSI/assets/57127783/4ceee7d4-92b5-451b-9e85-d1fc819692e1)


  **Yosys**: It is a framework for RTL synthesis. It provides a basic set of synthesis algorithms for various application domains. Yosys is the core component of most our implementation and verification flows.
  
![3](https://github.com/mavi62/IIITB_VLSI/assets/57127783/8382b5c5-2a14-43f7-a883-9fda887b7a37)


Below are the commands to perform above synthesis.

- RTL Design  - read_verilog
- .lib        - read_liberty
- netlist file- write_verilog

![4](https://github.com/mavi62/IIITB_VLSI/assets/57127783/a169bf08-ae9b-46c3-97f2-03f2872a9553)


In the directory of the verilog files, I used the following commands to synthesize and view the synthesized deisgn:
	
 ```bash
yosys> read_liberty -lib <path to lib file>
yosys> read_verilog <path to verilog file>
yosys> synth -top <top_module_name>
yosys> abc -liberty <path to lib file>
yosys> show
 ```
 Below is the screenshot of the synthesized design:


![synth_1](https://github.com/mavi62/IIITB_VLSI/assets/57127783/14be6283-143c-424d-afc3-650684a3b566)


**.lib :** It is a collection of logical modules like logic gates. It contains cells with different sppeds, no. of inputs etc. that can be used as required.

 I used the following command to generate the netlist:
 ```bash
 yosys> write_verilog -noattr <file_name_netlist.v>
 ```
 
 Below is the screenshot of the generated netlist:

 
![vim](https://github.com/mavi62/IIITB_VLSI/assets/57127783/483ec355-769d-49a3-a369-d750208e1282)

**Need for different speed of gates:**
  
![5](https://github.com/mavi62/IIITB_VLSI/assets/57127783/97828782-a3fd-4b23-9ee0-134616841b0d)
 
   - We need gates fast enough so that the total delay of all the gates is smaller than the T(clk).
   
![6](https://github.com/mavi62/IIITB_VLSI/assets/57127783/81bbc5b9-3343-4461-8f45-f4b5a9f15eb7)
 
   - If we want to capture B in next clock cycle rather than the same, we need to make the delay larger than the whole time, so some cells need to work slowly

**Fast cell VS slow cells:**
- A load in digital logic is a capacitor
- A faster charging or discharging means less delay
- To increase the rate of charging or discharging we need to widen the transistors.
- Wider transistor gives lower delay: but more is required and more power is required
- Narrow transistors give out more delay  : we need less area and less power is consumed.

</details>
  
## Day 2

<details>
 <summary> Summary </summary>
 I first synthesized a multiple module (made of two submodules) at the multiple module level 
 (both in hierarchical and flattened forms) then at the submodule level. Synthesis at the 
 submodule level is important for two reasons: 1-) when we have multiple instances of same module 
 (we synthesize once and replicate this netlist multiple times and stitch together the replicas 
 to get the multiple module netlist, and 2-) when we want to divide and conquer (in massive 
 designs) so that the tool can generate a portion by portion of the overall netlist and then we 
 can stitch together the netlist portions to get the multiple module netlist. After that, I 
 sumulated the different flop designs using iverilog and gtkwave, then synthesized the designs. 
 Finally, I synthesized 2 designs that were special; their synthesis used optimizations.
</details>
<details>
 <summary> Introduction to .lib </summary>

 Under this section, we get a better insight regarding .lib. We have the general overview that it 
 stores the models of all the standards cells, various variations and flavours as per the need of 
 specification provided. Getting an insight into the .lib file, we start with the file name -

sky130_fd_sc_hd__tt_025C_1v80  
 The name sky130 represemts that the library is based on 130nm technology. Under the nomenclature, we define PVT - process, voltage and temperature. Process refers to the variations due to the fabrication, ie. there will variations in the silicon fabricated even by the same machine. There is variation due to the voltage and temperature as well. Silicon is very sensitive to temperature. All these 3 determines how the silicon is going to perform. We aim to design such that silicon works in all the conditions, across various variations. These three are indicated under the name, tt stands for typical process, 25c indicates the temperature - 25C and 1v80 indicates the voltage of 1.80volts. It is to be noted, all the models under the said library are designed for the given PVT parameters.

We open the .lib file using gvim to go through various other informations it provides.

![1](https://github.com/mavi62/IIITB_VLSI/assets/57127783/9166ab42-c5a2-49fa-92da-aeac43319c97)


- It defines the technology begin used "CMOS" and the delay model as "table_lookup"
- It defines the units for various parameters and quanities, such as, 1ns for time, 1V for voltage, 1mA for current, 1kohm for resistance and 1pF for capacitance.
- It defines the operating conditions as "tt_025C_1v80".

Considering a two input and gate, and compare different two input and gate.

![2](https://github.com/mavi62/IIITB_VLSI/assets/57127783/eb41fc12-ca13-4666-b04c-c09e0e1204f7)


- The lib files conatins the power and timing information for the 4 possible outcomes.
- All three taken cells are 2 input and gates, but differ in their areas, and2_4 has a larger area than area2_2 and consequently more than and2_0.
- Having a larger area refers to the use of a wider cell. Wider cells will be faster, but consumes more power. This can be seen in the datials under the lib file.

</details>

<details>
<summary> Heirarchial vs Flat Synthesis </summary>
Under this section, we go over what is heirchial synthesis and flat synthesis. For this, we have taken the case of multiple_modul2s.v from verilog files to have a better unstanding.


![3](https://github.com/mavi62/IIITB_VLSI/assets/57127783/dadbd906-b57d-4356-9146-1d812b739ad5)

Gate level diagram

![4](https://github.com/mavi62/IIITB_VLSI/assets/57127783/aa1b5118-6e5d-4088-91ae-442e08ac5a42)

We go to the directory where we find the model in verilog files
```bash
$ cd Documents/ASICs/VLSI/sky130RTLDesignAndSynthesisWorkshop/verilog_files
$ yosys
read_liberty -lib ~/Documents/ASICs/VLSI/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog multiple_modules.v
synth -top multiple_modules
abc -liberty ~/Documents/ASICs/VLSI/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show multiple_modules
```
**Reading and Synthesis of the said module**

![5](https://github.com/mavi62/IIITB_VLSI/assets/57127783/2d07926d-beac-477a-8b29-b49a2e1be030)


![6](https://github.com/mavi62/IIITB_VLSI/assets/57127783/c48d2c5d-d3b8-4eb0-8b7c-3783efb3ee2d)


![7](https://github.com/mavi62/IIITB_VLSI/assets/57127783/35143b08-37af-4d27-8b3c-7b4998ce1564)


- we hit show and expect to attain a similar schematic we had drew
  
![8](https://github.com/mavi62/IIITB_VLSI/assets/57127783/ed575077-0342-4cb2-b367-f7fa8730f1b6)


- We get the image of the top module.
- We don't get to see the and and or gates. We see the modules u1 and u2, which are the instances of the gates.
- **This type of design is called an heirarchial design.**
- We generate the netlist file for the design.
```bash
write_verilog -noattr multiple_modules_hier.v
!gvim multiple_modules_hier.v  
```

![9](https://github.com/mavi62/IIITB_VLSI/assets/57127783/3dca3f09-010a-4942-88ce-7eeb91480eb2)


![10](https://github.com/mavi62/IIITB_VLSI/assets/57127783/be737612-ce56-4f93-bea6-a476a3b3bbf0)


- In the netlist generated, it is observed that the hierarchy is maintained. The top module has instances of sub moduke 1 and 2, and the two modules are seperately defined implementing the and and or gates.
- It is to be more, since this is CMOS technology, we implement the gates using a nand gate with inverted inputs for or gate and nor gate with inverted inputs for and gate.

Now we will look into flat design techcnique.
```bash
write_verilog -noattr multiple_modules_flat.v
!gvim multiple_modules_flat.v
```

![11](https://github.com/mavi62/IIITB_VLSI/assets/57127783/5d3dec12-9a48-42bd-a41b-0077da00df7e)


![12](https://github.com/mavi62/IIITB_VLSI/assets/57127783/202e8248-a395-4e4f-bdb7-b39170321d1b)


- In the new netlist, we don't see any instances of submodules such as u1 and u2.
- We get direct instances of and and or gates under the flat design.
- This type of design is known as flat desigin techniques.

```bash
flatten
show multiple_modules
```

![13](https://github.com/mavi62/IIITB_VLSI/assets/57127783/af4ed4df-4593-4f83-88ff-aabda6295485)


We saw how to synthesis the top module, now we will look into synthesis of submodules.

![14](https://github.com/mavi62/IIITB_VLSI/assets/57127783/bddf7c7c-1086-494c-be0a-98a56fbf5d6e)


- We only see submodule 1, we don't get to see the multiple module or submodule 2.


</details>
<details>
<summary> Various Flop coding styles and optimizations </summary>
Under this section, we go through all the various types of flops available and how to design and 
code them efficiently. All the required files are presen in the folder verilog_files.
To understand the need of flops, we refer the example of a simple circuit with delays as 2ns for 
and gate and 1ns for or gate.
 
![15](https://github.com/mavi62/IIITB_VLSI/assets/57127783/5007dae6-da27-4cf4-b06a-bdd38ac5e5da)


- Considering the input goes from 0 to 1 for a and b and simultaneously, 1 to 0 for c.
- Ideally for the transition from (001) to (110), the output should have been a constant at 1,
but because of the delay, we get outout as 0 for a brief period of 2ns.
- This is called a glitch.

![16](https://github.com/mavi62/IIITB_VLSI/assets/57127783/1dada71e-6c85-426d-90cb-4f06f17d1ee2)


- More the number of combinational circuits, more number of glitches appear, giving a glitchy output.
- To avoid this, we need an element to store the value. Comes the flops into picture.
- We use a D flipflop. They are a storage element. They are placed between combinational circuits and changes value only at clock edge.

![17](https://github.com/mavi62/IIITB_VLSI/assets/57127783/df49924f-c80d-489c-876f-bd4134ab494d)
 

- We need to initailise the flops, else the combinational circuits gives a garbage value. For this purpose we have reset and set pins. They can be asynchoronous and synchronous.

Types of flops

- Flops can be designed to be asynchronous or synchronous. It depends on whether the flop is sensitive to the reset and set parameters.
- Under asynchronous, the flop is sensitive to the reset or set, ie the design checks for them and the moment, reset is encountered, the output is pulled to 0 irrespective of the clock. For asynchronous set, the output is pulled to 1.
- The circuit design and timing diagram along with verilog code is displayed under the image below under column 1.
- Under the case of synchronous reset, the output is pulled to 0 at the next clock cycle. The design and timing diagram along the verilog code is shown under the column 2 of the image below.
- Sync reset can be understodd as the input is pulled to 0, thus output becomes 0 for next clock cycle.

![18](https://github.com/mavi62/IIITB_VLSI/assets/57127783/4f0c5aca-26db-47d2-9817-3d385bd7721e)


Now, we go through simuations of async reset, async set and sync async reset and observe the waveforms using gtkwave to have a better understand.

**RTL code for dff_asyncres**
```bash
module dff_asyncres ( input clk ,  input async_reset , input d , output reg q );
always @ (posedge clk , posedge async_reset)
begin
	if(async_reset)
		q <= 1'b0;
	else	
		q <= d;
end
endmodule
```
On execution of iverilog and gtkwave we get

![19](https://github.com/mavi62/IIITB_VLSI/assets/57127783/4d1b561d-602c-4237-a4ed-c20470501e84)


- We can observe that the output q goes to 0 when the reset is encountered.
- Now we synthesis the design using yosys.

![20](https://github.com/mavi62/IIITB_VLSI/assets/57127783/3c07e2ca-206a-44bc-a531-693e0e168120)


**RTL design of dff_async_set**

```bash
module dff_async_set ( input clk ,  input async_set , input d , output reg q );
always @ (posedge clk , posedge async_set)
begin
	if(async_set)
		q <= 1'b1;
	else	
		q <= d;
end
endmodule
```

- upon execution on terminal using iverilog and gtkwave

![21](https://github.com/mavi62/IIITB_VLSI/assets/57127783/a7552fd5-90e8-4e30-948a-54af71483c39)


- We can observe that the output q goes to 1 as soon as we encounter the set irrespective of that clock. -Now we synthesis the design using yosys.

![24](https://github.com/mavi62/IIITB_VLSI/assets/57127783/594eac37-0f87-441a-bfe0-12a1a6576c57)


**RTL code for dff_syncres**

```bash
module dff_syncres ( input clk ,  input sync_reset , input d , output reg q );
always @ (posedge clk )
begin
	if(sync_reset)
		q <= 1'b0;
	else	
		q <= d;
end
endmodule
```

- Upon executing iverilog and gtkwave

![23](https://github.com/mavi62/IIITB_VLSI/assets/57127783/e565029a-06a7-4dd7-83be-09cd45fe0503)


- It is observed that the output q is set to 0 at the next clock pulse when the reset is encountered, thus it is the case of sync reset.
- Now we synthesis the design using yosys.

![25](https://github.com/mavi62/IIITB_VLSI/assets/57127783/2e91298f-7a6f-4927-af27-5ce46db92a8c)

</details>
<details>
<summary> Interesting Optimisations</summary>
Under this section we look into two interesting cases and how they are executed and designed.

First we look into mul2.v

- Code for mul2.v
```bash
module mul2 (input [2:0] a, output [3:0] y);
	assign y = a * 2;
endmodule
```
- The block diagram and the truth table for the executed logic is shown under.

![26](https://github.com/mavi62/IIITB_VLSI/assets/57127783/513e2826-11bc-48d2-bcf1-8f9ef6f4b0a1)


- From these, we are able to infer that the logic requires the input to be multiplied with 2, and upon checking the output it is the input with 1'b0 padding.
- Thus the design for the logic needs no hardware to be mapped.
- We will confirm this using yosys.

![27](https://github.com/mavi62/IIITB_VLSI/assets/57127783/74cb4d2d-b03b-4826-b586-852944f6fff4)


- From the yosys synthesis, we observe the number of cells in design is 0 and there is no hardware to be mapped. These have been highlighted in the picture above.
- The schematic attained shows a similar result.
- This was done in case of multiplication with 2. For multiplication with 4, we give 2'b00 padding and for 8, we give 3'b000 padding. This goes on.

Now, we look into another special case.

- Condider a 3bit number a[2:0], and the logic to be implemented is that the output y[5:0] is equal to 9 times of a[2:0].
- Code for execution
```bash
module mult8 (input [2:0] a , output [5:0] y);
	assign y = a * 9;
endmodule
```
- explanation

![28](https://github.com/mavi62/IIITB_VLSI/assets/57127783/50c62c66-8895-4ef0-a07f-383b8f36ccfb)


- Multiplcation with 9 can be seen as multiplication with 8 and plus 1.
- We know multiplication with 8 is equal to 3'b000 padding, and adding the same 3 bit number to the padded number comes of as concatanation of {a,a}.
- Thus there are no standard cell required for the design. We verify this using yosys.

![29](https://github.com/mavi62/IIITB_VLSI/assets/57127783/3689c124-67fc-49dd-a85f-85de7ed6af83)


- We see that there are no standard cells required.
- We see the concatanation operation done in the netlist.
</details>


## Day 3

<details>
<summary> Summary </summary>
I have synthesized designs with optimizations. Combinational logic optimizations include 1-) 
constant propagation (when the combination is just propagating a constant) and 2-) boolean logic 
optimization (when boolean rules are used to simplify the expression). Sequential logic 
optimizations include 1-) sequential constant propagation (when constant is propagated with clock 
involved), 2-) state optimization (when unused states are optimized), 3-) retiming (when logic is 
split to decrease timing of the different logic portions and increase frequency), and 4-) 
sequential logic cloning (when physical aware synthesis is done to optimize the floop plan)
</details>
<details>
<summary> Introduction to Optimizations </summary>
Optimising the combinational logic circuit is squeezing the logic to get the most optimized digital design so that the circuit finally is area and power efficient. This is achieved by the synthesis tool using various techniques and gives us the most optimized circuit.

**Techniques for optimization for combinational logic**:

- Constant propagation which is Direct optimizxation technique
- Boolean logic optimization using K-map or Quine McKluskey

Here is an example for **Constant Propagation**

![1](https://github.com/mavi62/IIITB_VLSI/assets/57127783/495e88db-3295-4611-9bac-54bda55cec50)


In the above example, if we considor the trasnsistor level circuit of output Y, it has 6 MOS trasistors and when it comes to invertor, only 2 transistors will be sufficient. This is achieved by making A as contstant and propagating the same to output.

**Techniquies for Sequentional logic otimizations**

Below are the various techniques used for sequential logic optimisations:
- Basic
   Sequential contant propagation
- Advanced
   State optimisation
   Retiming
   Sequential Logic Cloning (Floor Plan Aware Synthesis)

-  The input of D ff is grounded, ir d=0, and the reset parameter is given. Here even if the
  reset is given or not the output output of the flop is constant at 0, hence the overall outcome
  is constant.

![2](https://github.com/mavi62/IIITB_VLSI/assets/57127783/e9bc2809-8aae-412a-a85c-156af0e32a11)


- Now taking the same circuit, but instead of reset, we give set. Now when the set is 1, the flop
output follows set. As soon as set is removed, the output goes to 0 at the next positive clock
edge. Thus now we can't remove the flop from design, Thus we retain the flop.

![3](https://github.com/mavi62/IIITB_VLSI/assets/57127783/eab791a2-bdaf-4c95-92b2-8915b304d0fe)


**Advanced Methods for Sequential logic Optimisation**

- State optimization in ASIC design is about finding the best trade-offs among performance, power
efficiency, area utilization, and other design objectives to create an effective and efficient
custom integrated circuit for a particular application.
- Re-timing is the technique used to optimize the timing performance of a digital circuit by
moving registers (flip-flops) to different locations within the circuit without changing its
functionality. The primary goal of retiming is to improve the critical path delay, which is the
longest path through the logic circuit that determines the maximum operating frequency.
- Sequential logic cloning or flip-flop cloning or state machine cloning is the technique used to
replicate or duplicate certain portions of sequential logic circuits. This technique is employed
to improve performance, reduce critical path delays, or optimize power consumption in a design
without altering its functional behavior.



</details>
<details>
	
<summary> Combinational logic optimizations </summary>

Let's consider an example concurrent statement assign **y=a?(b?c:(c?a:0)):(!c)**

The above expression is using a ternary operator which realizes a series of multiplexers, however, when we write the boolean expression at outputs of each mux and simplify them further using boolean reduction techniques, the outout y turns out be just **~(a^c)**

Command to optimize the circuit by yosys is

```bash
yosys> opt_clean -purge
```

opt_clean remove unused cells and wires. The -purge switch removes internal nets if they have a 
public name. This command identifies wires and cells that are unused and removes them. This 
command can be used to clean up after the commands that do the actual work.


In case of multiple models, it is important to flatten the design then followup with 
optimization.

**Lab 1-opt_check.v**
**RTL code**

```bash
module opt_check (input a , input b , output y);
	assign y = a?b:0;
endmodule
```

- after synthesis on yosys

![4](https://github.com/mavi62/IIITB_VLSI/assets/57127783/427d5869-34df-41d9-9995-9903f7fee603)


**Lab_2 opt_check2.v**
**RTL code**
```bash
module opt_check2 (input a , input b , output y);
	assign y = a?1:b;
endmodule
```
- Hardware after synthesis on yosys

![5](https://github.com/mavi62/IIITB_VLSI/assets/57127783/d6acfae8-c65f-4160-9a31-c2c6bb770510)


**Lab_3 opt_check3.v**
**RTL code**
```bash
module opt_check3 (input a , input b, input c , output y);
	assign y = a?(c?b:0):0;
endmodule
```
- hardware after synthesis on yosys

![6](https://github.com/mavi62/IIITB_VLSI/assets/57127783/7e114ac8-eae6-4d3e-b49b-73883be40233)

**Lab_4 opt_check4.v**
**RTL code**
```bash
module opt_check4 (input a , input b , input c , output y);
 assign y = a?(b?(a & c ):c):(!c);
 endmodule
```
- Hardware  after synthesis on yosys

![7](https://github.com/mavi62/IIITB_VLSI/assets/57127783/58e42398-1213-4704-b58a-3520f8d4e666)


**Lab_5 multiple_module_opt.v
**RTL code**

```bash
module sub_module1(input a , input b , output y);
 assign y = a & b;
endmodule


module sub_module2(input a , input b , output y);
 assign y = a^b;
endmodule


module multiple_module_opt(input a , input b , input c , input d , output y);
wire n1,n2,n3;

sub_module1 U1 (.a(a) , .b(1'b1) , .y(n1));
sub_module2 U2 (.a(n1), .b(1'b0) , .y(n2));
sub_module2 U3 (.a(b), .b(d) , .y(n3));

assign y = c | (b & n1); 


endmodule
```

- Hardware after synthesis on yosys

![module1](https://github.com/mavi62/IIITB_VLSI/assets/57127783/107eab44-deff-42a6-8be0-5707f5e43e1a)


**Lab_6 multiple_modules_opt2.v**
**RTL code**

```bash
 module sub_module(input a , input b , output y);
 assign y = a & b;
endmodule



module multiple_module_opt2(input a , input b , input c , input d , output y);
wire n1,n2,n3;

sub_module U1 (.a(a) , .b(1'b0) , .y(n1));
sub_module U2 (.a(b), .b(c) , .y(n2));
sub_module U3 (.a(n2), .b(d) , .y(n3));
sub_module U4 (.a(n3), .b(n1) , .y(y));


endmodule
```

- Hardware after yosys synthesis

![module2](https://github.com/mavi62/IIITB_VLSI/assets/57127783/c4e6e2f5-5527-478f-baf0-dcef17376903)

</details>

<details>
<summary> Sequentional Logic Optimizations </summary>

**Lab_1 dff_const1.v**
**RTL code**
```bash
module dff_const1(input clk, input reset, output reg q);
always @(posedge clk, posedge reset)
begin
	if(reset)
		q <= 1'b0;
	else
		q <= 1'b1;
end

endmodule
```

- Simulation on iverilog and gtkwave

![DFF_1](https://github.com/mavi62/IIITB_VLSI/assets/57127783/43fa19b4-a604-4995-bdac-5a77f236b15c)


- optimization using yosys

![DFF_1_yosys](https://github.com/mavi62/IIITB_VLSI/assets/57127783/5e88a820-939c-43c6-861c-09a6314aca67)


**Lab_2 dff_const2.v**
**RTL code**

```bash
module dff_const2(input clk, input reset, output reg q);
always @(posedge clk, posedge reset)
begin
	if(reset)
		q <= 1'b1;
	else
		q <= 1'b1;
end

endmodule
```

- Simulation using iverilog and yosys
  
![DFF_2](https://github.com/mavi62/IIITB_VLSI/assets/57127783/b97763f2-c798-4a88-bf62-466122e3fc3f)


- optimization using yosys
  
![DFF_2_yosys](https://github.com/mavi62/IIITB_VLSI/assets/57127783/36d9d7f9-199c-40a1-a549-63513425a5d6)


**Lab_3 dff_const3.v**
**RTL code**

```bash
module dff_const2(input clk, input reset, output reg q);
module dff_const3(input clk, input reset, output reg q);
reg q1;

always @(posedge clk, posedge reset)
begin
	if(reset)
	begin
		q <= 1'b1;
		q1 <= 1'b0;
	end
	else
	begin
		q1 <= 1'b1;
		q <= q1;
	end
end

endmodule
```

-simaulation using iverilog and gtkwave

![DFF_3](https://github.com/mavi62/IIITB_VLSI/assets/57127783/f1b8b12e-9ade-4137-9b2d-21a7898d0cf1)


-optimization using yosys

![DFF_3_yosys](https://github.com/mavi62/IIITB_VLSI/assets/57127783/7ab1a684-db78-4841-aab2-3bb234e2b35a)


**Lab_4 dff_const4.v**
**RTL code**

```bash
module dff_const4(input clk, input reset, output reg q);
reg q1;

always @(posedge clk, posedge reset)
begin
	if(reset)
	begin
		q <= 1'b1;
		q1 <= 1'b1;
	end
	else
	begin
		q1 <= 1'b1;
		q <= q1;
	end
end

endmodule
```

-Simulation using iverilog and gtkwave

![DFF_4](https://github.com/mavi62/IIITB_VLSI/assets/57127783/13ae2139-875c-41f7-9130-156919ca66b4)


-optimization using yosys

![DFF_4_yosys](https://github.com/mavi62/IIITB_VLSI/assets/57127783/4a36afa2-bed5-4548-abe0-9db3d46d14a8)


**Lab_5 dff_const5.v**
**RTL code**

```bash

module dff_const5(input clk, input reset, output reg q);
reg q1;

always @(posedge clk, posedge reset)
begin
	if(reset)
	begin
		q <= 1'b0;
		q1 <= 1'b0;
	end
	else
	begin
		q1 <= 1'b1;
		q <= q1;
	end
end

endmodule
```

-simulation using iverilog and gtkwave

![DFF_5](https://github.com/mavi62/IIITB_VLSI/assets/57127783/f72fd157-9d59-43a9-a9dd-8cbbf433cf0f)


-optimization using yosys

![DFF_5_yosys](https://github.com/mavi62/IIITB_VLSI/assets/57127783/50b724c7-3624-4e62-904c-3631f6ea80ce)


</details>

<details>
<summary> Sequential optimizations for unused outputs </summary>
Under this section, we look into how yosys synthesizer optimises the design in case of unused 
bits in the output. For this we have taken a 3 bit counter. In case 1, only the LSB is taken as 
final output, thus the first two are left unused. In case two, we take the entire 3 bits as 
output.
	
![8](https://github.com/mavi62/IIITB_VLSI/assets/57127783/9b2c8d49-d2fe-423e-82eb-89b56096832e)


**Lab_1 using count[0]**
**RTL code**

```bash
module counter_opt (input clk , input reset , output q);
reg [2:0] count;
assign q = count[0];

always @(posedge clk ,posedge reset)
begin
	if(reset)
		count <= 3'b000;
	else
		count <= count + 1;
end

endmodule
```

-synthesis using yosys

![9](https://github.com/mavi62/IIITB_VLSI/assets/57127783/4c3a34d4-4101-4c67-acd8-74f28ed849e2)


![10](https://github.com/mavi62/IIITB_VLSI/assets/57127783/19bb7c47-99dc-4b10-b862-96bae2054106)


**Lab_2 using all three bits count[2] and count[1] and count[0]
**RTL code**

```bash
module counter_opt (input clk , input reset , output q);
reg [2:0] count;
assign q = count[2:0] == 3'b100;

always @(posedge clk ,posedge reset)
begin
	if(reset)
		count <= 3'b000;
	else
		count <= count + 1;
end
```

- synthesis using yosys

![11](https://github.com/mavi62/IIITB_VLSI/assets/57127783/2a2a0827-9a8d-4b47-a7ba-40cf6409b1f5)


![12](https://github.com/mavi62/IIITB_VLSI/assets/57127783/3921800e-c7ac-45c9-9e33-ec13e1eb6d91)


- In the yosys generation, we see the design has encorporated 3 dff for the 3 bit counter.
- It is evident that the yosys synthesizer optimizes for the unsed bits in the output. This so important as illustrated because it saves a ton of space, and speed, and improves efficiency of the final design.
 </details> 


## Day 4

<details>
<summary> Summary </summary>
performed Gate Level Simulation (GLS). GLS is when the testbench is run with the netlist as 
design under test to ensure there are no synthesis and simulation mismatches, and it is important 
as it 1-) verifies the logical correctness of the post-synthesis design and 2-) ensures the 
timing of design is met. Synthesis and simulation mismatches can happen due to a lot of reasons 
including missing sensitivity list (some signal changes are not captured by the circuit because 
they are missing from the sensitivity list), blocking vs non-blocking assignments (inside an 
always block, "=" statements inside it are blocking meaning they are executed in order they are 
written, assignments (<=) on the other hand are non-blocking so they are executed in parallel => 
non-blocking should be used with sequential circuits. Note that the synthesis will yield same 
circuit with blocking and non-blockin; it will yield what would be obtained as if the statements 
where written in non-blocking format, so in case they weren't written as such a mismatch will 
occur with the simulation), and non-standard verilog coding.
</details>

<details>
<summary> GLS, Synthesis-Simulation mismatch and Blocking,Non-blocking statements </summary>
**GLS concepts and flow**
What is GLS-Gate Level Simulation?
GLS is generating the simulation output by running test bench with netlist file generated from 
synthesis as design under test. Netlist is logically same as RTL code, therefore, same test bench 
can be used for it.

Why GLS?
We perform this to verify logical correctness of the design after synthesizing it. Also ensuring 
the timing of the design is met.

Below picture gives an insight of the procedure. Here while using iverilog, we also include gate 
level verilog models to generate GLS simulation.

![1](https://github.com/mavi62/IIITB_VLSI/assets/57127783/2db01bcf-8c07-4551-995a-00479e7566f8)


**Synthesis Simulation Mismatch**
There are three main reasons for Synthesis Simulation Mismatch:
      -Missing sensitivity lis in always block
      -blocking vs non-blocking assignments
      -Non standard verilog coding
*Missing Sensitivity List*
To understand this we use examples for a mux with different sensitivity

-Code 1

```bash
module mux1 (input sel , i0, i1 ,
output reg y);

always@(sel)
begin
if(sel)
	y=i1;
else
	y=i0;
end

endmodule
```

-Code 2

```bash
module mux (input sel , i0, i1 ,
output reg y);

always@(*) 
begin
if(sel)
	y=i1;
else
	y=i0;
end

endmodule
```

- Mux 1 is sensitive to changes is changes in latches, ie the output y will change only at the changes of sel. Thus the changes of inputs i1 and i0 are not displayed in the output.
- Mux 2 is sensitive to all three, so when high sel, output covers all changes in i1, and for low sel, all changes in i0 are covered.
- Now, the simulation and synthesis of mux 2 wont have any mismatch.
- But mux1 will have mismatch,as simulators work on sensitivity list and the simulation will behave as a double edge triggered latch, while the synthesizer converts the logic into netlist and doesn't look into sensitivity list, thus synthesis will behave as a 2 input MUX.

*Blocking and Non-blocking statements*
Blocking statements execute the statemetns in the order they are written inside the always block. 
Non-Blocking statements execute all the RHS and once always block is entered, the values are 
assigned to LHS. This will give mismatch as sometimes, improper use of blocking statements can 
create latches.
</details>
<details>
<summary> Lab- GLS Synth Simulation Mismatch </summary>

**Lab_1 ternary_operator_mux.v**
**RTL code**

```bash
module ternary_operator_mux (input i0 , input i1 , input sel , output y);
	assign y = sel?i1:i0;
endmodule
```

- Simulation using iverilog and yosys

![2](https://github.com/mavi62/IIITB_VLSI/assets/57127783/632608c9-4ca2-488e-8e0c-847c0882185b)


- now we synthesis using yosys

![3](https://github.com/mavi62/IIITB_VLSI/assets/57127783/3e54eda4-0a6c-4af3-9bf3-626b6ff9e6f5)


- generated netlist
  
![4](https://github.com/mavi62/IIITB_VLSI/assets/57127783/769ad079-14a9-4603-9559-eeabf315815e)


-Running GLS using the netlist file generated during yosys

![5](https://github.com/mavi62/IIITB_VLSI/assets/57127783/3e99034b-35e7-4ba1-9f8d-8efeb50a773a)


**it is clear that both simulatons are same**

**Lab_2 bad_mux.v**
**RTL code**

```bash

module bad_mux (input i0 , input i1 , input sel , output reg y);
always @ (sel)
begin
	if(sel)
		y <= i1;
	else 
		y <= i0;
end
endmodule
```

- Simulation using iverilog and gtkwave
  
![6](https://github.com/mavi62/IIITB_VLSI/assets/57127783/572a896b-b776-473a-ae7b-9120c2a0c371)


- synthesis using Yosys
  
![7](https://github.com/mavi62/IIITB_VLSI/assets/57127783/87358744-7177-4124-93cc-c011afcbe0ff)


- Running GLS using netlist file generated during yosys

![8](https://github.com/mavi62/IIITB_VLSI/assets/57127783/965ec86e-5d95-4a72-89d5-06f26778ecf0)


- Under this, we see a clear mismatch between the simulation and synthesis designs. The RTL file
and netlist files aren't the same logic implemention. This happened due to the sensitivity
listing under the RTL file.
</details>
<details>
<summary> Lab on Synthesis_Simulation Mismatch and Blocking </summary>
In thissection we willlook into the mismatch between simulation and synthesis caused due to the blocking statements.
	
**RTL code**

```bash
module blocking_caveat (input a , input b , input  c, output reg d); 
reg x;
always @ (*)
begin
	d = x & c;
	x = a | b;
end
endmodule
```

- Running the simulation using iverilog and gtkwave
  
![9](https://github.com/mavi62/IIITB_VLSI/assets/57127783/dc882e67-515f-4e4c-aedb-fea35bd49176)


- Synthesis using yosys
  
![10](https://github.com/mavi62/IIITB_VLSI/assets/57127783/1fae9e56-075a-42a1-8ea2-92872be18a33)


- Netlist generated
  
![10 5](https://github.com/mavi62/IIITB_VLSI/assets/57127783/7fbfc00d-9bff-40c2-b871-c51055612488)


- Running GLS on the netlist file generated using iverilog and gtkwave
  
![11](https://github.com/mavi62/IIITB_VLSI/assets/57127783/46b86157-e3af-41ef-96ec-0280df84b28f)

  
- It is seen that the waveform matches with the expected output for d=((a|b).c).
- There is clear mismatch between the simulation and synthesis in this case. This happended coz
we used blocking statements, and while simulation, the design makes a flop, which wasn't the
intention of the original design.
</details>
