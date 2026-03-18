# Validation Checklist

Use this checklist after changing a skill.

## Core Files

- `SKILL.md` exists
- YAML frontmatter is present
- `name` is hyphen-case and under the length limit
- `description` clearly explains when the skill should be used
- `agents/openai.yaml` exists when UI metadata matters

## Metadata And Trigger Quality

- `agents/openai.yaml` display name matches the skill purpose
- `short_description` is consistent with the frontmatter description
- `default_prompt` explicitly mentions `$skill-name`
- the trigger description is narrow enough to avoid accidental over-invocation

## Internal Consistency

- references linked from `SKILL.md` exist
- referenced scripts or assets exist if mentioned
- handoffs to other skills are intentional
- the workflow in the body still matches the references
- there are no stale claims about files or steps that no longer exist

## Maintenance Quality

- `SKILL.md` stays concise
- references hold detailed reusable material instead of bloating the core file
- there are no unnecessary README or process-history files
- the skill does not duplicate another skill without a clear boundary

## Validation Result

Close with one of:

- validator passed
- fallback validation passed
- validation blocked with known issues
