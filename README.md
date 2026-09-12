# An AI-native system for research and project work

A small convention for working with a coding agent as a collaborator, and a spec from which your own agent builds it. It is shaped by what research needs, and only four of its eleven skills are particular to research: the rest serve any project you run. Files you own, in folders you own, readable without any tool. Designed for Claude Code, OpenAI Codex and Google Antigravity, and for whatever replaces them.

**Start here:** [The playbook](https://vsyakovlev77.github.io/ai-native-research/) · [Getting started](docs/getting-started.md) · [Walkthrough](docs/walkthrough.md) · [The spec](SPEC.md) · [The principles](PRINCIPLES.md) · [FAQ](docs/faq.md)

The playbook begins with a one-page explanation of why the system is shaped this way, and is the place to start if you are deciding whether any of this is for you; the spec is what your agent builds from. It is served from this repository at [vsyakovlev77.github.io/ai-native-research](https://vsyakovlev77.github.io/ai-native-research/); its source is [`playbook.html`](playbook.html) here, which GitHub itself shows as source rather than rendering.

---

## The idea in one paragraph

Research is a loop: questions → plans → actions → findings → questions. Each station gets a file or a document, written as a byproduct of the work, so that the agent arrives already knowing the project and the researcher never briefs it. The agent does the mechanical part — derivations, computations, analyses, searches, drafts — and checks its own work in a way a second context can reproduce, before the researcher reads one line. It also speaks: it says when it disagrees, explores within a budget it was granted, and keeps working while the researcher is away, queuing what needs their decision. The researcher does what only they can: state the question, approve the plan, do the experiment, judge, understand, and send. Nothing enters the record and nothing leaves the project without the researcher's hand.

Little of that record is particular to research. A proposal, a course, a piece of administration, a move has an aim, a state, a plan, facts it relies on, decisions with their reasons, material to file and a history, and gets exactly the same files and the same seven record skills. Research adds the loop and the standard of evidence that goes with it, and one line in `PROJECT.md` asks for it.

## Ten principles

1. **Questions first.** Every piece of research starts as a written question with what would count as an answer.
2. **Files, not chats.** The interface between you and the agent is a set of files that carry over between sessions, agents and years.
3. **Approve plans, not outputs.** Your judgment is cheapest before the work starts. The agent interviews you, writes the plan, you approve; deviations update the plan.
4. **Every finding checks itself.** Limiting cases, convergence, a located citation, an adversarial review in a fresh context — before you read it. Every finding carries its status.
5. **Teach the system, not the chat.** A correction with its reason goes into a file the agent reads every session. Say it once.
6. **Route judgment through the human, never data.** Layered briefings, news not state, batched decisions as choices, questions only you can answer.
7. **Close the loop.** Findings raise questions and decisions carry revisit conditions; the backlog fills itself and you choose from it.
8. **You send, you sign, you decide.** Nothing leaves the project by an agent's hand.
9. **Provenance everywhere.** Every plot, table and number traces to data, code, parameters and a date.
10. **The agent speaks.** It disagrees, conjectures and proposes in one line where it arises, explores within a budget you grant, keeps working while you are away, and owes you an explanation of every finding. Never about what should matter; always about what is true or could be tried.

## What you get

A project folder looks like this:

```
my-project/
├── AGENTS.md        instruction file for the agent
├── PROJECT.md       what and where: aim, state, status, next steps, open questions — 800 words
├── PLAN.md          how: the current plan, with owners and completion criteria
├── facts.md         what we rely on, each with provenance and a retirement condition
├── decisions.md     why, append-only, with revisit conditions
├── log.md           what happened, one line per operation
├── INDEX.md         where to look, and when
├── _WORKSPACE/      in-tray and bench: what you drop, what the agent makes with
│                    no home yet; two notes: what it learned, what waits on you
├── _FILED/          the agent's filing cabinet: read it, never rearrange it by hand
└── …                everything else is yours: code, data, questions, findings, drafts
```

and eleven named skills: seven that keep the record (`project-ask`, `project-file`, `project-plan`, `project-sweep`, `project-establish`, `project-revise`, `project-steward`) and four that do research (`research-question`, `research-act`, `research-review`, `research-write`). The seven serve every project; the four run where `PROJECT.md` declares a research project and stand aside elsewhere, the agent doing the work without them under the same rules. Three of the eleven carry the first week.

## What is meant to last

Agents and models will be replaced, and then replaced again. The point of agreeing on this among colleagues is not the implementation but a handful of standards simple enough to keep identical across people and across re-implementations: the record files and their meaning, the shape of a question, a plan and a finding, the status of a finding, what an agent may do to your work, and the names of the skills. Keep those, rebuild everything else freely, and no project is ever disrupted by a better model. §M of the spec says exactly which is which.

## How to adopt it

1. Read and edit [`SPEC.md`](SPEC.md). It is yours, kept wherever you will find it again, and it is what your agent builds the skills from — change it and ask for a rebuild, and the system changes with you.
2. Give it to your coding agent with the instruction in [Getting started §2](docs/getting-started.md#2-build-it).
3. Adopt one project. Ask it a question. Sweep at the end of the day.

At Attoworld, [`attoworld.md`](attoworld.md) holds what is local to us: the shared code repositories, the institution-hosted model, the compute. Your agent reads it only when a task reaches for one of those. If your subgroup keeps code worth naming, add a line to it.

## Status

Version 1, September 2026, at [github.com/vsyakovlev77/ai-native-research](https://github.com/vsyakovlev77/ai-native-research). Written for colleagues at Attoworld, theorists and experimentalists, students and group leaders alike. Issues and edits welcome; the spec's open questions (§N) are where opinions are most wanted.

[CC BY 4.0](LICENSE). Copy it, edit it for your group, redistribute your version; say what you changed and where it came from.
