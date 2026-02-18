# Repo Onboarder Skill

A skill for OpenClaw that provides specialized code analysis prompts based on [repo-onboarder-mcp](https://github.com/slawomir-g/repo-onboarder-mcp).
This skill equips the agent with architectural "lenses" (DDD, Quality, Refactoring) to analyze codebases directly.

## Capabilities

The skill defines specialized analysis procedures:
- **DDD Analysis:** Evaluate Strategic & Tactical design patterns.
- **Quality Assessment:** Review SOLID principles, Clean Code, and potential smells.
- **Refactoring Plan:** Identify and structure refactoring opportunities.
- **Dictionary Extraction:** Extract ubiquitous language and domain terms.
- **Documentation Generation:** Create READMEs or AI-optimized context summaries.

## Installation

1.  Navigate to the skill directory:
    ```bash
    cd skills/repo-onboarder
    ```

2.  Ensure the `prompts/` directory contains the `.md` templates.

No build or dependencies required. The agent uses its native tools (`read`, `exec`, `find`) to execute the analysis.

## Usage

Ask the agent to perform a specific analysis on a directory:

> "Analyze the `src/modules/orders` directory using the DDD lens."
> "Perform a Quality Assessment on `src/components/Button`."
> "Extract the Ubiquitous Language dictionary from `src/domain`."

The agent will automatically load the relevant prompt template and apply it to the files in the target directory.
