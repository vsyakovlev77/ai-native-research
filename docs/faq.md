# Questions people ask

**Half my projects are not research. Does this work for them?**
Yes, and they are not a second kind of thing, nor an afterthought: this is a project system that research extends, and the extension is optional. Every project gets the same record files, the same two intake routes and the same seven record skills — ask, file, plan, sweep, establish, revise, steward. What a research project adds is one line in `PROJECT.md` saying so, and with it the four `research-*` skills, which bring question documents, verification records, finding statuses and drafts measured against them. In a project without that line those four stand aside, in one sentence, and the agent simply does what you asked in the same turn — declining is the skill stepping back, not your request being refused. Everything that protects you is in the working-tree rules, which bind every agent working in your files whether a skill is running or not: raw data untouched, provenance on every computed object, sources opened before they are cited, and nothing sent that you did not authorise.

**Why six files? A README would do.**
Because each answers a different question and is read at a different time. `PROJECT.md`: what is this and where does it stand — read every session, 800 words, and what no longer fits moves to the file that owns it rather than being cut. `PLAN.md`: what are we doing next and who does it — read when planning or acting. `facts.md`: what do we rely on — read when reasoning. `decisions.md`: why did we choose this — read when a choice is questioned. `log.md`: what happened when — read forward from a date. `INDEX.md`: where is the thing — read when looking. Merging them means reading all of them to answer any of them, which spends the only scarce resource.

**Why can't I edit `_FILED/`?**
Nothing stops you — it is a promise, not a lock. But `INDEX.md` promises that everything under `_FILED/` is indexed and reachable by a trigger, and a file you add, rename, move or delete by hand breaks that promise silently: no operation reconciles the index against the tree, so a stale entry points at nothing and a hand-added file is invisible to every trigger that should have found it. Put material into `_WORKSPACE/` and let the agent file it; ask for a revision when something should go. Everything outside `_FILED/` and the six files is yours to arrange, including with other tools and other agents.

**My code lives in its own git repository inside the project. Is that a problem?**
No; it is the normal case. The record points at it and never files it. If the code has its own agent instruction file, that one supplements the project's; it does not replace it. If the code has its own agent harness maintaining it, fine — the research skills read the code and, when you ask, write to it, but nothing in the record claims to catalogue it.

**My group has its own code, its own cluster, its own model service. Do I have to use them, and where do they go?**

Nothing in the standard requires any of them, and installing the system pulls no code and runs no installer. If you do use them, they go in one site file at your root, which `CONVENTION.md` names in a single line saying when to read it, so that an agent learns of them at the moment a task reaches for one and not in every session. `attoworld.md` in this repository is a real one and doubles as the example. If your group has none, you have no site file and nothing changes.

**Do I have to write a plan for everything?**
No, and the test is not how many moves a request has. If your agent can carry it to a stopping point in this session, it is a direct request, and it plans its own moves inside it — where your harness puts that plan to you before executing, that is your approval and the system does not ask for a second one. `PLAN.md` is for what one session cannot finish: work spanning several, work with steps you own — a measurement, a conversation, a decision. It is also for work a session could finish whose cost you would want weighed first: restructuring code, a long run, a shared allocation, anything reaching outside your machine. When it is unclear how long something will take, it is a direct request; when it is unclear what it will cost, the agent asks.

**Do I need git?**
The record commits itself on sweep if the project is a repository, and recovery from a bad write is then trivial. Findings need it for a second reason: a finding's provenance names the version of the code that produced it, so without a repository it names a version nobody can recover. A repository whose code is untracked or uncommitted is the same defect wearing a repository's clothes, and `research-act` treats it as one: it escalates before the first finding it would produce on such code, because it may not commit your work itself and it is your commit that makes the provenance recoverable. `project-establish` says the same when it adopts a folder that is under no version control and offers to initialise one — it never does so without your approval, it writes the ignore rules that decide what your `CONVENTION.md` says to track, and it makes no commit in an adopted folder, since that first commit would be a commit of files it did not write. What it commits later, at a sweep, is only the record files it wrote itself, staged and committed by path, which leaves anything you had staged still staged. Without git the system still works and you lose both. Use git.

**The agent wrote a finding and I do not believe it.**
Say so, with the reason, in one sentence. The reason goes into the candidates note and, on sweep, into the record. Then run `research-review` on the finding in a fresh session and let the review decide; a review that cannot reproduce a check does not accept it. If you were right, the finding is refuted and stays refuted in its own document, so nobody repeats the error.

**Can two people share one project?**
Share the work, not the record. A shared git repository of code, data and documents is fine. Each person runs their own record on their own copy of the project folder, and the finding documents, plans and drafts are what pass between them. A shared record is deferred until someone actually needs one; see the spec §O.

**I am a group leader with fifteen projects. What do I get?**
`project-steward` for a one-line view of each; `project-ask` in any of them for "what changed since the last group meeting"; `research-write` for the report that has to leave; and a student's finding document, with its verification record and status, as the thing you read instead of a slide. Ordering work across projects is deliberately not done for you.

**I am a student. What is different for me?**
Nothing in the system. Two habits: ask for the explanation, not just the result ("walk me through the derivation in F4"), and put your supervisor's comments into `_WORKSPACE/` so they get filed and their reasons recorded. Your understanding is a deliverable; the system will not decide for you that you need it.

**What if my agent has no hooks?**
Then the rules the spec says are gated — nothing sent without your authorisation, never touch raw data — hold by instruction alone. The build instruction asks the agent to tell you which rules are gated on your harness. Knowing that is enough; agents follow instruction files well, and nothing goes out that you were not shown first.

**What survives when I switch agents next year?**
Everything §M of the spec calls the standard: the record files and their meaning, the shapes of a question, a plan and a finding, the status vocabulary, the working-tree rules, the skill names and their boundaries. Re-implementing means giving the spec to the new agent. A project written under the old implementation must be readable by the new one without conversion; that is the test.

**Why are questions and findings in my folder and not in the record?**
Because they are the work. The record holds the claim of a verified finding, with the document as provenance; the document itself, with its evidence, method and checks, is yours, arranged as you like, and the record only points at the folder. This keeps the record small and keeps you free to organise findings by topic, by paper, by year, or however your field does it.

**Why must the review run in a different context?**
Because the session that made a mistake will re-make it when asked to check. A fresh context with only the finding document and the evidence in front of it does not inherit the blind spot. On a harness with subagents this costs nothing; on one without, run the review in a new session. Your own approval is not a review either, however sure you are: a review is the reproduction of the checks in the record, and saying yes is a different act. It has its own route — accept the `tentative` claim at a sweep, and the record names your judgment as the check and the review that has not happened as what would retire the fact. That way `verified` never means "the boss said yes".

**The review says it verified my simulation. Did it actually run it?**
Check, once, that your reviewing context can. A review reproduces the recorded checks, and for a computed finding that means running the code — so the context doing it needs a shell and your project's runtime, not reading tools alone. A reviewer scoped down to reading files will produce a review that looks exactly like a real one, because it can read your test file and describe what it would do; it can even catch an analytical mistake, which is what reading is good for. What it cannot do is run the test, and nothing in the document it writes will say so. This is not hypothetical: it is the defect that took longest to find in the first system built to this spec. Read the tool list of whatever your build uses for `research-review` before you rely on a single `verified`. A check the reviewing context could not attempt is neither reproduced nor failed: `verified` is not available on it, and the finding stays `tentative` until a context that can attempt it does.

**What is "tentative"? Can I use tentative results?**
Tentative means produced and self-checked, not independently reviewed. There are four statuses and no more: `tentative`, `verified`, `refuted`, `superseded`. If that feels coarse — a result checked against the literature but not reproduced is not quite the same as one nobody has looked at — the nuance lives in the finding's verification record, which names every check that passed and every one that was not run, rather than in a fifth word everyone would have to learn. You can use them, quote them in a progress report labelled as tentative, and plan on them. They do not enter `facts.md` unless you accept them explicitly, in which case the record says the check was your judgment.

**I told it to write something into `facts.md` and it wrote a line in the candidates note instead.**
It is not refusing you. Your word is what the record is made of; the sweep is the route by which it gets there with the destination shown and the wording yours to approve, so that nothing arrives in `facts.md` that you did not see arrive. What it should do — and what to expect from a build that got this right — is write the candidates line and offer the sweep in the same turn, so the route costs you one approval rather than one session. An instruction to record something does not move the write somewhere else, however plainly it is put.

**How specific does an authorised route have to be?**
Specific enough that its silence is not read as permission. A route names the destination, the purpose, and the kinds of material it covers; where your project holds material the route must not carry and no confidentiality note names it, the route says so. "Literature search services may receive search queries" excludes nothing by itself — write what they receive and what they do not, and the route does the work a confidentiality note would otherwise have to.

**The agent disagrees with me.**
Good. It is obliged to say so, in one line with its reason, and then to do what you asked. The disagreement goes into the pending note so it survives the session; you may ignore it. It is not allowed to have views about what you should want or what matters — only about what is true, what might be true, and what could be tried. If it is wrong, say why once; that becomes a recorded correction.

**Can it work while I am away?**
Yes. A decision it cannot put to you is queued in `_WORKSPACE/pending.md` and it continues with every step that does not depend on the answer. Three operations are the exception and simply decline until you are back: sweeping, revising and establishing a project, because none of them can do anything at all before you have approved or answered something. On a harness with scheduled runs it can also explore overnight, within a budget you granted in `PROJECT.md`, and leave you a paragraph of surprises in the morning. You return to a short list of what waited, not to a run that stopped at its first question.

**What is the exploration budget?**
Permission to try things without a plan: so much compute, so much wall time, in a folder set aside for it. Exploration produces no findings and touches no record file; it produces proposals. Anything interesting becomes a finding only after you turn it into a question and a plan step reproduces it with proper checks. No budget means no exploration.

**Why does it keep explaining findings to me?**
Because understanding is a deliverable. Of a finding you read the claim, what it means in the words you would use at a talk, and which checks were not run. Accepting a claim into `facts.md` means you could defend it. If you cannot, ask, and it explains as far as you want; it will not just redo the work.

**The agent asks too many questions.**
Edit the *Escalates* lines in §H of your `SPEC.md` and ask your agent to rebuild the skill they govern — the skills are built from the spec, not reading it as they run, so an edit alone does not reach them. They are the exhaustive list of what a skill routes to you. The boundary is meant to be set by what a mistake would cost you, not by what the agent can do — so it should not need changing when the model improves, only when you find a question was never yours to answer.

**Where are the examples in the spec?**
Deliberately absent. A spec that shows instead of deciding gets copied instead of read. Examples are in the [walkthrough](walkthrough.md).

**How do I extend it?**
Add a project-local skill for a recurring procedure — the agent will propose one when it notices the recurrence; you approve. Add a check to the taxonomy in §D of your `SPEC.md` if your field has one it lacks, and ask for the research skills to be rebuilt so the addition reaches them. Add a monitor, a pre-registration convention or an evaluation suite when you have observed the failure that justifies it, and record the failure. Do not add a second convention for a second kind of project; add a sentence to the first.
