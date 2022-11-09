# Stage I - AUXILIARY CELL GENERATION

# ALIGN: Analog Layout, Intelligently Generated from Netlists

The goal of ALIGN (Analog Layout, Intelligently Generated from Netlists) is to automatically translate an unannotated (or partially annotated) SPICE netlist of an analog circuit to a GDSII layout.

**The Auxilary cell of any design is generate through the ALIGN tool**

![Capture](https://user-images.githubusercontent.com/67214592/200850964-529ae178-6405-4d19-9535-bcdda6fff54c.PNG)

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
  
