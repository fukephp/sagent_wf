# vgraph_loop

This repo is set up for planning before building. Work is tracked in GitHub Issues. Domain docs are single-context (`CONTEXT.md` + `docs/adr/`), created later when terms actually settle.

## How to plan

Pick one path depending on size:

| Size | What to type | What it does |
| --- | --- | --- |
| Small / one session | `/grill-me` then the idea | Stress-tests the plan. No tracker artifacts. |
| Same, but write glossary/ADRs as you go | `/grill-with-docs` then the idea | Same interview, plus `CONTEXT.md` / ADRs when terms or hard decisions lock. |
| Bigger than one session | `/wayfinder` then the idea | Charts a **map** as a GitHub issue, then decision tickets you work one at a time. |

For a new project, **`/wayfinder` is the planning path.** `/grill-me` is only enough if the destination is already small and clear.

### 1. Name the destination

Say what “done planning” looks like in one or two lines. Examples: a spec you can hand off, a locked architecture decision, a first shippable slice.

Wayfinder will grill you on this first. That destination **is** the scope. Anything past it goes in **Out of scope**, not the map.

### 2. Chart the map (one session)

`/wayfinder` plus the loose idea. It will:

1. Grill you until the destination is sharp.
2. Fan out breadth-first: open decisions, first takeable steps, fog you cannot ticket yet.
3. Create one GitHub issue labelled `wayfinder:map` with Destination, Notes, Decisions so far, Not yet specified, Out of scope.
4. Create child issues for questions you can already state, then wire **blocked by** edges.
5. Kick off any **research** tickets in the background.

If that pass finds no fog (the whole journey fits one session), you do **not** need a map. Stop and either grill deeper or go straight to tickets.

**Do not build yet.** Wayfinder plans. Execution only starts when the way is clear.

### 3. Work the map (one ticket per session)

New Agent chat, `/wayfinder` plus the map issue (URL or number).

It claims the next unblocked, unclaimed child, resolves it, closes it, and gists the answer on the map. Types:

- **grilling** — you answer questions (default)
- **prototype** — cheap artifact to react to
- **research** — agent looks things up
- **task** — setup that unblocks a decision (API signup, access, sample data)

Resolving a ticket graduates fog into new tickets. Repeat until the frontier is empty.

### 4. Turn the plan into build tickets

When the way is clear, run `/to-tickets` on the map or spec.

It breaks work into **vertical slices** (schema + API + UI + tests in one demoable bite), quizzes you on granularity and blockers, then publishes GitHub issues. Work the frontier: any ticket whose blockers are all closed.

### 5. Domain docs appear as a side effect

Do not start by writing `CONTEXT.md`. It is created when a term is actually resolved. ADRs only when a choice is hard to reverse, surprising, and a real trade-off.

## Starting a session

Paste a short dump of the idea, then invoke the skill. Example:

> `/wayfinder` I want to build vgraph_loop: [who it’s for, what they do, what “v1 works” looks like]. Chart the map.

Need to lock language/decisions into docs as you talk? Use `/grill-with-docs` instead for a smaller start.
