---
name: repo-onboarder-skill
description: Comprehensive codebase onboarding — generates AGENTS.md, DDD analysis, domain dictionary, quality assessment, refactoring suggestions, README, and validation documentation.
homepage: https://github.com/slawomir-g/repo-onboarder-skill
---

# Repo Onboarder Skill

Analyze codebases using specialized architectural lenses (DDD, Quality, Refactoring) directly with native tools (`read`, `find`, `exec`).

## Capabilities

When asked to "analyze repository", "onboard codebase", or "generate documentation":

1.  **Execute All Analysis Lenses Step by Step:**
    Run each analysis type sequentially, completing one before starting the next. The execution order is:
    1. `agents-md`: Generates `AGENTS.md` — the standard instruction file for AI coding assistants.
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
    - Use the agent's native file discovery tools (e.g., `list_dir`, `find_by_name`, `grep_search`) to list relevant source files.
    - Read the content of the most relevant files (limit: ~20 files or as needed).
    - _Do not_ dump the entire repository unless explicitly asked. Be selective.

4.  **Execute the Analysis:**
    - Mentally apply the prompt's instructions to the file contents you just read.
    - Perform the step-by-step reasoning (e.g., Domain Discovery, Strategic Analysis).
    - Construct the final output using the provided documentation template.

5.  **Save the Output:**
    - **`agents-md` lens**: Save the output as `AGENTS.md` in the **root** of the target project (not in `docs/`).
    - **All other lenses**: Save generated documentation to the `docs/` directory in the target project.
    - Naming convention for `docs/`: `docs/<type>-analysis.md` (e.g., `docs/ddd-analysis.md`, `docs/quality-analysis.md`).
    - Create the `docs/` directory if it does not exist.

6.  **Download Tech Stack Instructions (after all lenses):**
    - Read the `prompts/instructions-prompt-template.md` file from the skill directory and follow its procedure.
    - This step reads the generated `AGENTS.md` to identify the tech stack, then downloads community-maintained instruction files from [awesome-copilot](https://github.com/github/awesome-copilot/tree/main/instructions) into `.github/instructions/`.

## Example Interactions

> "Analyze the `src/modules/orders` directory using the DDD lens."
> "Perform a Quality Assessment on `src/components/Button`."
> "Extract the Ubiquitous Language dictionary from `src/domain`."

## Installation

Ensure the `prompts/` directory contains the template files. No external binaries required.
