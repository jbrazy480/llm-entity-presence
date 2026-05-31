# IndexNow and Bing submission

IndexNow tells participating engines (Bing and others) to crawl your URLs now.
Bing and Microsoft Copilot read the Bing index, so this is high leverage for
answer-engine visibility. It is free and fast.

## One time setup

1. Generate an API key: any hex string, 8 to 128 characters (for example a
   UUID with dashes removed). Treat it as the key value, call it `KEY`.
2. Host a key file at the site root so the engine can verify ownership:
   - File path: `https://DOMAIN/KEY.txt`
   - File contents: the key value `KEY` and nothing else.
   - In a Next.js App Router site this can be a static file in `public/` named
     `KEY.txt`, or a route handler that returns the key as plain text.
3. Confirm it serves: `curl -s https://DOMAIN/KEY.txt` should print exactly `KEY`.

## Submit URLs (single URL)

```bash
curl "https://api.indexnow.org/indexnow?url=https://DOMAIN/&key=KEY&keyLocation=https://DOMAIN/KEY.txt"
```

You can also submit directly to Bing's endpoint:

```bash
curl "https://www.bing.com/indexnow?url=https://DOMAIN/&key=KEY"
```

## Submit URLs (batch, recommended)

POST a small JSON body listing the canonical URLs.

```bash
curl -X POST "https://api.indexnow.org/indexnow" \
  -H "Content-Type: application/json" \
  -d '{
    "host": "DOMAIN",
    "key": "KEY",
    "keyLocation": "https://DOMAIN/KEY.txt",
    "urlList": [
      "https://DOMAIN/",
      "https://DOMAIN/blog",
      "https://DOMAIN/about"
    ]
  }'
```

A 200 or 202 response means accepted. Resubmit when content changes.

## Bing Webmaster Tools (do this too)

1. Go to Bing Webmaster Tools and add the site. You can import from Google
   Search Console once GSC is set up, which is the fastest path.
2. Verify ownership (DNS, meta tag, or the import flow).
3. Submit the sitemap: `https://DOMAIN/sitemap.xml`.
4. Use URL submission to push the home page and key pages.

## Notes

- Do not spam. Submit real, canonical URLs only, and resubmit on real changes.
- Keep the `KEY.txt` file in place; removing it breaks future verification.
- Zero em dashes in any file you create.
