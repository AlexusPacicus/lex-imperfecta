# Reviews

**Status: open. Seven points received on 26 November 2026; the author's decision on each is
pending.**

Every critique of the protocol: where it came from, what it says and what it changed. A critique
that changes nothing is recorded too, with the reason.

## How a critique is handled

* **Before the freeze** (Wednesday 2 December 2026, 23:59 Madrid time, 22:59 UTC; first set for
  Saturday 28 November and moved to work through R1–R7): a critique that changes the design changes
  the files of `protocol/` directly, in a commit that names its entry here.
* **After the freeze:** a critique that changes the design is written in `DEVIATIONS.md`, with its
  date and its reason, or carried to the next study. Its entry here says which.
* **Credit:** each reviewer is named as they choose, or not named. A critique that changes the
  design is acknowledged in the publication, with what it changed (`README.md`).

## Requests

Where review was asked for. If none arrives before the freeze, the report says so
(`protocol/PROTOCOL.md`, section 13).

| Date | Where | Closes |
|---|---|---|
| [AUTHOR: date] | Apart Research Discord, [AUTHOR: link to the thread] | Wednesday 2 December 2026, 23:59 Madrid time, for changes to the protocol |
| [AUTHOR: date] | The issues of this repository | Open; after the freeze, as above |

## Summary

| # | Received | Reviewer | Area | The point | Outcome |
|---|---|---|---|---|---|
| R1 | 26 Nov 2026 | Mimir's Well | statistics | The instruction-versus-enforcement comparison of compliance is exploratory, not confirmatory | Pending |
| R2 | 26 Nov 2026 | Mimir's Well | setup | Disk snapshots cannot establish compliance event by event, or see transient changes | Pending |
| R3 | 26 Nov 2026 | Mimir's Well | statistics | Hodges–Lehmann ratios are not transitive, so the derived token predictions do not follow | Pending |
| R4 | 26 Nov 2026 | Mimir's Well | statistics | The blocked randomisation is not reflected in the analysis | Pending |
| R5 | 26 Nov 2026 | Mimir's Well | construct | Strict compliance mixes enforcement, obedience and completion | Pending |
| R6 | 26 Nov 2026 | Mimir's Well | setup | Mutation scoring needs a protected environment, and the reference suite is not a ceiling | Pending |
| R7 | 26 Nov 2026 | Mimir's Well | statistics | A margin set by resources is not an acceptable rate of governance failure | Pending |

## Entries

The seven points arrived in one message in the Apart Research Discord, on 26 November 2026 at 11:59
Madrid time [AUTHOR: check the time in Discord] ([AUTHOR: link to the message]). Signed: "Mr.
Peloquin and Ms. Asteris Solenne (ChatGPT-assisted review), Mimir's Well". How the reviewers wish
to be credited was asked on 26 November 2026 and is pending. The reviewers offered counterexamples
and proposed corrections for each point; they were requested the same day.

### R1. The comparison of compliance between instruction and enforcement is exploratory

* **Received:** 26 November 2026, Apart Research Discord ([AUTHOR: link]).
* **Reviewer:** Mimir's Well (credit pending; see above).
* **Area:** statistics.
* **The critique:** the primary comparison of compliance between instruction and enforcement, which
  is the question of the title, is exploratory rather than confirmatory.
* **Outcome:** pending, the author's decision before the freeze.
* **What changed:** nothing yet.

### R2. Snapshots cannot establish compliance event by event

* **Received:** 26 November 2026, Apart Research Discord ([AUTHOR: link]).
* **Reviewer:** Mimir's Well (credit pending; see above).
* **Area:** setup.
* **The critique:** disk snapshots taken before and after a run cannot establish compliance for
  each write, nor detect an unauthorised change that is made and undone during the run.
* **Outcome:** pending, the author's decision before the freeze.
* **What changed:** nothing yet.

### R3. Hodges–Lehmann ratios are not transitive

* **Received:** 26 November 2026, Apart Research Discord ([AUTHOR: link]).
* **Reviewer:** Mimir's Well (credit pending; see above).
* **Area:** statistics.
* **The critique:** Hodges–Lehmann ratios are not transitive in general, so multiplying ratios
  estimated separately can give derived predictions that are mathematically wrong
  (`PREDICTIONS.md`, the derived token cells).
* **Outcome:** pending, the author's decision before the freeze.
* **What changed:** nothing yet.

### R4. The analysis ignores the blocked randomisation

* **Received:** 26 November 2026, Apart Research Discord ([AUTHOR: link]).
* **Reviewer:** Mimir's Well (credit pending; see above).
* **Area:** statistics.
* **The critique:** the runs are ordered by blocked randomisation, but the analysis treats the
  conditions as independent samples.
* **Outcome:** pending, the author's decision before the freeze.
* **What changed:** nothing yet.

### R5. Strict compliance mixes three things

* **Received:** 26 November 2026, Apart Research Discord ([AUTHOR: link]).
* **Reviewer:** Mimir's Well (credit pending; see above).
* **Area:** construct.
* **The critique:** strict compliance, as defined, conflates the success of the enforcement, the
  agent's obedience and the completion of productive work.
* **Outcome:** pending, the author's decision before the freeze.
* **What changed:** nothing yet.

### R6. Mutation scoring: a protected environment, and no ceiling

* **Received:** 26 November 2026, Apart Research Discord ([AUTHOR: link]).
* **Reviewer:** Mimir's Well (credit pending; see above).
* **Area:** setup.
* **The critique:** scoring the agent's tests by mutation needs an evaluation environment that the
  run cannot affect, and the reference tests are not necessarily a ceiling for the score.
* **Outcome:** pending, the author's decision before the freeze.
* **What changed:** nothing yet.

### R7. A margin set by resources is not an acceptable failure rate

* **Received:** 26 November 2026, Apart Research Discord ([AUTHOR: link]).
* **Reviewer:** Mimir's Well (credit pending; see above).
* **Area:** statistics.
* **The critique:** an equivalence margin set by what the study can afford must not be read as a
  practically acceptable rate of governance failure.
* **Outcome:** pending, the author's decision before the freeze.
* **What changed:** nothing yet.

Each entry has this form:

```
### R1. The point, in a few words

* **Received:** date, and where, with its link.
* **Reviewer:** the name the reviewer chose, or "not named".
* **Area:** statistics, construct, setup, or other.
* **The critique:** what it says, in one to three sentences.
* **Outcome:** changed, not changed, recorded as a deviation, or carried to the next study.
* **What changed:** the files and sections, with the commit. If nothing changed, why.
```
