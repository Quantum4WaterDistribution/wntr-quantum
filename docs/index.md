<!-- # WNTR -->

![wntr_quantum](./wntr_quantum_logo.png)

<!-- `wntr_quantum` builds on the python package [WNTR](https://github.com/USEPA/WNTR) to leverage quantum computing for the simulation and optimization of water networks. The main capablities of the software are: -->

<!-- ## Installation

To install wntr-quantum, run the following command from the command line:

```bash
pip install wntr-quantum
``` -->


<!-- <div class="text-center">
<a href="getting-started/" class="btn btn-primary" role="button">Getting Started</a>
<a href="user-guide/" class="btn btn-primary" role="button">User Guide</a>
</div> -->

<!-- ## Features -->

<div class="pt-2 pb-4 px-4 my-4 bg-body-tertiary rounded-3">
<h2 class="display-4 text-center">Features</h2>

<div class="row">
  <div class="col-sm-6">
    <div class="card mb-4">
      <div class="card-body">
        <h3 class="card-title">Quantum Enhanced Newton-Raphson Algorithm</h3>
        <p class="card-text">
            The  <a href="https://github.com/Quantum4WaterDistribution/wntr-quantum/blob/da5aaa40f0ee20b0d73716200a2f4f3d7a809825/wntr_quantum/sim/epanet.py#L75">QuantumEpanetSimulator</a> of `wntr_quantum` use quantum solvers to solve the linear systems required as part of the Newon-Raphson GGA algorithm.
        </p>
      </div>
    </div>
  </div>
  <div class="col-sm-6">
    <div class="card mb-4">
      <div class="card-body">
        <h3 class="card-title">Quantum Hydraulics Simulations</h3>
        <p class="card-text">
            The <a href="https://github.com/Quantum4WaterDistribution/wntr-quantum/blob/da5aaa40f0ee20b0d73716200a2f4f3d7a809825/wntr_quantum/sim/core_qubo.py#L14">FullQuboPolynomialSimulator</a> recast the hydraulics equation as a Quadratic Unconstrained Binary Optimization (QUBO) problem, that can be solved using quantum annealers.
        </p>
      </div>
    </div>
  </div>
</div>

<div class="row">
  <div class="col-sm-6">
    <div class="card">
      <div class="card-body">
        <h3 class="card-title">Quantum Optimization of Water Networks</h3>
        <p class="card-text">
            The <a href="https://github.com/Quantum4WaterDistribution/wntr-quantum/blob/da5aaa40f0ee20b0d73716200a2f4f3d7a809825/wntr_quantum/design/qubo_pipe_diam.py#L32">QUBODesignPipeDiameter</a> recast the hydraulics equation and the pipe-diameter optimization as a Quadratic Unconstrained Binary Optimization problem, that can be solved using quantum annealers.
        </p>
      </div>
    </div>
  </div>
  <div class="col-sm-6">
    <div class="card">
      <div class="card-body">
        <h3 class="card-title">Quantum Linear Solvers</h3>
        <p class="card-text">
            Multiple Gate Base and Annealer Quantum Linear solvers available to integrate in optimization and design problems.
        </p>
      </div>
    </div>
  </div>
</div>
</div>
