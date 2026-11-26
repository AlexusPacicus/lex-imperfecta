# lex-imperfecta

**Instruction or enforcement? A pre-registered study of a write rule for coding agents.**

A coding agent works in a repository with one write rule: the files of `tests/` are changed only
through a channel that records each change and its reason. Does it matter whether the agent gets
that rule as an instruction (in a session hook or in `CLAUDE.md`) or whether code outside the model
enforces it?

Four conditions, 20 runs each, with Claude Code and Claude Sonnet 5.5. The study measures
compliance, displacement (work that moves outside the governed path), the quality of the tests the
agent writes (by mutation), and cost. The enforcement is done by
[Actuarii](https://github.com/AlexusPacicus/actuarii), used here as the instrument, not evaluated as
a product.

**The name.** Roman law, in the rules attributed to Ulpian, sorted laws by their sanction. A *lex
perfecta* forbids an act and undoes it if it is done. A *lex imperfecta* forbids it and does
nothing if it is done: *imperfecta lex est quae vetat aliquid fieri, nec tamen si factum sit
rescindit*. A rule given only as an instruction is a *lex imperfecta*; the study asks whether it
achieves what enforcement by code does.

## Status

**Draft, not frozen.** The protocol freezes on **Wednesday 2 December 2026 at 23:59, Madrid
time** (22:59 UTC), in one commit published on Zenodo with its own DOI. No run has
been made. The harness and the code under test come after the freeze.

## Documents

| File | What it holds |
|---|---|
| [`protocol/PROTOCOL.md`](protocol/PROTOCOL.md) | The design: question, conditions, task, setup, analysis, threats to validity |
| [`protocol/definitions.md`](protocol/definitions.md) | Every term of the study, with the operation that decides it |
| [`protocol/PREDICTIONS.md`](protocol/PREDICTIONS.md) | The author's predictions, written before any run, each with what would refute it |
| [`REVIEWS.md`](REVIEWS.md) | Every critique received: where it came from, what it says and what it changed |

## Reviews wanted

Criticism, not approval. Any depth is welcome: a single point that changes the design counts as
much as a full review. Three areas where it helps most:

* **Statistics:** the verdict letters, Newcombe intervals, Hodges–Lehmann on log tokens,
  Bonferroni for three confirmatory cells.
* **Construct:** the definitions of compliance, displacement and leak, and the list of covered
  paths.
* **Setup:** the isolation of each run and the four conditions.

Comment in an [issue](../../issues) or in the thread in the Apart Research Discord.

**Credit:** every critique that changes the design is acknowledged by name in the publication, with
your permission, along with what it changed. Critiques that arrive before the freeze change the
protocol directly; after it, the invitation stays open, and critiques that change the design are
recorded as deviations or carried to the next study, with the same credit. Every critique, and
what it changed, is recorded in [`REVIEWS.md`](REVIEWS.md).

## How this was written

The protocol was drafted in English with Claude (Anthropic) from the author's decisions, taken in
Spanish; the author reviewed every section. The predictions are the author's; their wording was
drafted with Claude from the author's statements.

## Author

Alexis Zapico Fernández ([@AlexusPacicus](https://github.com/AlexusPacicus)).

## Licence

The study's text (the documents of `protocol/`, this README and `REVIEWS.md`) is licensed under
[CC BY 4.0](LICENSE-TEXT). Its code (the harness and the analysis, which come after the freeze) is
licensed under [Apache-2.0](LICENSE). The code under test, added after the freeze, keeps its own
MIT licence and notice.
