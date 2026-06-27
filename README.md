# OmegaPacman

OmegaPacman flips Pac-Man: instead of controlling Pac-Man to escape, 4 ghost agents learn — via Reflexion on per-ghost and shared SKILL.md — how to cooperate and catch Pac-Man. Nobody coded the teamwork; it emerges.

a turn-based grid chase game where ghost agents learn team strategy via Reflexion on per-ghost and shared SKILL.md files — Alpha series? this is Omega

## Baseline (before learning)

Starting metrics on the corridor maze, so we can compare against learned results later. Measured over a headless batch of games (`Run 200 games` in the UI / `OMEGA.runBatch`).

| Ghost strategy | Catch rate | Avg turns-to-catch |
| --- | --- | --- |
| **Random** (empty SKILL.md — the "before") | **40.6%** | **32.6** |
| Hand-written `chase`/`intercept` in the .md (reference ceiling) | ~100% | ~7 |

These are the **"before" numbers**. The hand-written chase/intercept row is only a reference ceiling — it shows what good teamwork can achieve, not a strategy we ship. The goal of OmegaPacman is for the ghosts to discover effective teamwork *themselves* via Reflexion (verbal reinforcement written back into per-ghost and shared SKILL.md), closing the gap from 40.6% toward the ~100% ceiling — without anyone coding the strategy.

## Related Work

- **Multi-Agent Evolve** (2025/10) — spins up Proposer/Solver/Judge roles from a single base LLM to extend self-play self-improvement to general domains. https://arxiv.org/html/2510.23595v1
- **Cultural Evolution of Cooperation among LLM Agents** (2024/12) — each generation of agents plays a game; high-resource agents survive to the next generation, others are discarded, and new agents condition their strategy on survivors. https://arxiv.org/pdf/2412.10270
- **LLM-Hanabi** (2025/10) — evaluates multi-agent cooperative play in an imperfect-information game via theory-of-mind. https://github.com/git-disl/awesome-LLM-game-agent-papers

Emergent cooperation among LLM agents is an active research area, but prior work mostly studies text-based economic and social games whose results are read off benchmark tables. OmegaPacman's contribution is to make this *visible*: emergent ghost teamwork in a familiar arcade game, with a clear before/after you can watch unfold. It is not a new claim about whether cooperation can emerge — it is a new way to *show* it, in the spirit of how DeepMind made reinforcement learning legible through Atari.
