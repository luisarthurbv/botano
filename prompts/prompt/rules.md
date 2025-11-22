# Prompt Authoring Rules

## Goals
- **Clarity**: State the exact objective, audience, and constraints.
- **Determinism**: Reduce ambiguity with explicit formats and acceptance criteria.
- **Grounding**: Provide all needed context and data. Avoid requiring outside assumptions.

## Structure Your Prompt
- **System/role**: Define the assistant’s role and boundaries.
- **Task**: One sentence describing the primary objective.
- **Context**: Inputs, background, domain rules, links, or files.
- **Constraints**: Limits, policies, time, tools, or APIs allowed.
- **Output format**: Exact schema, headings, code block languages, or JSON shape.
- **Style guide**: Tone, brevity, bullet rules, or citation style.
- **Edge cases**: Known tricky conditions and how to handle them.
- **Quality checks**: Checklist or tests the output must pass.

## Do / Don’t
- **Do**: Be explicit, give examples, show negative examples, and set evaluation criteria.
- **Do**: Use numbered steps and checklists for multi-part tasks.
- **Do**: Pin units, versions, and definitions (e.g., timezone, locale, currency).
- **Don’t**: Ask for unspecified data; instead, ask the model to request missing info.
- **Don’t**: Mix multiple unrelated tasks in one prompt.
- **Don’t**: Rely on implicit defaults; always define.

## Output Formatting
- Prefer deterministic structures.
- Specify headings and list style.
- For JSON, provide an exact schema and example. Instruct: “Return only JSON.”
- For code, specify language fences, runtime, and expected entrypoint.

## Evaluation and Safety
- Add a self-check step: ask the model to verify constraints before finalizing.
- Require citation or quoting for external facts when applicable.
- For sensitive actions or tools, require explicit user confirmation steps.

## Iteration Workflow
- Start with a minimal prompt → test → add constraints → add examples → lock format.
- Version prompts. Keep a change log and test cases for regressions.

---

## Reusable Meta-Prompt: “Create a Prompt by Calling a Prompt”

Use this when you want the model to generate a high-quality prompt for a task. Fill the placeholders and run it as a single prompt to produce a finalized prompt you can reuse.

```text
You are a prompt engineer. Create a single, production-ready prompt for an AI assistant to accomplish the task described below. Output only the final prompt, nothing else.

Inputs for prompt design:
- Goal: <clear objective>
- Audience/Users: <who will use the output>
- Context/Artifacts: <links, files, data, definitions>
- Tools/Permissions: <allowed tools/APIs and constraints>
- Constraints: <time limits, policies, formats, domains>
- Output Format: <exact headings/JSON schema/code fences>
- Style Guide: <tone, brevity, formatting rules>
- Edge Cases: <tricky cases to handle>
- Acceptance Criteria: <tests or checklist>

Requirements for the prompt you produce:
1) Include role definition, task, context, constraints, output format, style, edge cases, and a self-check step.
2) Make all requirements explicit and testable. Avoid ambiguity.
3) Instruct the assistant to request any missing information before proceeding.
4) If a schema is specified, require strict adherence (e.g., “Return only JSON in this schema”).
5) Keep it concise and actionable.

Return only the final prompt, formatted for direct use.
```

## Example JSON Schema Instruction

```text
Return only valid JSON matching this schema:
{
  "title": "string",
  "summary": "string",
  "items": [
    { "id": "string", "status": "pending|in_progress|completed", "priority": "low|medium|high" }
  ]
}
```

## Quick Checklist
- **Objective** defined in one sentence
- **Role** and boundaries set
- **Context** sufficient and scoped
- **Constraints** explicit and testable
- **Format** exact and deterministic
- **Examples** positive and negative
- **Edge cases** covered
- **Self-check** and confirmation steps

