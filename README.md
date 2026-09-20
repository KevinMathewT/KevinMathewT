## Kevin Mathew T

**Applied AI / ML Systems @ C3 AI** · San Francisco Bay Area

Production AI systems — agentic workflows, ML systems, research engineering. Forward-deployed work
for industrial customers today; ML team at Goldman Sachs before that. MSCS, NYU Courant.

---

### Selected work

**[dynadust3r-unofficial](https://github.com/KevinMathewT/dynadust3r-unofficial)** — Stereo4D (CVPR 2025)
describes DynaDUSt3R but releases no training code or weights. Rebuilt the pipeline: motion head,
losses, multi-GPU training, and a streaming data path over ~4 TB — naive MP4+NPZ decoding starved
the GPUs, so clips became WebDataset shards with geometry computed on the fly. 29 h on 4×H100;
**0.098 m EPE3D** on ADT. [Weights](https://huggingface.co/KevinMathew/dynadust3r-unofficial-weights)
and [datasets](https://huggingface.co/datasets/KevinMathew/stereo4d-lefteye-perspective) released.

**Agentic development tooling @ C3 AI** *(proprietary)* — An orchestrator agent decomposes
natural-language requirements into specialized subagents that generate C3 Reliability application
and model components, validate the output, and iteratively correct it when invalid.

**[DiffuserV2](https://github.com/KevinMathewT/DiffuserV2)** — Velocity-parameterized diffusion
planning with MPPI sampling and segmented replanning. Matches or beats Diffuser (ICML 2022) on
Maze2D at **half the diffusion steps**; +21% on U-Maze.

**[JEPA world model](https://github.com/KevinMathewT/Deep-Learning-CSCI-GA-2572-Final-Project)** —
Action-conditioned latent dynamics in **89K parameters**. Spatial conv latents, VICReg, and an
inverse-dynamics auxiliary loss that recovers the action from the latent difference — resists
collapse while forcing the latent to encode dynamics. 4.40 MSE on normal probes.

**[Multi-agent planning](https://github.com/KevinMathewT/pldm_overcooked_ai)** — Latent dynamics +
MPPI planning on Overcooked-AI. Built the Q-value network and training stack; merged upstream
[#1](https://github.com/MultiAgentPlanning/pldm_overcooked_ai/pull/1) ·
[#3](https://github.com/MultiAgentPlanning/pldm_overcooked_ai/pull/3) ·
[#4](https://github.com/MultiAgentPlanning/pldm_overcooked_ai/pull/4). Planning and control, not LLM agents.

**[RL RoboSoccer](https://github.com/KevinMathewT/RL-RoboSoccer-FirstPlace)** — First place, AI
RoboSoccer. A2C; the win came from observation design, not the algorithm.

---

### Selected open source

- **[pico-llm#23](https://github.com/pico-llm/pico-llm/pull/23)** — RoPE and NoPE positional
  embeddings, model refactor, parallelized TinyStories tokenization. +423/−115, merged after 12
  review comments.
- **[pldm_overcooked_ai](https://github.com/MultiAgentPlanning/pldm_overcooked_ai/pulls?q=is%3Apr+author%3AKevinMathewT)**
  — Q-value network and training pipeline (+1085), 1D value-shape fix, MPPI planner fix.
- **[pytorch-lightning#4459](https://github.com/Lightning-AI/pytorch-lightning/pull/4459)** —
  one-line documentation fix.

---

### Background

**C3 AI** — Data Scientist (June 2026–), Data Science Intern (2025). Forward-deployed work on C3 AI
Reliability and agentic development tooling. As an intern, built a zero-retrain P&ID symbol
recognition pipeline (YOLOv12n → MobileNetV3 triplet embeddings → class-adaptive k-NN) at 93.8%
mean accuracy across seven reference splits.

**NYU Courant** — MS Computer Science, 3.909/4.0. Student researcher, Fouhey AI Lab.

**Goldman Sachs** — ML team, Enterprise Technology Operations, 2021–2024. Internal LLM resolution
assistant over Llama 3 and Mixtral 8x7B with PEFT, automating ~90% of knowledge-based tickets in a
~100k/month workflow. Distributed log analysis with a custom pattern-matching DSL over Celery — 11x
fewer production alerts. RoBERTa classification and entity extraction for financial email
operations at ~92%, replacing an LSTM pipeline.

---

[LinkedIn](https://www.linkedin.com/in/kevinmathewt/) · [Hugging Face](https://huggingface.co/KevinMathew)
