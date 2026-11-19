# AI negative-answer source review prompt

A prompt for finding the web pages behind negative AI answers about a brand, checking what those pages actually say, and building a source-review list.

It's written for [Letaido](https://letaido.com) with [Ahrefs Brand Radar](https://ahrefs.com/brand-radar) data and [Apify](https://apify.com) for scraping. It should work with any AI agent that can read your AI-visibility tracking data and scrape web pages.

## How to use it

1. Copy the prompt below.
2. Replace everything in **[brackets]** with your own brand, domains, competitors, assistants, country, and date range.
3. Review every match yourself before contacting anyone. Sentiment labels, claim extraction, and passage classification are all automated and will make mistakes.

## The prompt

```text
Using my Ahrefs Brand Radar data, find the web pages behind negative AI answers about [Brand] and build me a source-review list.

Scope: brand [Brand] (domains: [brand.com, …]); competitors [Competitor A, B, …]; assistants [ChatGPT, Gemini, Perplexity, Copilot]; country [US]; date range [last 30 days]. Use only answers labelled negative about [Brand] that have citations.

1. Pull the answers. Fetch every negative answer in scope with its full text, assistant, date, and the pages it cites or lists.

2. Extract the claims. From each answer, list every distinct claim that presents a disadvantage, cost, or limitation of [Brand], with the exact quote and the source it sits next to. Group similar claims into recurring objections (e.g. "high fees," "account holds"), and keep different claims separate.

3. Map the sources. Group the pages as owned ([Brand]'s domains), competitor, or third party. Count how many answers cite each page and on how many days, so I can see which keep coming back.

4. Check the pages. Scrape each page with Apify. For every objection, find the passage on the page that states it, and quote it verbatim (max 40 words), including any context the answer left out. If a page couldn't be read, mark it "couldn't read." Don't count it as not supporting the claim.

5. Classify each passage:
   - Negative claim: the page itself criticizes [Brand] or compares it unfavorably.
   - Neutral fact: it only states a price, rate, or feature, which the AI turned into a criticism.
   - Not supported: the page was read and doesn't say it.
   Check every quote against the page text and drop any that don't match exactly.

6. Build the report: a chart of cited pages by group (owned, competitor, third party), the top recurring objections, and a source-review list showing each page's URL, objection, verbatim quote, answers citing it, and days cited. Flag a page for correction outreach only when you can identify a factual error, an outdated claim about the current product, or missing context that materially changes its meaning, and include evidence for the proposed correction. List accurate criticism and subjective opinions separately. List pages where AI misread neutral facts separately too; they need clearer content on our side, not outreach.

7. Optional: for each page flagged for outreach, find the author's public contact details and draft a short, friendly correction request with the exact passage and the evidence.

Flag anything you're unsure about. I'll review every match before contacting anyone.
```

## Things to keep in mind

- A cited page is associated with an answer. That doesn't prove the page caused the criticism.
- A page making a negative claim doesn't necessarily need correcting. Fair criticism is product feedback, not an outreach target.
- A correction on a source page doesn't guarantee AI answers will change. Re-check the same prompts afterwards and track the two separately.
