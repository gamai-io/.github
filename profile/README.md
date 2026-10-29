# gamAI

**Open agent infrastructure: proof, immunity, honesty.**

Most agent stacks optimize what a model can do. We build the layer that makes
what it *did* checkable.

**Launch article (BS):** [Agent koji ne laže: dokaz, imunitet i poštenje](https://gamai.io/blog/evidence-first-agent-runtime.html)

## Trust layer

| Project | What it is | Signal |
|---|---|---|
| [gamai-trust](https://github.com/gamai-io/gamai-trust) | Aggregate API + CLI + MCP for the three trust checks | 5/5 tests, 3 demos, offline |
| [sigil](https://github.com/gamai-io/sigil) | Proof-carrying execution profile: grants, receipts, signed bundles | v0.22.1, conformance suite |
| [gamai-guard](https://github.com/gamai-io/gamai-guard) | Multilingual prompt-injection guard: lexical → analytic → embedding | **29/30 blocked, 0/10 false positives** (blind DE/FR/ES/BS) |
| [crossnode-bench](https://github.com/gamai-io/crossnode-bench) | Claim-vs-truth benchmark across nodes; false success is a metric | demo **46/48, 2 false successes detected** |
| [polymorph](https://github.com/gamai-io/polymorph) | Effect leases, pinned-hash execution and signed execution bundles | 100% out-of-lease denial, 0% benign denial |

```bash
git clone https://github.com/gamai-io/gamai-trust
cd gamai-trust && ./repro.sh
```

## Applied

| Project | What it is | Signal |
|---|---|---|
| [floor-copilot](https://github.com/gamai-io/floor-copilot) | Evidence-gated invoice intake for industrial distributors | live demo, 21 s/invoice, arithmetic + VAT gate |
| [rush](https://github.com/gamai-io/evidence-first-agent-runtime/tree/main/rush) | Containment-first web agent: guard → plan → Docker/Vultr sandbox → evidence ledger | live on Vultr, 6 s/run, injection + destructive refused |

Live demos: [Floor Copilot](https://contabo-vps.tailf8e6be.ts.net/floor/) · [rush on Vultr](http://45.76.91.239:8098/)

## Platform

| Project | What it is |
|---|---|
| [gama-lang](https://github.com/gamai-io/gama-lang) | GAMA-L: AI-first polymorphic language + GAMA-OS |
| [gamai-skills](https://github.com/gamai-io/gamai-skills) | Open-source agent skills, CI-validated on every push |
| [gama-agent](https://github.com/gamai-io/gama-agent) | Local agent model (GGUF) |
| [gama-hifz](https://github.com/gamai-io/gama-hifz) | Self-hosted Qur'an study app: 114 surahs, audio, translation, offline ASR check |

## Principles

- **Refusal is a feature.** "I could not confirm that" beats a confident lie.
- **A block is memory.** Every stopped attack should make the next variant cheaper to stop.
- **Measure the claim, not the answer.** False success is a metric.
- **Price the isolation.** bubblewrap → runc → seccomp → gVisor, with latency recorded.

## Links

- Website: [gamai.io](https://gamai.io)
- Contact: admin@gamai.io
- License: MIT or Apache-2.0 per repository

*Small-N results are labeled; nothing here is a state-of-the-art claim.*
