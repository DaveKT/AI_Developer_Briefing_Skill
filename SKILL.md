---
name: ai-developer-briefing
description: Generate AI developer briefings that synthesize multiple articles into actionable guidance for development teams using AI coding tools. Use when the user requests an AI briefing, AI status report, AI developer update, or provides a collection of AI-related article links to summarize. Requires at least four articles. Outputs a markdown briefing with executive summary, key implications, article reviews, guardrails, and next steps.
---

# AI Developer Briefing

Generate comprehensive briefings that synthesize AI-related articles into actionable guidance for cloud development teams adopting AI coding tools.

## Prerequisites

- Minimum of four articles (links or full text)
- If a link is inaccessible, halt and request the article content before proceeding

## Workflow

1. Collect all provided links and article content
2. Attempt to fetch each link using web_fetch
3. If any link fails, stop and request the missing content from the user
4. Once all content is available, analyze for themes and implications
5. Generate the briefing following the output structure below
6. Output as markdown to `/mnt/user-data/outputs/`

## Output Structure

Use this exact section order. Date auto-generates from current date.

```markdown
# AI Developer Briefing

[Current Date in "Month Day, Year" format]

## TABLE OF CONTENTS
1. Executive Summary
2. Key Implications for Cloud Development Teams
3. Article Briefings
   - [Article listings]
4. Program Guardrails and Operating Principles
5. Recommended Next Steps

## EXECUTIVE SUMMARY

[Bullet points synthesizing the most salient findings across all articles. Scale with article count: 4-5 bullets for 4-6 articles, 6-8 bullets for 7+ articles. Focus on unifying themes rather than per-article summaries.]

## KEY IMPLICATIONS FOR CLOUD DEVELOPMENT TEAMS

### What AI Coding Tools Excel At (Based on Current Evidence)
[Bulleted list derived from article findings]

### Where AI Coding Tools Introduce Risk
[Bulleted list derived from article findings]

## ARTICLE BRIEFINGS

### A[n]. [Article Title]
**Source:** [Publication] ([Date])
**Link:** [URL]

[Adaptive subsections based on article type - see Article Subsection Patterns below]

[Repeat for each article]

## PROGRAM GUARDRAILS AND OPERATING PRINCIPLES

[Bulleted list of proposed best practices derived from article content. Focus on AI coding tool usage, code review, testing, and risk management.]

## RECOMMENDED NEXT STEPS

[Numbered list of concrete actions. Balance safety/quality improvements with agility/speed gains.]

**Bottom line:**
[One to two sentence synthesis of the core message]
```

## Article Subsection Patterns

Adapt subsections based on article type:

**Comparative/Benchmark Articles:**
- What Was Tested
- Key Findings
- Why This Matters
- Takeaway

**Opinion/Experience Articles:**
- Core Lessons (condensed list)
- Why This Matters
- Takeaway

**News/Announcement Articles:**
- What Happened
- Key Details
- Why This Matters
- Takeaway

**Technical/Tutorial Articles:**
- Key Points
- Best Practices Identified
- Why This Matters
- Takeaway

**Research/Analysis Articles:**
- Methodology
- Key Findings
- Limitations
- Takeaway

## Content Guidelines

### Executive Summary
- Synthesize across articles; avoid per-article summaries
- Identify contradictions or tensions between sources
- Prioritize actionable insights over general observations

### Key Implications
- Ground each implication in specific article evidence
- Distinguish between well-supported claims and speculation
- Focus on AI coding tools: agents, assistants, code generation, automated testing

### Article Briefings
- Keep briefings concise: 150-300 words per article
- "Why This Matters" should connect to development team concerns
- "Takeaway" should be one actionable sentence

### Guardrails
- Derive from article content, not general best practices
- Include both protective measures and enabling practices
- Prioritize guardrails that address risks identified in the articles

### Next Steps
- Concrete and actionable within a sprint or quarter
- Balance immediate actions with longer-term initiatives
- Reference specific article findings where relevant

## Writing Style

- Professional and direct
- Active voice
- No emoji
- Minimal formatting; use bold sparingly for emphasis
- Use en-dashes for ranges, not em-dashes in prose

## Link Handling

When a provided link cannot be fetched:

1. Note which links failed
2. Do not proceed with partial content
3. Request the user provide the article text directly
4. Resume only when all content is available

Example response when links fail:
```
The following links could not be accessed:
- [URL 1]: [error reason]
- [URL 2]: [error reason]

Provide the article content directly (copy/paste or file upload) to proceed with the briefing.
```
