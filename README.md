Minimal Hierarchical Reinforcement Learning for Procedural Generalization
Abstract
Flat reinforcement learning agents often fail to generalize in environments with procedural variation, sparse rewards, or long-horizon credit assignment. Hierarchical Reinforcement Learning (HRL) promises to address these issues, but many existing implementations are either overly abstract, difficult to interpret, or tightly coupled to large frameworks.

This repository provides minimal, interpretable, and correct implementations of hierarchical RL methods, with a focus on understanding when and why hierarchy helps. The code is designed as research infrastructure: easy to read, easy to modify, and suitable as a reference baseline for experiments on procedural generalization.

Motivation
Despite decades of research, HRL remains underused in practice. Common reasons include:

Implementations are complex and opaque
Experimental gains are hard to reproduce
Failure modes are rarely documented
It is unclear when hierarchy is actually beneficial
This project takes the opposite approach:

Minimal first, performance second.

We aim to expose the core mechanisms of HRL—temporal abstraction, subgoals, termination, and credit assignment—without unnecessary engineering overhead.

Core Ideas
The implementations in this repository are built around the following principles:

Explicit hierarchy: high-level policies select subgoals; low-level policies execute actions
Interpretable state representations: tabular and tile-coded baselines before neural networks
Procedural environments: emphasis on generalization, not memorization
Ablation-friendly design: easy to remove or modify components
Methods (Informal Overview)
We consider a two-level hierarchical agent:

High-level policy selects a subgoal or option at a slower temporal scale
Low-level policy acts to reach the selected subgoal
Training uses a semi-Markov decision process (SMDP) formulation, with:

Option termination based on goal achievement or timeouts
Independent learning signals for high- and low-level policies
Optional learned subgoals via online clustering
The initial focus is on tabular and linear function approximation methods to ensure clarity and stability.

Environments
The primary environments used are:

Grid-based navigation tasks with sparse rewards
Procedurally generated layouts (maze-like structures)
These environments are intentionally simple, allowing failure modes to be visualized and understood.

Experimental Results
Key empirical findings demonstrated in this repository include:

Flat agents often overfit to training layouts and fail catastrophically on unseen ones
Hierarchical agents with subgoals show improved robustness to procedural variation
Learned subgoals adapt to environment structure and reduce manual tuning
Removing termination or hierarchy collapses performance
Results are presented through learning curves, rollout visualizations, and controlled ablations.

Visualizations
The repository includes tools for:

Animated rollouts comparing flat vs hierarchical agents
Learning curves with variance across random seeds
Failure-case demonstrations
Visual evidence is treated as a first-class research artifact.

When NOT to Use This Repository
This project is not intended for:

Production-scale reinforcement learning
Maximum-performance benchmarking
Black-box policy optimization
If you need a highly optimized RL library, consider Stable-Baselines or CleanRL.

Research Use
This repository is suitable for:

HRL baselines in academic papers
Teaching and coursework
Reproducibility studies
Algorithmic ablations
If you use this code in academic work, please cite it.

Citation
A citation file is provided in CITATION.cff. A paper-style technical report may follow.

Roadmap
[x] Flat tabular baselines
[x] Hierarchical Q-learning
[x] Procedural generalization experiments
[ ] Option-Critic implementation
[ ] PPO low-level controller
[ ] Extended ablation study
License
MIT License. See LICENSE for details.

Author
Felix Pankratov

This project is maintained as open research infrastructure. Feedback, issues, and replication attempts are welcome.
