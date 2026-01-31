# Example Briefing Annotation

This reference shows the expected output format with annotations explaining each section's purpose.

## Executive Summary Example

The executive summary should identify cross-cutting themes, not list articles:

**Good example:**
- AI coding agents accelerate early development but struggle with final integration and edge cases
- Model selection should be task-specific; no single model dominates all use cases
- Agent interoperability standards (MCP, AGENTS.md) are maturing rapidly
- Test suites and golden datasets are the primary enabler for safe AI-assisted development

**Avoid:**
- Article 1 discusses X
- Article 2 covers Y
- Article 3 mentions Z

## Key Implications Example

Ground implications in evidence from the articles:

**Good example:**
### What AI Coding Tools Excel At
- Translating code between modern languages when behavior is well-specified
- Generating scaffolding, adapters, and glue code
- Writing tests when correctness criteria are already defined
- Exploring architectural options quickly

### Where AI Coding Tools Introduce Risk
- Silent business-rule drift during refactoring
- Over-engineering through unnecessary abstractions
- Context loss in long-running agent sessions
- False confidence from rapid early progress

## Article Briefing Length

Target 150-300 words per article. Example structure for an opinion piece:

### A2. 10 Things I Learned From Burning Myself Out With AI Coding Agents
**Source:** Ars Technica (Jan 19, 2026)
**Link:** [URL]

#### Core Lessons
1. Agents amplify expertise; they do not replace it
2. Models excel at mainstream stacks, fail at niche or legacy contexts
3. The last 10% of development remains slow and human-driven
4. Feature creep accelerates when agents propose additions freely
5. Context loss is constant without externalized memory

#### Why This Matters
Development teams with large application portfolios face compounding review overhead. Rapid agent-driven changes across many components create false progress signals while increasing integration risk.

#### Takeaway
Limit agent scope per task and track review cost alongside code volume.

## Guardrails Example

Derive from article content:

- AI-assisted code requires provable correctness before merge
- All agent-generated changes require human review
- AGENTS.md or equivalent configuration required in all repositories
- Golden datasets required for business logic validation
- No agent autonomy in security, authentication, or financial logic

## Next Steps Example

Concrete and time-bound:

1. Define "AI-safe" vs "AI-restricted" work areas for the codebase
2. Establish a minimal model evaluation rubric tied to actual workloads
3. Add AGENTS.md templates to repository standards
4. Identify candidate datasets for golden test suites
5. Schedule developer training on agent failure modes

## Bottom Line Example

One to two sentences that synthesize the core message:

**Good example:**
AI tools will not replace development expertise but will amplify both strengths and mistakes. Deliberate adoption with clear guardrails is the path to sustainable productivity gains.

**Avoid:**
- Overly generic statements ("AI is changing everything")
- Hedged non-conclusions ("More research is needed")
