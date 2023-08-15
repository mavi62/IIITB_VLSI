# IIITB_VLSI

This github repository summarizes the progress made in the VSD-HDP tapeout program. Quick links:

[Day 0 : Open Source Labs installation](#day-0)

[Day 1 : Introduction to Verilog RTL design and Synthesis](#day-1)

[Day-2-Timing libs,hierarchical,flat synthesis,efficient flop coding styles](#Day-2-Timing-libs-hierarchical-flat-synthesis-efficient-flop-coding-styles)


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
  <summary>Simulation</summary>
  
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


  **Yosys**:It is a framework for RTL synthesis. It provides a basic set of synthesis algorithms for various application domains. Yosys is the core component of most our implementation and verification flows.
  
![3](https://github.com/mavi62/IIITB_VLSI/assets/57127783/8382b5c5-2a14-43f7-a883-9fda887b7a37)


Below are the commands to perform above synthesis.

- RTL Design  - read_verilog
- .lib        - read_liberty
- netlist file- write_verilog

![4](https://github.com/mavi62/IIITB_VLSI/assets/57127783/a169bf08-ae9b-46c3-97f2-03f2872a9553)


![synth_1](https://github.com/mavi62/IIITB_VLSI/assets/57127783/14be6283-143c-424d-afc3-650684a3b566)


**.lib :** It is a collection of logical modules like logic gates. It contains cells with different sppeds, no. of inputs etc. that can be used as required.

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

# Day-2

<details>
<summary>Introduction to timing .libs</summary>
</details> 
