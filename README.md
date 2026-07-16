# User Story Solution Architect

A reusable **Cursor skill** that acts as a Solution Architect: it turns a rough
feature ask into an **implementation-ready Salesforce user story** — a concrete
business persona, **Given/When/Then** acceptance criteria in business language, a
Technical Implementation section, verified components, and effort sizing — in minutes.

It is **vertical-agnostic**: the SA discipline is universal, and the domain knowledge
is a drop-in reference file. Works for **PNM, Health & Life Sciences, Insurance, FSC,
Comms**, or a **custom greenfield** org — on an existing codebase or a brand-new build.

## What it produces

Every generated story follows one contract:

- **Concrete persona** — a real business role, never "the user".
- **Given / When / Then** acceptance criteria written in business language.
- **Technical Implementation** table — components + change type.
- **Definition of Done** and a **Clarification Questions** table for unknowns.
- **Effort sizing** (S / M / L / XL / XXL).
- **Grounded components** — verified against the codebase (falls back gracefully when
  no code-graph is available; proposes + flags on greenfield).

## Install

The skill lives under `.cursor/`, which Cursor auto-loads.

### Project-level (per repository) — recommended

```bash
# From the root of THIS repo, copy the .cursor payload into your target repo:
cp -R .cursor /path/to/your-project/

# or clone and copy:
git clone https://github.com/p-kothapalli/user-story-solution-architect.git
cp -R user-story-solution-architect/.cursor /path/to/your-project/
```

Reload the Cursor window. Done — it activates automatically.

### User-level (available in every workspace)

Copy the skill folder into your user-level Cursor skills directory (confirm the exact
path in **Cursor → Settings → Rules & Skills**), then copy the rule alongside your
other user rules:

```bash
cp -R .cursor/skills/user-story-architect ~/.cursor/skills/
```

## Use

In a repo with the skill installed, just ask in natural language:

- "Write a user story for &lt;capability&gt;"
- "Break this scope doc into stories"
- "Fix story for defect &lt;id&gt;"

It detects the workflow mode (new / refactor / epic / bug), asks 5–16 clarifying
questions, verifies components, and generates the story in the canonical format.

## Verify it loaded

Type *"write a user story for a test field"* — if it responds by asking which vertical
and a few clarifying questions, it's installed correctly.

## Optional: component grounding via MCP

For full structural grounding (caller/dependent/test context), configure the
`code-review-graph` MCP server in your `.cursor/mcp.json`. Without it the skill still
works — it falls back to file search.

## Repository layout

```
.cursor/
  skills/user-story-architect/
    SKILL.md                      # the skill (navigational overview)
    references/                   # AC patterns, output template, object models, examples
    evaluations/                  # eval scenarios + rubric
  rules/
    use-user-story-solution-architect.mdc   # trigger rule
```

## Notes

- Ships with a PNM (Provider Network Management) knowledge pack as the first vertical.
  Add a new vertical by dropping a `references/<vertical>-object-model.md`.
- The skill is versioned; see the Version History table in `SKILL.md`.
