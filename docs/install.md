# Getting Started with WNTR-Quantum

An introductory tutorial!

## Installation

To install `wntr_quantum` from the GitHub repository, do:

```console
git clone git@github.com:Quantum4WaterDistribution/wntr-quantum.git
cd wntr-quantum
python -m pip install .
```

## Installation of EPANET Quantum

WNTR Quantum can use a dedicated EPANET solver that allows to offload calculation to quantum linear solvers. This custom EPANET code can be found at : https://github.com/QuantumApplicationLab/EPANET. To install this sover follow the instructions below:


```
# clone EPANET
git clone https://github.com/Quantum4WaterDistribution/EPANET

# build EPANET
cd EPANET
mkdir build
cd build 
cmake .. 
cmake --build . --config Release

# copy the shared lib
cp lib/libepanet2.so <path to wntr-quantum>/wntr-quantum/wntr_quantum/epanet/Linux/libepanet22_amd64.so

# export environment variable
export EPANET_TMP=<path to tmp dir>/.epanet_quantum 
export EPANET_QUANTUM = <path to EPANET_QUANTUM>
```

## Simple Example

The example below shows how to use the Variational Quantum Linear Solver to solve the linear systems required in the Newton-Raphson-GGA algorithm.

```python
import wntr
import wntr_quantum
from qiskit.circuit.library import RealAmplitudes
from qiskit.primitives import Estimator
from qiskit_algorithms import optimizers as opt
from quantum_newton_raphson.vqls_solver import VQLS_SOLVER

# define the water network 
inp_file = 'Net2Loops.inp'
wn = wntr.network.WaterNetworkModel(inp_file)

# define the vqls ansatz
n_qubits = 3
qc = RealAmplitudes(n_qubits, reps=3, entanglement="full")
estimator = Estimator()

# define the VQLS solver
linear_solver = VQLS_SOLVER(
    estimator=estimator,
    ansatz=qc,
    optimizer=[opt.COBYLA(maxiter=1000, disp=True), opt.CG(maxiter=500, disp=True)],
    matrix_decomposition="symmetric",
    verbose=True,
    preconditioner="diagonal_scaling",
    reorder=True,
)

# use wntr-quantum to solve the network
sim = wntr_quantum.sim.QuantumEpanetSimulator(wn, linear_solver=linear_solver)
results_vqls = sim.run_sim(linear_solver=linear_solver)
```