# Lambda-Q — Prospective Reproducibility Protocol on Rigetti Cepheus (D30K)

**Lambdainfo Tecnologia Ltda. · Public release text RV-05 · 12 November 2026**

**Purpose:** Pre-register the acquisition and evaluation procedure for 30,000 future complete shots. The public timestamp will be the actual date and time of the GitHub release and Zenodo archive, not the historical dates printed below. No positive result or minimum accuracy is promised.

## 1. Research question and scope

Can the established Lambda-Q processing configuration reproduce its previously reported logical-error inference and selective-qualification behavior in three new, temporally separated sessions on the same physical Rigetti Cepheus repetition-code chain? The study measures reproducibility; it is not a claim of universal fault tolerance, commercial quantum advantage, or transfer to other devices.

The primary evaluated implementation is **the historical Lambda-Q processing pipeline used for D10K (9 November 2026) and D16K (10 November 2026)**, with the original decision and selection rules. The primary implementation will **not be replaced by alternative parametrizations**, and no formulas or threshold values will be altered for D30K. The existing algorithm may compute *unlabeled*, block-dependent statistics from acquired detector measurements. Thus the execution procedure is committed, but not every intermediate numerical weight is constant across blocks. No new correctness labels may be used to retune or select a model.

### Public description of the Lambda-Q architecture

Lambda-Q is a proprietary, multi-layer classical-processing architecture developed for the analysis, recovery and qualification of logical information from quantum processors. It uses available experimental measurements to produce logical decisions whose performance is assessed through integer error counts, realized coverage and paired comparisons on the same physical shots. This pre-registration evaluates the **complete processing system**, without disclosing the internal layering sequence, module responsibilities, decoding methods, decision rules, proprietary coefficients or source code. The SHA-256 commitments in §3 preserve artifact identities; verifying the private execution end to end requires controlled access under agreed confidentiality.

## 2. Hardware and prospective acquisition

| Parameter | Pre-registered value |
|---|---|
| QPU | Rigetti Cepheus-1-108Q via Amazon Braket (`us-west-1`) |
| Device ARN | `arn:aws:braket:us-west-1::device/qpu/rigetti/Cepheus-1-108Q` |
| Quantum code | Repetition, `d=5`, `R=1`, final-detector convention |
| Physical data qubits | `74, 82, 90, 100, 102` |
| Physical ancillas | `73, 81, 99, 101` |
| Prepared patterns | `00000`, `01010`, `10101`, `11111` |
| Sessions | `S01`, `S02`, `S03`; at least 24 hours between the last submitted task of a session and the first of the next |
| Each session | 4 byte-identical QASM circuits × 2,500 shots = **10,000 shots** |
| Overall | **12 planned tasks and 30,000 shots** |

All four original circuits are reused byte for byte in each session. Actual times, queue delays, task status, available calibration provenance and task identifiers will be recorded. No fixed maximum separation or promise of different hardware calibrations is made. If QPU access is unavailable, the delayed or missed session and its reason are reported; no session or preparation is replaced or omitted to favor a result. Re-execution of a failed task must preserve its original identity, with the prior ARN/status and all attempts disclosed. A duplicate paid submission must never be automatic.

Historical nominal cost basis: 12 × USD 0.30 plus 30,000 × USD 0.000425 = **USD 16.35**; not a current price quote or spending authorization. QPU execution requires a separate explicit approval.

## 3. Cryptographic commitment to existing private artifacts

The table gives full SHA-256 identifiers. Private values, internal modules and raw memory state are **not included** in this public release. The controls listed as candidate revisions must be verified byte for byte against the execution environment before any QPU submission; the release must be amended *before collection* if an approved executable differs from these digests.

| Artifact | SHA-256 |
|---|---|
| `LAMBDA3_CAMPO_CONGELADO_20261031.json` | `cec4b9d9957bacffffe6c9fb8f89ab2ecbc74819b4065ef4a7431eaadbd7fcbf` |
| `LIMIAR_CONGELADO_20261108.json` | `5811c3db3cce3426ba0e58e06f23035ff2a0cbb45e062ee139e8f2a82f04b11c` |
| `LOG_L8_CONGELADO_20261108.json` | `c43cba708013e1dee0ed7e2f0dfaba68d9d038f336dee66a87c4b232135e58fb` |
| `QASM 00000` | `f46c7930d032e7ec5b2a13f69989d3be393f646028d0d8814898de68e205240c` |
| `QASM 01010` | `c4ea78bb5fcbd1e33fe067a29bf8a17208f38920c8a4c682915db48cd251bbd7` |
| `QASM 10101` | `a9b29d7f34414992b8dafb1e2a90592a969b0550f67ee0b823740980f35f1cf7` |
| `QASM 11111` | `f602234065fe3d4821c8f37b31e9e1a7fcc7b090dc5640c88cb2cf2b337b6670` |
| `LAMBDAQ_ORIGINAIS_CADEIA_D_20261109.zip (historical private package)` | `abb8b62c96563c2113fcf02909c2beecece7809536b14220db344f889d0a60cf` |
| `controle_d30k.py (candidate)` | `5bed16a97cd1838d80d34f07101c30b279bc7572e36ac201aa7784bc84e97755` |
| `verificar_d30k.py (candidate)` | `596c3b8d56b21b004c3f58f5b5963c0e45072d25ec9ccca0d28ef92d9c0dfe04` |


Historical field freeze date: 31 October 2026; historical threshold and memory freeze date: 8 November 2026. The historical threshold derivation corpus was reported as 24,200 observations completed by 5 November 2026 (1,200 on 24 October; 3,000 on 26 October; 5,000 on 30 October; 15,000 on 5 November). Task-level provenance and the absence of overlap with subsequent evaluation data are subject to independent verification. D10K and D16K results do not become part of D30K's prospective score.

Hashes establish byte identity **when the underlying private files are presented to an authorized auditor**. A hash alone does not prove a claimed earlier creation date or independently reproduce private algorithms.

## 4. Public measurement definition

For each shot, `p[0..4]` are the five known preparation bits, `d[0..4]` are the final measured data bits, and `S[0..3]` are the four ancilla measurement bits, in the recorded order. The publicly defined detector and observable mapping is:

```text
T[c]       = p[c] XOR p[c+1]                c = 0..3
D[c]       = S[c] XOR T[c]                  c = 0..3
D[4+c]     = S[c] XOR d[c] XOR d[c+1]      c = 0..3
L_observed = XOR(d[0..4]) XOR XOR(p[0..4])
```

The *full-coverage logical-error count* is the integer number of shots where a method's prediction of the logical parity flip disagrees with `L_observed`. The outcome labels are used for evaluation **after** a prediction/selection decision is recorded, not to choose it. Each valid acquired shot remains in the complete-shot denominator. An abstention is reported, not removed from the raw record.

## 5. Frozen selection settings; no performance promise

The previously used selection settings are **100%**, **nominal 90%** and **nominal 66.7%**. Their original private numerical cutoffs and historic error bands are committed by the threshold artifact in §3; numerical coefficients are not disclosed. They will **not** be moved to force realized coverage or error rates into a band. The original frozen memory and rule configuration will not be learned from D30K correctness labels.

*Nominal coverage* identifies a fixed selection mode. *Realized coverage* is the actual integer count accepted divided by the number of complete shots. These need not coincide, particularly because the unchanged historical pipeline includes unlabeled data-dependent processing. Whether observed coverage falls within the historical pre-specified acceptance bands will be reported, including `OUTSIDE`/`FORA` when applicable. An `OUTSIDE` result is **not changed to a success or failure after the fact**. The selective error rate always names the accepted-shot denominator, distinct from the 100%-coverage result.

No maximum logical-error rate, exact achieved coverage, guaranteed improvement or favorable outcome is required or forecast in this pre-registration. This is a **prospective reproducibility and estimation study**, not a preregistered binary pass/fail performance claim.

## 6. Reference methods and comparisons

The same physical shots will support three predefined reference classes: (a) no correction, predicting no logical parity flip; (b) uniform-weight MWPM over the eight detectors; and (c) exact logical-class maximum likelihood under a uniform fault model, using the same detectors and a fixed reference probability as defined in its source implementation. No reference method may use the absolute logical observable as a predictor, and no reference model may be fitted to D30K correctness labels. Any comparator requiring a parameter not verified as frozen before data acquisition will be identified as **secondary/exploratory**, not silently treated as confirmatory.

The complete-shot error difference is reported as an integer on paired shots, together with the count of cases corrected by Lambda-Q but missed by the comparator and the count of cases corrected by the comparator but missed by Lambda-Q. No preset positive difference is required. Statistical summaries must respect preparation/session stratification; exploratory significance is labeled exploratory unless a fully specified testing and multiplicity rule is publicly committed before acquisition.

## 7. Mandatory results disclosure

Publish 12 per-cell records (three sessions × four known preparations) and per-session summaries before any pooled total: shot count, logical errors for full coverage per method, accepted count and errors among accepted for each selection setting, observed coverage, measured conditional error, QASM digest, raw digest, task identifier and execution UTC time. Publish the count of interrupted/failed/retried tasks and exceptions; missing data are not imputed. All results, including deterioration and out-of-band results, must be retained. Individual 2,500-shot cells document heterogeneity but are not asserted to prove small differences on their own.

All new D30K shots are evaluation observations. Derived results must be traceable to their raw source. Predicted decisions must be committed in a trace before any post-hoc diagnostic or parameter revision. Information access necessary to verify that protocol requirement will be available through controlled independent audit, not through disclosure of proprietary code in this public release.

## 8. Prior evidence, separated from the prospective cohort

The following historical counts were **reported earlier, not independently reprocessed in this editorial preparation**, and are not D30K results:

| Dataset (historical) | Date | Complete shots | Full-coverage errors | Accepted (historic nominal two-thirds mode) | Errors among accepted |
|---|---|---:|---:|---:|---:|
| D10K | 2026-11-09 | 10,000 | 260 | 6,877 | 50 |
| D16K | 2026-11-10 | 16,000 | 330 | 10,909 | 69 |
| Descriptive sum | — | 26,000 | 590 | 17,786 | 119 |

The descriptive full-coverage error rate is **590/26,000 = 2.2692%**. Among accepted results it is **119/17,786 = 0.6690%**, with **17,786/26,000 = 68.4077%** realized coverage. Those are conditional historical measures, not physical device fidelity and not guaranteed D30K predictions. The earlier D16K historical-band audit reported out-of-band (`FORA`) findings. Any subsequent re-analysis with an alternative processing configuration must be labeled **retrospective and separate**, not conflated with these baseline runs.

## 9. Intellectual property, provenance and publication sequence

The public material consists of this protocol, a cryptographic manifest and a short description. No private decoder implementation, internal module interfaces, numeric cutoffs, physical-field coefficients, private learning log, credentials or unpublished raw dataset is released. Qualified third-party reproduction of the private pipeline requires access under mutually agreed confidentiality and applicable authorization.

The approved protocol and hashes will be published as a GitHub release and archived in Zenodo with a DOI **before the first D30K submission**. After collection, a subsequent results release will reference the predecessor DOI and disclose the required results, hashes, provenance and all protocol deviations. Any changed configuration after the public timestamp constitutes a **new explicitly identified protocol version before acquisition**, never an invisible substitution.

**Status:** publication-ready protocol. Release timestamp, GitHub URL and Zenodo DOI will be recorded only after actual publication. No D30K task is authorized or claimed here; paid execution requires separate approval.
