# gamAI — evidence before claims

We build infrastructure that makes an AI agent's report **checkable**: a claim is recorded, an
independent probe looks at the real system, and the verdict is one of
`CONFIRMED` / `REFUTED` / `UNVERIFIABLE`. Missing evidence never becomes a pass.

Every number in this organization is supposed to ship with a command, a date and an N.
Index of all of them: [VERIFY.md](VERIFY.md). If a row does not run, the claim is not verified.

## Start here

| What you want | Repo |
|---|---|
| See the gate in action (claim vs evidence, signed receipts) | [`audit-evidence`](https://github.com/gamai-io/audit-evidence) |
| Benchmark agent honesty across nodes | [`crossnode-bench`](https://github.com/gamai-io/crossnode-bench) |
| Verification runtime for agents | [`proofgate-runtime`](https://github.com/gamai-io/proofgate-runtime) |
| Signed execution profile (grants → receipts → anchor) | [`sigil`](https://github.com/gamai-io/sigil) |
| Multilingual prompt-injection guard | [`gamai-guard`](https://github.com/gamai-io/gamai-guard) |
| Cut model calls deterministically | [`gama-fastpath`](https://github.com/gamai-io/gama-fastpath) · [`gama-offline`](https://github.com/gamai-io/gama-offline) |
| A language where proof is syntax | [`gama-lang`](https://github.com/gamai-io/gama-lang) |

## How we work

- **Claims:** a number ships with `command + date + N`, or it is marked *self-reported*.
- **Failures:** negative and null results are published; retracted figures stay visible as retracted.
- **Audits:** `CONFIRMED` / `REFUTED` / `UNVERIFIABLE` per action, hash-chained and Ed25519-signed.
- **Limits:** each repo states what it does *not* prove — see `LIMITS.md` where relevant.

Apache-2.0 unless stated otherwise.
