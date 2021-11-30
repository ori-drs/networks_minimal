# Networks Minimal

This repository contains Eigen-based C++ implementation of a Multi-Layer Perceptron (MLP) and a Gated
Recurrent Unit (GRU) network. In addition, the repository also provides example scripts to export PyTorch
network parameters to ```.txt``` files. These parameters can then be loaded into the C++ networks.

This README assumes that ```$PROJECT_DIR``` refers to the root of this repository.


## Build
To build the shared library and the example executables:

```
cd $PROJECT_DIR
mkdir build && cd build
cmake .. -DCMAKE_BUILD_TYPE=Release
make
```

This will generate a shared library at ```$PROJECT_DIR/lib```. To execute the examples provided in
```$PROJECT_DIR/examples/<robot>_actuation.cpp```:
```
cd $PROJECT_DIR/build
./<robot>_actuation
```
Here, ```<robot>``` can either be **a1** or **boxy**.


## Parameter Export
Example code to export PyTorch network parameters is provided in 
```$PROJECT_DIR/scripts/torch_export.py```. To
execute this, creating a virtual environment is recommended:
```
cd $PROJECT_DIR
python3 -m venv venv
source venv/bin/activate
pip install -e .
```
After this, execute the script using:
```
python scripts/torch_export.py
```

This will create the ```$PROJECT_DIR/scripts/exported_paramters``` directory, and the network
parameters will be stored here.


## Features
As of yet, you can only load network parameters and perform a forward pass with the MLP and GRU
implementations. The MLP also allows computation of network Jacobian using the ```gradient()```
function.


## Potential Optimizations
The current implementation builds upon dynamic Eigen matrices. A static implementation
could possibly offer better performance. This is currently not a priority since most of the
forward passes for smaller networks can be performed in microseconds. However, any
contribution from the community in this direction is highly encouraged.


## Author(s)

* Siddhant Gangapurwala <siddhant@gangapurwala.com>
