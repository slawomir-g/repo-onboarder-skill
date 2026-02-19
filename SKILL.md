---
name: repo-onboarder
description: Analyze codebases using specialized architectural lenses (DDD, Quality, Refactoring) based on repo-onboarder-mcp logic.
homepage: https://github.com/slawomir-g/repo-onboarder-mcp
metadata: { "clawdbot": { "emoji": "🔍", "requires": { "bins": ["find"] } } }
---

# Repo Onboarder Skill

Analyze codebases using specialized architectural lenses (DDD, Quality, Refactoring) directly with native tools (`read`, `find`, `exec`).

## Capabilities

When asked to "analyze repository", "onboard codebase", or "generate documentation":

1.  **Execute All Analysis Lenses Step by Step:**
    Run each analysis type sequentially, completing one before starting the next. The execution order is:
    1. `ai-context`: AI-optimized context summary.
    2. `ddd`: Domain-Driven Design (Strategic & Tactical patterns).
    3. `dictionary`: Ubiquitous Language / Dictionary.
    4. `quality`: Quality Assessment (SOLID, Clean Code).
    5. `refactoring`: Refactoring suggestions.
    6. `readme`: Generate documentation.
    7. `judge`: Validation of generated documentation against repository context.

    For each lens, complete steps 2–5 fully before proceeding to the next lens.

2.  **Load the Procedure (Prompt Template):**
    - Read the `prompts/<type>-prompt-template.md` file from the skill directory.
    - Read the `prompts/<type>-documentation-template.md` file (if applicable).
    - _Adopt the persona_ and _follow the analysis steps_ defined in the prompt.

3.  **Explore the Target Files:**
    - Use `exec find <path> -maxdepth <depth> ...` to list relevant source files (default depth: 5).
    - Use `read` to load the content of the most relevant files (limit: ~20 files or as needed).
    - _Do not_ dump the entire repository unless explicitly asked. Be selective.

4.  **Execute the Analysis:**
    - Mentally apply the prompt's instructions to the file contents you just read.
    - Perform the step-by-step reasoning (e.g., Domain Discovery, Strategic Analysis).
    - Construct the final output using the provided documentation template.

5.  **Save the Output:**
    - Save generated documentation to the `docs/` directory in the target project.
    - Naming convention: `docs/<type>-analysis.md` (e.g., `docs/ddd-analysis.md`, `docs/quality-analysis.md`).
    - Create the `docs/` directory if it does not exist.

## Example Interactions

> "Analyze the `src/modules/orders` directory using the DDD lens."
> "Perform a Quality Assessment on `src/components/Button`."
> "Extract the Ubiquitous Language dictionary from `src/domain`."

## Installation

Ensure the `prompts/` directory contains the template files. No external binaries required.
