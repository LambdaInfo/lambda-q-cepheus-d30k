# LAMBDA-Q D30K — Experimental results on Rigetti Cepheus

**Published:** 2026-11-16  
**Results dataset, version 1:** https://doi.org/10.5281/zenodo.24273951  
**Results dataset, all versions:** https://doi.org/10.5281/zenodo.24273950  
**Prior registration (RV-05):** https://doi.org/10.5281/zenodo.24171772

## Experimental scope

The campaign comprises 30,000 physical shots acquired in three sessions (S01, S02 and S03), with 10,000 shots per session. Each session used four circuit preparations, with 2,500 shots per preparation. The experimental geometry used five data qubits, four ancilla qubits and one syndrome-extraction round (R = 1) on Rigetti Cepheus through Amazon Braket.

## Reported results

| Session | Shots | Recorded LAMBDA-Q errors | Error rate |
|---|---:|---:|---:|
| S01 | 10,000 | 356 | 3.5600% |
| S02 | 10,000 | 289 | 2.8900% |
| S03 | 10,000 | 274 | 2.7400% |
| **Total** | **30,000** | **919** | **3.0633%** |

| Nominal selection policy | Accepted shots | Observed coverage | Errors among accepted shots | Conditional error rate |
|---|---:|---:|---:|---:|
| 90% | 27,701 | 92.3367% | 674 | 2.4331% |
| 66.67% | 20,465 | 68.2167% | 197 | 0.9626% |

The percentages are derived from the reported integer counts and rounded to four decimal places. Nominal policy percentages are not observed coverages.

## Scientific interpretation and limitations

These are reported post-pipeline observations, not performance improvements relative to a matched reference decoder. Raw physical measurement statistics and post-pipeline error rates are not directly comparable as equivalent decoder baselines. The aggregate LAMBDA-Q outcomes were recorded by the campaign verifier; they cannot be independently recalculated from the publicly released physical measurement records alone.

The full public dataset, aggregate results, report, and provenance materials are deposited with Zenodo under the version-specific DOI above. This document is a companion index only. It neither modifies the prior registration (RV-05) nor discloses internal LAMBDA-Q algorithms, proprietary formulas, model weights or source code.
