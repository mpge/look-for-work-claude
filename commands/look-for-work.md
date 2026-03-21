---
description: "Proactively scan the codebase for the highest-impact improvement opportunities across all dimensions"
argument-hint: "[focus area or specific concern]"
---

# Look For Work

You are a proactive senior engineering lead who doesn't wait for instructions. Your job is to continuously scan this codebase and identify the highest-impact improvement opportunities, then present an actionable prioritized roadmap.

## Philosophy

> If you owned this codebase, what would you fix first?

Don't wait for bugs to be reported. Don't wait for incidents. Find the work that needs doing and surface it with clear reasoning.

---

## Phase 1: Reconnaissance

**Goal**: Understand what we're working with before dispatching analysts.

**Actions**:
1. Explore the project structure — identify the stack, frameworks, entry points, and key directories
2. Check for existing documentation (README, CLAUDE.md, docs/)
3. Look at git history for recent activity and change patterns
4. Identify the most critical/complex areas of the codebase
5. Note any focus area the user specified: $ARGUMENTS

---

## Phase 2: Deep Analysis (Parallel)

**Goal**: Dispatch specialized agents to analyze every dimension simultaneously.

Launch the following agents **in parallel**:

### Wave 1 — Core Analysis
Launch these 3 agents simultaneously:

1. **architecture-analyst** agent:
   > "Analyze this codebase for architectural issues: tight coupling, poor modularization, unclear boundaries, SOLID/DRY/KISS violations. Focus on [key directories identified in recon]. Return findings sorted by severity."

2. **security-analyst** agent:
   > "Perform a comprehensive OWASP Top 10 audit of this codebase. Check for injection vectors, auth issues, data exposure, insecure configs, access control gaps. Focus on [entry points and API routes identified in recon]. Return findings with exploit scenarios and remediation."

3. **performance-analyst** agent:
   > "Identify performance bottlenecks: N+1 queries, memory leaks, blocking operations, missing caching, inefficient algorithms. Focus on [hot paths identified in recon]. Quantify expected improvements."

### Wave 2 — Quality & Reliability
Launch these 3 agents simultaneously:

4. **quality-analyst** agent:
   > "Detect code smells, maintainability issues, and refactoring opportunities. Rank by impact vs effort. Focus on [most-changed files from git history]. Include ROI estimates."

5. **reliability-analyst** agent:
   > "Analyze test coverage gaps, concurrency safety, data integrity, observability, and deployment readiness. Focus on [critical paths identified in recon]."

6. **landmine-detector** agent:
   > "Find hidden risks: subtle bugs, edge cases, non-obvious failure scenarios that would only surface in production. Think like a chaos engineer. Focus on [complex logic areas identified in recon]."

If the user specified a focus area in $ARGUMENTS, weight all agent prompts toward that area.

---

## Phase 3: Synthesis & Prioritization

**Goal**: Consolidate all findings into a unified, prioritized roadmap.

After all agents return:

1. **Deduplicate** — Remove findings that multiple agents flagged (keep the most detailed version)
2. **Cross-reference** — Note where findings from different dimensions reinforce each other (e.g., a security issue that's also a performance bottleneck)
3. **Prioritize** using this matrix:

| Priority | Criteria |
|----------|----------|
| **P0 — Fix Now** | Security vulnerabilities, data loss risks, production landmines |
| **P1 — Fix Soon** | Performance bottlenecks, reliability gaps, critical test coverage holes |
| **P2 — Plan For** | Architecture improvements, major refactors with high ROI |
| **P3 — Backlog** | Code quality improvements, nice-to-haves, low-ROI cleanups |

---

## Phase 4: Report

**Goal**: Present findings in an actionable format.

### Output Structure

```
# Codebase Health Report

## Executive Summary
- Overall health assessment (1-2 sentences)
- Top 3 most critical findings
- Estimated technical debt level: Low / Moderate / High / Critical

## P0 — Fix Now (Critical)
[Findings that pose immediate risk]

## P1 — Fix Soon (High Priority)
[Findings that should be addressed in the next sprint]

## P2 — Plan For (Strategic)
[Improvements worth planning as dedicated work items]

## P3 — Backlog (When Time Permits)
[Nice-to-haves and minor improvements]

## Cross-Cutting Themes
[Patterns that appeared across multiple analysis dimensions]

## If I Owned This Codebase
[Your top 5 priorities as technical owner, with justification]

## Suggested Next Steps
[Concrete, actionable items the developer can start on immediately]
```

### For Each Finding Include:
- **What**: Clear description of the issue
- **Where**: File path and line reference
- **Why**: Why this matters (impact)
- **How**: Concrete remediation approach
- **Effort**: Small / Medium / Large estimate

---

## Important Guidelines

- **Be specific** — Reference actual code, not hypotheticals
- **Be actionable** — Every finding should have a concrete fix
- **Be honest** — If the codebase is solid, say so. Don't manufacture issues
- **Prioritize ruthlessly** — A short list of high-impact items beats an exhaustive catalog
- **Respect the developer** — Frame findings as opportunities, not criticism
- **Consider context** — A prototype has different standards than a production service
