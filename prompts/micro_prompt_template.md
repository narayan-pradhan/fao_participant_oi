# Micro Prompt Templates
Use these for small fixes. Don't use master prompt for small bugs.

## Template 1: Bug Fix
---
Context: Read prompts/master_prompt_v1.md. You are working on NSE F&O Automation project (v1.0).

Task: Fix ONLY this bug: [DESCRIBE BUG IN ONE LINE, e.g., "fetch_daily_data.py gets 403 from NSE"]

File to edit: [e.g., fetch_daily_data.py]
Constraint: Do NOT modify other files. Do NOT change HTML structure.

Expected output: Provide only the fixed file content with explanation of what was changed.

---

## Template 2: Feature Addition
---
Context: Read prompts/master_prompt_v1.md and prompts/changelog.md. Current version is v1.0.

New Feature to add for v1.1: [DESCRIBE FEATURE, e.g., "Add Hindi translation in Layman's Story"]

Deliverables:
1. Updated file(s)
2. Changelog entry for v1.1

---

## Template 3: Enhancement / Refactor
---
Context: Project is NSE F&O Automation. Refer to master_prompt_v1.md.

Goal: Improve [e.g., HTML co-relation UX] without breaking existing pipeline.

Current issue: [Describe]

Improve it by: [Describe]

---

## Template 4: Quick Question to AI
---
I have a project defined in prompts/master_prompt_v1.md.

Question: [Your question]

Don't generate code, just explain the best approach with pros/cons.
