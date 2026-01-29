# Design-Log Methodology
A structured approach to AI-assisted software development that eliminates "context drift" and transforms AI from a simple coder into a true architectural partner.

## Overview
As projects grow, AI models often hit a "Context Wall" - making suggestions that conflict with previous decisions or losing track of the codebase's architectural evolution. The **Design-Log Methodology** solves this by maintaining a version-controlled history of intent, decisions, and implementation results.

Instead of writing complex prompts, you maintain a `./design-log/` folder. The AI reads these logs to understand the "why" behind your code before it ever touches a line of production logic.

![The workflow](./the%20workflow.png)

## Key Principles
- **Read Before You Write**: The AI must check existing logs to understand constraints and reuse existing patterns.

- **Design Before You Implement**: No code is written until a Markdown log is created, reviewed, and approved.

- **The Socratic Method**: The AI is instructed to ask questions within the log to clarify edge cases and logic gaps before implementation.

- **Immutable History**: The "Design" section of a log is frozen once coding begins. All changes, deviations, and results are appended to an "Implementation Results" section, ensuring the history remains honest.

## Benefits
- **Zero-Drift Implementation**: Prevents the AI from hallucinating or ignoring previous architectural choices.

- **Simple Prompting**: You can initiate complex features with a single sentence because the AI finds its own context in the logs.

- **Traceable Decisions**: Unlike traditional documentation, logs capture the state of mind and the "Questions & Answers" that led to a specific design.

## Resources
- Full Methodology & Rules: [Why I Stop Prompting and Start Logging: The Design-Log Methodology](https://www.wix.engineering/post/why-i-stop-prompting-and-start-logging-the-design-log-methodology) (Wix Engineering Blog)

- Deep Dive Presentation: [Download the Presentation PDF](./Why%20I%20Stop%20Prompting%20and%20Start%20Logging_%20The%20Design-Log%20Methodology.pdf)

## How to Use This Repo

To implement this methodology, you need to provide your AI agent with the specific "rules of the game."

### The Rule itself

This is a copy of the rule file [design-log-rules.md](./design-log.mdc).

```
---
description: "This rule provides standards for design log files"
alwaysApply: true
---

# Jay Framework Project Rules

## Design Log Methodology

The project follows a rigorous design log methodology for all significant features and architectural changes.

### Before Making Changes
1. **Check design logs** in `./design-log/` for existing designs and implementation notes
2. **For new features**: Create design log first, get approval, then implement
3. **Read related design logs** to understand context and constraints

### When Creating Design Logs
1. **Structure**: Background → Problem → Questions and Answers → Design → Implementation Plan → Examples → Trade-offs
2. **Be specific**: Include file paths, type signatures, validation rules
3. **Show examples**: Use ✅/❌ for good/bad patterns, include realistic code
4. **Explain why**: Don't just describe what, explain rationale and trade-offs
5. **Ask Questions (in the file)**: For anything that is not clear, or missing information
6. **When answering question**: keep the questions, just add answers
7. **Be brief**: write short explanations and only what most relevant
8. **Draw Diagrams**: Use mermain inline diagrams when it makes sense
9. **Define verification criteria**: how do we know the implementation solves the original problem

### When Implementing
1. **Follow the implementation plan** phases from the design log
2. **Write tests first** or update existing tests to match new behavior
3. **Do not Update design log** initial section once implementation started
4. **Append design log** with "Implementation Results" section as you go
5. **Document deviations**: Explain why implementation differs from design
6. **Run tests**: Include test results (X/Y passing) in implementation notes
7. **After Implementation** add a summary of deviations from original design

### When Answering Questions
1. **Reference design logs** by number when relevant (e.g., "See Design Log #50")
2. **Use codebase terminology**: ViewState, Contract, JayContract, phase annotations
3. **Show type signatures**: This is a TypeScript project with heavy type usage
4. **Consider backward compatibility**: Default to non-breaking changes

### On User Feedback
1. **Assess feedback type**: Clarification → answer directly; Bug → fix or design log; Feature → evaluate design log need; Implementation issue → append to existing log
2. **Append to existing design log** if: relates to in-progress work, missed constraint, implementation deviation, or refines existing design
3. **Create new design log** if: new feature, multi-component change, architectural challenge, or affects multiple design logs
4. **Ask clarifying questions** when: goal unclear, scope ambiguous, trade-offs exist, or missing context
5. **Proceed directly** when: feedback specific and actionable, solution straightforward, no significant trade-offs
6. **When uncertain**: State assumptions, propose options (quick fix vs. proper solution), ask for preference

```

### 1. Setup Instructions

#### For Cursor
1. Create a `.cursor/rules` folder in your project root.
2. Copy the file [design-log-rules.md](./design-log.mdc) into that folder.
3. Cursor will now automatically follow the methodology when you use **Composer** or **Chat**.

#### For Claude Code (CLI)
1. Create a `.claude/rules/` folder in your project root.
2. Copy the file [design-log-rules.md](./design-log.mdc) into that folder.

### 2. Initialize the Directory
Create a directory named `design-log` in your project root:
```bash
mkdir design-log
```