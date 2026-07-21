# Day 2 — July 21, 2026

_Notes from the second day of the DL4SCI 2026 Summer School._

## Sessions

### Discrete Diffusion — Ferdinando Fioretto (University of Virginia)

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

#### Application — microstructure material design (constrained porosity)

- Task: design material **microstructures** with a **constrained porosity** (target/allowed
  pore fraction).
- **Challenges:**
  - **Data sparsity** — few training samples.
  - **Out-of-distribution constraints** — the requested porosity constraints on the generated
    materials can fall **outside** the training distribution.

#### Experimental results — physics-informed motion

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

#### Augmented Lagrangian sampling

- Use **augmented Lagrangian** sampling when:
  - the constraint set $C$ is **highly non-convex**, or
  - **only violation residuals** can be computed (you can measure *how much* a constraint is
    violated, but not project/solve it exactly).

<!-- Notes go here -->

## Key takeaways

<!-- Summarize the main points -->

## Questions & follow-ups

<!-- Things to revisit -->
