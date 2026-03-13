# personalization-quality-scoring

Use this skill to evaluate the output of your personalization engine (human or AI) before it reaches the prospect's inbox. Protect the brand reputation.

## The 5-Point Quality Rubric

Score every hook or personalized intro on the following criteria (0-2 points each). A passing score is 7+.

### 1. Relevance to the Pitch (0-2 pts)
Does the observation logically lead to the problem you solve?
- **0 pts:** Complete disconnect ("Go Yankees. Need a CRM?")
- **1 pt:** Weak connection ("Saw you use Salesforce, we help with data.")
- **2 pts:** Tight alignment ("Saw you just rolled out Salesforce CPQ, usually that means quoting errors are spiking. We fix that.")

### 2. Specificity (0-2 pts)
Could you send this same exact sentence to another person at a different company?
- **0 pts:** Yes, easily ("Looks like things are growing fast at Acme.")
- **1 pt:** Yes, but only to a small subset ("Saw Acme is hiring engineers.")
- **2 pts:** Absolutely not, it only applies to them ("Loved your podcast episode where you discussed the challenge of scaling Kubernetes clusters across three regions.")

### 3. Length Constraints (0-2 pts)
Is it too long to read on mobile?
- **0 pts:** Over 25 words/3 lines.
- **1 pt:** 15-25 words.
- **2 pts:** Under 15 words. Punchy.

### 4. Tone and Formality (0-2 pts)
Does it sound like a confident peer?
- **0 pts:** Overly deferential ("I hope you don't mind me reaching out...") or overly aggressive.
- **1 pt:** Polite but slightly stiff/corporate.
- **2 pts:** Casual, peer-to-peer, professional.

### 5. AI "Tells" (0-2 pts)
Does it sound like ChatGPT wrote it?
- **0 pts:** Uses buzzwords ("delve", "landscape", "innovative"), weird formatting, or sounds overly enthusiastic.
- **1 pt:** A bit robotic but passable.
- **2 pts:** Sounds like a tired human wrote it on a Tuesday morning.

## Output Contract
When asked to evaluate a hook or email intro, provide:
- A score out of 10 based on the rubric above
- Specific line-item deductions where the copy failed
- A rewritten version of the hook that achieves an 8+ score
