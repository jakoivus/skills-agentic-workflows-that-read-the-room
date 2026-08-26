---
name: update-github-info
description: Update Mona's GitHub Info content from official GitHub sources.
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
tools:
  edit:
  web-fetch:
  github:
    toolsets:
      - repos
network:
  allowed:
    - github.blog
    - github.com
    - awesome-copilot.github.com
safe-outputs:
  create-pull-request:
    title-prefix: "Mona: "
    labels:
      - documentation
---

Read `notes/mona-notes.md` before drafting any changes.

Use web fetch to read both `https://github.blog/latest/` and `https://github.blog/changelog/`. Also web fetch `https://awesome-copilot.github.com/workflows/`. Use the GitHub repository API tools to read relevant repository guidance and reference files. Treat those official sources and the repository notes as the basis for the update.

Update `site/content/github-info.md` with short, practical summaries that help developers learn GitHub faster. Mention the source whenever a change comes from the GitHub Blog or GitHub Changelog, and preserve the existing Markdown structure and useful content.

Use the `create-pull-request` safe output to open a pull request containing the content update for Mona to review. Do not write changes directly to `main`.
