# Personal Learning OS — Example NLA Architecture

> Example OS-level architecture for an individual learner.
> Focus: goals → curriculum → practice → reflection.

---

## 1. Overview

- **System name**: Personal Learning OS
- **One-line description**:  
  An AI-native operating system that helps learners turn vague goals into structured study plans, daily practice, and measurable progress.

- **Primary purpose / mission**:  
  Make self-directed learning predictable and sustainable by managing goals, content, practice sessions, and reflection in one place.

- **Target users**:
  - Students learning in parallel with school/university
  - Working professionals reskilling/upskilling
  - Self-taught learners building long-term skills

- **Core domain(s)**:
  - Goal definition and skill breakdown
  - Curriculum design and content curation
  - Practice scheduling and spaced repetition
  - Progress tracking and reflection

- **Scope (v0.1)**:
  - Includes:
    - Clear learning goal definition
    - Simple skill tree and roadmap generation
    - Weekly learning plan and daily sessions
    - Basic progress logging and reflection prompts
  - Excludes:
    - Full LMS features (grading, cohorts, admin tools)
    - Social/community features
    - Formal credentialing/badges

---

## 2. Problem & Context

- **What problem does this system solve?**

  Many learners:
  - Set goals like “learn data science”, “improve English”, “study for exam”
  - Get lost in content overload (courses, videos, articles)
  - Fail to maintain consistent practice or see progress clearly

- **Why OS-level / multi-layer?**

  - Learning spans months or years, not days.
  - It involves:
    - goal setting
    - planning
    - practice
    - feedback
    - reflection
  - A single to-do list or note app is not enough to manage these dynamics.

- **Key constraints**:

  - Must remain simple enough not to overwhelm early users.
  - Should not pretend to be a formal teacher or give fake credentials.
  - Progress indicators must be honest; no “fake progress bars”.

- **Assumptions**:

  - Learner can invest a small but regular time budget (e.g., 30–60 minutes/day).
  - Basic logging (what they studied, for how long) is possible.
  - System can access some content sources (links, course lists, etc.) or accept manual entry.

---

## 3. Layer Stack (Language-First)

| Layer ID | Layer Name                     | Role in the system                                                                      | Main inputs                                       | Main outputs                                                           |
|---------:|--------------------------------|------------------------------------------------------------------------------------------|---------------------------------------------------|------------------------------------------------------------------------|
| L1       | Goal & Context Capture         | Captures learner goals, constraints, prior knowledge, and time budget                    | Learner answers, background info                  | Structured LearningProfile                                             |
| L2       | Skill Map & Roadmap Layer      | Breaks high-level goals into skills, milestones, and a rough roadmap                     | LearningProfile, domain templates                 | SkillTree, MilestoneRoadmap                                            |
| L3       | Content & Activity Planner     | Maps skills to concrete activities (lessons, exercises, projects)                        | SkillTree, available resources, learner preferences| WeeklyPlan, DailyActivities                                            |
| L4       | Session Guide & Tutor Layer    | Guides daily sessions: what to do today, how, and with what focus                        | DailyActivities, LearningProfile                  | Session scripts, prompts, questions, mini-explanations                 |
| L5       | Progress & Reflection Layer    | Captures what actually happened, perceived difficulty, and reflection notes              | Session logs, learner feedback                     | ProgressLog, updated skill estimates                                   |
| L6       | Adaptation & Difficulty Engine | Adjusts plan difficulty, pacing, and content mix based on progress and feedback          | ProgressLog, skill estimates                      | Updated WeeklyPlan / DailyActivities                                   |
| L7       | Safety & Well-being Layer      | Ensures learning load is healthy, avoids burnout, and reminds learners to rest/adjust    | Time budget, stress indicators, reflection notes  | Warnings, rest suggestions, load adjustments                           |

---

## 4. Core Flows (Data, Knowledge, Control)

### 4.1 Data / Knowledge Flow

- **Main data sources**:

  - Learner-provided:
    - goals
    - prior experience
    - available time
  - Content:
    - links to courses, videos, books
    - recommendations selected by the learner or suggested by the system
  - Ongoing logs:
    - completed sessions
    - perceived difficulty
    - quiz results (if any)

- **How information moves between layers**:

  1. L1 builds a structured **LearningProfile**.
  2. L2 constructs a **SkillTree** and milestones from the profile.
  3. L3 converts the SkillTree into a calendar-like plan (weeks/days).
  4. L4 uses the plan to guide each session.
  5. L5 records what actually happened and how the learner felt.
  6. L6 adjusts the plan based on performance + feedback.
  7. L7 overlays limits and well-being checks.

- **Where knowledge is stored / updated**:

  - LearningProfile and SkillTree persist across weeks.
  - ProgressLog accumulates over time and is summarized into:
    - “Current level per skill”
    - “Time invested”
    - “Consistency over weeks”

### 4.2 Control / Orchestration Flow

- **Who makes decisions?**

  - L3: suggests schedules and activities.
  - L6: modifies plan in response to performance.
  - L7: can suggest load reduction when needed.
  - Learner: always controls final goals, time budgets, and acceptance of changes.

- **How requests move through the system**:

  - New goal:
    `Learner → L1 → L2 → L3 → L4 → (first sessions)`
  - Daily use:
    `Learner opens app → L4 (today’s session) → L5 (log) → L6/L7 updates → future sessions`

- **Feedback loops**:

  - Progress and reflections loop back into:
    - L2 (skill estimates)
    - L3 (plan)
    - L6 (difficulty, pacing)
    - L7 (well-being)

---

## 5. Feedback Loops & Adaptation

- **Where does the system learn or adapt?**

  - From:
    - session completion rates
    - self-reported difficulty
    - quiz or checkpoint results
  - L6 uses this to:
    - slow down or speed up
    - add more practice or more theory
    - adjust review frequency

- **Signals that trigger updates**:

  - Multiple missed sessions → less aggressive plan, more review.
  - Repeated “too easy” → harder tasks, faster progression.
  - Repeated “too hard” → more scaffolding, simpler tasks, extra explanations.

- **What cannot be changed automatically?**

  - The core goal (e.g., “learn programming”) — only learner can change.
  - Maximum weekly time budget.
  - Any mental health boundaries if explicitly set by learner.

---

## 6. Interfaces

### 6.1 External Interfaces

- **Interfaces to learners**:

  - Initial goal-setting flow:
    - “What do you want to learn?”
    - “By when?”, “Why?”, “How much time per week?”
  - Daily session guide:
    - “Today’s focus is…”
    - “Here’s what we’ll do in the next 30–45 minutes.”
  - Weekly review:
    - “Here’s what you did, what changed, and what’s next.”

- **Interfaces to content**:

  - Manual input:
    - learner pastes links or titles they want to follow.
  - Optional:
    - integration with course platforms (read-only progress)
    - web search for content suggestions (with learner approval)

### 6.2 Internal Interfaces

- Core services:

  - `ProfileBuilder` (L1)
  - `SkillMapper` (L2)
  - `PlanGenerator` (L3)
  - `SessionGuide` (L4)
  - `ProgressTracker` (L5)
  - `AdaptiveEngine` (L6)
  - `WellbeingGuard` (L7)

---

## 7. Safety, Governance, and Well-being

- **Risks**:

  - Overloading learners (too much plan, guilt spiral)
  - Pushing through when they are burnt out
  - Creating unrealistic expectations

- **Safety mechanisms**:

  - L7 monitors:
    - streak length and intensity
    - self-reported stress/fatigue
    - missed session streaks
  - System can:
    - recommend lighter weeks
    - suggest breaks
    - flag when goals might be too aggressive

- **Governance decisions**:

  - Learner controls:
    - whether to track sensitive reflections
    - how long logs are kept
  - System clearly states:
    - it is a learning assistant, not a mental health professional.

- **Logging & traceability**:

  - Learner can see:
    - when and how their plan changed
    - what signals triggered the change
    - a timeline of their learning journey

---

## 8. Implementation Notes (Optional)

- **Planned tools**:

  - LLM for:
    - skill breakdown
    - explanation generation
    - reflection prompts
  - Standard DB for:
    - profile, plans, logs
  - Simple web/mobile UI

- **MVP constraints**:

  - Single learning goal per workspace at first.
  - Simple “beginner → intermediate → advanced” skill levels.
  - No complex analytics dashboard (just simple charts).

---

## 9. Test & Evaluation Scenarios

1. **New learner**:  
   Learner with no prior knowledge sets a goal (e.g., “learn Python in 3 months”) → system generates a reasonable roadmap and first week plan.

2. **Busy professional**:  
   Limited time (3×30 min/week) → plan respects constraints and suggests realistic milestones.

3. **Inconsistent week**:  
   Learner misses several sessions → plan adapts without blame, offers a revision week.

4. **Too easy**:  
   Learner marks tasks as very easy → system accelerates difficulty in next cycles.

5. **Burnout signal**:  
   Learner reports high stress → L7 suggests lighter load and more review rather than pushing forward.

---

## 10. Future Extensions (Optional)

- Group mode:
  - Learning circles or mentor-led groups
- Advanced analytics:
  - skill radar charts, time-on-task breakdown
- Certification bridge:
  - mapping achievements to external exams or credentials
