# AI Developer Briefing Skill

A Claude skill for generating structured briefings that synthesize AI-related articles into actionable guidance for development teams adopting AI coding tools.

## Overview

This skill accepts a collection of article links (minimum four) and produces a comprehensive markdown briefing covering:

- Executive summary with cross-cutting themes
- Key implications for development teams
- Individual article reviews with adaptive formatting
- Proposed guardrails and operating principles
- Concrete next steps

## Installation

1. Download `ai-developer-briefing.skill`
2. In Claude, navigate to Settings > Skills
3. Upload the skill file

## Usage

Provide Claude with four or more links to AI-related articles:

```
Generate an AI developer briefing from these articles:

- https://example.com/article-1
- https://example.com/article-2
- https://example.com/article-3
- https://example.com/article-4
```

If any links are inaccessible, the skill will halt and request the article content directly before proceeding.

### Alternative Input

Articles can also be provided as:
- Pasted text in the conversation
- Uploaded files (markdown, text, PDF)
- A mix of links and direct content

## Output Format

The skill generates a markdown file with the following structure:

```
# AI Developer Briefing
[Date]

## TABLE OF CONTENTS
1. Executive Summary
2. Key Implications for Cloud Development Teams
3. Article Briefings
4. Program Guardrails and Operating Principles
5. Recommended Next Steps
```

### Article Subsection Patterns

The skill adapts article review structure based on content type:

| Article Type | Subsections |
|--------------|-------------|
| Comparative/Benchmark | What Was Tested, Key Findings, Why This Matters, Takeaway |
| Opinion/Experience | Core Lessons, Why This Matters, Takeaway |
| News/Announcement | What Happened, Key Details, Why This Matters, Takeaway |
| Technical/Tutorial | Key Points, Best Practices Identified, Why This Matters, Takeaway |
| Research/Analysis | Methodology, Key Findings, Limitations, Takeaway |

## Example Output

See [example-briefing.md](example-briefing.md) for a sample briefing demonstrating the expected output format.

## Configuration

The skill uses these defaults:

- **Target audience**: Cloud development teams
- **Focus area**: AI coding tools (agents, assistants, code generation)
- **Output format**: Markdown
- **Minimum articles**: 4

## File Contents

```
ai-developer-briefing/
├── SKILL.md                      # Main skill definition
└── references/
    └── example-annotation.md     # Annotated examples for each section
```

## License

MIT
