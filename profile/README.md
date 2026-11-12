<!-- gamai-matrix-header-v1 -->
<div align="center">

<img src="./assets/header.svg" alt="gamAI — trust layer for AI agents" width="100%" />

<a href="https://github.com/gamai-io">
  <img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=600&size=20&duration=3200&pause=900&color=4FC3FF&center=true&vCenter=true&width=760&lines=evidence+before+assertion;decidable+before+%C2%B7+isolated+while+%C2%B7+provable+after;measured%2C+not+marketed" alt="gamAI" />
</a>

<p>
  <a href="https://github.com/gamai-io?tab=repositories"><img src="https://img.shields.io/badge/repos-17-00A3FF?style=flat-square&labelColor=02060f" alt="repos" /></a>
  <a href="https://github.com/gamai-io/proofgate-runtime"><img src="https://img.shields.io/badge/proofgate-runtime-4FC3FF?style=flat-square&labelColor=02060f" alt="proofgate" /></a>
  <a href="https://github.com/gamai-io/evidence-first-agent-runtime"><img src="https://img.shields.io/badge/evidence--first-runtime-4FC3FF?style=flat-square&labelColor=02060f" alt="efr" /></a>
  <img src="https://img.shields.io/badge/python-3.11%2B-00A3FF?style=flat-square&labelColor=02060f&logo=python&logoColor=white" alt="python" />
  <img src="https://img.shields.io/badge/license-Apache--2.0-0066CC?style=flat-square&labelColor=02060f" alt="license" />
</p>

<img src="./assets/divider.svg" alt="" width="100%" />

</div>

## Šta je gamAI

gamAI je **trust layer za AI agente**: sloj koji odlučuje _prije_ izvršenja, izoluje _tokom_ izvršenja i dokazuje _poslije_ izvršenja. Agent koji tvrdi da je posao završen — a nije — je najskuplji bug u produkciji. Naš odgovor nije bolji prompt, nego **provjerljiv dokaz**.

Tri invarijante koje svaki repo u organizaciji poštuje:

| Invarijanta          | Značenje                                                             | Gdje se provodi                         |
| -------------------- | -------------------------------------------------------------------- | --------------------------------------- |
| **Decidable before** | svaka akcija ima odluku prije izvršenja (allow / deny / needs-proof) | `proofgate-runtime`, `dsc`              |
| **Isolated while**   | izvršenje u ograđenom prostoru (srt / bwrap / microVM)               | `gama-sandbox`, `sigil`                 |
| **Provable after**   | tvrdnja se poredi sa stvarnim stanjem, rezultat je potpisan          | `evidence-first-agent-runtime`, `sigil` |

<div align="center"><img src="./assets/divider.svg" alt="" width="100%" /></div>

## Kako radi

<div align="center"><img src="./assets/terminal.svg" alt="gamAI pipeline: gate → model → tools → isolation → evidence → verify" width="100%" /></div>

Claim ulazi u gate. Gate odlučuje. Model se izvršava u izolaciji sa ograničenim alatima. Sve što se desilo ide u evidence log (JSONL + SHA-256). Verifikacija poredi tvrdnju sa opservacijom — i ako se ne slažu, tvrdnja je **refuted**, ne "vjerovatno tačna".

<div align="center"><img src="./assets/divider.svg" alt="" width="100%" /></div>

## Ekosistem

<div align="center"><img src="./assets/ecosystem.svg" alt="gamAI slojevi: core, proof, measurement, verticals" width="100%" /></div>

<div align="center"><img src="./assets/divider.svg" alt="" width="100%" /></div>

## Flagship

| Repo                                                                                         | Šta rješava                                              | Dokaz                                          |
| -------------------------------------------------------------------------------------------- | -------------------------------------------------------- | ---------------------------------------------- |
| [**proofgate-runtime**](https://github.com/gamai-io/proofgate-runtime)                       | gate koji odlučuje prije akcije; fail-closed po defaultu | deterministički, bez LLM-a u kritičnoj putanji |
| [**evidence-first-agent-runtime**](https://github.com/gamai-io/evidence-first-agent-runtime) | runtime gdje je dokaz primarni artefakt, ne log          | evidence chain + verifikacija tvrdnji          |
| [**sigil**](https://github.com/gamai-io/sigil-public)                                        | potpisivanje i verifikacija receipt-a                    | SHA-256 chain, offline verifikacija            |
| [**crossnode-bench**](https://github.com/gamai-io/crossnode-bench-public)                    | mjerenje pouzdanosti agenata kroz više čvorova           | javni dataset + reproducibilni runovi          |
| [**gamai-guard**](https://github.com/gamai-io/gamai-guard-public)                            | politike i granice za toolske pozive                     | policy engine, audit trail                     |

<div align="center"><img src="./assets/divider.svg" alt="" width="100%" /></div>

## Principi

- **Mjereno, ne marketinški.** Svaka tvrdnja u README-u ima run ili test iza sebe.
- **Fail-closed.** Ako dokaz nema, odgovor je `unverified` — nikad `ok`.
- **Bez magije.** Determinitički sloj je odvojen od modela; model je zamjenjiv dio.
- **Lokalno prvo.** Radi bez clouda; cloud je opcija, ne uslov.
- **Otvoreno.** Javni repoi, javni benchmark, javni rezultati — uključujući one koji nam ne idu u prilog.

<div align="center"><img src="./assets/divider.svg" alt="" width="100%" /></div>

## Stack

<p align="center">
  <img src="https://skillicons.dev/icons?i=python,fastapi,docker,linux,git,githubactions,postgres,redis,bash&theme=dark" alt="stack" />
</p>

<div align="center"><img src="./assets/stats.svg" alt="gamAI organizacija: 17 repoa, 5 flagship, Python, Apache-2.0" width="100%" /></div>

<div align="center"><img src="./assets/divider.svg" alt="" width="100%" /></div>

## Kontakt

- Web: **gamai.io**
- Organizacija: [github.com/gamai-io](https://github.com/gamai-io)
- Sigurnost: vidi [SECURITY.md](https://github.com/gamai-io/.github/blob/main/SECURITY.md)

<!-- gamai-matrix-footer-v1 -->
<div align="center">

<img src="./assets/divider.svg" alt="" width="100%" />

<sub><code>evidence before assertion</code> · <code>decidable before · isolated while · provable after</code></sub>

<sub>© gamAI · trust layer for AI agents</sub>

</div>
