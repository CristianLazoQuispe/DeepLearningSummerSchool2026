# References — models, methods & papers mentioned

Consolidated list of models, techniques, and papers referenced in the DL4SCI 2026 lectures.
Links are added only where verified; others are marked _(look up)_.

## Day 1

### Generative AI for Science — Arash Vahdat (Nvidia)

**Molecules**
- **SMILES** — string notation for molecules _(look up)_.
- **SAFE** — Sequential Attachment-based Fragment Embedding (fragment-based strings) _(look up)_.
- **SAFE-GPT** — autoregressive fragment model _(look up)_.
- **GenMol** — fragment-based **discrete diffusion** model _(look up)_.
- **ReaSyn** (Reaction Synthesis) — encoder–decoder transformer predicting synthetic pathway _(look up)_.

**Proteins**
- **La-Proteina** — fully-atomistic protein design (encoder–decoder) _(look up)_.
- **Complexa** — protein binder design _(look up)_.

**Concepts**
- Reward-tilted / RL-as-inference distribution $q^*(x)\propto p_\theta(x)\exp(R(x;c)/\lambda)$.
- Three paradigms: generative training, post-training alignment w/ RL, test-time search.

### Accelerated Diffusion Models — Julius Berner (Nvidia)

- **Flow matching** — interpolation + velocity field.
- **DiT** (Diffusion Transformer) with adaLN time-conditioning _(look up)_.
- **Latent diffusion** (compress to latent, e.g. VAE / representation encoder).
- **Rectified flow / Reflow** — straighten trajectories _(look up)_.
- **Optimal transport coupling** (mini-batch OT).
- **FlashAttention** — hardware-optimized attention _(look up)_.
- **FLUX.2-dev** — image model used as inference-speedup case study _(look up)_.
- **State-space models (SSMs)** — sub-quadratic sequence models _(look up)_.
- **Progressive distillation** — learn large jumps from smaller ones _(look up)_.
- **Consistency models / Eulerian flow maps** — self-consistency along trajectory _(look up)_.
- **Lagrangian flow maps** — differentiate flow map w.r.t. target time $t$.
- **Pi-Flow (π-Flow)** — parallel decoding distillation _(look up)_.
- **Adversarial distillation** — Projected GANs on teacher features, diffusion init _(look up)_.
- **Variational Score Distillation (VSD)** — divergence via teacher score _(look up)_.
- **Schrödinger bridges / stochastic interpolants** _(look up)_.

### Transformers, Scaling and Hardware — Jacob Austin (Anthropic)
- _TODO: fill in from slides/recording._

### Large Physics Models (Science Application) — Dar Mehta (Casual Labs)
- Themes: counterfactual, credit assignment, generalization.
- LPM for weather (recover physical states from raw noisy inputs; causal structure to predict/control).

### Atomic AI Foundation Models (Science Application) — Alex Morehead (Berkeley Lab)
- Ways to build FMs: autoregressive vs bidirectional.
- **Zatorm-1** — atomic AI foundation architecture _(name to verify against slide)_.

## Day 2

### Discrete Diffusion — Ferdinando Fioretto (University of Virginia)

- **Constraint-based / constrained diffusion** — sampling as sequential optimization.
- **Augmented Lagrangian sampling** — for non-convex constraints / residual-only (verifiers).
- **CADM** — constraint-aware diffusion model (protein design) _(look up)_.
- **RFdiffusion** — protein-design baseline _(look up)_.
- Applications: microstructure/porosity, physics-informed motion, safe multi-robot autonomy,
  protein design, inverse design of mechanical metamaterials.

---

_Note: papers specific to my own longitudinal-brain research (BrLP, Temporal Flow Matching,
Anatomically Guided Latent Diffusion, single-cell trajectory inference, etc.) are kept in my
private `ideas/` notes, not here._
