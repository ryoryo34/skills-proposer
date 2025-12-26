# Root Cause (Why) Patterns

A catalog of root cause patterns for detecting skill candidates from conversations.

## Root Cause Categories

### 1. Lack of Project-Specific Knowledge

**Typical Friction Points**:
- User explains "This project uses XX"
- Proposed wrong libraries or patterns
- Wrote code that violates project conventions

**Why**: Claude doesn't know project-specific tool choices, conventions, or patterns

**Skillification Direction**:
- Document project's tech stack and conventions in `references/`
- Include selection rationale (ADR)

### 2. Lack of Domain Knowledge / Business Rules

**Typical Friction Points**:
- User repeatedly explains business terminology
- Made incorrect assumptions about business logic
- Misunderstood relationships between domain entities

**Why**: Claude doesn't know the project's domain model or business rules

**Skillification Direction**:
- Place domain glossary and entity relationship diagrams in `references/`
- Document business rules and constraints

### 3. Insufficient Understanding of Type Definitions / Schemas

**Typical Friction Points**:
- Repeatedly fixed type errors
- Misunderstood API response structure
- Misunderstood database schema

**Why**: Claude doesn't know the project's type definitions, schemas, or data structures

**Skillification Direction**:
- Place major type definitions and schemas in `references/`
- Explain type usage patterns and constraints

### 4. Insufficient Understanding of Workflows / Procedures

**Typical Friction Points**:
- Skipped steps in the process
- Proceeded without meeting prerequisites
- Didn't know project-specific workflows

**Why**: Claude doesn't know project-specific procedures or dependencies

**Skillification Direction**:
- Define workflows and checklists in `SKILL.md`
- Explicitly state prerequisites and dependencies

### 5. Lack of Architectural Decision Context

**Typical Friction Points**:
- Couldn't answer "Why is it like this?"
- Proposed alternatives that were already considered
- Proposed changes that contradict design intent

**Why**: Claude doesn't know the rationale or trade-offs behind architectural decisions

**Skillification Direction**:
- Place ADRs (Architecture Decision Records) in `references/`
- Record decision context and rejected alternatives

### 6. Lack of Implicit Conventions / Practices

**Typical Friction Points**:
- Code review feedback: "We do it this way here"
- Didn't know team's implicit understandings
- Violated undocumented rules

**Why**: Claude doesn't know unwritten conventions or team practices

**Skillification Direction**:
- Document implicit conventions in `SKILL.md` or `references/`
- List "do's" and "don'ts"

## Skillification Criteria

### When to Skillify

| Root Cause | Criteria |
|-----------|----------|
| Project-specific | This knowledge isn't useful in other projects |
| Recurring | Same friction point occurred 2+ times |
| Solvable with knowledge | Problem wouldn't have occurred if known beforehand |
| Stable knowledge | Knowledge that doesn't change frequently |

### When Not to Skillify

| Situation | Reason |
|-----------|--------|
| One-time problem | Not worth skillifying if it won't recur |
| Frequently changing information | High maintenance cost |
| Claude's general knowledge | Something Claude already knows |
| Context-dependent judgment | Requires different judgment each time |

## Analysis Checklist

Checklist for analyzing conversations:

- [ ] Where did the user request corrections or fixes?
- [ ] Why didn't Claude know that?
- [ ] Could we have done it correctly from the start with this knowledge?
- [ ] Is this problem likely to occur again?
- [ ] Can't we handle this by improving existing skills?

