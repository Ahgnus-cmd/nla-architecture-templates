# Governance & Risk Checklist (NLA Designs)

> Use this as a quick sanity check for any architecture written in natural language.

---

## 1. Ownership & Responsibility

- [ ] Who owns this system/flow?
- [ ] Who is allowed to change the architecture?
- [ ] Who reviews high-impact changes?

---

## 2. Safety & Misuse

- [ ] What are the main harms or failures this system could cause?
- [ ] Are there any hard limits or guardrails described?
- [ ] Is there a clear “stop / shut down” path if something goes wrong?

---

## 3. Data & Privacy

- [ ] What data does this system touch?
- [ ] Is any of it sensitive (personal, financial, health, etc.)?
- [ ] Where is data stored, and for how long?

---

## 4. Transparency & Traceability

- [ ] Are important decisions logged somewhere?
- [ ] Can we reconstruct *why* a certain decision was made?
- [ ] Is there any audit log or trace described?

---

## 5. Maintenance & Evolution

- [ ] Who maintains this architecture over time?
- [ ] How often is it reviewed?
- [ ] Is there a safe way to roll back changes?

---

## 6. Alignment with Intent

- [ ] Does the current design still match the original intent/purpose?
- [ ] Have any new risks appeared since the first design?
- [ ] Do we need to update the architecture document now?
