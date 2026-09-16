# Walkthrough: one project, one loop

This page shows the system in use on one invented research project, from a question to a verified finding and the next question. Everything here is illustration; the spec decides, this page only shows. File contents are shortened, and the project is fictional though the physics is the kind done at Attoworld.

**The project.** A theorist supports an experimental colleague who measures, with field-resolved pump-probe spectroscopy, how the reflected probe waveform from a thin transparent-conducting-oxide film changes under a strong few-cycle pump. The theorist's job is to say whether a simple model explains what is measured.

---

## The folder

```
tco-reflection/
├── AGENTS.md            ← instruction file: points at the root documents, carries the standing rules
├── PROJECT.md           ← 800 words: aim, state, status, next steps, open questions; the two lines that make this a research project
├── PLAN.md              ← the current plan
├── decisions.md         ← why things were decided, append-only
├── facts.md             ← what the project currently relies on, with provenance
├── log.md               ← what happened, one line per operation
├── INDEX.md             ← where to look, and when
├── _WORKSPACE/          ← in-tray and bench: drop papers, emails, data descriptions
│                         here; new files with no home yet land here too
│   ├── candidates.md    ← what the agent learned, waiting for the next sweep
│   └── pending.md       ← what waits on you: queued decisions and proposals
├── _FILED/              ← the agent's filing cabinet; you don't edit this
└── research/            ← YOUR territory, named by you: questions, findings, drafts
    ├── questions/
    ├── findings/
    ├── drafts/
    ├── explore/         ← exploration output, within the budget PROJECT.md grants
    └── model/           ← code, its own git repository if you like
```

Two territories. The six record files, the instruction file, `_WORKSPACE/` and `_FILED/` are the **record**; the agent maintains them under the rules of the spec. Everything else is the **work**, yours, arranged however you like; the agent reads it freely and writes to it when you ask, but never files or prunes it. The record points at the work; it does not swallow it.

Two lines of `PROJECT.md` are what make this a research project, and they are the theorist's — no skill alters them:

```
Research project: yes.
Questions, findings and drafts: research/
```

They live there rather than in `AGENTS.md` because the instruction file's name differs by harness, and a project must be recognisable as a research project by whatever opens it next. `AGENTS.md` holds the pointers to the root documents, the standing rules about the two inbox notes, and anything local the theorist wants every session to know.

---

## Day 1 — a question

The theorist opens the project in their coding agent and says:

> The experimentalist's new data shows a phase shift of the reflected probe that grows with pump intensity. I want to know whether the plain Drude picture with a hot-electron collision rate explains it. Use `research-question`.

The skill reads `PROJECT.md` and `INDEX.md`, then asks four things — through the agent's question tool, as choices where it can:

1. What counts as "explains it"? *(offered: within the experimental error bars at every intensity / within 10 % / qualitatively — recommended: within error bars, since the experimentalist can supply them)*
2. Is the collision-rate model fitted or taken from the literature? *(fitted, with the literature value as a check / literature only)*
3. Is there a pump intensity above which the plain model is already known to fail? *(only the researcher knows this)*
4. Priority relative to the two open questions already in `PROJECT.md`?

The theorist answers with three letters and one sentence ("above about 200 GW/cm² I expect non-thermal effects, but that is a hunch"). The skill writes `research/questions/Q3-drude-phase-shift.md`:

```markdown
# Q3 — Does a Drude model with a hot-electron collision rate explain the measured probe phase shift?

**Question.** For the 300 nm film, is the intensity-dependent phase shift of the reflected probe
waveform reproduced by a Drude model with a temperature-dependent collision rate $\eta(T_e)$?

**Why it matters.** If yes, the experiment is a clean measurement of $\eta(T_e)$; if no, it is
evidence of non-thermal carrier dynamics, which is the more interesting outcome and changes the plan.

**What would count as an answer.** The fitted model reproduces the phase shift $\Delta\phi$ versus
pump–probe delay at all three pump intensities within the experimental error bars supplied by the
experimentalist; if it fails, the residual is quantified per intensity.

**What is already known.**
- Film thickness $300\ \mathrm{nm}$, $\lambda_\mathrm{ENZ} \approx 1240\ \mathrm{nm}$ (facts.md, from the sample sheet filed 2026-08-02).
- Literature value $\eta(T_e)$ from the reference in `_FILED/literature/…` (INDEX trigger: "when parameterising the collision rate").
- The researcher expects the model to fail above $\sim 200\ \mathrm{GW/cm^2}$ (stated 2026-09-11, a hunch, not a result).

**Constraints.** Error bars not yet received. Compute: laptop-scale. Confidentiality: the data is
unpublished — see the note in PROJECT.md.

**Priority.** Above Q1 and Q2 (researcher, 2026-09-11).
**Status.** open
**Raised by.** the researcher, from the experimentalist's data of 2026-09-09.
**Plan / findings.** —
```

One line goes to the candidates note (`_WORKSPACE/candidates.md`), and `log.md` gets:

```
- 2026-09-11: research-question wrote research/questions/Q3-drude-phase-shift.md
```

---

## Day 1 — a plan

> Plan Q3. Use `project-plan`.

`project-plan` first invites the theorist's own position ("How would you approach it?") and then writes `PLAN.md`:

```markdown
# Plan

**Serves.** Q3 (research/questions/Q3-drude-phase-shift.md)
**Approach.** Time-domain Drude model with $\eta(T_e)$, driven by the measured pump waveform,
propagated through the film by a transfer-matrix step; fit $\eta(T_e)$ to the lowest-intensity data,
predict the other two. Chosen over a Boltzmann model because it is a day's work and, if it fails,
the failure is itself the result.

**Steps.**
1. *(researcher)* Obtain error bars and the pump waveform from the experimentalist.
   Agent prepares: a one-paragraph email draft listing exactly what is needed and why.
   Done when: three CSV files with uncertainty columns are in `research/model/data/raw/`.
2. *(agent)* Implement the model in `research/model/`; reproduce Fig. 3 of the reference paper
   as a check. Done when: the reproduced figure matches within line width, regenerable by `make fig3`.
3. *(agent)* Fit $\eta(T_e)$ at the lowest intensity; predict the other two.
   Done when: $\Delta\phi(\tau)$ for all three intensities is plotted against data with error bars.
4. **Decision point.** If the highest intensity is outside error bars: stop, show the residual,
   ask whether to extend to a Boltzmann model (new plan) or to publish the discrepancy as is.

**Budget.** Two working days of agent time; none of the researcher's beyond step 1.
**Risks.** The pump waveform may be unavailable → use a Gaussian with the measured duration and
say so in the finding.
**Approved.** —
```

The theorist reads it, changes "within line width" to "within 5 %", and says "approved". `project-plan` writes `Approved. 2026-09-11` and a decision:

```markdown
- **2026-09-11**: Drude-first approach for Q3.
  - *Decision*: Try the Drude model with $\eta(T_e)$ before any Boltzmann treatment.
  - *Reasoning*: A day of work; a failure is itself informative.
  - *Revisit condition*: If step 4 shows a residual above the error bars at the highest intensity.
```

`PROJECT.md` next steps now read: "1. (you) get error bars and pump waveform from the experimentalist — draft email is in `research/drafts/`. 2. (agent) model + Fig. 3 reproduction. …"

---

## Day 2 — actions

The theorist sends the email (the agent drafted it; the theorist sends it), receives the files, drops them into `research/model/data/raw/`, and says:

> Do steps 2 and 3 of the plan.

`research-act` works for a while. It writes code, reproduces Fig. 3, fits, predicts, and produces figures, each with a provenance line beside it:

```
fig_phase_shift_vs_delay.png — generated 2026-09-12 by research/model/plot_phase.py at commit 3f2a9c1
  from data/raw/run_{1,2,3}.csv with params.yaml (eta0=…, T_ref=…)
```

It runs the checks that apply to a computed result — convergence in time step (halved twice, change below 0.3 %), energy bookkeeping in the propagation, Fig. 3 reproduction, regeneration from a clean checkout — and writes `research/findings/F7-drude-phase-shift.md`:

```markdown
# F7 — Drude + $\eta(T_e)$ reproduces the probe phase shift at 50 and 120 GW/cm², not at 250

**Claim.** For the 300 nm film, a Drude model with a fitted $\eta(T_e)$ reproduces
$\Delta\phi(\tau)$ within error bars at $50$ and $120\ \mathrm{GW/cm^2}$, and underestimates the
peak shift by $0.12 \pm 0.03\ \mathrm{rad}$ at $250\ \mathrm{GW/cm^2}$.

**What it means.** Up to about 120 GW/cm² the electrons heat, collide more often, and the
film's reflection phase follows the hot-electron collision rate alone — the measurement is a clean
thermometer for $\eta(T_e)$. At 250 GW/cm² something the thermal picture does not contain adds a
tenth of a radian: either the distribution is no longer thermal on the probe's timescale, or a
parameter we hold fixed is not.

**Kind of evidence.** computed
**Method.** … (six sentences)
**Provenance.** research/model at commit 3f2a9c1; data/raw/run_{1,2,3}.csv (received 2026-09-12);
params.yaml; `make all` regenerates every figure.

**Verification record.**
- convergence in $\Delta t$: $\Delta t \to \Delta t/4$ changes peak $\Delta\phi$ by 0.3 % — pass
- energy bookkeeping: absorbed energy equals field work to 0.1 % — pass
- reproduction of Fig. 3 of [ref, p. 4]: within 4 % — pass (`make fig3`)
- regeneration from clean checkout: pass
- not run: comparison with an independent implementation (none exists yet)

**Status.** tentative
**Review record.** —
**Questions raised.** What accounts for the residual at 250 GW/cm²: non-thermal distribution,
a change in effective mass, or the pump waveform assumption?
**Supersedes.** —
```

The theorist reads three lines — the claim, what it means, and the "not run" line. That is all that was required of them, and the middle one is the one worth their time. The candidates note gets one line (a question was raised), and `log.md` one; the finding itself waits for review, which the reply says.

---

## Day 2 — review

> Review F7. Use `research-review`.

Because `research-review` must not run in the session that produced the finding, the agent hands it to a subagent with a clean context (or, on a harness without subagents, the theorist runs it in a fresh session). The reviewer reproduces every check — it actually runs `make all` and `make fig3`, it re-halves the time step — and then attacks: it tries a pump waveform with 20 % longer duration and finds the residual at 250 GW/cm² survives; it checks the claim against `facts.md` and finds no contradiction. It writes into F7:

```markdown
**Status.** verified
**Review record.** 2026-09-12, subagent of the producing session — the weakest of the four kinds
of independence, and the one to improve on if this claim ever carries weight. All four recorded
checks reproduced.
Additional: residual at 250 GW/cm² robust to ±20 % pump duration. Claim does not exceed evidence.
```

and appends to the candidates note: "F7 verified — propose for facts.md".

---

## Day 2 — the record catches up

> Sweep.

`project-sweep` reads the candidates note and proposes, tier by tier, through the question tool:

- **facts.md** (recommended): the claim of F7, provenance `research/findings/F7-drude-phase-shift.md` reviewed by a subagent of the producing session, retirement condition "a Boltzmann treatment or new data changes the residual at 250 GW/cm²".
- **PROJECT.md** (recommended): open question "What accounts for the 0.12 rad residual at 250 GW/cm²?"; status updated; Q3 off the open list.
- **pending.md**: one proposal (thickness dependence of $\eta$) — keep or dismiss? The theorist keeps it.
- **decisions.md** (your call): none this time.

The theorist approves with one click. The sweep writes, clears the candidates lines it acted on — here, all of them — commits the record by path, and logs:

```
- 2026-09-12: sweep: F7 → facts.md; new open question on the 250 GW/cm² residual; Q3 answered.
```

Q3's own document is closed by `research-question`, the only skill that writes it: the status becomes `answered` and names F7 as the finding that met the criterion. The record's open-question list and the question document say the same thing, each in its own place.

The revisit condition of the 2026-09-11 decision has now been met. The next time `project-plan` runs, it will say so and ask whether to plan a Boltzmann model. That is the loop closing: a finding raised a question, the question is on the page, and the decision that would have been forgotten is on the table.

---

## Day 2, evening — the agent speaks

While fitting, `research-act` noticed something it was not asked about, and said so in one line at the end of its reply:

> One thing you did not ask: the fitted $\eta(T_e)$ is 30 % above the literature value in `facts.md`, and the literature film was 100 nm. If $\eta$ depends on thickness, the residual at 250 GW/cm² may be a thickness effect, not a non-thermal one. Recorded as a proposal.

The line also went into `_WORKSPACE/pending.md`:

```
- [proposal] 2026-09-12: fitted η(T_e) is 30 % above the literature value (100 nm film); a thickness
  dependence of η would explain the 250 GW/cm² residual without non-thermal dynamics. Worth a question?
```

The theorist owes this a glance, nothing more. A week later they will pick it up with `research-question`; today they ignore it.

---

## Day 2, night — exploration while nobody is watching

`PROJECT.md` grants an exploration budget: four hours of laptop compute per night, in `research/explore/`. A scheduled run invokes `research-act` on the exploratory question Q4 ("Is there anything in the residual's dependence on delay that a Drude model cannot produce?"). Overnight it runs thirty parameter sweeps. It writes nothing to the record and no finding document. In the morning `_WORKSPACE/pending.md` holds one paragraph:

```
- [proposal] 2026-09-13, exploration Q4, 3.6 h used: 29 of 30 sweeps are Drude-like. One is not:
  with a two-component η the residual's delay dependence reproduces to within error bars, but only
  if the second component has a 40 fs onset. Reproducible: research/explore/2026-09-13/sweep_17/.
  Not a finding until planned and checked.
```

Also in the note, a queued decision: the run wanted to extend one sweep beyond the budget and could not ask. The theorist answers "no" in place, and the next session acts on it.

---

## Day 3 — text that leaves the project

> Draft a progress note to the experimentalist on Q3. Use `research-write`.

The skill reads `facts.md` and F7, and writes `research/drafts/2026-09-13-to-ben.md`, short, with the verified claim stated plainly and the residual stated as verified but unexplained. It does not send it. It escalates one thing: "You asked me to say we will have the Boltzmann result by Friday. That is a commitment on your behalf and no plan exists for it. Include it?" The theorist says no, reads the draft, and sends it themselves.

---

## What the theorist actually did

Over three days: stated a question and answered four short prompts; changed one number in a plan and approved it; sent one email; dropped three files in a folder; read three lines of a finding — the claim, what it means, and the checks not run; glanced at two proposals and answered one queued decision with a word; clicked approve on a sweep; declined one commitment; sent one note. Everything else was done by the agent, checked by a second agent, and entered the record only with the theorist's approval.

---

## A week later: what "news, not state" looks like

> What changed since Monday?

`project-ask` reads `log.md` forward from Monday and answers in four lines: Q3 answered (F7, verified); one new open question; one revisit condition met and waiting for a decision; nothing filed. If the theorist wants the full picture, they ask; they are not handed it.

---

## The same loop for an experimentalist

Swap the roles. The experimentalist's question is "Does the phase shift depend on the film thickness?"; the plan's step 1 is owned by them ("measure 100 nm and 500 nm films at 120 GW/cm²") and the agent prepares a parameter table and a note of what the theory predicts *before* the measurement; step 2 is owned by the agent ("rerun the analysis pipeline on the new raw data; inject a synthetic signal to confirm the pipeline recovers it"); the finding's kind of evidence is `measured`, its provenance names the instrument and the run, and its verification record includes the pipeline rerun and the synthetic-signal test. Nothing else in the system changes.

---

## The same loop for a student and a supervisor

The student runs their own system on their own project folder. The supervisor runs theirs. What passes between them is documents: the student's finding document, with its verification record and status, is what the supervisor reads; the supervisor's comments go into the student's inbox and are filed. Neither edits the other's record. When the student asks their agent "explain the derivation in F4 to me step by step", they get coaching; the system does not decide for them that they should understand it — they ask.
