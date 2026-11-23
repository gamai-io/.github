# VERIFY — repo → claim → how to check it

One row per repository. If a row's command does not run, the claim is not verified.
Last full pass: **2026-11-24**.

| Repo | Headline claim | Verify with |
|---|---|---|
| `gama-offline` | cache serves repeats in ~1.7 ms; 66.7% hit on cacheable, 0% on fresh | `python3 bench/bench_cache.py` |
| `gama-decision-os` | token saving 75.5% (24 h, n=2,021); L0 decides in ~2 µs | `python3 benchmarks/ledger_stats.py` · `python3 benchmarks/decision_latency.py --n 500` |
| `gama-decision-os` | 10k async agents, 0 errors | `python3 benchmarks/lumi_10k/verify_stress.py` |
| `agentmujo-training` | 30,798 fail-closed gate records, 0 false successes | artefact archive + `crossnode-bench` v1.6.2 |
| `crossnode-bench` | honest fleet 25,600/25,600; liar run 28,800 with 400 detected | `RELEASE_v1.4.0.md` + shipped records |
| `gamai-guard` | 29/30 blind multilingual attacks, 0/10 FP | `python3 bench/eval_blind.py` |
| `gamai-evals` | withdrawn older numbers; new figures per convention | see README tables + `tests/` |
| `gama-fastpath` | PDV 17% → 2808.00; T1 block 0.03 ms | `python3 -m unittest discover -s tests` |
| `sigil` | 49/49 conformance checks | `repro.sh` in repo |
| `polymorph` | E1 20/20 allow, 40/40 deny, 0 FP/FN | `./repro.sh` |
| `proofgate-runtime` | confirmed/refuted verdicts per claim | `tests/` + `audit-evidence` |
| `evidence-first-agent-runtime` | 16/16 proofgate tests; 8/8 attacks detected | `pytest` in subfolders |
| `evidence-gate-runtime` | 25,600 controlled trials, 93.75% pass | **self-reported — dataset not public yet** |
| `gama-sandbox` | Firecracker / gVisor overhead | **indicative — harness not shipped** |
| `gama-shard` | Firecracker cold boot 2.39 s | **archived — claim unverified** |
| `gama-retrieval` | embed 5 docs/s, recall@5 1.0 | `python3 embed_qdrant_bench.py`, `retrieval_eval.py` |
| `gnp-trust`, `mandate`, `dsc`, `gama-lang` | see each README | `pytest` / `demo/demo.sh` |
| `demo` | two 25,600 runs kept separate | `README.md` two-run table |
| `audit-evidence` | 5/6 planted lies caught, 0 false alarms, signed chain | `./reproduce.sh` |
| `claims-lint` | flags numbers without a reproducer | `python3 claims_lint.py README.md` |

## Rule

A number ships with **command + date + N**. Without all three it is either removed or explicitly
marked *self-reported* / *not reproduced*. This file is the index; the READMEs carry the detail.
