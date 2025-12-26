---
name: skill-proposer
description: Analyze conversations and suggest skill candidates (evaluation-driven development). Use when asked to suggest skills, analyze conversation for improvements, find repeating patterns, or identify automation opportunities. Triggers include "suggest skills", "skill candidates", "analyze improvements".
---

# Skill Suggestion (Evaluation-Driven Development)

Analyze conversations to identify **root causes (Why) of Claude's failures** and propose **new skill creation** or **updates to existing skills**.

## Analysis Perspective: Why, Not What

Focus on the underlying causes (Why) rather than surface phenomena (What).

| What (Phenomenon) | Why (Root Cause) |
|------------------|------------------|
| Repeatedly wrote the same code | Didn't know project-specific patterns |
| Repeatedly fixed errors | Didn't understand project's type definitions or conventions |
| Repeatedly explained the same thing | Lacked domain knowledge or business rules |
| Repeatedly discussed decisions | Didn't know the background of architectural decisions |
| Made workflow mistakes | Didn't know project-specific procedures |

## Analysis Process

### Step 1: Identify "Friction Points" in the Conversation

Look for the following signals:

- Places where the user requested corrections or fixes
- Places where the user provided additional explanations
- Places that required multiple exchanges
- Places where Claude made incorrect assumptions

### Step 2: Analyze Root Causes (Why)

For each friction point, ask:

1. **Why didn't Claude know this?**
   - Because it's project-specific knowledge
   - Because it's domain-specific rules
   - Because implicit conventions exist

2. **Could we have done it correctly from the start if we had this knowledge?**
   - Yes → Worth skillifying
   - No → A different approach is needed

3. **Can existing skills handle this?**
   - Yes → Propose updating existing skills
   - No → Propose creating a new skill

4. **Would this knowledge be useful in other contexts?**
   - Yes → Valuable as a general-purpose skill
   - No → A one-time fix is sufficient

### Step 3: Generate Proposals

Propose either "new creation" or "existing skill update" for each root cause:

#### For New Skill Creation

```markdown
## New Skill: [Name]

**Friction Point**: [Specific location in conversation where the problem occurred]

**Root Cause (Why)**:
[Why Claude failed - missing knowledge or context]

**What the Skill Can Solve**:
[What would improve if we had this knowledge]

**Proposal**:
- name: [skill-name]
- description: [description]
- Knowledge to include:
  - [ ] [Specific knowledge, conventions, patterns]

**Priority**: [High/Medium/Low]
```

#### For Existing Skill Updates

```markdown
## Existing Skill Update: [Skill Name]

**Target Skill**: [Path to existing skill]

**Friction Point**: [Specific location in conversation where the problem occurred]

**Root Cause (Why)**:
[Why the existing skill couldn't cover this]

**Update Content**:
- Knowledge to add:
  - [ ] [Specific knowledge, conventions, patterns]
- Sections to fix:
  - [ ] [Sections in existing documentation that are insufficient or incorrect]

**Priority**: [High/Medium/Low]
```

## Output Format

```markdown
# Skill Proposal Report

## Analysis Summary
- Identified friction points: [number]
- Root cause categories: [list of categories]
- New skill proposals: [number]
- Existing skill update proposals: [number]

## Root Cause Analysis

### Friction Point 1: [Specific Problem]
- **What**: [What happened on the surface]
- **Why**: [Why it happened - knowledge Claude lacked]

## New Skill Proposals

### 1. [Skill Name]
[Format as new skill creation]

## Existing Skill Update Proposals

### 1. Update [Skill Name]
[Format as existing skill update]

## Next Actions
- [ ] Confirm root cause validity with user
- [ ] Create new skill (use /skill-creator)
- [ ] Update existing skill (edit target file directly)
```

## Notes

- Don't propose skills based solely on surface patterns (What)
- Always ask "Why didn't Claude know this?"
- Don't skillify one-time problems
- **Prioritize updating existing skills over creating new ones when existing skills can solve the problem**
- In existing skill update proposals, clearly specify sections to add or fix

