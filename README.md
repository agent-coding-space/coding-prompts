# Prompts for Claude Code

A searchable, editable library of prompts for working with Claude Code — one set
for dropping into an **existing codebase**, one for starting a **fresh project**.

It is a single static `index.html`: no build step, no dependencies, no server.

## Using it

Open `index.html` in a browser, or visit the deployed GitHub Pages URL.

- **Click any prompt** to copy it to the clipboard.
- **`/`** focuses search — it spans both libraries at once.
- **`n`** starts a new prompt; **`⌘/Ctrl + Enter`** saves it; **`Esc`** cancels.
- **Star** a prompt to pin it to the top.
- **Export / Import** move your library between browsers as JSON.
- **Reset to defaults** restores the seed set (export first — it overwrites).

Prompts with `[brackets]` are templates; fill in the bracketed part before use.

## Where your prompts are stored

Everything lives in the browser's `localStorage` under the key `promptlib:v1`.
Nothing is sent anywhere and there is no account. That means edits are per
browser and per device — use Export/Import to move them, and export before
clearing site data.

(If the page is running inside a host that provides `window.storage`, it uses
that instead; otherwise `localStorage`.)

## Deploying

The site is the repository root — `index.html` plus nothing else it needs.
`.github/workflows/pages.yml` publishes it to GitHub Pages on every push to the
default branch, and can also be run by hand from the Actions tab.

`configure-pages` runs with `enablement: true`, so the workflow turns Pages on
itself; there is nothing to switch on in repo settings. The live URL appears in
each run summary and under Settings -> Pages.

Nothing here is Pages-specific, so any static host works too: serve the
repository root, or just open `index.html` from disk.

## Editing

`index.html` holds the markup, styles, and script in that order. The default
prompt set is the `seed()` function in the script — edit it there to change what
a fresh visitor sees. Everything else is plain DOM: state in `S`, view state in
`ui`, and a full re-render on change.
