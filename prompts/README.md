# How to use this Prompt System

1. **Master Prompt** is your main blueprint. Keep it versioned (v1, v2...).
2. **Changelog** - Write WHY you changed something. Future you will thank you.
3. **Modules** - Break big prompt into small reusable parts for focused AI tasks.
4. **Micro Prompt Template** - For daily small fixes.

## Workflow for future update:

When you want to add a feature:
1. Copy prompts/master_prompt_v1.md -> prompts/master_prompt_v2.md
2. Edit v2 with new requirement
3. Add entry to changelog.md
4. Use this prompt to AI: "Read prompts/master_prompt_v2.md and implement it"

When you want to fix a bug:
1. Use a micro prompt from micro_prompt_template.md
2. Don't touch master prompt.

## For Cursor / VS Code users:
- .cursor/rules/project.mdc and .github/copilot-instructions.md already contain summary.
- AI will auto-follow them.
