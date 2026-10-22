# gamAI

**Open agent infrastructure: proof, immunity, honesty.**

Most agent stacks optimize what a model can do. We build the layer that makes
what it *did* checkable.


**Launch article (BS):** [Agent koji ne laže: dokaz, imunitet i poštenje](https://gamai.io/blog/evidence-first-agent-runtime.html)

## Flagship

### [evidence-first-agent-runtime](https://github.com/gamai-io/evidence-first-agent-runtime)

Three dependency-free components, MIT, one command to reproduce:

| Component | What it answers | Measured on our corpus |
|---|---|---|
| **proofgate** | Did it actually happen? | `confirmed` / `refuted` / `unverified`; 10 confirmed + 2 refuted + 0 unverified; tamper-evident SHA-256 |
| **agent-immunity** | Has this attack been seen before? | injection success 100% → **0%** in 3 rounds; utility 100%; false denial 0%; ~1.3 ms |
| **crossnode-bench** | Does the agent lie about other machines? | demo: **46/48**, names **2 false successes** that a naive scorer counts as passes |

```bash
git clone https://github.com/gamai-io/evidence-first-agent-runtime
cd evidence-first-agent-runtime && ./repro.sh
```

## More from gamAI

| Project | What it is |
|---|---|
| [gama-lang](https://github.com/gamai-io/gama-lang) | GAMA-L: AI-first polymorphic language + GAMA-OS (AI-native terminal OS) |
| [gama-hifz](https://github.com/gamai-io/gama-hifz) | Self-hosted Qur'an study app: 114 surahs / 6236 verses, audio, translation, TTS, offline ASR check |
| [gamai-skills](https://github.com/gamai-io/gamai-skills) | 992 open-source agent skills, CI-validated on every push |
| [gama-agent](https://github.com/gamai-io/gama-agent) | Local agent model (GGUF) |

## Principles

- **Refusal is a feature.** "I could not confirm that" beats a confident lie.
- **A block is memory.** Every stopped attack should make the next variant cheaper to stop.
- **Measure the claim, not the answer.** False success is a metric.
- **Price the isolation.** bubblewrap → runc → seccomp → gVisor, with latency recorded.

## Links

- Admin: [@gamai-io-user](https://github.com/gamai-io-user)

- Website: [gamai.io](https://gamai.io)
- Contact: admin@gamai.io
- License: MIT (per repository)

*Small-N results are labeled; nothing here is a state-of-the-art claim.*
