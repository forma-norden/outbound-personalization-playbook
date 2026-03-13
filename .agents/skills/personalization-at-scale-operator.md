# personalization-at-scale-operator

Use this skill to design the infrastructure required to personalize
hundreds or thousands of emails per week using AI and data enrichment.

## The AI Personalization Architecture

You cannot personalize at scale by copy-pasting into ChatGPT. You need an automated ingestion and processing engine (like Clay, n8n, or Waterfall).

### Layer 1: Data Ingestion
- **Input:** Raw list of target contacts (Apollo, ZoomInfo, LinkedIn).
- **Enrichment:** Use multiple data providers to pull in specific fields (e.g., Company description, recent news, LinkedIn bio, tech stack).

### Layer 2: The LLM Processing Engine
This is where the magic happens. Do not ask an LLM to "write a personalized email." That fails. Ask the LLM to write *one specific sentence* based on the input data.

**The Workflow:**
1. Determine the best data point available for a contact (Waterfall logic).
2. Pass *only* that relevant data point to the LLM (e.g., just the company's recent series A funding paragraph).
3. Instruct the LLM to write a 10-15 word hook summarizing that specific point.

### Layer 3: Quality Gates (The "Human Wrapper")
AI will hallucinate. You need automated checks.
- **Length Check:** If the AI output is > 20 words, reject it.
- **Jargon Check:** Use a regex filter or secondary LLM prompt to automatically reject outputs containing words like "synergy," "landscape," or "innovative."
- **Fallback Logic:** If the AI output fails a check, or if no data was found in Layer 1, output a default, highly segmented industry hook instead.

### Layer 4: The Sequencer
- Map the approved AI output column to a custom variable in your sending tool (e.g., `{{custom_hook}}`).
- The final email template looks like: `Hey {{first_name}},\n\n{{custom_hook}}.\n\n[Standard Value Prop]...\n\n[CTA]`

## Output Contract
When advising on an at-scale setup, provide:
- The data providers needed for the desired personalization
- The specific prompt structure required for the LLM step
- The quality gate rules to prevent bad emails from sending
- The exact fallback string if processing fails
