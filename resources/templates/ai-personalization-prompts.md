# AI Personalization Prompts

Production-ready prompt templates for use in Clay, n8n, or directly in LLM APIs to generate high-quality, human-sounding hooks.

## Prompt 1: The "Recent News" Summarizer

**Goal:** Turn a dense press release or news article snippet into a casual, 10-15 word observation.

**System Prompt:**
```text
You are an SDR at a B2B tech company. Your writing style is casual, brief, and slightly cynical. You never use marketing jargon. You use lowercase for everything except proper nouns.
```

**User Prompt:**
```text
Read this snippet of news about {{company_name}}:

"[Insert News Snippet from Data Provider]"

Extract the single most important strategic event from this text (e.g., an acquisition, a new product launch, a major hire).
Write a 1-sentence observation to open a cold email.
Start with "saw " or "noticed ".
Max length: 15 words.
Do not use words like: excited, thrilled, innovative, pioneer, landscape, delving.

Example Good Output: "saw you guys just acquired Acme to expand into the EU market."
Example Bad Output: "Noticed that your innovative company recently completed a strategic acquisition of Acme to dominate the European landscape."
```

## Prompt 2: The "Hiring Post" Hook

**Goal:** Reference a specific open role to highlight an impending operational challenge.

**User Prompt:**
```text
{{company_name}} is currently hiring for a {{job_title_open_role}}. Here is a snippet from the job description:
"[Insert Job Description Snippet]"

Write a 1-sentence observation about *why* they are hiring this person based on the snippet.
Start with "saw you're looking for a [role] to help with [specific objective]."
Max length: 20 words.
Keep it extremely casual. No jargon.
```

## Prompt 3: The "LinkedIn Bio" Extractor

**Goal:** Pull the core philosophy or main responsibility out of a prospect's LinkedIn 'About' section.

**User Prompt:**
```text
Here is the LinkedIn bio for {{first_name}}, who is the {{current_job_title}} at {{company_name}}:
"[Insert Bio Snippet]"

Identify the one specific metric or core responsibility they care about most based on this text.
Write a 1-sentence hook referencing this.
Format: "noticed in your bio that you're heavily focused on [metric/responsibility]..."
Max length: 15 words.
If the bio is completely blank or generic (e.g. "experienced professional with a demonstrated history..."), return exactly the word "FAILED_EXTRACTION".
```

## Prompt 4: The "Tech Stack" Transition

**Goal:** Connect their adoption of a specific software to the common pain point associated with it.

**User Prompt:**
```text
I see that {{company_name}} recently installed {{technology_name}} on their website.
Write a 1-sentence hook noting this installation.
Format: "noticed you guys are running [technology] over at [Shortened Company Name]."
Note: Strip any "Inc" or "LLC" from the company name.
Max length: 12 words.
```

## The Quality Gate "Judge" Prompt

**Goal:** An automated secondary check to run on the outputs of the prompts above before sending.

**System/User Prompt:**
```text
Evaluate the following email sentence: "{{generated_hook}}"
Answer ONLY with "PASS" or "FAIL".
Rules for FAILURE:
- Contains more than 20 words.
- Contains the words: synergy, innovative, thrilled, excited, landscape, delve.
- Sounds like a corporate press release.
If it passes all rules, type "PASS".
```
