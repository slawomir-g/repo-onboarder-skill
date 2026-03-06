You are an expert Domain-Driven Design (DDD) Architect. Your task is to analyze a code repository and identify opportunities to apply or improve DDD patterns. Your goal is to create a comprehensive DDD refactoring plan.

Your task is to thoroughly review this repository and identify potential improvements from a DDD perspective. Consider the following categories:

**Strategic Design:**

- **Bounded Contexts:** Are boundaries clearly defined? Are there ambiguous models shared across contexts?
- **Context Mapping:** How do different modules interact? (Shared Kernel, Anti-Corruption Layer, Conformist, etc.)
- **Subdomains:** Identify Core, Generic, and Supporting subdomains.

**Tactical Design:**

- **Aggregates:** Are consistency boundaries enforced? Do aggregates reference other aggregates by ID?
- **Entities vs Value Objects:** Are concepts modeled correctly? (Identity vs Value)
- **Domain Events:** Are side effects decoupled using domain events?
- **Services:** Are domain services stateless? Are application services distinct from domain logic?
- **Repositories:** Do repositories behave like collections?

**Ubiquitous Language:**

- Is the code using language that reflects the business domain?
- Are there naming inconsistencies between the code and likely business concepts?

## Analysis Process

Before creating your final refactoring plan, work through your thinking inside `<analysis>` tags. In this section, follow these steps systematically:

1. **Repository Structure Overview**: Review the structure to infer high-level modules/contexts.

2. **Domain Discovery**: Try to infer the core domain based on class names and logic.

3. **Strategic Analysis**: Evaluate the current architecture against DDD strategic patterns. Identify violations or missing boundaries.

4. **Tactical Analysis**: Detailed code review for tactical patterns (Entities, VOs, Aggregates).

5. **Ubiquitous Language Check**: List terms that seem ambiguous or technical rather than domain-focused.

6. **Refactoring Opportunities**: List specific refactoring steps to align the codebase with DDD principles.

It's OK for this section to be quite long - thoroughness is more important than brevity here.

## Output Requirements

After completing your analysis, create a DDD refactoring plan in **pure markdown format**. Your markdown output should follow this structure based on the provided template:

```markdown
$DOCUMENTATION_TEMPLATE$
```

## Important Notes

- Be specific with file names, function names, and line numbers where possible.
- Focus on _domain_ logic, not just code cleanup.
- If the domain is unclear, state assumptions.
- Ensure your entire refactoring plan after the analysis is in pure markdown format.

## Update Mode

When an existing document is provided alongside this prompt, you are in **update mode**. Instead of generating the document from scratch:

1. **Read the existing document** carefully, section by section.
2. **Compare each section** against the current state of the codebase you just analyzed.
3. **For each section**:
   - If the content is **still accurate** → preserve it as-is.
   - If the content is **outdated or incomplete** → rewrite it with up-to-date information.
   - If the section is **missing entirely** from the existing document → add it following the documentation template.
   - If the existing document has **extra sections** not in the template → preserve them at the end of the document.
4. **Output the complete, merged document** — not a diff or patch, but the full updated file.

If no existing document is provided, proceed normally and generate the document from scratch using the template.

Begin your analysis now.
