# Google Search Console checklist

Google AI Overviews and classic Google results both depend on Google having
crawled and indexed the site. This is the gate. Do it on launch day.

## 1. Add and verify the property

- Use a Domain property (covers http, https, and all subdomains).
- Verify with a DNS TXT record at the domain's DNS host (most robust). Google
  gives you a `google-site-verification=...` TXT value to add.
- Confirm verification succeeds in Search Console before moving on.

## 2. Submit the sitemap

- In Search Console, open Sitemaps and submit `https://DOMAIN/sitemap.xml`.
- Confirm it is read with status Success and the expected URL count.

## 3. Request indexing of the pillar pages

- Use URL Inspection on the home page URL, then "Request indexing".
- Repeat for the most important pages (about, key product pages).
- There is a small daily quota, so prioritize the few pages that matter most.
- Indexing is not instant. It can take from a day to a couple of weeks. Check
  back and re-request if a page is still "Discovered, not indexed".

## 4. Speed up discovery with a backlink

- A single real, strong inbound link (for example the GitHub profile or repo,
  or a real partner site) helps Google find and trust the site faster. See the
  GitHub profile README template.

## 5. Bing Webmaster Tools

- Add the site (import from Search Console is fastest), submit the sitemap, and
  submit the home page. See the IndexNow how-to for the API path.

## 6. Monitor and tune

- Watch Coverage and Pages reports for indexing status and errors.
- Use the Performance report to see which "who is X" style queries surface the
  site once it is indexed.
- Re-check on a schedule (for example weekly) until the entity appears.

## Common gotchas

- The site must serve real HTML (not a blank JavaScript shell), or Google may
  index almost nothing. Verify with a JavaScript-off `curl` first.
- The canonical tag and the sitemap must point to the same canonical URLs.
- A `noindex` left in robots meta or headers will block everything. Confirm the
  robots meta is `index, follow`.
