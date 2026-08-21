# 1. Product

**Name:** Arena
**Brand:** Arena by Ingoga

Arena is a workspace where humans and AI agents understand, execute, review, and deliver work together.

Arena is being built by extending the public OpenCode project rather than replacing its existing strengths.

The fundamental workflow is:

**Arena → Work → Deliver**

These are not three disconnected applications. They are three stages of the same piece of work.

The same project context must flow through all three stages.

---

# 2. Product Principle

Arena exists to make collaborative work between humans and AI understandable, structured, and accountable.

The user should not have to think about:

* prompt engineering
* agent orchestration
* model selection
* context injection
* complex workflows
* internal AI architecture

The system handles this underneath the interface.

The human should primarily think about:

**What are we doing?
Why are we doing it?
Who should work on it?
Is the result correct?**

---

# 3. Core Product Model

Every project revolves around one shared structured object called the:

## Work Contract

The Work Contract is progressively created in Arena and remains the source of truth throughout execution and delivery.

It should contain, where relevant:

* project identity
* source files
* context
* current understanding
* goal
* scope
* constraints
* expected outcomes
* success criteria
* plan
* tasks/workstreams
* departments involved
* human participants
* AI participants
* responsibilities
* deliverables
* evidence
* decisions
* approvals
* current status

Do not create separate competing sources of truth for Arena, Work, and Deliver.

---

# 4. Stage One — Arena

Arena is the thinking and preparation layer.

It happens before execution.

The user journey should progressively move through:

**Understand → Goal → Plan → Team → Ready**

### Understand

The user can start with existing project files, repositories, documents, instructions, or an empty project.

AI and humans build a shared understanding of the project.

AI may summarize, identify missing context, identify ambiguity, and suggest assumptions.

Humans remain able to edit, correct, or confirm the understanding.

### Goal

Define what needs to be accomplished.

Keep this concise.

The system may derive:

* primary goal
* expected outcome
* important constraints
* success criteria

### Plan

Turn the goal into understandable workstreams or tasks.

Do not expose unnecessary orchestration complexity.

Plans should be editable and should evolve when the project changes.

### Team

Assign participants.

Participants can be:

* humans
* AI agents

Humans and agents should exist within the same collaboration model whenever possible.

Do not design entirely separate systems for humans and AI.

### Departments

Departments represent expertise and organizational context.

Examples:

* Engineering
* Design
* Finance
* Research
* Operations
* Marketing
* Legal

Departments are NOT primarily folders or visual organization.

A department tells Arena what expertise, agents, tools, context, standards, and responsibilities may be relevant to that part of the work.

Departments should stay lightweight in the UI.

Their deeper orchestration happens underneath the interface.

### Ready

Before execution, Arena creates a concise execution brief from the Work Contract.

The user should clearly understand:

* what is being done
* why
* who is responsible
* what success looks like

Then they can start work.

---

# 5. Stage Two — Work

Work is the execution environment.

This should preserve as much of the existing OpenCode execution experience as reasonably possible.

Do not rebuild OpenCode without a strong reason.

Arena feeds structured context into Work.

Conceptually:

`Work Contract → relevant context → tasks → participants → execution`

The execution layer should understand the project goal and task context instead of operating from isolated prompts.

Humans and AI agents may both perform work.

Their outputs should become part of the same work record.

Agents can call tools or specialist agents when necessary, but implementation complexity should remain largely invisible to the end user.

---

# 6. Stage Three — Deliver

Deliver is the review, validation, approval, and preparation layer.

The core comparison is:

**Requested ↔ Delivered**

Deliver should evaluate outputs against:

* original goal
* scope
* requirements
* assigned tasks
* success criteria
* relevant decisions

The system should surface meaningful gaps instead of creating large reports by default.

Prefer states such as:

* Passed
* Needs attention
* Missing
* Changed
* Ready for approval

AI agents may review specialist work.

Humans may review and comment.

AI can recommend approval.

## Final approval must always be human.

The final human action is called:

**Seal**

Once sealed, the work can be considered formally approved and ready for delivery.

---

# 7. Product Navigation

The primary product structure is:

**Arena | Work | Deliver**

Avoid adding more top-level product areas unless there is a strong architectural reason.

Features should normally belong inside one of these three stages.

If a proposed feature cannot clearly answer where it belongs, reconsider whether it should exist.

---

# 8. UX Constitution

Arena should feel:

* calm
* precise
* lightweight
* capable
* institutional
* modern

Reference qualities:

* Perplexity — clarity and low cognitive load
* Apple — flow and polish
* IBM — institutional confidence
* Notion — composable building blocks
* Stripe — simplicity and precision

These are directional references, not designs to copy.

## UI rules

Prefer:

* progressive disclosure
* clear hierarchy
* generous spacing
* short labels
* strong defaults
* contextual actions
* inline editing
* reusable blocks
* few navigation levels
* visible next action

Avoid:

* dashboard clutter
* excessive cards
* unnecessary tabs
* large configuration forms
* complex workflow diagrams
* showing every agent at once
* technical AI terminology where normal language works
* exposing internal prompts
* forcing users to understand orchestration
* unnecessary modals
* duplicated information
* decorative UI without functional value

Before adding UI, ask:

**Does the user need to see this to make a decision or continue the work?**

If not, hide it, simplify it, or keep it in the system layer.

---

# 9. Interaction Principle

At any point, the user should be able to answer:

1. Where am I?
2. What is happening?
3. What do I need to do next?

If the interface cannot answer these quickly, simplify it.

---

# 10. Humans and AI

Do not design AI as a separate novelty feature.

Humans and agents are both participants in work.

They may have different:

* permissions
* capabilities
* responsibilities
* approval authority

But they should operate through the same work model wherever possible.

Use clear visual distinction where necessary, but avoid creating separate parallel products.

Only humans may issue final Seal approval.

---

# 11. Agent Behaviour

AI agents should receive only the context relevant to their assignment while remaining aware of the broader project goal.

A specialist should understand:

* the project
* the relevant goal
* their task
* constraints
* dependencies
* expected output
* available tools
* who or what receives their result

Agents should produce structured work that can be passed to another human or agent.

Their work should be recorded.

---

# 12. Files and Context

Files should not simply be attachments.

Files can become project context, evidence, inputs, intermediate work, or deliverables.

Arena should understand why a file exists and how it relates to the Work Contract.

Avoid duplicating files unnecessarily between Arena, Work, and Deliver.

---

# 13. Architecture Principle

Prefer extending existing OpenCode architecture rather than replacing working systems.

Before implementing a major new subsystem:

1. inspect the existing OpenCode implementation
2. determine whether it can be extended
3. reuse existing patterns when appropriate
4. isolate Arena-specific functionality cleanly
5. avoid breaking upstream compatibility unnecessarily

New Arena functionality should primarily live within the application layer around `packages/app` unless architecture requires otherwise.

Do not modify core OpenCode behaviour merely for visual convenience.

---

# 14. Lightweight Architecture

Arena should behave as a lightweight coordination layer over execution.

Avoid building a heavy enterprise workflow engine unless future evidence requires it.

Prefer:

* structured objects
* events
* simple states
* composable capabilities
* clear interfaces

over deeply coupled workflow logic.

---

# 15. State

Work should maintain continuity across the lifecycle.

A project may conceptually progress through states such as:

`Draft → Framing → Ready → Working → Review → Approval → Sealed`

Do not make users manually manage these states unless necessary.

The system should infer transitions wherever practical.

---

# 16. Scope Guard

Before implementing a feature, evaluate:

### Does it improve one of these?

* understanding the work
* defining the goal
* planning the work
* assigning responsibility
* executing work
* collaboration between humans and AI
* preserving context
* validating work
* approving work
* delivering work

If not, it is probably outside Arena's current scope.

Do not introduce adjacent features simply because they are technically possible.

---

# 17. Non-Goals

Arena is currently NOT intended to become:

* a generic project management suite
* a Jira clone
* a Slack clone
* a Notion clone
* an HR system
* a full ERP
* a generic autonomous-agent playground
* a complex no-code workflow builder
* an AI model configuration dashboard
* a traditional organizational chart product

Capabilities from these categories may exist only when they directly serve the Arena → Work → Deliver lifecycle.

---

# 18. Product Decision Order

When making a tradeoff, prioritize:

1. user clarity
2. continuity of project context
3. simple workflow
4. reliability
5. reuse of OpenCode
6. extensibility
7. visual polish
8. additional features

Do not sacrifice clarity for feature density.

---

# 19. Implementation Rule for Agents

Before making a meaningful product change, an AI coding agent should:

1. read `ARENA_CONSTITUTION.md`
2. inspect the relevant existing implementation
3. identify which stage the change belongs to:

   * Arena
   * Work
   * Deliver
4. identify how it interacts with the Work Contract
5. avoid introducing new concepts when an existing concept can serve the same role
6. preserve existing OpenCode behaviour unless the task specifically requires changing it
7. implement the smallest coherent solution
8. verify that the result follows the UX Constitution

If a requested implementation conflicts with this document, explicitly surface the conflict before introducing a new architectural direction.

---

# 20. Definition of Done

A feature is not complete simply because it functions.

It should also:

* clearly belong to the Arena lifecycle
* have an obvious purpose
* use existing terminology
* preserve project context
* avoid duplicate concepts
* minimize user decisions
* work for both human and AI participation where appropriate
* remain visually simple
* handle loading, empty, error, and success states
* be understandable without documentation
* not unnecessarily damage OpenCode compatibility

---

# 21. Core Vocabulary

Use these names consistently:

**Arena**
The framing, understanding, planning, and assignment stage.

**Work**
The execution stage based on OpenCode.

**Deliver**
The validation, approval, and delivery stage.

**Work Contract**
The shared structured source of truth connecting all stages.

**Participant**
A human or AI agent involved in work.

**Department**
A contextual collection of expertise, agents, tools, standards, and responsibilities.

**Deliverable**
An expected output from the work.

**Evidence**
Information showing how or why a result satisfies a requirement.

**Seal**
Final human approval of completed work.

Do not casually introduce alternative terms for these concepts.

---

# 22. Onboarding Summary

Anyone joining the Arena project should understand this first:

Arena adds structure around OpenCode.

Before work happens, **Arena** helps humans and AI understand what they are doing.

Then **Work** uses OpenCode to execute it.

Finally **Deliver** checks the output against what was originally agreed and asks a human to Seal it.

Everything revolves around the same Work Contract.

The product should make sophisticated human + AI coordination feel simple.

When uncertain about a design decision, choose the solution that removes complexity from the user while preserving meaningful control.
