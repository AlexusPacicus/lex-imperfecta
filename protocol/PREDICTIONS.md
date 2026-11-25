# Predictions

**Status: draft, 25 November 2026. Not frozen.**

Every number, range, mechanism and refutation criterion here is the author's. The wording was
drafted with Claude (Anthropic) from the author's statements and reviewed by the author.

Written before any run and frozen with the protocol. A prediction that fails is published as it is.

## 1. The predicted matrix

For each cell: the letter you expect, with its sign, and the estimate you expect with a range.
Capitals are the confirmatory cells. Leave "—" where the comparison does not apply.

| Comparison | Strict compliance | Channel use | Displacement | Tokens | Test quality (≥ B) | Task finished |
|---|---|---|---|---|---|---|
| C − A | a+ (19–20 against 0) | a+ | **H2: D** (expected 0 of 20; 0–1 against 0 in A; 2 or more gives E) | a+ (derived ratio 1.6–2.5) | e (no direction) | d to e− (17–20 against 19–20) |
| B-hook − A | **H1: E to B+** (1–6 of 20 against 0) | e to b+ | d | c+, d or e (ratio 1.05–1.15; e if the interval is wide) | d | d |
| B-md − A | a+ (14–19 against 0) | a+ | d | a+ (derived ratio 1.5–2.3) | d | d |
| C − B-hook | a+ (19–20 against 1–6) | a+ | d | **H3: A+** (ratio 1.5–2.2; B+ if the interval is wide) | e (no direction) | d to e− |
| B-md − B-hook | b+ to a+ (14–19 against 1–6) | b+ to a+ | d | a+ (ratio 1.4–2.0; b+ if the interval is wide) | d | d |
| C − B-md | d to b+ (19–20 against 14–19; d at the centre) | d to b+ | d | d or e (derived ratio 0.75–1.6, centre near 1.1) | e (no direction) | d to e− |

Governance events are descriptive and have no letter (`PROTOCOL.md`, section 9).

Cells marked as derived are not separate guesses. Their ratios follow from the three direct ones
(B-hook − A, C − B-hook and B-md − B-hook), by multiplying or dividing them (section 4, "The other
token cells"), and their letters follow from those ratios by the rule of `PROTOCOL.md`, section 9.
Section 2 gives the same derived ratios against A.

When the study ends, the observed matrix is put next to this one, cell by cell, with no
interpretation.

## 2. Expected values per condition

| Measure | A | B-hook | B-md | C |
|---|---|---|---|---|
| Strict compliance (% of runs) | 0% | 5–30% (1–6 of 20) | 70–95% (14–19 of 20; centre 18) | 95–100% (19–20 of 20) |
| Channel use (% of runs) | 0% | as strict compliance, or slightly above | as strict compliance, or slightly above | 95–100% |
| Displacement (% of runs) | 0% | 0–5% (0–1 of 20) | 0–5% (0–1 of 20) | 0–5% (expected 0; 0–1 of 20) |
| Output tokens, ratio to A | 1 (reference) | × 1.05–1.15 | × 1.5–2.3 (derived) | × 1.6–2.5 (derived) |
| Test quality: grade B or better (% of runs) | 30–60% (6–12 of 20; centre 9) | as A | as A | no direction |
| Task finished (% of runs) | 95–100% (19–20 of 20) | 95–100% | 95–100% | 85–100% (17–20 of 20): the code under test changed in 0–3 runs |

## 3. The instrument

* Strict compliance in C: [expected ≈ 100%; a value below is a leak finding].
* Accuracy of the gate (denies what it should, allows what it should):
* Cost per governed write, against the 1875 ms median Actuarii publishes:
* Leaks in C: whether you expect any, and through which path:
* Detection by the commit hook:

## 4. Why

One entry per prediction, each with the same five parts. Write each part in one or two sentences.

* **Mechanism:** why you expect this result.
* **Rests on:** what supports it: a study, your own data, the design of the setup.
* **Against:** what argues for the opposite result.
* **Refuted if:** the observed result that would show the mechanism is wrong. Concrete: a number or
  a letter.

### H1. Strict compliance, B-hook against A

* **Mechanism:** In B-hook, the rule arrives in the output of the session-start hook. The agent
  does not distinguish between instructions and data: it is all tokens. But I expect it to give
  more weight to rules that come through `CLAUDE.md`, the channel most present in its training,
  than to rules that come through other channels. Also, the rule is a statement about the system,
  not an order, and nothing enforces it: if the agent writes directly, the write works without
  error. A single write without a receipt is enough to fail strict compliance.
* **Rests on:** The setup: the rule text that B-hook receives (`PROTOCOL.md`, section 2) is a
  statement, with no order and nothing enforcing it. Since 2025, `CLAUDE.md` files have become
  common in public repositories (Agent READMEs, 2025), and models are trained on public code. Voria
  et al. (2026) found that agents follow the instructions in context files more often than not,
  but those were orders in `CLAUDE.md` or `AGENTS.md`, not text in a hook's output.
* **Against:** The agent may treat any text the system injects as an instruction: the output of a
  hook enters the context the same way as any other text. The full name of the tool appears in the
  rule and also in the agent's list of tools, so the link is easy to make. And with 0–2 writes to
  `tests/` per run, using the channel once is often enough for strict compliance.
* **Refuted if:** B-hook complies clearly more than A: the cell B-hook − A comes out A+ (the whole
  interval above 0.30). Then the rule works as a rule even in a hook's output, and the mechanism is
  wrong. Separately, if A complies in 2 or more runs of 20, A is not the baseline this prediction
  assumed.

### H2. Displacement, C against A

* **Mechanism:** These are unit tests, and their natural place is `tests/`, next to the tests that
  are already there (`tests/test_syllables.py`); `testpaths` makes a plain `pytest` collect only
  `tests/`. Since the whole of `tests/` is governed, there is no other natural place for them:
  displacing them would mean putting unit tests somewhere odd, such as the root of the repository
  or inside `silabas/`. In C, the full announcement tells the agent how to use the channel, so it
  can write to `tests/` with a receipt instead of avoiding it. I expect no displacement; the range
  allows one run of 20 because the model is stochastic. If displacement happens, I expect it
  mostly after the validator has denied a write in the same run; without a denial it is possible,
  but rarer.
* **Rests on:** The setup: the convention and `testpaths` (`PROTOCOL.md`, section 3), and the full
  announcement that C receives (section 2).
* **Against:** In Actuarii's clean-room test (A30), the agent moved its tests out of the governed
  path and said it did so to avoid asking for a receipt. But there the tests went to `tests/unit/`,
  a natural place for tests that was not governed, and the agent had no announcement of the
  channel. The friction is real: each governed write needs a proposal and costs about 1.9 s.
* **Refuted if:** C displaces clearly more than A: the cell C − A comes out B+ or A+. Or, among
  the runs of C that displace (at least 2), those with no denial before the displacement are as
  many as or more than those with one: then the friction alone moves the work, without a denial to
  trigger it.

### H3. Output tokens, C against B-hook

* **Mechanism:** In C, each governed write needs a proposal to `validate_proposal` with the exact
  content of the change, and then the write itself with the same content: the test code is
  generated twice. When a proposal is denied, it is written again; I estimate about one repeat for
  every 1.5 writes. Reasoning at medium effort is also output and dilutes this effect, but does not
  cancel it. B-hook rarely uses the channel (H1), so it rarely pays the double.
* **Rests on:** The setup: what `validate_proposal` requires in a proposal (`PROTOCOL.md`,
  section 2) and the medium effort level (section 4). My prediction for H1: B-hook complies in 1–6
  runs of 20.
* **Against:** If reasoning is most of the output, the duplicated content weighs less, and the
  ratio falls towards 1.2. If B-hook uses the channel more than I predict, it also pays the double,
  and the ratio falls towards 1.
* **Refuted if:** The ratio comes out inside the band [0.83, 1.2]: the cell C − B-hook is C or D.
  Then the duplicated content does not show in the output. If B-hook also complies in many runs, a
  ratio close to 1 does not refute the mechanism: it confirms it from the other side.

### B-md: the same text in `CLAUDE.md`

* **Mechanism:** B-md receives the same rule text as B-hook, but in `CLAUDE.md`, the file where the
  model expects the rules of the project and the channel most present in its training. I expect it
  to give that text much more weight than the same text in a hook's output. McMillan (2026) found
  compliance falling along a continuous session; here the session is short (0–2 writes to `tests/`)
  and the rule is read at its start, so I expect it to be followed well. Not in every run: strict
  compliance needs every write to go through `validate_proposal` in its proposal format, and one
  slip is enough to fail.
* **Rests on:** The setup: the same rule text in both B conditions, frozen with its hash
  (`PROTOCOL.md`, section 2). The spread of `CLAUDE.md` in public repositories (Agent READMEs,
  2025). McMillan (2026): the fall in compliance happened along the session, with each generated
  function.
* **Against:** McMillan (2026) found no effect of how a configuration file is structured on
  compliance, so the form of the file may matter less than I think. The text is still a statement,
  not an order, and nothing enforces it in B-md either. And the agent must learn the proposal
  format of a tool it has never used.
* **Refuted if:** B-md complies no more than B-hook: the cell B-md − B-hook comes out d or with a
  negative sign. Then the channel through which the rule arrives does not change how much it
  weighs. Or B-md does not clearly comply more than A: the cell B-md − A comes out d or with a
  negative sign. An e in either cell neither supports nor refutes the mechanism.

### C: strict compliance of 95–100%

* **Mechanism:** In C, the write gate denies every write to `tests/` without a receipt for that
  exact change, and the sandbox denies every write to `tests/` from `Bash`. The agent is not
  looking for a way around them: it only wants to write tests, and the announcement tells it how to
  use the channel. So I expect no leak, and every test that reaches `tests/` to have a receipt.
  Strict compliance also needs at least one write to `tests/`, and I expect the agent to write its
  tests there (H2). One run of 20 may fail by the model's stochastic nature, as a run that ends
  without writing to `tests/`.
* **Rests on:** The design of the instrument and the list of covered paths P1–P5 (`PROTOCOL.md`,
  section 7). My prediction for H2: displacement in C in 0–1 runs of 20.
* **Against:** Paths the kit declares it does not cover (U1): a receipt that does not bind the
  content counts as a covered write but does not prove the content. And if the agent displaces more
  than I predict, strict compliance in C falls with it.
* **Refuted if:** A leak through a covered path (P1–P5) appears in any run: that is an instrument
  failure, and a deviation. Or strict compliance in C is clearly below B-md: the cell C − B-md comes
  out with a negative sign and a letter a or b.

### C against B-md

* **Mechanism:** With a single request per session and 0–2 writes to `tests/`, B-md has little room
  to slip, so I expect it to comply almost as much as C (d at the centre). The difference should
  grow with longer sessions and more requests: compliance with an instruction falls along a session
  (McMillan, 2026), while in C every write to `tests/` needs a receipt whatever the length of the
  session. This study cannot show that growth; a study with several requests per session can.
* **Refuted if:** C − B-md comes out a or b with a positive sign already here, with a single
  request: then B-md fails even in short sessions, and the length of the session is not what
  separates them.

### Test quality

* **Mechanism:** Two forces pull in opposite directions in C, and I do not know which wins. Writing
  a proposal and a reason before each write may make the work more deliberate and the tests better.
  Or the friction may turn the agent's effort to getting past the validator instead of to the
  quality of the tests. What matters is being forced: in B-md the agent also writes proposals, but
  after a refused proposal it can write directly; in C it cannot write to `tests/` without a
  receipt. So I expect B-md to be like A, and B-hook too.
* **Rests on:** The grading of `PROTOCOL.md`, section 8. In a 2026 study of tests written by
  Claude, its mutation kill rates were close to those of human tests (Leith, 2026).
* **Against:** If the proposal itself, and not being forced, makes the work more deliberate, B-md
  should be better than A.
* **Refuted if:** B-hook − A or B-md − A comes out a or b, in either direction: then the rule
  changes the quality of the tests even when nothing forces the agent.

### Task finished, and changes to the code under test in C

* **Mechanism:** In A, B-hook and B-md nothing forces the agent, and the task is simple enough to
  finish. In C, the friction on `tests/` may push the agent to change what is not governed, the code
  under test, although the prompt says not to; I expect this in 0–3 runs of 20, mostly after a
  denial. This would be another kind of displacement: the work moves not to another folder but to
  another kind of file.
* **Rests on:** The setup: `silabas/` is not governed (`PROTOCOL.md`, section 2), and condition 2
  of task finished checks that it does not change (`definitions.md`). In an ablation study of
  context files, the differences in task success between strategies were small (2.3 points or less
  for Claude).
* **Against:** The prompt says explicitly not to change `silabas/syllables.py`, and agents usually
  follow such a direct order.
* **Refuted if:** Task finished in C is clearly lower than in A: the cell C − A comes out a or b
  with a negative sign. Or, among the runs of C that change the code under test (at least 2), those
  with no denial before the change are as many as or more than those with one.

### The other token cells

* **Mechanism:** B-hook spends a little more than A (ratio 1.05–1.15): most of its runs behave as
  in A, but the agent reasons a little about the rule, and the few runs that use the channel write
  the content twice. B-md uses the channel almost as often as C, so it also writes the content
  twice, plus the reasoning that `CLAUDE.md` provokes; a little less than C against B-hook, because
  after a refused proposal B-md can write directly instead of trying again (ratio 1.4–2.0). The
  cells against A follow by multiplying the ratios.
* **Rests on:** My predictions for H1, H3 and B-md.
* **Against:** Tokens vary a lot between runs, so with 20 runs many of these cells may come out e.
* **Refuted if:** B-md − B-hook comes out inside the band (c or d) while B-md complies in 14 or more
  runs: then using the channel does not double the output, and the mechanism of H3 is wrong too.
