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

    For each lens, complete steps 2–6 fully before proceeding to the next lens.

2.  **Load the Procedure (Prompt Template):**
    - Read the `prompts/<type>-prompt-template.md` file from the skill directory.
    - Read the `prompts/<type>-documentation-template.md` file (if applicable).
    - _Adopt the persona_ and _follow the analysis steps_ defined in the prompt.

3.  **Check for Existing Document:**
    - Determine the output path for the current lens:
      - `agents-md` → `AGENTS.md` in the project root.
      - All other lenses → `docs/<type>-analysis.md`.
    - Attempt to read that file.
    - If the file **exists**: pass its content to the analysis step as context. The agent enters **update mode** (see the "Update Mode" section in the prompt template).
    - If the file **does not exist**: proceed normally in **create mode**.

4.  **Explore the Target Files:**
    - Use the agent's native file discovery tools (e.g., `list_dir`, `find_by_name`, `grep_search`) to list relevant source files.
    - Read the content of the most relevant files (limit: ~20 files or as needed).
    - _Do not_ dump the entire repository unless explicitly asked. Be selective.

5.  **Execute the Analysis:**
    - Mentally apply the prompt's instructions to the file contents you just read.
    - Perform the step-by-step reasoning (e.g., Domain Discovery, Strategic Analysis).
    - In **update mode**: follow the "Update Mode" instructions in the prompt template — compare the existing document against the current codebase state and produce an updated version.
    - In **create mode**: construct the output from scratch using the documentation template.

6.  **Save the Output:**
    - **`agents-md` lens**: Save the output as `AGENTS.md` in the **root** of the target project (not in `docs/`).
    - **All other lenses**: Save generated documentation to the `docs/` directory in the target project.
    - Naming convention for `docs/`: `docs/<type>-analysis.md` (e.g., `docs/ddd-analysis.md`, `docs/quality-analysis.md`).
    - Create the `docs/` directory if it does not exist.
    - In both **create** and **update** mode, write the complete document to the output path.

## Example Interactions

> "Analyze the `src/modules/orders` directory using the DDD lens."
> "Perform a Quality Assessment on `src/components/Button`."
> "Extract the Ubiquitous Language dictionary from `src/domain`."

## Selective Execution

You can run a **single lens** instead of the full pipeline. When asked to run a specific analysis:

1. Load only the requested lens's prompt and documentation templates.
2. Follow steps 2–5 from the Capabilities section for that single lens.
3. Skip the `judge` lens unless explicitly requested.

**Examples:**

> "Run only the `quality` lens on `src/`."
> "Generate just the `ddd` analysis."
> "Re-run the `judge` lens to validate all docs."

When running selectively, the lens can still reference previously generated docs (e.g., `judge` can read `docs/*.md`), but should not fail if they don't exist.

## Configuration

The following aspects can be customized per-run:

| Option               | Default     | Description                                                                                       |
| -------------------- | ----------- | ------------------------------------------------------------------------------------------------- |
| **Output directory** | `docs/`     | Where analysis markdown files are saved (except `agents-md` → project root)                       |
| **File read limit**  | ~20 files   | Maximum source files to read per lens. Increase for large projects, decrease for focused analysis |
| **Target scope**     | Entire repo | Can be narrowed to a specific directory or module (e.g., `src/domain/`)                           |
| **Output language**  | English     | Language of the generated documentation. Can be changed per instruction                           |

To customize, include the option in your prompt:

> "Analyze `src/` with quality lens, read up to 30 files, output in Polish."

## Limitations

- **Repository size**: Best results on repositories with up to ~500 source files. Larger monorepos should be analyzed per-module.
- **File read limit**: Each lens reads ~20 files by default. Very large codebases may require multiple focused runs.
- **Token context**: Analysis quality depends on the agent's context window. If the repo is very large, critical files might be missed — use targeted scope.
- **Monorepo support**: Not built-in. For monorepos, run the skill on each sub-project separately by specifying the sub-project directory as the target scope.
- **Binary/generated files**: The skill ignores binary files, build artifacts, and generated code. It focuses on human-written source code.
- **Git history**: Some lenses (e.g., `agents-md`, `readme`) use `git log` for temporal analysis. If running on a shallow clone or a repo without git history, these sections will be limited.

## Supported Languages & Frameworks

The skill is **language-agnostic** — it works on any codebase. However, prompt templates contain specific guidance for common stacks:

| Language              | Framework/Build Tool                          | Support Level                              |
| --------------------- | --------------------------------------------- | ------------------------------------------ |
| Java                  | Maven, Gradle, Spring Boot                    | ⭐ Best — most detailed prompt guidance    |
| JavaScript/TypeScript | npm, Node.js, React, Next.js, Angular, NestJS | ⭐ Best                                    |
| Python                | pip, pyproject.toml, Django, FastAPI          | 🟢 Good                                    |
| Go                    | go.mod                                        | 🟢 Good                                    |
| Rust                  | Cargo                                         | 🟡 Basic                                   |
| C#/.NET               | NuGet, .csproj                                | 🟡 Basic                                   |
| Other                 | Any                                           | 🟡 Basic — general analysis patterns apply |

Projects using well-known frameworks get richer analysis because the prompts know what patterns to look for (e.g., Spring Boot conventions, React component patterns).

## Installation

Ensure the `prompts/` directory contains the template files. No external binaries required.
