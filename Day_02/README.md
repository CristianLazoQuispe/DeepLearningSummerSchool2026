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

<!-- Notes go here -->

## Key takeaways

<!-- Summarize the main points -->

## Questions & follow-ups

<!-- Things to revisit -->
