# System Flow Template (Feature / Pipeline)

> Use this template to design a single feature, workflow, or pipeline
> inside a larger system or OS using natural language only.

---

## 1. Flow Summary

- **Flow name**:
- **Short description** (one sentence):
- **Belongs to system / OS**:
- **Primary user story**:
  - As a (user type), I want to (goal), so that (value).

---

## 2. Inputs & Outputs

- **Inputs**:
  - User inputs:
  - System inputs (data, configuration, context):

- **Outputs**:
  - To the user:
  - To other systems or layers:

If helpful, describe using simple pseudo-types, e.g.:

- `Input`:
  - `UserRequest`
  - `CurrentContext`
- `Output`:
  - `FlowResult`
  - `LogEntry`

---

## 3. Step-by-Step Flow (Language-Only)

Describe the flow in clear steps.

1. Step 1:
2. Step 2:
3. Step 3:
4. Step 4:
5. Step 5:

- **Branching / conditions**:
  - What happens if input is invalid?
  - What if external systems fail?

---

## 4. Involved Layers / Modules

- **Which layers/modules of the OS are involved?**

Example structure:

- Interface layer:
- Context / Profile layer:
- Core logic / Reasoning layer:
- Memory / Storage layer:
- Governance / Safety layer:
- Execution / Integration layer:

- **Responsibility of each in this flow**:
  - Layer/module → What it does in this specific flow.

---

## 5. Edge Cases & Failure Modes

- **What can go wrong in this flow?**
  - Missing or malformed inputs:
  - Timeouts or external errors:
  - Conflicting commands or constraints:

- **How should the system respond?**
  - Retry?
  - Ask user for clarification?
  - Fail safe with a clear message?
  - Escalate to a human?

---

## 6. Metrics & Feedback

- **How do we know this flow works well?**
  - Quality:  
    (e.g. accuracy, relevance, user satisfaction)
  - Performance:  
    (e.g. latency, throughput)
  - Reliability:  
    (e.g. error rate, retry success rate)

- **Feedback signals**:
  - Which events or feedback are logged?
  - Is there explicit user rating or thumbs up/down?
  - How are these signals used to improve future runs?

---

## 7. Notes & Open Questions

- Implementation hints (optional):
- Dependencies or prerequisites:
- Open questions / decisions not made yet:
- Future enhancements for this flow:
