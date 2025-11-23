# Governance & Risk Checklist for NLA-Based Systems

> Use this checklist as a quick governance and risk review
> for any architecture designed in natural language.

---

## 1. Ownership & Responsibility

- [ ] A clear **owner** for this system/flow is defined.
- [ ] It is clear **who can change the architecture** (role or team).
- [ ] High-impact changes require **review or approval** (by whom?).

---

## 2. Scope & Impact

- [ ] The **intended scope** of the system/flow is documented.
- [ ] Potential **impacted users/stakeholders** are identified.
- [ ] There is an understanding of **where this system can cause harm** if misused or misconfigured.

---

## 3. Safety & Misuse

- [ ] Main **failure modes or harms** are explicitly listed  
      (technical, ethical, financial, security, reputation).
- [ ] There are **hard limits / guardrails** defined  
      (what the system must never do).
- [ ] There is a **“stop / shut down” path** if something goes wrong.
- [ ] Known **misuse scenarios** have a defined response  
      (e.g. refusal, escalation, warning).

---

## 4. Data & Privacy

- [ ] Types of data used by this system are documented  
      (personal, financial, health, internal, public, etc.).
- [ ] Sensitive data (if any) is clearly identified and minimized.
- [ ] Data storage locations and retention duration are defined.
- [ ] Access control is described (who/what can see which data).
- [ ] If required, compliance frameworks are considered  
      (e.g. GDPR, company internal policies).

---

## 5. Transparency & Traceability

- [ ] Important decisions and actions are **logged**.
- [ ] There is a way to **reconstruct why** a decision was made  
      (inputs, versions, configuration).
- [ ] Users or admins can see:
  - [ ] what version of logic or policy was used
  - [ ] which data sources were involved

---

## 6. Maintenance & Evolution

- [ ] It is clear **who maintains** this system over time.
- [ ] There is a plan for **regular review** of:
  - architecture,
  - data sources,
  - safety rules.
- [ ] There is a **safe rollback strategy** if a change causes problems.
- [ ] Automation / adaptation boundaries are documented  
      (what can change itself vs. what needs human approval).

---

## 7. Alignment with Intent

- [ ] The current design is still aligned with the **original intent/purpose**.
- [ ] Any **scope creep** or hidden expansion is acknowledged.
- [ ] New risks discovered after deployment are recorded.
- [ ] There is a clear trigger/condition to **update the architecture document**.

---

## 8. Communication

- [ ] Key stakeholders understand:
  - what the system does,
  - what it does **not** do,
  - how to escalate issues.
- [ ] User-facing messages are clear about limitations  
      (e.g. “this is assistance, not legal advice”).
- [ ] There is a channel for users or operators to report problems.

---

You can duplicate this checklist per system/flow
and keep it alongside your architecture documents.
