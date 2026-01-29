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