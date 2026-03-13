# personalization-data-collection-ops

Use this skill to identify the best data providers for specific personalization signals and understand the operational requirements to extract them.

## Data Source Matrix by Signal Type

### Company Level Signals
| Signal | Best Provider | Cost/Difficulty |
|--------|---------------|-----------------|
| Recent Funding | Crunchbase, PitchBook, Clay (via native integration) | Low |
| Hiring Trends (Generic) | LinkedIn Insights, PredictLeads | Medium |
| Specific Role Openings | Apollo, Clay (Scraping Indeed/LI jobs) | Low |
| Tech Stack Install | BuiltWith, HG Insights, Wappalyzer | Medium/High |
| Press / News | Google News API, Owler | Medium (Requires LLM summarization) |

### Individual Level Signals
| Signal | Best Provider | Cost/Difficulty |
|--------|---------------|-----------------|
| LinkedIn About/Bio | Prospeo, CoPilot, PhantomBuster | High (Rate limits apply) |
| Recent LinkedIn Posts | PhantomBuster, Clay (requires cookie auth) | Very High (Fragile) |
| Podcast/Article mentions| Perplexity API, Google Custom Search | Medium |
| Past Employment History | LinkedIn (via scraping APIs), Apollo | Low |

## Operational Setup Requirements

### 1. The Enrichment Waterfall
Do not rely on a single provider. Set up a waterfall in Clay or n8n:
- **Step 1:** Ask Provider A (Cheapest, e.g., Apollo). If true, stop. If false:
- **Step 2:** Ask Provider B (More expensive, e.g., Clearbit). If true, stop. If false:
- **Step 3:** Ask Provider C (Most expensive, e.g., direct scraping).

### 2. Data Cleaning Before LLM Processing
Raw data from APIs is ugly. It contains HTML tags, legal entities ("Acme Corp LLC"), and irrelevant boilerplate.
- **Operation:** You must run a regex or basic script node to clean the data *before* passing it to an LLM.
- **Example:** Strip "Inc.", "LLC", "GmbH" from company names so the AI sounds human ("Acme" not "Acme Inc.").

### 3. Rate Limit Management
Scraping LinkedIn data is notoriously fragile.
- You absolutely must rotate LinkedIn session cookies if using tools like PhantomBuster.
- For high volume, rely on third-party aggregators rather than direct scraping whenever possible.

## Output Contract
When asked about data sourcing, provide:
- The optimal provider waterfall for the specific signal requested
- The expected cost barrier to entry
- Instructions on how to clean the data output before using it in a campaign
