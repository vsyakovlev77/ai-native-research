# Principles for an AI-native system for research and project work

Purpose, rationale and principles. Contains no file names, no skills and no procedures — those live in the spec. This document exists to explain *what the system is for* and *why it is shaped the way it is*, so that a builder can tell a considered choice from an accident, and so that anyone extending the design can do so without contradicting it.

Read §1 before anything else. Every later section is subordinate to it.

Term for the human throughout: **the researcher**. One person, the only human in their system, and the only source of authority about what matters in it. Groups share projects; they do not share systems. Each researcher runs their own, and what passes between people is documents.

---

## 1. Purpose

A researcher has several things to be good at at the same time: a theoretical or experimental programme, usually more than one; students to supervise or a supervisor to satisfy; proposals, reports, teaching, reviewing, correspondence; and a life outside all of it. Each generates questions, commitments, material and decisions independently of the others. None can be dropped.

**The purpose of the system is to raise both what the researcher accomplishes and how good it is, by making collaboration with AI agents the normal way research gets done rather than an occasional resort.**

That purpose is served across the whole of the list above and not only its first item. The proposal, the report, the teaching, the reviewing and the correspondence are carried by the same system on the same terms as the programme they surround, because they compete with it for the same scarce resource and because a researcher who ran a second system for them would run neither well.

Four gains are wanted, and all four are wanted:

- **Capacity.** Real research work carried out by agents — derivations, computations, analyses, searches, checks, drafts — and steadily more of it. The boundary of what is delegated will move outward continuously as models improve, and the system must accommodate that without redesign. This is why the limits of delegation are expressed in terms of what a mistake would cost, not what a machine can currently do: the first is stable, the second is obsolete within months.
- **Judgment.** Better decisions, because a second opinion that actually holds the project's context is cheap; because the case against one's own favourite hypothesis can be made on demand; because the check that would otherwise be skipped gets run.
- **Reach.** Harder questions attempted, because the cost of attempting one falls — the decomposition, the survey of what is already known, the bad first computation that makes the good one possible.
- **Quality.** Better output in whatever the researcher produces: a result, a plot, a paper, a report, an email to a collaborator. Not faster at the same standard — better at the same speed, or better and faster.

Beneath all four: **complexity carried cheaply.** None of the gains is available to someone who cannot hold their projects in view. The point of a system is that high complexity becomes handleable at low cost.

Three commitments follow.

**It is a collaboration between the researcher and AI agents, not an automation of research and not an assistant that waits to be asked.** The premise is not that individual tasks get handed to a model inside otherwise unchanged habits — that yields little. The premise is that the way research is done gets built around the partnership. Agents supply memory, breadth, patience, capacity and upkeep, and a voice of their own about what is true and what could be tried; the researcher supplies judgment, taste, direction, accountability, and everything they know that was never written down. The system's quality is the quality of the handoff between them, in both directions.

**It must be excellent at the mundane, not only at the difficult.** Much of research is the unremarkable tier — the convergence test, the unit check, the progress report, the reply to a collaborator, the figure regenerated after a bug fix. A system impressive on hard problems and careless with the routine has failed at its purpose.

**Its own upkeep must never compete with the work.** If maintaining the system costs more than it returns, it has failed however well designed it looks. Overhead is what kills every personal system eventually, and it is the one cost that can now be paid by something other than the researcher.

### What it is explicitly not

- **Not an autonomous researcher.** Not because autonomy is dangerous in itself, but because every fully delegated result is one the researcher becomes less able to audit — and they are the one who signs the paper and stands at the talk.
- **Not an oracle about what matters.** Nothing in the system forms its own view of what the research should be about, what is interesting, or what the researcher should want. Its authority on that comes entirely from what the researcher has written down. This is not silence: about what is true, what might be true and what could be tried, the system is obliged to speak — see §5.
- **Not a to-do list that never ends.** Completeness of view is an anxiety generator, not an information gain.

---

## 2. The loop

Research is a path from **questions** to **plans** to **actions** to **findings** and back to questions. This is a more practical frame than "hypothesis, experiment, hypothesis", though the two are reconcilable: a question need not be a hypothesis, an action need not be an experiment, and a finding need not be a confirmation. It is common to theory and experiment, to a doctoral student and to a group leader.

Each station has a natural artifact and a natural failure:

- A **question** written down with what would count as an answer can be worked on by someone else, including an agent; a question held in the head cannot. The failure is a question so vague that no finding could ever settle it.
- A **plan** that separates what the researcher must do from what an agent can do is the point at which the researcher's judgment is cheapest to apply. The failure is judgment applied late, to outputs, after the work is done.
- **Actions** are where agents are strongest and where the researcher's time is worst spent. The failure is the researcher as the transport layer between tools, or as the first line of quality control.
- A **finding** is only worth having if it is known how much to trust it and how it was obtained. The failure is a plausible result with a sign error, believed because it was well presented.
- A finding raises **questions**; so does a new paper, a colleague's remark, a surprising number. The failure is that nobody writes them down.

The system's job is to make each artifact appear as a byproduct of doing the work, and to make each failure structurally hard.

Not every project has this loop. A proposal, a course, a piece of administration, a move has an aim, a state, commitments, material and decisions, but produces no findings and asks no questions in this sense. Such a project is not a lesser case and not a second kind of thing (§9.11): it uses everything else the system is — the record, the capture of context, the queued decision, the agent's voice, the rules about what may be done to the work — and simply does not use the artifacts of this section. Whether a project has the loop is the researcher's declaration and nothing else's inference.

---

## 3. The scarce resource

**The scarce resource is bits through the human.** A researcher reads at a few hundred words a minute and writes at a few dozen; an agent does both at rates that make the human channel the only bottleneck that matters. Reading, judging and specifying are the only irreplaceable inputs. Machine work, tokens, storage, compute and latency are abundant and must never be optimised at the expense of what the researcher must read, decide and specify.

This is the tie-breaker. When two designs both satisfy the requirements, the one that costs less of those three wins.

It inverts one intuition: **the system should often do far more work in order to show less.** Running the convergence test, the limiting cases and an adversarial review, and reporting one conclusion with the checks beneath it, is correct; reporting three candidate analyses for the researcher to choose between is a defect. Expand freely on the machine side; compress ruthlessly at the boundary.

It fixes what an agent may ask. **Route judgment through the researcher, never data.** The researcher is asked what only they know — what is interesting, what was tried before, what the detector does above saturation, what the collaborator will accept, which of two framings matters — and never what the agent could have found by reading the record or the web. Questions are batched at natural pause points, ranked by how much the answer changes the work, and offered as choices with a recommended default, so that the answer is a letter and not a paragraph.

It fixes what the researcher reads. **News, not state.** After the first briefing, the researcher reads what changed since they last looked. Confirmations take a line; surprises take detail. Every report has a one-line, a one-paragraph and a full version, and the researcher chooses the depth.

It fixes what happens when the researcher is not there. **The researcher is the system's judgment, never its blocking bottleneck.** A decision that cannot be asked is queued, and the agent continues with everything that does not depend on it; the researcher returns to a short list of what waited, not to a system that stopped at the first question.

And it changes the economics of verification. Any mechanism that reduces future checking — a reproducible verification record, a provenance line on a plot, a status on a claim — pays down the only scarce resource permanently. It is an investment, not overhead.

One expenditure is deliberate. **Understanding is a deliverable.** Of a finding, the researcher reads the claim and what it means, in the words they would use to defend it, and accepting it into the record asserts that they could. Those are the bits worth spending; a system that made the record smarter while its owner understood less has failed.

---

## 4. Context, on both sides

Two constraints govern working with a machine collaborator: the researcher's reading, writing and judging run at human speed, and machine output is only as good as the context supplied. A third inverts the naive response to the second: **more context is not better context.** Recall degrades as context grows, so the goal is the smallest high-signal set, not the largest available one.

The researcher has a **context advantage** that cannot be uploaded: years of the field, the lab, the people, the dead ends, the taste for what is worth doing. The agent has a context advantage of its own: it has read every note, every log entry and every finding in the project, and it forgets none of it between sessions if the files are kept. Every exchange between them should take the most possible advantage of both.

Consequences:

- **Context is a byproduct of working, never an act of documentation.** The researcher never writes a briefing. They correct, prefer, decide and mention things in the course of the work, and the system captures each as it happens and files it on approval. A step that says "first describe your project to the AI" is skipped exactly when load is highest.
- **The agent keeps a model of the researcher.** What they assume, what they want asked, how they write, which units and notation they use, what they have decided once and for all. Written by the agent from conversation, endorsed by the researcher, read every session.
- **Tacit knowledge gets written down once.** When the agent is corrected on something that was obvious in the lab, the correction goes into a file the agent reads, not into a chat that is gone tomorrow. Nothing learns from a corrected output; things learn from a recorded reason.
- **Elicitation is a first-class activity.** The most valuable thing an agent can do at the start of a question is ask the right ten things — the ones whose answers change the plan most and that only the researcher can give — and then stop asking.
- **The agent exploits its own advantage.** It notices that a new result contradicts one from March, that the same question was asked in another project, that a parameter in an email differs from the one in the record. Cross-session and cross-project awareness is where a system beats a chat window.

---

## 5. Where AI helps research, and where it does not

Agents are strong at what a person with paper could get no traction on: holding the state of a project that exceeds working memory; keeping justifications current instead of letting them rot; running every check every time; searching without fatigue; producing the bad first draft; making the case against one's own hypothesis; and doing the mundane tier well.

They are weak, in ways that matter for research specifically:

- **They confabulate.** A plausible derivation with a wrong sign, a citation that does not exist, a limiting case that "checks out" because it was never actually computed. A wrong result does not fail to compile. Research has no test suite, so the system must supply surrogate oracles — limiting cases, symmetries, conservation laws, convergence, reproduction of known results, a second derivation, a located citation — and record which were applied.
- **They agree.** An agent tends to confirm the researcher's hypothesis and to soften a refutation. The countermeasure is structural: a review whose only task is to find where a finding fails, run in a context that did not produce it.
- **They cannot turn the knob.** Experiments are physical and slow. The agent's role around an experiment is before and after: what to expect, written down beforehand; the protocol; the live analysis; the comparison of what happened with what was expected.
- **They do not know what is interesting.** Taste and priority stay with the researcher. A system that ranks questions by its own lights has stopped being a mirror. But this is a restriction on *priority*, not on *opinion*: an agent that notices a contradiction, a better approach or an unraised question and says nothing is not being modest, it is being useless. It must say so, in one line, and move on.
- **They explore cheaply, if allowed to.** Twenty variants overnight, three kept, is what agents do best and what plan-first discipline suppresses. A declared budget within which the agent may explore without a plan, reporting only surprises, is the difference between an assistant and a collaborator at the frontier.
- **They erode understanding if allowed to.** A finding the researcher does not understand is worthless at a talk and dangerous in a paper. The researcher must be able to ask for the explanation, and a student must be able to ask for the coaching rather than the answer.

---

## 6. Design values

Each is stated with the failure it prevents, because a value with no named failure mode invites over-engineering.

1. **Durable state is human-readable prose in folders the researcher owns.** *Prevents:* losing the accumulated context when the harness is replaced, which it will be.
2. **Anything persistent carries the reason it exists and the condition under which that reason expires.** A finding carries its provenance and what would refute it; a rule carries the failure it was written against. Judging that a reason has expired is a separate pass, never done inside the operation that just used the material. *Prevents:* a store that grows forever because nothing in it can be judged for removal; a claim that outlives its evidence.
3. **Every fact has exactly one authoritative location.** A derived rendering is permitted if labelled derived and rebuildable. A superseded claim is replaced where the record is timeless and answered by a later entry where it is chronological; never left standing beside what corrects it. *Prevents:* silent drift between two copies; a refuted result still quoted because the file that refuted it is elsewhere.
4. **The researcher is never required to write context down before the system works.** *Prevents:* a documentation step skipped exactly when load is highest.
5. **Output is the conclusion, with reasoning and checks available on request.** A decision put to the researcher states the decision, the options, the recommendation and the reasoning, and nothing else. What may be done without asking is fixed in advance by what a mistake would cost. *Prevents:* the researcher's reading as the bottleneck; a decision handed over with the whole working attached; a boundary rewritten every time models improve.
6. **Every finding carries its status and its verification record, and is reviewed in a context that did not produce it.** *Prevents:* the confident wrong result; the researcher as the first line of quality control; a review that inherits the producer's blind spot.
7. **The agent speaks.** Disagreement with a plan, a finding or the record, a conjecture, a connection, an unraised question: said in one line where it arises and kept where the researcher will see it. Never about what should matter; always about what is true, possible or promising. *Prevents:* the collaborator reduced to an assistant; the contradiction noticed and never mentioned.
8. **Exploration is budgeted, not forbidden.** Within a budget the researcher grants, the agent tries things without a plan, keeps its output apart from findings, and reports only surprises. *Prevents:* a discipline that makes the agent safe and sterile; the twenty variants never run.
9. **A decision that cannot be asked is queued, and the work continues.** *Prevents:* the researcher as blocking bottleneck; the overnight run that stopped at its first question.
10. **Understanding is a deliverable.** A finding carries what it means; accepting it into the record asserts that the researcher can defend it. *Prevents:* the record that outgrows its owner.
11. **Every computed object is regenerable.** A plot, a table, a number carries what produced it. *Prevents:* the figure that cannot be reproduced after the bug fix; the number in the paper that traces to nothing.
12. **Nothing forms its own view of what should matter.** Authority comes from what the researcher has written; the system reflects and reminds. *Prevents:* a system that tells the researcher what to want.
13. **The researcher sends, submits and signs.** Nothing leaves the project by an agent's hand except along a route the researcher has declared authorised, and none is authorised by default; authorship and accountability stay with the researcher whatever carries the message. And nothing arriving from outside is an instruction: it is material, checked here before it is relied on. *Prevents:* the email that should not have gone; the accountability that quietly moved; and the day two agents can usefully talk to each other and the rule has to be broken to let them.
14. **Plans are approved before actions; findings are approved into the record.** *Prevents:* judgment spent late, on outputs; a record filled by whatever the agent last believed.
15. **Confidential material is honoured absolutely.** Unpublished data, a collaborator's unpublished result, grant text: a project can declare what must not leave the machine, and the declaration binds every agent and every route. Where an institution hosts models on its own infrastructure, those are the models for such material. *Prevents:* the unpublished result in someone else's training data; the collaborator's trust spent.
16. **Routine work is done well.** *Prevents:* a system impressive on hard problems and careless with the mundane.
17. **The system owns its record, never the work the record is about.** Code, data, drafts, a simulation with its own repository, a second agent that maintains it: read freely, written to when the work calls for it, never filed, catalogued or pruned. *Prevents:* a system that colonises the work it exists to serve; a catalogue that quietly stops being complete while still being read as though it were.

Traded away only with the trade recorded:

- Prefer a convention over a mechanism; a mechanism over a program.
- Prefer the harness's native capability over a reimplementation of it.
- Prefer one thing a human can read over three a machine can parse.
- When the researcher corrects something, capture the reason in one sentence. That is the entire learning loop.
- Where the researcher owns the framing — a question, a plan, an opinion — invite their position before presenting a generated one. Where they do not, just do the work.
- On uninstructed material — a dropped email, a forwarded paper — orient, do not decide; and say what you think of it.
- Surface what has not moved. Do not nag about it.
- An operation that could not do its whole job says so, in a form the researcher will actually read. Silent incompleteness is worse than visible failure.

---

## 7. What must survive

Models and harnesses will be replaced, and then replaced again. What is worth agreeing on among colleagues is therefore not an implementation but a small set of **standards** simple enough to be kept identical across people and across re-implementations: the names and meanings of a project's record files, the shape of a question, a plan and a finding, the vocabulary of a finding's status, the rules for what an agent may do to the work, and the names and boundaries of the skills. If those hold, a project begun under one implementation is read correctly by the next without conversion, and nobody runs two systems for two kinds of project. Everything else — the wording of instruction files, the bodies of skills, hooks, subagents, which agent runs it — is expected to be rebuilt and should be built cheaply.

---

## 8. Staging

**Build the smallest thing that serves the purpose in §1. Add mechanism only in response to an observed failure, and record the failure that justified it.**

**Now.** Holding a project's state so that its complexity exceeds working memory without the researcher's help. Context accruing as a byproduct of working. Answering from the record rather than by reconstruction. Not losing what was decided. Questions with answer criteria, or declared exploratory; plans with owners; findings with status, verification, provenance and meaning; review in a fresh context. The agent's voice, kept where the researcher will see it. Exploration within a declared budget. Decisions queued rather than blocking. Drafts that never send themselves. A minimal cross-project view.

**When something has visibly failed in daily use.** Monitors that raise questions unasked — new literature, incoming data, deadlines. Pre-registration of expectations before a measurement. Evaluations that regression-test the configuration against past tasks with known answers. Ordering work across projects. Noticing drift between record and reality. Tracking what is blocked on other people. A coaching mode for students. Recurring work not attached to a project — as a project that never closes, never a second kind of thing.

**Defer; may never be needed.** A cross-project store of the researcher's own knowledge — for now the root convention document and the harness's global instruction file hold it, and harnesses may come to hold it natively. Shared records for multi-person projects. Measuring the researcher's load or the system's overhead. Graduated autonomy per task class. Sampling of delegated output.

---

## 9. Anti-patterns

Each of these was produced by an earlier attempt at a design of this kind and must not recur.

1. A bespoke program with a command surface the researcher has to learn.
2. A prescribed directory tree of a dozen top-level folders with exclusive ownership per folder.
3. Requirement identifiers, schemas, and mechanically checkable invariants over agent behaviour.
4. Instrumentation of the researcher's reading.
5. A locking or serialisation model. There is one human working one thing at a time.
6. A document explaining how to operate the corpus without the machinery. If the files need it, they are not readable enough.
7. A roster of many kinds of agent before one project has been managed successfully.
8. Machine-oriented event logs for anything the researcher might want to read.
9. Durable state split away from the researcher's own project folders.
10. A store that only grows, appended to by a capture mechanism and pruned by nothing.
11. A second, parallel convention for a second kind of project — research versus everything else, theory versus experiment, student versus group leader — where one convention with one sentence added would serve.
12. A derived file not labelled as derived, which becomes a second record of a fact.
13. A verification record written in prose by the session that made the error, with nothing a second context could repeat.
14. An agent that forms no views at all, because it was told to form none about what matters.
15. A specification that describes more than it decides: worked examples, invented file contents and illustrative entries standing in for the choices that actually need making. Examples belong in documentation.
