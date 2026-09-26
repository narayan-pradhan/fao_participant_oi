# HOW TO CREATE V2, V3 WITHOUT MISTAKES - Step by Step

## The 5-Minute Process

### Step 1: Copy, Don't Edit
NEVER edit v1.0 directly.
```
prompts/master_prompt_v1.md  -> Copy to -> prompts/master_prompt_v2.md
```

### Step 2: Add "WHAT CHANGED" at top
At the top of v2.md, add 3-4 lines summary:
```
## WHAT CHANGED IN V2
- NEW: ...
- FIX: ...
- CLOSED: Q1, Q2
```
This helps AI focus only on delta, not re-read whole doc.

### Step 3: Close Open Questions
In Section 7, move question from OPEN to CLOSED and add final decision:
Before:
  Status: OPEN
After:
  Status: CLOSED on 2026-10-01
  Final URL: https://...

### Step 4: Add "WHAT NOT TO TOUCH"
This is CRITICAL to prevent AI from breaking working code:
```
## 10. WHAT TO KEEP / WHAT NOT TO TOUCH
- DO NOT TOUCH: .github/workflows/daily-publish.yml
- TOUCH ONLY: fetch_daily_data.py, generate_story.py
```

### Step 5: Update changelog.md
Add entry BEFORE you ask AI to code. This forces you to think clearly.

### Step 6: Use this Micro Prompt to call AI

> "Read prompts/master_prompt_v2.md and prompts/changelog.md
>  Current production is v1.0 and works.
>  Implement ONLY the delta mentioned in 'WHAT CHANGED IN V2'.
>  Respect 'WHAT NOT TO TOUCH' list.
>  Output: Updated files + changelog confirmation."

## Common Mistakes to Avoid

1.  MISTAKE: Editing v1 directly -> You lose rollback. FIX: Always copy to v2.
2.  MISTAKE: Using big master prompt for small bug -> AI rewrites whole project. FIX: Use micro_prompt_template.md for bugs.
3.  MISTAKE: Leaving question OPEN but expecting AI to guess correctly. FIX: Add Assumption + Instruction to AI.
4.  MISTAKE: Not telling AI what NOT to touch -> AI breaks working workflow. FIX: Add Section 10.
5.  MISTAKE: Vague feature: "Make story better". FIX: Be specific: "Add Hindi translation using deep-translator, keep FII/OI in English".

## Example of Good vs Bad Update Request

BAD: "Add Hindi to story and fix graph"
- AI doesn't know which library, which dialect, which graph?

GOOD: "In generate_story.py, after generating English story, add Hindi translation using deep-translator library (from deep_translator import GoogleTranslator). Keep technical terms FII, DII, OI in English. Save to data/story/YYYY-MM-DD.json with keys en, hi. Update index.html section id='layman-story' to show both with tabs."
- AI has exact library, exact file, exact logic.

