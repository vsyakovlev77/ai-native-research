# Getting started

You need: a coding agent you already use (Claude Code, OpenAI Codex and Google Antigravity are the three this is written for), a folder where your projects live, and about an hour. You do not need to be a programmer. You will not write code; your agent will. Not everything you use it for has to be research: the record and seven of the eleven skills serve any project you run, and research adds the other four.

---

## 1. Read and edit the spec

Read [`SPEC.md`](../SPEC.md). It is written to be edited: change what you disagree with, delete what you will not use, keep the parts §M of the spec calls the standard so that your projects stay readable by colleagues' systems and by next year's re-implementation. If you only change one thing, change the *Escalates* lines — they decide what the agent asks you and what it settles alone.

Read [`PRINCIPLES.md`](../PRINCIPLES.md) once, so that when you extend the system later you can tell a considered choice from an accident.

---

## 2. Build it

Create a folder for your projects if you do not have one, for example `~/projects/`. Put `SPEC.md` and `PRINCIPLES.md` in it; at Attoworld, put `attoworld.md` there too and answer yes when the agent asks about local resources. Open the folder in your coding agent and say:

> Read PRINCIPLES.md and SPEC.md in this folder. Implement the system they describe for this harness. Build the skills so that each carries what it needs to run: no skill reads SPEC.md while it runs, embeds a path to it, or fails without it, and a skill I lend a colleague must still mean what it says. No instruction file you write may name SPEC.md either, at any level, so that I can rename it or move it without touching anything. SPEC.md stays at this root as my authority and as what you rebuild from; never copy it into a project. Write CONVENTION.md at this root holding only what SPEC.md leaves to me — this folder as the configured root, my standing preferences, my notation and units, my environment and package manager — and repeating no part of the spec. Install the eleven skills at user level in the folder this harness reads, in the SKILL.md format, with the check references and genre references the research skills need; write every instruction file SPEC §B asks for outside a project, including the harness's own always-loaded one, which names this folder as the configured root by path; and tell me, per rule in SPEC §F, whether you enforce it by a hook or by instruction. Ask me once whether local resources apply — shared code repositories, an institution-hosted model, compute beyond this machine — and if they do, put them in one site file at this root and add to CONVENTION.md a single line naming that file and the condition for reading it; if I say no, write nothing about it. Do not create any project yet. Do not invent file formats beyond what SPEC §B–§G require; leave them to be decided when each file is first written.

Review what it produces. The two things worth reading line by line are `CONVENTION.md` and the instruction file, since every skill reads them while it runs, unlike the spec, which the skills were built from and no longer consult. When you later change your mind about a boundary, edit `SPEC.md` and ask the agent to rebuild the skill it governs — the edit alone does not reach what runs. The skills you can skim.

Nothing reads `SPEC.md` once the build is done, so it need not stay in your projects folder — the instruction above puts it there because that is where the agent reads it from, and once the skills are built it is free to move. Keep it wherever you will find it when you want to change it — if you already keep a repository of your own documents, that is a better home than a folder full of projects. Keep exactly one copy: a second is a second authority, and it will drift.

While you are in `CONVENTION.md`, write down the things you do not want an agent guessing at: your package manager, your plotting defaults, your notation and units, the language you write in. Each is one line, too small to be a rule of the system and too irritating to leave unwritten.

---

## 3. Adopt your first project

Pick one live project — not your most important one. Open its folder in the agent and say:

> Adopt this folder into the convention. Use `project-establish`.

The skill reads what is there, derives an aim and a state, scaffolds the record files, indexes what it can classify, and asks you to confirm the aim and state. It does not interview you. At the same pause it asks whether this is a research project, and if it is, the folder where questions, findings and drafts will live; both become your own lines in `PROJECT.md`, which no skill alters (see the [walkthrough](walkthrough.md)). Answer no and nothing is lost: the record and the seven record skills are identical either way, and the four `research-*` skills simply stand aside where you have not asked for them — the agent still does the work, under the same working-tree rules. If any material in the folder must not leave your machine, write a confidentiality note in `PROJECT.md` now.

Then ask it something: "What is the state of this project?" If the answer is right, you are running.

---

## 4. The first week

You will use three skills most days and can ignore the rest until you need them:

- **Ask.** "What changed since Tuesday?" "Why did we choose the length gauge?" — `project-ask`.
- **Do.** "Derive the low-field limit of this expression." "Run the convergence study." "Search for measurements of X in Y." — `research-act`, which the agent picks on its own from the description; in a project you did not declare a research project it simply does the work, under the same working-tree rules.
- **Sweep.** At the end of a session in which you corrected something, decided something or learned something: "Sweep." — `project-sweep` proposes what to record and writes it on your approval.

Add as you need them: `research-question` when a question is worth writing down properly; `project-plan` before work that will outlast one session; `research-review` before a finding goes into the record; `research-write` for anything that leaves the project; `project-file` when the inbox has something in it; `project-revise` when a store has grown; `project-steward` for the view across projects.

Four habits carry everything:

1. **Drop things into `_WORKSPACE/`.** A paper, an email, a data description, a colleague's plot. Filing is the agent's job, and `_FILED/` is the one folder you leave to it: read anything there, but add, rename, move and delete nothing by hand, because `INDEX.md` promises that everything under it is indexed and nothing checks that promise afterwards. Removal is a revision you approve. It works the other way too: a notebook, a literature search, a draft report the agent makes in a session lands there unless your project already has a folder for that kind of thing, so an hour's loose output is filed in one operation.
2. **Correct in one sentence with the reason.** "No — use atomic units here, the rest of the code does." The agent notes it; the next sweep records it; you will not have to say it again. A correction that is about you rather than about this project (your units, your package manager, how you write) is proposed for `CONVENTION.md` instead, and on your approval the sweep appends it there, to the one section of that file it may write.
3. **Nothing leaves without you.** No email, submission or shared file goes out except along a route you declared or by a send you approved after seeing exactly what would go. The agent drafts, and asks.
4. **Glance at what waits on you.** `_WORKSPACE/pending.md` holds the decisions the agent could not ask you and the things it wants to say — a disagreement, a conjecture, a question you did not raise. Answer the decisions; pick up or ignore the rest. It owes you a line; you owe it a glance.

And one setting: if you want the agent to try things on its own — twenty variants overnight, three kept — grant an exploration budget in `PROJECT.md`. Without one, it explores nothing.

---

## 5. Where things go, per harness

The spec fixes the file names of the record and the skill names; the harness fixes where its own files live. The table below is taken from each product's own documentation as of September 2026. What has actually been run: the spec has been built from scratch five times on Claude Code, in throwaway roots, and the last of those was exercised through a full loop — a question, a plan, work, a review, a sweep. It has also been built once on Antigravity and used daily for several weeks, on a tree of about fifteen projects, one of them a research project carried through two milestones. The defects those runs turned up are in this document and in the spec. Nothing has been built on Codex. So treat the Codex column as the starting point for your agent rather than as a test report, and correct any of the three in the repository when you find a difference. The pattern is the same everywhere: one instruction file per project (`AGENTS.md`), which the other harnesses' native files reference by one line; skills once, at user level, in the folder your harness reads.

| | Claude Code | OpenAI Codex | Google Antigravity |
|---|---|---|---|
| Instruction file, per project | `CLAUDE.md` — one line: `@AGENTS.md` | `AGENTS.md` (read directly) | `AGENTS.md` (read directly at the workspace root); `.agents/rules/*.md` for further rules |
| Instruction file, global | `~/.claude/CLAUDE.md` | `~/.codex/AGENTS.md` | `~/.gemini/GEMINI.md` |
| Skills, user level | `~/.claude/skills/<name>/SKILL.md` | `~/.agents/skills/<name>/SKILL.md` | `~/.gemini/config/skills/<name>/SKILL.md` |
| Skills, project level | `.claude/skills/` | `.agents/skills/` (also read at parent and repository root) | `.agents/skills/` |
| Interactive question tool | yes (`AskUserQuestion`) | plan-mode input only; escalations otherwise end the turn | yes (`ask_user`) |
| Subagent with fresh context | yes (`.claude/agents/`) | yes (`.codex/agents/*.toml`) | yes (`.agents/agents/*.md`) |
| Hooks (deterministic gates) | yes: `PreToolUse` can allow, ask or deny | partial: prompt-submit and session hooks; tool-use hooks arriving | yes: `PreToolUse` can allow, ask or deny |
| Scheduled runs | scheduled tasks | Automations | sidecars |

All three read the same `SKILL.md` format, so one set of skill folders serves all three; link or copy it into the folder each harness reads. Project-local skills — the ones the agent proposes for a project's recurring procedures — go into the project-level folder and are versioned with the work.

**Which rules are gated and which are instructed.** Where the harness has `PreToolUse` hooks, the implementation should gate: any command that sends mail or posts to a service; any write under a folder you have named as raw data; any write to `decisions.md` other than an append. Where it does not, these rules hold by instruction, and you should know that. Ask your agent to tell you which is which for your harness; the build instruction in §2 asks for exactly that.

---

## 6. The git boundary

Agents may stop looking for instruction files and skills at the root of a git repository or at the folder you opened, and none of the three promises not to. If your project folder is itself a git repository — most are — then an `AGENTS.md` or a skills folder *above* it may not be found. The layout assumes it will not be, which costs nothing if your harness is more generous: every project carries its own instruction file, `CONVENTION.md` is referenced by an explicit path, and skills are installed at user level rather than at your projects root. Explicit reads by path still work across the boundary; only discovery stops. Your `SPEC.md` is not referenced at all — nothing reads it while the system runs, so you can rename or move it and nothing breaks.

---

## 7. Confidentiality

Unpublished data, a collaborator's unpublished results, grant text, personal data of students or patients: decide per project what must not leave your machine, and write it in one sentence in `PROJECT.md`. Every agent honours it under the spec's working-tree rules; where the harness has permission deny-lists, the implementation should also deny reads of the folders you name by tools that reach the network.

Members of the Max Planck Society and many German universities have access to models hosted on GWDG's own infrastructure through an Academic Cloud account, reachable by web chat and by an OpenAI-compatible API. For confidential material, a project can name such a model as the only one permitted. For everyone else the rule is the plain one: do not put into an external AI service anything you would not put into an email to a stranger.

---

## 8. When it goes wrong

- **The agent answers from memory instead of the record.** Ask it to use `project-ask` by name; if it still does, the instruction file is not being read — check that it sits inside the project folder, not above it.
- **The record and reality have drifted.** Sweep more often; a sweep takes a minute. If a store has grown stale, `project-revise`.
- **A `verified` finding turns out not to have been reviewed properly** — the reviewing context could not run what it attested to, or was not independent after all. The finding goes back to `tentative`, which is the one route back from `verified`; the review record says what the earlier review lacked, and the next sweep proposes what the facts resting on it now carry. The claim is not thereby false, only no longer reviewed.
- **A finding was wrong and it is in `facts.md`.** Run `research-review` on it in a fresh session; on `refuted`, the next sweep proposes the retirement and removes the fact on your approval. The finding document keeps the history.
- **The plan step chafes.** Then it is being asked for too often. `PLAN.md` is for work one session cannot finish — spanning days, or carrying steps you own. It is also for work a session *could* finish whose cost makes the approach worth settling first: restructuring code rather than adding to it, a run long enough that a wrong parameter is expensive, anything spending a shared allocation, anything reaching outside your machine. Length is one test, cost is the other, either alone makes a plan. Anything else your agent can carry to a stopping point today is a direct request, and it sequences its own moves within it; if your harness already plans a complex task and asks you to approve that plan, it is your gate on those moves and the system does not add a second. For work whose shape you do not know yet, grant a budget and let it explore.
- **The pending note fills up.** Proposals are meant to be ignored cheaply; dismiss them at the next sweep. If they are consistently useless, say why once — that reason is a correction and gets recorded.
- **It asks too much or too little.** Edit the *Escalates* lines in §H of your `SPEC.md`; they are yours, and the skills are rebuilt from them.
