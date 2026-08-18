# Justified Intervention

Coding agents can make changes quickly, but they are less reliable at deciding
how much change a situation warrants.

Justified Intervention is a set of working rules for that decision. It asks an agent
to stay close to the user's intent, learn how the repository works, respect the
authority it has been given, and support its conclusions with evidence.

> **An intervention must never exceed the evidence that justifies it.**

## Why this exists

Many expensive agent mistakes start in ordinary ways. A plausible guess is treated
as a fact. A local symptom is fixed while the shared cause survives. An unrelated
refactor slips into a small request. A test passes, but it never exercised the
behavior the user cared about. A tool is available, so the agent assumes it is allowed
to use it.

These mistakes come from failures of scope, evidence, and judgment.

Justified Intervention addresses them without turning every task into a ceremony. It
works across languages and repositories, and it does not prescribe an architecture,
framework, or development methodology.

## The idea in brief

The rules keep four things aligned:

- **Intent:** what outcome the user needs, including the limits of the request.
- **System:** what the repository actually does, rather than what the agent expects.
- **Authority:** what the agent is allowed to read, change, run, or affect.
- **Evidence:** what has been observed and verified instead of merely inferred.

That means investigating before committing to an explanation, fixing the
cause rather than the visible symptom, preserving contracts and existing work, and
stopping once the requested outcome has been demonstrated.

See [PHILOSOPHY.md](PHILOSOPHY.md) for the principles and limits.

## What is in `AGENTS.md`

[AGENTS.md](AGENTS.md) turns the philosophy into instructions for coding agents. It
covers:

- how to distinguish a review from permission to edit;
- how to investigate, bound, implement, and verify a change;
- when tests, dependencies, plans, or delegated work are justified;
- how to preserve contracts and pre-existing user changes;
- which local actions are routine and which effects need explicit approval;
- how to report evidence, limitations, and unresolved decisions.

The file is self-contained. It works on its own as global guidance or as
a repository-level policy. Project-specific instructions can still refine it, and a
larger workflow can build on it without becoming a dependency of the philosophy.

## Install

The commands below download the current `AGENTS.md` from this repository. They use
`-o`, so they **replace any file already present at the destination**. If you already
have agent instructions, use the review-first option and merge the rules deliberately.

### Global Codex guidance

```bash
mkdir -p ~/.codex
curl -fsSL https://raw.githubusercontent.com/iamdantz/agents/main/AGENTS.md \
  -o ~/.codex/AGENTS.md
```

### One repository

Run this from the repository root:

```bash
curl -fsSL https://raw.githubusercontent.com/iamdantz/agents/main/AGENTS.md \
  -o AGENTS.md
```

### Review before installing

```bash
curl -fsSL https://raw.githubusercontent.com/iamdantz/agents/main/AGENTS.md \
  -o /tmp/justified-intervention-AGENTS.md
```

Read that file, then copy or merge only what belongs in your existing instruction
chain.

## Not a framework

Justified Intervention is concerned with the quality and legitimacy of a change, not
with prescribing one universal way to organize development. It can govern a short
one-file correction or sit underneath a structured process with specifications,
worktrees, test-driven development, subagents, and code review.

In either case, the same questions remain: Is this what the user asked for? Does the
repository support the explanation? Is the action authorized? What evidence will show
that the work is done?

## Background

The philosophy addresses common failures in software agents: overfitted patches,
weak traceability, invented packages, lost context, unsafe permission expansion, and
prompt injection. The complete source list and the connection between those findings
and the policy live in the
[foundation section of the philosophy](PHILOSOPHY.md#foundation).
