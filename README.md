# aqc-hackathon

Access the Colab notebook [here](https://colab.research.google.com/drive/1QYMdiAY7yfpPI6iaBXpyNrLU_9pytog3).
---

## What this repository is

This repository is a practical exploration of **portfolio optimisation under constraints**, built in response to the [**Africa Quantum Consortium – Hack the Horizon**](https://aqchackthehorizon25.lovable.app) challenge ([Quantum Finance Track](https://drive.google.com/file/u/1/d/1SXz_EkpQKyebwm4GSu6VFZYKnCfvNSWz/view?usp=sharing&pli=1)).

The challenge frames portfolio selection as a binary optimisation problem under real-world constraints: fixed portfolio size, sector limits, transaction costs, and turnover. It also invites participants to explore quantum and quantum-inspired methods, alongside classical baselines.

---

## The core idea

Rather than jumping straight into a large quantum optimisation problem, the notebook follows a **hybrid, data-first approach**:

* Define the portfolio problem cleanly and explicitly.
* Enforce constraints early and visibly.
* Use classical heuristics and scoring to narrow the search space.
* Apply quantum optimisation only to a small, controlled subproblem.
* Score all outputs using the same objective, regardless of solver.

The goal is not to claim quantum advantage, but to show how quantum methods can fit into a realistic portfolio decision workflow.

---

## Why the problem is structured this way

Current quantum tooling is sensitive to problem size. Binary variables and constraints expand quickly, and both simulators and exact solvers become impractical long before reaching full-scale portfolios.

To deal with this, we:

* Use **shortlists** to limit the quantum search space.
* Enforce sector caps during shortlist construction, not inside the QUBO.
* Keep only one hard constraint in the quantum model: pick exactly N assets.
* Add guards to stop execution if the optimisation problem grows too large.

This keeps runtime predictable and makes the quantum step demonstrable end-to-end.

---

## What the quantum step represents

The quantum cell is a **small, bounded demo**, not a full portfolio optimiser.

It takes a shortlist of assets and solves the same selection problem in two ways:

* A classical exact solver (when feasible).
* QAOA on a simulator.

Both outputs are then evaluated using the same scoring function used elsewhere in the notebook. This makes the comparison concrete and avoids treating quantum results as special or separate.

---

## What this is (and isn’t)

This is:

* A transparent implementation of constrained portfolio optimisation.
* A hybrid classical–quantum workflow that actually runs.
* A faithful, scoped response to the hackathon brief.

This is not:

* A production trading system.
* A claim of quantum advantage.
* A full financial model with covariance matrices and market dynamics.

---

## How to read the notebook

Read it top to bottom. Each cell builds on the previous one. The quantum step only makes sense once the classical setup, scoring logic, and constraints are clear (and have been run in sequence).

Contact/queries: Mo Shehu — mo@shehudev.com.


