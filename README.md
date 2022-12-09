# OpenFASoC

**OpenFASoC: Fully Open-Source Autonomous SoC Synthesis using Customizable Cell-Based Synthesizable Analog Circuits**

OpenFASOC is focused on open-source automate analog generation from user specification to GDSII with fully open-sourced tools.
This project is led by a team of researchers at the University of Michigan is inspired from FASoC whcih sits on proprietary tools. (See more about FaSoC at [website](https://fasoc.engin.umich.edu)

Prerequisites
****************

1. Yosys for logic synthesis
2. Openroad for placing and routing
3. Klayout to produce the final GDS file
4. Magic for DRC and LVS checks as well as PEX
5. Ngspice for simulation

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

#Stage I - AUXILIARY CELL GENERATION

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

* [CDL](https://github.com/Bandaanusha/OPENFASOC/blob/main/Aux_cell_generator_outputs.md)
* [GDS, LEF](https://github.com/DebanganaMukherjee/OpenFASOC/blob/main/AUXCELL_GENERATOR_OUTPUTS.md)
  
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
  
