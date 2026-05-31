# JSON-LD templates

Copy-paste structured data for the entity site. Replace every `{{PLACEHOLDER}}`.
Put each block in its own `<script type="application/ld+json">` tag in the page
head or body. Keep the FAQPage answer text identical to the visible FAQ text.

Rules:
- Use the real domain for `{{URL}}` (no trailing slash in the variable; the
  templates add slashes where needed).
- `sameAs` must list only real, verified profile URLs. Delete any line you do
  not have a real URL for. An empty entry is worse than a missing one.
- `description` on the Person node must be the canonical answer, verbatim.
- Add `VideoObject` only for videos actually embedded or linked on the page.
- Add `Review` only for real, attributable testimonials. Never add
  `aggregateRating` or a star-rating badge you cannot verify.

---

## Person (the core of the entity)

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Person",
  "@id": "{{URL}}/#person",
  "name": "{{FULL_NAME}}",
  "alternateName": "{{BRAND_OR_HANDLE}}",
  "url": "{{URL}}/",
  "jobTitle": "{{JOB_TITLE}}",
  "description": "{{CANONICAL_ANSWER}}",
  "knowsAbout": ["{{TOPIC_1}}", "{{TOPIC_2}}", "{{TOPIC_3}}"],
  "worksFor": { "@id": "{{URL}}/#organization" },
  "sameAs": [
    "{{YOUTUBE_URL}}",
    "{{INSTAGRAM_URL}}",
    "{{LINKEDIN_URL}}",
    "{{X_URL}}",
    "{{GITHUB_URL}}"
  ]
}
</script>
```

## Organization

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Organization",
  "@id": "{{URL}}/#organization",
  "name": "{{ORG_NAME}}",
  "alternateName": "{{FULL_NAME}}, {{BRAND_OR_HANDLE}}",
  "url": "{{URL}}/",
  "logo": "{{URL}}/{{LOGO_PATH}}",
  "image": "{{URL}}/{{OG_IMAGE_PATH}}",
  "description": "{{ORG_DESCRIPTION}}",
  "founder": { "@id": "{{URL}}/#person" },
  "areaServed": "{{AREA_SERVED}}",
  "sameAs": ["{{YOUTUBE_URL}}", "{{LINKEDIN_URL}}"]
}
</script>
```

## WebSite

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "WebSite",
  "@id": "{{URL}}/#website",
  "url": "{{URL}}/",
  "name": "{{SITE_NAME}}",
  "alternateName": "{{ALT_SITE_NAME}}",
  "description": "{{SITE_DESCRIPTION}}",
  "publisher": { "@id": "{{URL}}/#organization" },
  "inLanguage": "en-US"
}
</script>
```

## FAQPage (text must match the visible FAQ verbatim)

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "@id": "{{URL}}/#faq",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "Who is {{FULL_NAME}}?",
      "acceptedAnswer": { "@type": "Answer", "text": "{{CANONICAL_ANSWER}}" }
    },
    {
      "@type": "Question",
      "name": "{{QUESTION_2}}",
      "acceptedAnswer": { "@type": "Answer", "text": "{{ANSWER_2}}" }
    },
    {
      "@type": "Question",
      "name": "{{QUESTION_3}}",
      "acceptedAnswer": { "@type": "Answer", "text": "{{ANSWER_3}}" }
    }
  ]
}
</script>
```

## VideoObject (one per embedded video; omit if no videos)

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "VideoObject",
  "name": "{{VIDEO_TITLE}}",
  "description": "{{VIDEO_DESCRIPTION}}",
  "thumbnailUrl": ["{{VIDEO_THUMBNAIL_URL}}"],
  "contentUrl": "{{VIDEO_WATCH_URL}}",
  "embedUrl": "{{VIDEO_EMBED_URL}}",
  "uploadDate": "{{YYYY-MM-DD_IF_KNOWN}}",
  "publisher": { "@id": "{{URL}}/#organization" }
}
</script>
```

For a YouTube video with id VIDEO_ID:
- thumbnail: `https://img.youtube.com/vi/VIDEO_ID/maxresdefault.jpg`
- watch: `https://www.youtube.com/watch?v=VIDEO_ID`
- embed: `https://www.youtube.com/embed/VIDEO_ID`

If `uploadDate` is unknown, delete that line rather than guessing.

## Review (real, named testimonials only)

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Review",
  "reviewBody": "{{EXACT_QUOTE}}",
  "author": { "@type": "Person", "name": "{{REVIEWER_NAME}}" },
  "itemReviewed": { "@id": "{{URL}}/#organization" }
}
</script>
```

You can also attach reviews inline on the Organization node as a `review`
array. Do not add `aggregateRating` unless you have a real, verifiable
aggregate from a legitimate source.

## Validate

After publishing, run the page through Google Rich Results Test and the
Schema.org validator. Fix any error before requesting indexing.
