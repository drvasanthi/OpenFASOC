# OpenFASoC

**OpenFASoC: Fully Open-Source Autonomous SoC Synthesis using Customizable Cell-Based Synthesizable Analog Circuits**

OpenFASOC is focused on open-source automate analog generation from user specification to GDSII with fully open-sourced tools.
This project is led by a team of researchers at the University of Michigan is inspired from FASoC whcih sits on proprietary tools. See more about FASoC at [website](https://fasoc.engin.umich.edu)

Pre-requisites
****************

1. `Yosys` for logic synthesis
2. `Openroad` for placing and routing
3. `Klayout` to produce the final GDS file
4. `Magic` for DRC and LVS checks as well as PEX
5. `Ngspice` for simulation

## Manual Installation

> Step 1 - Git clone fasoc repo

```
$  git clone https://github.com/idea-fasoc/openfasoc  
```

> Step 2 - Go to the root directory of the repo and install all required Python libraries using:

```
pip install -r requirements.txt  
```

> Step 3 - Using Conda

OpenFASoC's dependencies can be very easily installed if you're using a Conda environment. If you're not, start by [installing Miniconda](https://docs.conda.io/projects/conda/en/latest/user-guide/install/linux.html)

```
$ conda create --name "openfasoc" python=3.8  
$ conda activate openfasoc  
```

# Example - Design Flow of Temperatore Sensor Generator

This generator creates a compact mixed-signal temperature sensor based on the topology from [this paper](https://ieeexplore.ieee.org/document/9816083). It consists of a ring oscillator whose frequency is controlled by the voltage drop over a MOSFET operating in subthreshold regime, where its dependency on temperature is exponential.

![image](https://user-images.githubusercontent.com/67214592/206749704-9e007c56-7f9a-4f43-9a9a-00df8e8d6a34.png)

  Block diagram of the temperature sensor’s circuit

The physical implementation of the analog blocks in the circuit is done using two manually designed standard cells (Auxiliary Cell):

* HEADER cell, containing the transistors in subthreshold operation;
* SLC cell, containing the Split-Control Level Converter.

![image](https://user-images.githubusercontent.com/67214592/206750794-8dac8329-4d50-48f4-aea0-58c8cc5a5804.png)

Step 1 - Understanding Input

![image](https://user-images.githubusercontent.com/67214592/206842807-611c2d3d-b86c-4b49-8f45-5b5b9a21ac5f.png)

![image](https://user-images.githubusercontent.com/67214592/206842888-bf185015-b080-493e-9a70-b97964ce95f9.png)

Step 2 - Logic Synthesis

![image](https://user-images.githubusercontent.com/67214592/206842918-290e54aa-e639-45cc-bc36-8cf998674883.png)

![image](https://user-images.githubusercontent.com/67214592/206843915-d6bf5bcf-2619-419a-9dca-a466f37ac443.png)

Step 3: Automatic Place and Route - Floorplan

![image](https://user-images.githubusercontent.com/67214592/206843093-7e9f3cd4-c0d6-48f0-b647-fd1bff389223.png)

![image](https://user-images.githubusercontent.com/67214592/206843964-31490288-97be-4717-a41e-d18b66ede239.png)

![image](https://user-images.githubusercontent.com/67214592/206843977-a54586b0-c2e5-4d26-a2f3-227ddda2e427.png)

![image](https://user-images.githubusercontent.com/67214592/206843990-02e37d57-37db-476a-999d-fd90dbeaa4fd.png)

Step 4: Placement

![image](https://user-images.githubusercontent.com/67214592/206843156-492a899a-f2d2-4c37-815a-9b752e09c140.png)

![image](https://user-images.githubusercontent.com/67214592/206844048-f6bf532f-3f48-43b3-91ba-c8ad82e651d8.png)

![image](https://user-images.githubusercontent.com/67214592/206844055-6f0cecee-aa31-4746-a856-407e47c78469.png)

Step 5: CTS

![image](https://user-images.githubusercontent.com/67214592/206843168-a03df1dc-e6cc-4c8f-b9ff-a6f5edb1145f.png)

Step 6: Routing

![image](https://user-images.githubusercontent.com/67214592/206843179-0f20b92c-fb8b-450b-be18-8efae35f2a48.png)

![image](https://user-images.githubusercontent.com/67214592/206844281-cd562a32-4044-44f4-bcb6-35b4bf357672.png)

![image](https://user-images.githubusercontent.com/67214592/206844365-b987a8ee-3d66-4140-9294-f5dfe2adee38.png)

Step 7: DRC and LVS

![image](https://user-images.githubusercontent.com/67214592/206843191-5f0a5d32-2b88-4d9d-a173-f611938938ac.png)

![image](https://user-images.githubusercontent.com/67214592/206843201-5e1b0cb9-5a71-4ce9-9d01-873f47a20080.png)

![image](https://user-images.githubusercontent.com/67214592/206845588-67cf164d-93ba-48ee-a93c-6ea683550441.png)

# Stage I - AUXILIARY CELL GENERATION

# ALIGN: Analog Layout, Intelligently Generated from Netlists

The goal of ALIGN (Analog Layout, Intelligently Generated from Netlists) is to automatically translate an unannotated (or partially annotated) SPICE netlist of an analog circuit to a GDSII layout.

**The Auxilary cell of any design is generate through the ALIGN tool**

![image](https://user-images.githubusercontent.com/67214592/201029622-8a8e54db-fd87-4f43-8a7b-5596a1145e4f.png)

## Inputs

* SPICE netlist   
* SKY130 PDK

## Outputs

* Design JSON: Final layout in JSON form which can be viewed using the ALIGN Viewer.  
* Layout GDS: Final layout of the design. The output GDS can be imported into any GDSII viewer.

# Tool Installation

The following dependencies must be met by your system:
  * gcc >= 6.1.0  
  * python >= 3.7
  
Note: In case you have multiple gcc versions installed on your system, we recommend explicitly setting the compiler paths as follows:
```console
$ export CC=/path/to/your/gcc
$ export CXX=/path/to/your/g++
```

### Step 1: Clone the ALIGN source code to your local environment
```
$ git clone https://github.com/ALIGN-analoglayout/ALIGN-public
$ cd ALIGN-public
```

### Step 2: Create a Python virtualenv
```
$ python -m venv general
$ source general/bin/activate
$ python -m pip install pip --upgrade
```

### Step 3: Install ALIGN as a USER
```
$ pip install -v .
```

### Step 4:For python developers:
```
$ pip install -e .[test]
$ pip install setuptools wheel pybind11 scikit-build cmake ninja  
$ pip install -v -e .[test] --no-build-isolation  
$ pip install -v --no-build-isolation -e . --no-deps --install-option='-DBUILD_TESTING=ON'  
```

### Step 5: Add pdk
```
git clone https://github.com/ALIGN-analoglayout/ALIGN-pdk-sky130  
```


## Output Database:

* GDS, LEF
  
### The outputs generated from aux_cell is given to ver_dir as an input.

https://github.com/mahati-basavaraju/openFasoc_Flow.git

## Contributer

  * Vasanthi D R

## Acknowledgement
  
  * Kunal Ghosh, Director, VSD Corp. Pvt. Ltd.
  * Madhav Rao, Professor, IIIT-Bangalore.
  * Nanditha Rao, Professor, IIIT-Bangalore.

## Contact Information

  * Vasanthi D R, PhD Scholar, International Institute of Information Technology, Bangalore vasanthidr11@gmail.com
  * Kunal Ghosh, Director, VSD Corp. Pvt. Ltd. kunalghosh@gmail.com
  * Madhav Rao, Professor, IIIT-Bangalore. mr@iiitb.ac.in
  * Nanditha Rao, Professor, IIIT-Bangalore. nanditha.rao@iiitb.ac.in
  
