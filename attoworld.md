# attoworld.md — local resources at Attoworld

A **site file**: the answers, for one institution, to questions the standard asks but cannot answer. What shared code exists, which model may see confidential material, what compute is available and what a run on it must record. Everything here is local to Attoworld and to the Max Planck Institute of Quantum Optics; a researcher elsewhere replaces it with their own or has none.

**How it is read.** Not every session. `CONVENTION.md` carries one line naming this file and the condition under which to open it, in the shape `INDEX.md` uses, so that the cost in context is one line and the content is read only when a task reaches for it. The line to add at install:

> For shared group code, an institution-hosted model, or compute beyond this machine, read `<root>/attoworld.md`.

**What it never holds.** API keys, tokens, passwords, account names, paths that identify a person's home directory. Keys live where the harness keeps secrets, never in the record and never in this file.

**How it is extended.** One entry per resource: what it is, where it lives, what an agent may do with it unasked, and what it must leave to the researcher. Keep an entry to a few lines. A subgroup with a resource worth naming adds it by pull request.

---

## Shared code

| Repository | What it is |
|---|---|
| https://github.com/NickKarpowicz/Attoworld | Attoworld's shared Python code for calculations, data analysis and plotting. |
| https://github.com/Data-Science-Group-Attoworld | Repositories of the data science group. |

Neither is required, and naming them here installs nothing.

**For the agent.** Before writing new analysis or plotting code, check whether one of these already does it, and say what you found. Take a library's interface from the source or the documentation of the version actually present, never from memory: a plausible function name that does not exist produces a number that reaches a finding. Adding a dependency to the work, or installing one, is proposed to the researcher with what it changes, never done silently.

## Institution-hosted inference (GWDG)

GWDG's SAIA offers OpenAI-compatible endpoints at `https://chat-ai.academiccloud.de/v1` with a bearer token; the key is obtained through the KISSKI booking form with an Academic Cloud account. Documentation: https://docs.hpc.gwdg.de/services/ai-services/saia/index.html

**Internal models only.** SAIA serves open-weight models hosted at GWDG (internal) and non open-weight models proxied to Microsoft Azure (external). Only the internal ones keep material on institutional infrastructure. An external model is a third party, and material that a confidentiality note in `PROJECT.md` covers must not reach one.

**For the agent.** A confidentiality note may name an internal SAIA model as the only model permitted for the material it covers; where it does, that is where that material is worked on and nowhere else. Absent such a note, calling SAIA for bulk work of the project's own is ordinary work. The worst outcome of a mistake here is a spent quota, not a leak, provided the model is internal.

## Compute (MPCDF)

The Max Planck Computing and Data Facility hosts the compute available beyond the researcher's own machine. Job submission is by Slurm.

**Access.** Nothing here is particular to Attoworld. Every scientist employed at the Max Planck Institute of Quantum Optics may, on request, obtain access to the MPCDF systems and services; it is what affiliation with the Max Planck Society provides by default, not a group resource. The services are described at https://www.mpcdf.mpg.de/services/overview

**For the agent: you do not submit unasked.** A batch job runs under the researcher's account and spends an allocation held in their name, so submitting, resubmitting or cancelling one is an action taken on their behalf: it needs the researcher's approval, given per job in conversation or per project in `PROJECT.md`, and none is given by default. Without it, a run on MPCDF is a plan step owned by the researcher, and the agent's work is what comes before and after it: the job script, the inputs, the parameter table, the expected cost, and the note of what the run is meant to settle; then the analysis of what came back. Watching a running job, reading its status and fetching its output are ordinary work and need no approval. Do not add a helper that submits or cancels on its own.

**Provenance of a cluster run.** §F requires every computed object to carry the script, the data, the code version, the parameters and the date. A run here adds: the system, the job id, the environment or modules loaded, and where the output lives. Recorded when the run is reported back or its output fetched.

**Confidential material** does not go to shared infrastructure unless the note in `PROJECT.md` says it may.

**Still open.** Which MPCDF systems a given subgroup actually uses, where its project data lives, and any convention for job scripts are not recorded here, because they vary by subgroup and none has been written down. A subgroup with such a convention adds it as an entry, by pull request.
