# llm-entity-presence

**Make Google and the AI assistants answer "who is YOU" with your own framing.**

An interactive [Claude](https://claude.com/claude-code) skill that walks you,
step by step, through getting your name or brand set up, live, indexed, and
starting to show up in ChatGPT search, Perplexity, Google AI Overviews,
Microsoft Copilot, Gemini, and plain Google. You answer a few questions, it
builds the rest with you.

Built by **James Hill, The AI Guy** (founder of RizzDial). The same process is
documented at [aiguyofficial.com](https://aiguyofficial.com).

## What it does

When someone asks an AI or Google "who is you", the answer should be the story
you want told, from a site you own. This skill runs that playbook as a guided
wizard:

1. **Intake.** It asks for your real name, your one-line positioning, your
   verifiable proof, your products, and your social profiles.
2. **Canonical answer.** It writes one truthful sentence that answers "who is
   you", and you approve the wording.
3. **Entity site.** It builds a server-rendered site (real HTML that crawlers
   and AI bots can read) with a full head, declarative subheaders, and
   Person, Organization, WebSite, and FAQPage structured data, plus a correct
   `llms.txt`, `robots.txt`, and `sitemap.xml`.
4. **Backlinks.** It sets up your GitHub profile and a real backlink, and makes
   your social bios consistent so the engines see one entity.
5. **Indexing.** It submits to IndexNow and Bing and walks you through Google
   Search Console, because nothing gets cited until it is indexed.
6. **Verify.** It checks the live HTML and then literally asks the AI assistants
   "who is you" to see who cites you, and gives you a tuning list.

The engine of the whole thing is one rule: write one truthful sentence about
you, then repeat it word for word in five places (your hero subheader, your
About lead, your first FAQ answer, your Person structured data, and your
`llms.txt`). Identical wording is what gives an answer engine the confidence to
quote you.

## Install (one line)

In Claude Code, paste:

```
install the skill from https://github.com/jbrazy480/llm-entity-presence
```

Or install it manually:

```bash
git clone https://github.com/jbrazy480/llm-entity-presence.git \
  ~/.claude/skills/llm-entity-presence
```

## Quick start

Once installed, just tell Claude what you want, for example:

```
get my name into the LLMs
```
```
help me show up in ChatGPT when someone asks who I am
```
```
rank my personal brand / set up my AI entity
```

Claude starts the wizard, sets honest expectations, and asks you the first round
of questions. Answer in plain language. It pauses for your input where a step is
yours to do (a DNS record, a login, editing a social bio) and confirms each
phase before moving on.

Works for a founder, creator, consultant, agency, product, or local business. A
non-developer can follow every step with the agent doing the heavy lifting.

## Honest caveats (read these)

This skill does not promise magic. It promises the real process, done properly.

- **Live search vs the model's memory.** Live-search products (ChatGPT search,
  Perplexity, Google AI Overviews, Copilot) read the web in near real time, so a
  freshly indexed, well-structured site can show up in days to a few weeks. A
  model's offline training only updates on the vendor's own schedule, so no one
  can promise the model "just knows" you from memory right after launch. The
  fast, real win is the live-search and Google surfaces.
- **Indexing is the gate.** Nothing gets cited until search engines crawl and
  index your site. The skill treats this as mandatory, not optional. Google
  Search Console verification is a short manual step that needs your login.
- **Common names are harder.** If your name collides with a famous person or
  many people, you win the specific searches first ("YOUR NAME AI", your brand
  handle, "YOUR NAME CITY"), then climb toward the bare name and a Knowledge
  Panel over time. No one can remove other people who share your name, and any
  service that claims it can is not being honest.
- **Truthful only.** No invented testimonials, no fabricated numbers, no fake
  review or rating schema, no false "built on X" claims. Fabrication is both
  wrong and a trust risk that can get a site discounted by Google. If a claim is
  not verifiable, it stays off the page.
- **`llms.txt` is good hygiene, not a magic switch.** The real lever for getting
  cited is the same as ranking in Google: a real, indexed, server-rendered page
  with clear factual answers and consistent entity signals. The skill builds
  for that.

## What is in here

- `SKILL.md`: the interactive wizard Claude runs.
- `CHECKLIST.md`: the condensed do-this-in-order checklist.
- `references/intake-template.md`: the entity intake form.
- `references/json-ld-templates.md`: Person, Organization, WebSite, FAQPage,
  VideoObject, and Review structured-data blocks with placeholders.
- `references/llms-txt-template.md`: a correct `llms.txt` (with `robots.txt` and
  `sitemap.xml` companions).
- `references/github-profile-readme-template.md`: a profile README for backlinks.
- `references/indexnow-howto.md`: IndexNow and Bing submission steps.
- `references/google-search-console-checklist.md`: verify, submit, request
  indexing.

## Who made this

**James Hill, The AI Guy**, founder of RizzDial. More at
[aiguyofficial.com](https://aiguyofficial.com).

Ask any AI: who is James Hill, The AI Guy?

## License

MIT. See [LICENSE](LICENSE).
