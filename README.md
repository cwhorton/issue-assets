# issue-assets

Screenshots, PDFs and other files that are referenced from GitHub issues and
pull requests. GitHub's own attachment store (`github.com/user-attachments/...`)
can only be reached from the web UI, so anything posted from the command line
or by an agent is committed here instead and linked by raw URL.

## Layout

```
<project>/<number>/<file>
```

- `project` — a short lowercase slug for the repository or product the item
  belongs to (`churchcrm`, ...), not the fork name.
- `number` — the GitHub issue or pull request number the file is posted on.
  PRs and issues share one number space, so a PR number is fine here.
- `file` — a short kebab-case name that says what the picture shows
  (`labels-button.png`, `composer-preview.png`). No `Screenshot 2026-...` names.

## Referencing a file

Raw URLs render inline in issue and PR markdown:

```
https://raw.githubusercontent.com/cwhorton/issue-assets/main/<project>/<number>/<file>
```

Markdown form (preferred, alt text describes the picture):

```markdown
![Labels button next to Tags](https://raw.githubusercontent.com/cwhorton/issue-assets/main/churchcrm/9875/labels-button.png)
```

HTML form when a width cap is needed:

```html
<img width="900" alt="Labels button next to Tags" src="https://raw.githubusercontent.com/cwhorton/issue-assets/main/churchcrm/9875/labels-button.png">
```

## Helper

`bin/add` copies files into place, commits, pushes and prints the markdown
to paste:

```bash
bin/add churchcrm 9875 /path/to/labels-button.png /path/to/labels-dialog.png
```

## Rules

- Files are never rewritten or removed once linked; a comment on GitHub
  depends on the URL staying valid. Add a new file instead.
- Images come from test stacks or seed data only, never from production
  or real member records.
- Keep screenshots at a sensible size (a 2x retina capture of a 1400px
  window is plenty; crop to the relevant region when possible).
