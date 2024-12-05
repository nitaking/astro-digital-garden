---
title: Tasks
tableOfContents: false
prev: false
next: false
description: My todo list
---

- [ ] Write about `@beoe/rehype-vizdom`
  - Write about interactivity
- [ ] Write about `@beoe/rehype-d2`
- [ ] Add more options for `starlight-digital-garden`
  - option to check for broken links?
- [ ] Write about `starlight-digital-garden`
- [ ] Starlight SEO/SMO plugin
  - `astro-robots-txt`
  - microdata
  - social image
  - date in sitemap
- [ ] Add a grammar checker
- [ ] Implement [[faceted-search]]
- [ ] Add [View Transitions](https://docs.astro.build/en/guides/view-transitions/)
  - See [starlight#694](https://github.com/withastro/starlight/pull/694#issuecomment-2021611520)
- [ ] Implement better user action tracking (beyond page navigations)
  - If search was used
  - If external links were clicked
  - If page preview was shown
- [ ] Remove H1 on the tags page

## Ideas

- Footnotes:
  - Mention how footnotes can be shown on the side, like in [Tufte design](https://edwardtufte.github.io/tufte-css/)
  - See https://gwern.net/sidenote

## Color for Tag

I can easily generate a color from the tag:

```js
import ch from "color-hash";
const colorHash = new ch.default();
colorHash.hex(tag);
```

I can use it in:

- [x] Color chip near the tag or maybe a color underline?
- [x] Euler diagram
- [x] Content graph
- [ ] Social images - to generate a colorful "border"

I implemented a prototype in the branch [tag-color](https://github.com/stereobooster/astro-digital-garden/tree/tag-color).

## From Other Articles

```dataview list
SELECT dv_link(), dv_task()
FROM tasks JOIN documents ON documents.path = tasks.from
WHERE (frontmatter ->> '$.draft' IS NULL OR frontmatter ->> '$.draft' = false)
  AND url != '/tasks/'
  AND checked = false
ORDER BY updated_at DESC, path, tasks.start;
```
