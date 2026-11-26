# VERIFY — repo → claim → how to check it

One row per public repository. If a row's command does not run, the claim is not verified.
Last full pass: **2026-11-26**.

| Repo | Headline claim | Verify with | Status |
|---|---|---|---|
| `gama-mandate` | 0.68.11: claim receipts, signer options, claims gate | `python3 tools/claims.py --check` → `{"claims":"consistent","tests":472,"version":"0.68.11"}`; `tools/verify_pypi.py` at the tag → 0 diff | verified at release |
| `gamai-tripwire` | 0.8.15: redacted-log corpus, 2 flagged (1 high / 1 medium) | `python -m pytest -q` → 165 passed | verified at release |
| `gamai-plugins` | 0.2.11 on PyPI | `python -m pytest -q` → 45 passed | verified at release |
| `sigil-tenant` | 4.0.3: per-tenant keys, metering, no redirects | `pytest` → 10 passed | verified at release |
| `crossnode-bench` | v1.7.0: honest fleet 25,600/25,600, liar run 28,800 with 400 detected; reports checkable | `python3 crossnode.py --demo` → 48 records / 46 pass / 2 false success; `python -m pytest tests -q` → 105 passed; `python3 crossnode.py --verify-report <report.json>` → `"ok": true` | verified 2026-11-26 |
| `demo` | the page is generated, not typed | `make verify` (fetches pinned crossnode-bench v1.4.0 artifacts, re-checks 6 sha256, exits 1 on a hand edit) | verified 2026-11-26 |
| `dsc` | one gate, one money parser | `pytest -q` → 211 passed; `grep -rn "def parse_amount\|T1 = \[" dsc` → one of each | verified 2026-11-26 |
| `gama-fastpath` | deterministic gate blocks destructive intent; cache is keyed by the whole request | `python -m unittest discover -s tests` → 31 passed (installs `dsc` pin); gate returns `blocked:true` with a stable code for `rm -fr /`, `curl … \| bash`, `delete from` without WHERE | verified 2026-11-26 |
| `gama-offline` | answer cache; hit rate is a bench artifact, not traffic | `python3 bench/bench_cache.py` → 2 of 3 repeats in the shipped loop; the module counter on the same script reports 44.4% | verified 2026-11-26 |
| `gama-sandbox` | filesystem + network isolation without Docker | `bash tests/smoke.sh` → `SMOKE_OK`; `bash tests/test_env_isolation.sh` → `passed=18 failed=0` | verified 2026-11-26 |
| `gnp-trust` | token gate, tiers, leases with fencing | `pytest -q` → 33 passed; the same suite fails 15 on the pre-hardening daemon | verified 2026-11-26 |
| `sigil` | conformance suite | CI job: 46 passed / 0 failed / 3 skipped (remote anchor, container key isolation, public FreeTSA); `python -m sigil.conformance --offline` → 12/12 | verified 2026-11-26 |
| `polymorph` | effect lease; capability may change shape, not scope | `./repro.sh` → 20/20 benign allowed, 40/40 malicious denied, 15/15 + 3/3 + 5/5 unit | verified 2026-11-26 |
| `gamai-guard` | multilingual injection cascade | `python3 bench/eval_blind.py` → lexical 4/30, embedding 29/30, 0/10 false positives | verified 2026-11-26 |
| `gamai-trust` | verify claims, remember refusals, score false success | `pytest -q` → 12 passed | verified 2026-11-26 |
| `proofgate-runtime` | verify claims; receipts require a key | `PYTHONPATH=src python -m unittest discover -s tests` → 30 passed; unsigned MCP `make_receipt` is refused | verified 2026-11-26 |
| `evidence-gate-runtime` | record, verify, replay an action | `python3 tests/run_tests.py` → 14 tests, 2 skipped without proofgate | verified 2026-11-26 |
| `evidence-first-agent-runtime` | umbrella: proofgate + immunity + bench | `python -m pytest -q` → 22 passed; `bash repro.sh` → OK | verified 2026-11-26 |
| `agentmujo-training` | release hashes verify; datasets use only registered tools | `python -m pytest -q` → 191 passed; `amj dataset verify --version 0.4.0` → 13 files, 4496 rows, all sha256 match; `amj dataset conformance` → 0 unregistered | verified 2026-11-26 |
| `gamai-evals` | manifests are what they say | `python -m pytest -q tests` → 3 passed; `phase1_eval_600` is exactly the union of `screenspot_300` + `uivision_300` | verified 2026-11-26 |
| `gama-decision-os` | gate latency and token saving | `python3 benchmarks/decision_latency.py --n 500` → p50 0.0025 ms, 0 wrong; `python3 benchmarks/ledger_stats.py` → 85.4% (24 h, n=3,252) **on 2026-11-26 — the ledger grows, so the percentage is a snapshot, not a constant** | verified 2026-11-26 |
| `claims-lint` | flags numbers without a reproducer, date or N | `python -m pytest -q tests` → 4 passed | verified 2026-11-26 |
| `one-skeleton-two-apps` | two apps from one skeleton, with receipts | CI: `python3 run_demo.py` → CONFIRMED / CONFIRMED / REFUTED, chain ok; `--tamper` → `ok: false, at: 2` | verified 2026-11-26 |
| `gama-retrieval` | retrieval benches | `python3 embed_qdrant_bench.py --selftest` and the other three `--selftest` scripts | archived; numbers from 2026-11-04, not re-measured |
| `gama-shard` | Firecracker microVM shard | — | archived; harness not shipped, numbers indicative |

## Rule

A number ships with **command + date + N**. Without all three it is removed or marked
*self-reported* / *not reproduced*. Two kinds of figure are never CI-checkable and say so
in the repo: numbers from a live database (`gama-decision-os` ledger) and numbers that need
hardware (`gama-cell` KVM latency, `gama-shard`).
