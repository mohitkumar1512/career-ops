# Mode: deep — Deep Research Prompt

## Language

This mode is **user-facing**: the output is a research/interview-prep doc the
user reads, not application content sent to the company. Override the shared
"language of the JD (EN default)" rule for this mode and resolve the output
language in this order:

1. **User prompt language** — if the user wrote `/career-ops deep` (or its
   surrounding chat) in Spanish, French, German, Japanese, etc., emit the
   doc in that language.
2. **`config/profile.yml`** — if `language.modes_dir` is set
   (`modes/de`, `modes/fr`, `modes/ja`), prefer that locale.
3. **JD language** — only as a last resort, when the user prompt has no
   language signal (e.g., a bare URL with no surrounding chat).

Generate a structured prompt for Perplexity/Claude/ChatGPT with 6 axes:

```
## Deep Research: [Company] — [Role]

Context: I'm evaluating an application for [role] at [company]. I need actionable information for the interview.

### 1. AI Strategy
- What products/features use AI/ML?
- What is their AI stack? (models, infra, tools)
- Do they have an engineering blog? What do they publish?
- What papers or talks have they given about AI?

### 2. Recent moves (last 6 months)
- Relevant hires in AI/ML/product?
- Acquisitions or partnerships?
- Product launches or pivots?
- Funding rounds or leadership changes?

### 3. Engineering culture
- How do they ship? (deploy cadence, CI/CD)
- Mono-repo or multi-repo?
- What languages/frameworks do they use?
- Remote-first or office-first?
- Glassdoor/Blind reviews on eng culture?

### 4. Likely challenges
- What scaling problems do they have?
- Reliability, cost, latency challenges?
- Are they migrating anything? (infra, models, platforms)
- What pain points do people mention in reviews?

### 5. Competitors and differentiation
- Who are their main competitors?
- What is their moat/differentiator?
- How do they position vs competition?

### 6. Candidate angle
Given my profile (read from cv.md and profile.yml for specific experience):
- What unique value do I bring to this team?
- Which of my projects are most relevant?
- What story should I tell in the interview?
```

Tailor each section with the specific context of the evaluated role,
in the language resolved in the **Language** section above.
