---
name: repo-onboarder
description: Analyze codebases using specialized architectural lenses (DDD, Quality, Refactoring) based on repo-onboarder-mcp logic.
homepage: https://github.com/slawomir-g/repo-onboarder-mcp
metadata: {"clawdbot":{"emoji":"🔍","requires":{"bins":["find"]}}}
---

# Repo Onboarder Skill

Analyze codebases using specialized architectural lenses (DDD, Quality, Refactoring) directly with native tools (`read`, `find`, `exec`).
Based on [repo-onboarder-mcp](https://github.com/slawomir-g/repo-onboarder-mcp).

## Capabilities

When asked to "analyze code", "perform DDD analysis", "assess quality", or "extract domain dictionary":
1.  **Select the Analysis Type:**
    - `ddd`: Domain-Driven Design (Strategic & Tactical patterns).
    - `quality`: Quality Assessment (SOLID, Clean Code).
    - `refactoring`: Refactoring suggestions.
    - `dictionary`: Ubiquitous Language / Dictionary.
    - `readme`: Generate documentation.
    - `ai-context`: AI-optimized context summary.

2.  **Load the Procedure (Prompt Template):**
    - Read the `prompts/<type>-prompt-template.md` file from the skill directory.
    - Read the `prompts/<type>-documentation-template.md` file (if applicable).
    - *Adopt the persona* and *follow the analysis steps* defined in the prompt.

3.  **Explore the Target Files:**
    - Use `exec find <path> -maxdepth <depth> ...` to list relevant source files (default depth: 3).
    - Use `read` to load the content of the most relevant files (limit: ~20 files or as needed).
    - *Do not* dump the entire repository unless explicitly asked. Be selective.

4.  **Execute the Analysis:**
    - Mentally apply the prompt's instructions to the file contents you just read.
    - Perform the step-by-step reasoning (e.g., Domain Discovery, Strategic Analysis).
    - Construct the final output using the provided documentation template.

## Example Interactions

> "Analyze the `src/modules/orders` directory using the DDD lens."
> "Perform a Quality Assessment on `src/components/Button`."
> "Extract the Ubiquitous Language dictionary from `src/domain`."

## Installation

Ensure the `prompts/` directory contains the template files. No external binaries required.
