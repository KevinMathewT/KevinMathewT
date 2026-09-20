## Kevin Mathew T

**Applied AI / ML Systems @ C3 AI** · San Francisco Bay Area

I build production AI systems — agentic development workflows, ML systems, and research
engineering. Today that means forward-deployed work for large industrial customers in energy,
chemicals, and manufacturing. Before that, LLM and NLP systems on the ML team at Goldman Sachs,
and 3D vision / world-model research at NYU Courant.

MSCS, NYU Courant · ex-Goldman Sachs (ML, Enterprise Technology Operations) · ex-Fouhey AI Lab

---

### Selected work

**[dynadust3r-unofficial](https://github.com/KevinMathewT/dynadust3r-unofficial)** — reimplementing a training pipeline the authors never released

Stereo4D (CVPR 2025) describes DynaDUSt3R — a model predicting per-pixel 3D points and 3D motion
from stereo video — but releases no training code or weights. I rebuilt the pipeline from the
paper: model heads, losses, multi-GPU training, and a data path over a ~4 TB dataset.

The hard part was I/O, not modeling. Naive per-sample MP4 + NPZ decoding starved the GPUs, so the
dataset is converted into WebDataset tar shards streamed with per-worker sharding and resampling,
with geometry computed on the fly. Trained ~29 h on 4×H100 (98k iterations, effective batch 16).
Code, [weights](https://huggingface.co/KevinMathew/dynadust3r-unofficial-weights), and
[preprocessed datasets](https://huggingface.co/datasets/KevinMathew/stereo4d-lefteye-perspective)
are public; best checkpoint reaches **0.098 m EPE3D** on ADT motion evaluation.

`PyTorch` · `Accelerate` · `WebDataset` · `Hydra` · `CUDA`

<br>

**Agentic development tooling @ C3 AI** *(proprietary — described at a conceptual level)*

Reusable agent templates for C3 AI Reliability development workflows, built on C3's internal
coding system. An orchestrator agent decomposes a natural-language requirement into specialized
subagents that generate application and model components against domain-specific platform context,
then validate the generated output and iteratively correct it when invalid.

Alongside this: forward-deployed delivery on C3 AI Reliability, where industrial assets (pumps,
compressors, crushers) stream multi-sensor telemetry and models flag emerging equipment problems.
Enterprise data, model and application configuration, production workflows, deployment, and
customer-specific debugging.

<br>

**[DiffuserV2](https://github.com/KevinMathewT/DiffuserV2)** — diffusion planning with velocity parameterization

Extends Diffuser (ICML 2022) by reparameterizing trajectory diffusion to predict velocity rather
than noise, and adds MPPI-weighted sampling plus segmented periodic replanning for drift recovery.
On sparse-reward Maze2D, matches or beats the original Diffuser **using half the diffusion steps** —
up to +21% on U-Maze. Full results table, including where it does *not* win, in the repo.

`Diffusion models` · `Model-based planning` · `Offline RL`

<br>

**[JEPA world model](https://github.com/KevinMathewT/Deep-Learning-CSCI-GA-2572-Final-Project)** — action-conditioned latent dynamics in 89K parameters

Action-conditioned JEPA trained on 2.5M frames of two-room navigation trajectories, predicting
future states purely in representation space. Uses a 2D convolutional encoder that keeps latents
spatial, VICReg regularization, and an inverse-dynamics auxiliary loss that recovers the action
from the latent difference — which both resists collapse and forces the latent to encode dynamics.
**4.40 MSE** probe_normal / **7.58** probe_wall at 88,997 parameters. ~15 architecture variants
were explored to get there.

`World models` · `Self-supervised learning` · `Representation collapse`

<br>

**[Multi-agent planning on Overcooked](https://github.com/KevinMathewT/pldm_overcooked_ai)** — Q-value learning for a planning-based latent dynamics model

Contributor to a latent-dynamics multi-agent planning project on Overcooked-AI. I built the
Q-value network and its training stack from scratch, then fixed value-shape and planning bugs that
were corrupting rollouts. Merged upstream:
[#1](https://github.com/MultiAgentPlanning/pldm_overcooked_ai/pull/1) ·
[#3](https://github.com/MultiAgentPlanning/pldm_overcooked_ai/pull/3) ·
[#4](https://github.com/MultiAgentPlanning/pldm_overcooked_ai/pull/4).
This is multi-agent planning and sequential decision-making — not LLM agents.

<br>

**[RL RoboSoccer](https://github.com/KevinMathewT/RL-RoboSoccer-FirstPlace)** — first place, AI RoboSoccer (BITS Pilani)

A2C agent for a multi-agent soccer environment. The win came from representation, not algorithm:
replacing raw coordinates and velocities with distances and direction vectors to the ball and both
goals roughly doubled score. Ablation table in the repo.

---

### Selected open source

- **[pico-llm/pico-llm#23](https://github.com/pico-llm/pico-llm/pull/23)** — added rotary (RoPE) and
  no-position (NoPE) embedding strategies to the transformer, refactored the model into its own
  module, and parallelized TinyStories tokenization with a process pool. +423/−115 across 7 files,
  merged after 12 review comments.
- **[MultiAgentPlanning/pldm_overcooked_ai](https://github.com/MultiAgentPlanning/pldm_overcooked_ai/pulls?q=is%3Apr+author%3AKevinMathewT)**
  — Q-value network and training pipeline ([#1](https://github.com/MultiAgentPlanning/pldm_overcooked_ai/pull/1), +1085),
  1D value-shape correction and inference refactor ([#3](https://github.com/MultiAgentPlanning/pldm_overcooked_ai/pull/3)),
  MPPI planner fix and experiment harness ([#4](https://github.com/MultiAgentPlanning/pldm_overcooked_ai/pull/4)).
- **[Lightning-AI/pytorch-lightning#4459](https://github.com/Lightning-AI/pytorch-lightning/pull/4459)**
  — one-line documentation fix for `ReduceLROnPlateau`.

---

### Background

**C3 AI** — Data Scientist, June 2026–present · Data Science Intern, 2025.
Forward-deployed work on C3 AI Reliability and agentic development tooling. As an intern, built a
zero-retrain P&ID symbol recognition pipeline — YOLOv12n region proposals → MobileNetV3 triplet-loss
embeddings → class-adaptive k-NN — reaching 93.8% mean accuracy across seven reference splits, with
DocTR OCR and asset-hierarchy extraction, tiling and NMS for 4K–6K inference, and annotation and
evaluation tooling packaged for internal reuse. New symbol classes are added by example, without
retraining.

**NYU Courant** — MS Computer Science, 3.909/4.0. Student researcher, Fouhey AI Lab.

**Goldman Sachs** — Enterprise Technology Operations, ML team, 2021–2024.
Built an internal LLM resolution assistant over Llama 3 and Mixtral 8x7B grounded in internal
knowledge, with PEFT experimentation, automating ~90% of knowledge-based tickets in a workflow
handling ~100k tickets/month. Built a distributed log analysis and root-cause system — log
clustering plus a custom pattern-matching DSL executed in parallel with Celery across ~15 Linux
servers — cutting global production alerts 11x. Earlier: a RoBERTa classification and entity
extraction system for operational financial email workflows at ~92% accuracy, replacing an LSTM
pipeline, served FP16 on CPU; blue-green deployment and canary rollout infrastructure; and a
graph-algorithms tool converting automation workflow DAGs into operational runbooks.

---

**Currently** going deeper on agentic systems and AI engineering — orchestration, evaluation, and
the infrastructure that makes agents reliable in production.

[LinkedIn](https://www.linkedin.com/in/kevinmathewt/) · [Hugging Face](https://huggingface.co/KevinMathew)
