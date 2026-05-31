# llm-entity-presence checklist

A condensed, do-this-in-order run. Check each box. Truthful only. Zero em dashes.

## Step 1: Intake
- [ ] Filled `references/intake-template.md` with truthful data only.
- [ ] Locked the exact name string and the canonical domain.
- [ ] Moved any unverifiable claim to "Unconfirmed" (off the public site).

## Step 2: Canonical answer
- [ ] Wrote ONE entity sentence, name first, truthful, no dashes.
- [ ] Binds name + category + strongest qualifier in one self-contained line.
- [ ] Stored it once so the five copies cannot drift.

## Step 3: Build the entity site (server-rendered)
- [ ] Stack serves real HTML to bots (SSR or static; not a blank JS shell).
- [ ] Full head: title (<=60), meta description (<=155), canonical, Open Graph,
      Twitter summary_large_image, robots index/follow with max-image-preview:large,
      author, theme-color, favicon set.
- [ ] Section H2s are declarative entity sentences (claims, not vague labels).
- [ ] Canonical answer appears verbatim in: hero subheader, About lead, FAQ #1.
- [ ] JSON-LD added: Person + Organization + WebSite + FAQPage (+ VideoObject,
      + Review only if real). Person.description = canonical answer verbatim.
      FAQPage text matches the visible FAQ.
- [ ] `llms.txt` at root, real newlines, opens with canonical answer, ends with
      citation guidance. Zero literal backslash-n.
- [ ] `robots.txt` with absolute sitemap URL.
- [ ] `sitemap.xml` lists real canonical URLs only.
- [ ] Deployed to production on the canonical domain.

## Step 4: Off-site backlinks and consistency
- [ ] GitHub profile README set (name repo), bio + website set to the domain.
- [ ] Every social profile: same name, same one-line bio, domain in link field.
- [ ] Cross-linked: site footer + Person.sameAs list all profiles; profiles
      link back to the site.
- [ ] At least one real backlink live (GitHub repo, Gist, partner, directory).

## Step 5: Index
- [ ] IndexNow key file hosted; URLs submitted (see references/indexnow-howto.md).
- [ ] Bing Webmaster Tools: site added, sitemap submitted.
- [ ] Google Search Console: verified, sitemap submitted, indexing requested
      for the home page and key pages (see the GSC checklist).

## Step 6: Verify and tune
- [ ] JS-off curl shows title, H1, canonical sentence, FAQ, and JSON-LD types.
- [ ] llms.txt, robots.txt, sitemap.xml all return 200 and look correct.
- [ ] Structured data validated (Rich Results Test or Schema.org validator).
- [ ] Queried "who is X" in ChatGPT search, Perplexity, Google AI Overviews,
      and Copilot; recorded which cite the site.
- [ ] Logged a tuning list and set a re-check date (indexing is not instant).

## Guardrails (every run)
- [ ] No fabricated testimonials, numbers, reviews, ratings, or commit history.
- [ ] No false platform or partnership claims.
- [ ] Zero em dashes and en dashes in everything produced.
- [ ] A non-developer could follow each step with an agent.
