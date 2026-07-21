# Day 2 — July 21, 2026

_Notes from the second day of the DL4SCI 2026 Summer School._

## Sessions

### Discrete Diffusion — Ferdinando Fioretto (University of Virginia)

**Talk structure — 3 topics:**
1. **Foundations** — _How should we think of constrained generation?_
2. **Applications** — _From convex to black-box constraints and verifiers._
3. **Discrete diffusion** — _How can global rules steer local token updates?_

#### Topic 1 — Foundations: how should we think of constrained generation?

- Recap of the **diffusion reverse process** — how to **update $x_t$** step by step
  (denoising from $x_t$ toward $x_{t-1}$).
- **Constraint-based diffusion**
  - **Key idea:** recast the **sampling process as a sequential optimization problem**
    (each reverse step = an optimization step, so constraints can be enforced along the way).

##### Concept — what is constrained generation?

- **Constrained generation** = generating samples that **must satisfy given constraints**, not
  just "look realistic". Output must land in a **feasible set** defined by rules.
- **Examples:**
  - **Physics:** respect a **conservation law** (mass, energy), PDEs, or physically valid ranges.
  - **Chemistry / molecules:** chemically **valid** structures (correct valences), target property.
  - **Geometry:** symmetries, boundary conditions, no collisions.
  - **Tabular:** columns sum to 100%, age ≥ 0, etc.
- **Two types:**
  - **Hard constraints** — must always hold (e.g. chemical valence).
  - **Soft constraints** — penalized when violated, but tolerated a bit.
- **Why it's hard in diffusion:** the reverse process denoises freely, so by default it does
  **not** guarantee feasibility. Fix: recast each sampling step as an **optimization** →
  project / push the sample toward the constraint-satisfying region at every step, so the final
  output satisfies the constraint.
- **Analogy:** free generation = drawing freely; constrained generation = **drawing inside the
  lines** (the sequential optimization corrects the stroke at each step so it stays in bounds).

#### Topic 2 — Applications: from convex to black-box constraints and verifiers

##### Application — microstructure material design (constrained porosity)

- Task: design material **microstructures** with a **constrained porosity** (target/allowed
  pore fraction).
- **Challenges:**
  - **Data sparsity** — few training samples.
  - **Out-of-distribution constraints** — the requested porosity constraints on the generated
    materials can fall **outside** the training distribution.

##### Experimental results — physics-informed motion

- Generate **video frames that adhere to physical principles**.
- **Interesting:** applied **at inference time** (constraints enforced during sampling, not
  retraining).
- Discretized kinematics used (notation approximate from slide):
  $$p_t = p_{t-1} + \left(v_t + \tfrac{1}{2}\,\frac{dv_t}{dt}\right), \qquad
    v_{t+1} = \frac{dp_t}{dt} + \frac{dv_t}{dt}$$
- **Challenges:**
  - **Satisfying ODEs** (make the trajectory obey the governing equations).
  - **Generalize to out-of-distribution constraints.**
- **Key insight:** what was previously **out-of-distribution** in terms of *data similarity*
  becomes **in-distribution** at the level of the … _(physics / constraints / governing laws?
  TODO — finish from slide)_.
  - Intuition: raw samples may look OOD in pixel/data space, but once you measure them by whether
    they **satisfy the physics**, they lie inside the feasible/physical distribution.

##### Augmented Lagrangian sampling (black-box constraints / verifiers)

- Use **augmented Lagrangian** sampling when:
  - the constraint set $C$ is **highly non-convex**, or
  - **only violation residuals** can be computed (you can measure *how much* a constraint is
    violated, but not project/solve it exactly).

##### Application — safe autonomy (multi-robot setting)

- **Key results:** high success rates in **all scenarios (96–100%)**, while **SOTA models'
  performance drops significantly** as the number of robots grows (SOTA degrades by **> 15%**).

##### Application — protein design

- Problem with the naive approach: you have to **generate many samples** and then check which
  ones satisfy the **physical / chemical / biological constraints** (low yield of valid designs).
- Baseline: **RFdiffusion** → they propose **CADM** (constraint-aware diffusion model).
- **Result:** generating **usable structures in 21.0%** of total generations (and **up to 83.0%**
  for **well-posed ligands**).

##### Application — inverse design of mechanical metamaterials

- Goal: **target stress–strain responses** (design a material that produces a desired
  stress–strain curve).
- **Metamaterials:** materials with specific mechanical properties obtained from **periodic
  arrangements of small-scale structural building blocks**.
- **Challenge:** go **from the desired stress–strain curve → to a corresponding small-scale
  structure** (the inverse design problem).

#### Topic 3 — Discrete diffusion: how can global rules steer local token updates?

- Core question: **how can global rules steer local token updates?** In discrete diffusion each
  step updates **local tokens**, yet constraints are often **global** (over the whole sample) —
  the challenge is making global constraints guide the per-token discrete updates.

##### Application — synthetic chemistry: molecular generation

- **Small vocabulary** (~**80 tokens**) → **easy to train** and gets **good results**.
- **But:** the **search for valid molecules is still hard** — even with a tiny vocab and good
  training, ensuring the generated molecules satisfy validity constraints remains the bottleneck.

<!-- Notes go here -->


## Key takeaways

<!-- Summarize the main points -->

## Questions & follow-ups

<!-- Things to revisit -->
