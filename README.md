# Look For Work — Claude Code Plugin

A proactive codebase analysis agent that scans for the highest-impact improvement opportunities across 15 dimensions.

## Installation

```bash
/install-plugin mpge/look-for-work-claude
```

## Usage

```
/look-for-work
/look-for-work security          # Focus on security
/look-for-work performance       # Focus on performance
```

## What It Does

When you say "look for work", this plugin dispatches 6 specialized agents in parallel to analyze your codebase across:

| Agent | Covers |
|-------|--------|
| **Architecture Analyst** | Coupling, modularization, SOLID/DRY/KISS, design integrity |
| **Security Analyst** | OWASP Top 10, threat surfaces, auth, injection, data exposure |
| **Performance Analyst** | N+1 queries, memory leaks, blocking ops, caching, algorithms |
| **Quality Analyst** | Code smells, maintainability, refactor opportunities with ROI |
| **Reliability Analyst** | Test coverage, concurrency safety, data integrity, observability, deployment |
| **Landmine Detector** | Hidden bugs, edge cases, production-only failures, business logic risks |

Results are synthesized into a prioritized roadmap:

- **P0 — Fix Now**: Security vulnerabilities, data loss risks
- **P1 — Fix Soon**: Performance bottlenecks, reliability gaps
- **P2 — Plan For**: Architecture improvements, high-ROI refactors
- **P3 — Backlog**: Quality improvements, nice-to-haves

## Philosophy

> If you owned this codebase, what would you fix first?

Don't wait for bugs. Don't wait for incidents. Find the work that needs doing.

## License

MIT
