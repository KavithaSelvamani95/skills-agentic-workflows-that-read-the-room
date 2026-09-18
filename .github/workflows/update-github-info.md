---
name: update-github-info
description: Draft website updates for Mona's GitHub Info site from official GitHub sources.
model: gpt-4.1
on:
  workflow_dispatch:
  schedule:
    - cron: '17 9 * * *'
safe-outputs:
  create-pull-request:
    title-prefix: "[mona] "
    draft: true
    fallback-as-issue: false
tools:
  edit:
  web-fetch:
network:
  allowed:
    - github.com
    - github.blog
    - awesome-copilot.github.com
---

# Update Mona's GitHub Info website

Read `notes/mona-notes.md` before making changes.

Use these official sources:

- `notes/mona-notes.md`
- GitHub Blog: https://github.blog/latest/
- GitHub Changelog: https://github.blog/changelog/
- Awesome Copilot workflows: https://awesome-copilot.github.com/workflows/

Use `web-fetch` to read the public GitHub Blog, GitHub Changelog, and Awesome
Copilot workflows pages. Use GitHub repository API tools, rather than terminal,
CLI, or sandboxed commands, to read repository guidance and reference files.

Identify recent updates relevant to Mona's GitHub Info website. Update
`site/content/github-info.md` with concise, practical information for readers.
Preserve the existing content structure and include clear source context for
each update based on the GitHub Blog or GitHub Changelog.

Open a pull request for Mona to review using `safe-outputs` with
`create-pull-request`. Include a clear summary of the sources reviewed and the
updates made in the pull request description. Do not write directly to `main`.

Check that the workflow configuration is syntactically valid, but do not
compile this workflow.