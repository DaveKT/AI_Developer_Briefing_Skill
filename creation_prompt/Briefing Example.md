# AI Developer Briefing  

January 22, 2026

## TABLE OF CONTENTS
1. Executive Summary
2. Key Implications for the USDA Farm Loan Modernization  
3. Article Briefings  
	- A1. Has Gemini Surpassed ChatGPT? (Model Evaluation)  
	- A2. 10 Things I Learned From Burning Myself Out With AI Coding Agents  
	- A3. Big Tech Joins Forces With Linux Foundation To Standardize AI Agents  
	- A4. How AI Coding Agents Work — And What To Remember If You Use Them  
	- A5. Porting Open Source Code With LLMs (Simon Willison)  
	- A6. Porting JustHTML With GPT-5.2 (Simon Willison)  
4. Program Guardrails and Operating Principles  
5. Recommended Next Steps


## EXECUTIVE SUMMARY

- **AI coding agents are powerful but fragile.** They accelerate the *first 80–90%* of work and struggle with the last 10%—the part that matters most in regulated systems.  
- **Humans remain accountable.** AI-generated code that “looks right” but is unproven is a liability. Proven correctness is the new productivity signal.  
- **Model choice matters by task.** Gemini now shows stronger factual grounding and consistency on informational and procedural tasks, while ChatGPT retains strengths in style and creative synthesis. Neither is universally “better.” 
- **Agent interoperability is standardizing fast.** MCP, AGENTS.md, and open agent runtimes are converging into a de facto standard stack. This is directly relevant to long-lived government programs that must avoid vendor lock-in.
- **AI is safest where you have an oracle.** Replay tests, golden datasets, conformance suites, and invariants turn agents from risks into multipliers.

## KEY IMPLICATIONS FOR THIS MODERNIZATION

### What AI Is Good At (Today)
- Translating code between modern languages *when behavior is well-specified*
- Generating scaffolding, adapters, and glue code
- Writing tests **when you already know what “correct” means**
- Exploring architectural options quickly

### What AI Is Dangerous At
- Silent business-rule drift
- Over-engineering retries, wrappers, and abstractions
- “Vibe coding” without deep review
- Long-running agent sessions that lose context and reintroduce old bugs

## ARTICLE BRIEFINGS

### A1. Has Gemini Surpassed ChatGPT? We Put the AI Models to the Test  
**Source:** Ars Technica (Jan 21, 2026)  
**Link:** [https://arstechnica.com/features/2026/01/has-gemini-surpassed-chatgpt-we-put-the-ai-models-to-the-test/](https://arstechnica.com/features/2026/01/has-gemini-surpassed-chatgpt-we-put-the-ai-models-to-the-test/)
 

#### What Was Tested
Ars compared **default, non-paid models**:
- ChatGPT 5.2
- Gemini 3.2 Fast

They evaluated both across:
- Math and reasoning
- Factual biography
- Procedural guidance
- Creative writing
- Safety-critical scenarios

#### Key Findings
- **Gemini outperformed ChatGPT on factual accuracy and procedural reasoning**, avoiding hallucinations in biographies and technical explanations.
- **ChatGPT made several confident factual errors**, including invented career details and flawed step-by-step guidance.
- **In a safety-critical scenario (landing a plane)**, ChatGPT’s refusal and redirection was ultimately judged more useful than Gemini’s technically correct but unsafe instructions.

#### Why This Matters Here
For loan systems:
- **Factual correctness > stylistic fluency**
- A model that hallucinates eligibility logic or repayment behavior is unacceptable.
- Model evaluation must be task-specific, not reputation-based.

**Program takeaway:** Maintain a short, recurring model evaluation loop tied to *your actual workloads*, not benchmarks.

### A2. 10 Things I Learned From Burning Myself Out With AI Coding Agents  
**Source:** Ars Technica (Jan 19, 2026)  
**Link:** [https://arstechnica.com/information-technology/2026/01/10-things-i-learned-from-burning-myself-out-with-ai-coding-agents/](https://arstechnica.com/information-technology/2026/01/10-things-i-learned-from-burning-myself-out-with-ai-coding-agents/)

#### Core Lessons (Condensed)
1. **People are still necessary.** Agents amplify expertise; they do not replace it.
2. **Models are brittle outside training norms.** They excel at mainstream stacks, fail badly at niche or legacy contexts.
3. **True novelty is hard.** Semantic bias pulls agents toward familiar patterns—even when wrong.
4. **The 90% problem is real.** The last 10% is slow, tedious, and human-driven.
5. **Feature creep accelerates.** Agents happily add features instead of stabilizing systems.
6. **Context loss is constant.** Agents forget unless you externalize memory.
7. **Busyness increases.** More output ≠ less work; review and coordination load explodes.

#### Why This Matters Here
A modernization with **dozens of applications** is exactly where burnout happens:
- Too many parallel agent-driven changes
- Too much review overhead
- False confidence from rapid early progress

**Program takeaway:** Limit agent scope. Measure review cost, not just code volume.

### A3. Big Tech Joins Forces With Linux Foundation To Standardize AI Agents  
**Source:** Ars Technica (Dec 9, 2025)  
**Link:** [https://arstechnica.com/ai/2025/12/big-tech-joins-forces-with-linux-foundation-to-standardize-ai-agents/](https://arstechnica.com/ai/2025/12/big-tech-joins-forces-with-linux-foundation-to-standardize-ai-agents/)

#### What Happened

The Linux Foundation launched the **Agentic AI Foundation (AAIF)** to steward:
- **Model Context Protocol (MCP)** – standardized tool/data access for agents
- **AGENTS.md** – repo-level instructions for agent behavior
- **goose** – an open-source, model-agnostic agent runtime

Founding supporters include Anthropic, OpenAI, Google, Amazon, Microsoft, and others.

#### Why This Matters Here

This mirrors what CNCF did for Kubernetes:
- Early chaos → eventual standardization
- Long-lived programs benefit most from neutrality

**Program takeaway:** Treat agent interfaces like infrastructure standards, not experiments.

### A4. How AI Coding Agents Work — And What To Remember If You Use Them  
**Source:** Ars Technica (Dec 24, 2025)  
**Link:** [https://arstechnica.com/information-technology/2025/12/how-do-ai-coding-agents-work-we-look-under-the-hood/](https://arstechnica.com/information-technology/2025/12/how-do-ai-coding-agents-work-we-look-under-the-hood/)

#### How Agents Actually Work

- A supervising LLM decomposes tasks and delegates to sub-agents
- Agents run tool loops: read → write → test → revise
- Context is finite and degrades (“context rot”)
- Agents rely on **compression**, losing detail over time
- Multi-agent systems consume **15× tokens** vs chat

#### Best Practices Identified

- Force planning before coding
- Externalize memory in files (AGENTS.md, CLAUDE.md)
- Version control aggressively
- Avoid “vibe coding” in production systems

#### Why This Matters Here

Loan systems are **stateful, rule-dense, and compliance-heavy**—the worst case for unmanaged agent loops.

**Program takeaway:** Agents are tools, not teammates. Architecture and intent must come from humans.

### A5. My Answers to the Questions I Posed About Porting Open Source Code With LLMs  
**Source:** Simon Willison (Jan 11, 2026)  
**Link:** https://simonwillison.net/2026/Jan/11/answers/

#### Key Points
- LLM ports are derivative works → licensing still applies
- Attribution and provenance matter
- AI-generated code should be labeled honestly
- Confidence comes from tests, not generation method

### A6. I Ported JustHTML From Python to JavaScript With GPT-5.2 in 4.5 Hours  
**Source:** Simon Willison (Dec 15, 2025)  
**Link:** [https://simonwillison.net/2025/Dec/15/porting-justhtml/](https://simonwillison.net/2025/Dec/15/porting-justhtml/)

#### Why It Worked
- A large, existing conformance test suite
- Clear functional expectations
- Incremental verification

**Program takeaway:** Tests are the real accelerator.

## PROGRAM GUARDRAILS (RECOMMENDED)

- **AI-assisted code must be provably correct**
- **All agent-generated changes require human review**
- **AGENTS.md required in all repos**
- **Golden datasets required for business logic**
- **Replay and invariants before refactors**
- **No agent autonomy in security, IAM, or financial logic**

## RECOMMENDED NEXT STEPS

1. Define “AI-safe” vs “AI-restricted” work areas
2. Establish a minimal model evaluation rubric
3. Add AGENTS.md templates to repos
4. Identify high-value oracle datasets
5. Train developers on agent failure modes

**Bottom line:**  
AI will not replace your expertise—but it will amplify both your strengths and your mistakes.  
Use it deliberately.