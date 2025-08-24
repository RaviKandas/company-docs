# Decision Making Process

How we make decisions efficiently and transparently.

## Decision Framework

We use different decision-making approaches based on the impact and reversibility of the decision.

### Decision Types

| Type | Impact | Reversibility | Process | Timeframe |
|------|--------|--------------|---------|-----------|
| **Type 1** | High | Hard to reverse | RFC + Consensus | 1-2 weeks |
| **Type 2** | Medium | Reversible | Team discussion | 2-3 days |
| **Type 3** | Low | Easy to reverse | Individual decides | Immediate |

## Decision Principles

1. **Bias for action** - Most decisions are reversible
2. **Data-informed** - Use data, but don't be paralyzed by it
3. **Disagree and commit** - Once decided, everyone supports
4. **Document everything** - Future us needs context
5. **Time-bound** - Every decision has a deadline

## Type 1: Major Decisions (RFC Process)

For architectural changes, major features, or strategic shifts.

### RFC (Request for Comments) Template

```markdown
# RFC: [Title]

## Status
Draft | In Review | Decided | Implemented

## Summary
One paragraph explaining the proposal

## Motivation
Why are we doing this? What problem does it solve?

## Detailed Design
The meat of the proposal. Include:
- Technical approach
- Implementation plan
- Migration strategy
- API changes

## Alternatives Considered
What other options were evaluated?
Why weren't they chosen?

## Risks & Mitigations
What could go wrong?
How do we handle it?

## Success Metrics
How do we know this worked?

## Timeline
Key milestones and dates

## Open Questions
What still needs to be figured out?

## Decision
[To be filled after decision]
- Date: 
- Participants:
- Outcome:
- Rationale:
```

### RFC Process

1. **Draft** (Author)
   - Write RFC using template
   - Share in #rfcs channel
   - Tag relevant stakeholders

2. **Review** (1 week)
   - Gather feedback
   - Update based on input
   - Address concerns

3. **Decision Meeting**
   - Present final RFC
   - Discuss remaining concerns
   - Make decision

4. **Document**
   - Update RFC with decision
   - Communicate broadly
   - Create implementation tickets

## Type 2: Team Decisions

For feature priorities, tool choices, or process changes.

### Quick Decision Template

```markdown
# Decision: [What we're deciding]

## Context
Brief background (2-3 sentences)

## Options
1. Option A: [pros/cons]
2. Option B: [pros/cons]
3. Option C: [pros/cons]

## Recommendation
Which option and why

## Decision
- Chosen: Option X
- Decided by: @names
- Date: YYYY-MM-DD
```

### Process

1. **Propose** in Slack/meeting
2. **Discuss** for 24-48 hours
3. **Decide** with team consensus
4. **Document** in decisions log

## Type 3: Individual Decisions

For implementation details, minor improvements, or daily choices.

### Guidelines

- **Just do it** - You have autonomy
- **Inform if needed** - Let team know FYI
- **Document if novel** - Help others learn
- **Escalate if unsure** - When in doubt, ask

## Decision Making Methods

### 1. Consensus
Everyone agrees (or can live with it)
- **Use for**: Critical, long-term decisions
- **Pros**: Full buy-in
- **Cons**: Slow, can lead to compromise

### 2. Consent
No one objects strongly
- **Use for**: Most team decisions
- **Pros**: Faster than consensus
- **Cons**: May lack enthusiasm

### 3. Consultative
Decision maker gets input, then decides
- **Use for**: Time-sensitive decisions
- **Pros**: Fast, clear ownership
- **Cons**: Less buy-in

### 4. Delegation
Empower someone to decide
- **Use for**: Domain-specific decisions
- **Pros**: Leverages expertise
- **Cons**: Requires trust

## DACI Framework

For complex decisions with multiple stakeholders:

- **D**river: Who's driving this decision?
- **A**pprover: Who has final say?
- **C**ontributors: Who provides input?
- **I**nformed: Who needs to know?

### DACI Example

```markdown
Decision: Migrate to new CI/CD platform

Driver: @jane (DevOps Lead)
Approver: @john (CTO)
Contributors: @engineering-team
Informed: @all-hands
```

## Decision Velocity

### Speeding Up Decisions

1. **Set deadlines** - "We decide by Friday"
2. **Default to reversible** - Try it for 2 weeks
3. **Smaller groups** - 3-5 people max
4. **Async first** - Document, comment, decide
5. **Bias for action** - 70% confidence is enough

### When to Slow Down

- Irreversible consequences
- High cost of being wrong
- Affects many stakeholders
- Legal/compliance implications
- Core architecture changes

## Documenting Decisions

### Decision Log

Keep a central log of all decisions:

```markdown
# Q1 2024 Decisions

| Date | Decision | Type | Driver | Link |
|------|----------|------|--------|------|
| 2024-01-15 | Adopt TypeScript | Type 1 | @sarah | [RFC](link) |
| 2024-01-22 | Change standup time | Type 3 | @team | [Thread](link) |
| 2024-02-01 | New monitoring tool | Type 2 | @ops | [Doc](link) |
```

### Architecture Decision Records (ADRs)

For technical decisions:

```markdown
# ADR-001: Use PostgreSQL for main database

## Status
Accepted

## Context
We need to choose a primary database

## Decision
We will use PostgreSQL 14+

## Consequences
- Need to train team on PostgreSQL
- Must plan migration from MySQL
- Better JSON support for our use case
```

## Revisiting Decisions

### When to Revisit

- New information available
- Context has changed
- Decision isn't working
- Scheduled review time

### How to Revisit

1. Document what's changed
2. Assess impact of changing
3. Follow appropriate process
4. Update documentation

## Anti-patterns to Avoid

### ❌ Analysis Paralysis
Endless research without deciding

**Fix**: Set a deadline

### ❌ Decision by Committee
Everyone must agree on everything

**Fix**: Clear decision rights

### ❌ Shadow Decisions
Decisions made without transparency

**Fix**: Document all decisions

### ❌ Revisiting Constantly
Questioning every decision

**Fix**: Commit period before revisiting

### ❌ No Owner
Nobody accountable for decision

**Fix**: Always assign a driver

## Decision Escalation

When to escalate:

1. **Deadlocked** - Team can't agree
2. **Out of scope** - Beyond team authority
3. **High risk** - Major consequences
4. **Cross-functional** - Affects multiple teams

How to escalate:

```markdown
## Escalation Request

**Decision needed**: [What]
**Stuck because**: [Why escalating]
**Options**: [What are the choices]
**Recommendation**: [Your view]
**Needed by**: [Date]
**Impact of delay**: [Consequences]
```

## Tools & Templates

- **RFCs**: [RFC template](link)
- **ADRs**: [ADR template](link)
- **Decision matrix**: [Template](link)
- **DACI template**: [Template](link)

## Examples of Good Decisions

### Example 1: Technology Choice
"We'll use React for our frontend because:
- Team has expertise
- Large ecosystem
- Good performance for our needs
- Decision by: Engineering team
- Revisit in: 1 year"

### Example 2: Process Change
"Moving standup to async because:
- Team is distributed
- Saves 2.5 hours/week
- Trial for 1 month
- Decision by: Team consent"

## Remember

> "A good decision now is better than a perfect decision later."

Most decisions are reversible. When in doubt, try something and learn! 🚀