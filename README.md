# Static Site Generator

A custom-built static site generator written in Python. It converts Markdown content into a fully styled HTML website, complete with support for inline formatting, images, links, code blocks, blockquotes, and lists. Based on the Boot.dev course [Build a Static Site Generator in Python
](https://www.boot.dev/courses/build-static-site-generator-python).

**Live site:** [Demo](https://SandorTeleki.github.io/static-site-generator/)

## Features

- Converts Markdown to HTML with full inline syntax support (bold, italic, code, links, images)
- Block-level parsing: headings, paragraphs, ordered/unordered lists, blockquotes, code blocks
- Recursive page generation from a content directory
- Configurable base path for deployment to subdirectories (e.g. GitHub Pages)
- Recursive static file copying (CSS, images, etc.)
- Templating with `{{ Title }}` and `{{ Content }}` placeholders

## Project Structure

```
├── content/          # Markdown source files
├── static/           # Static assets (CSS, images)
├── src/              # Python source code
├── tests/            # Unit tests
├── docs/             # Generated site (served by GitHub Pages)
├── template.html     # HTML template
├── main.sh           # Local dev: build + serve
├── build.sh          # Production build with basepath
└── test.sh           # Run unit tests
```

## Local Setup

**Requirements:** Python 3 (no external dependencies)

1. Clone the repo:

   ```
   git clone https://github.com/SandorTeleki/static-site-generator.git
   cd static-site-generator
   ```

2. Make the scripts executable (if needed):

   ```
   chmod +x main.sh build.sh test.sh
   ```

3. Run locally:

   ```
   ./main.sh
   ```

   This generates the site into `docs/` with `/` as the base path, then starts a local server at [http://localhost:8888](http://localhost:8888).

4. Run tests:

   ```
   ./test.sh
   ```

## Production Build

To build for GitHub Pages (or any subdirectory deployment):

```
./build.sh
```

This runs the generator with `/static-site-generator/` as the base path, so all internal links and asset references work correctly when served from a subdirectory.

## Adding Content

- Add Markdown files to `content/` (nested directories become URL paths)
- Add static assets to `static/`
- Rebuild with `./main.sh` (local) or `./build.sh` (production)

Each Markdown file must have an `# H1` heading — it becomes the page title.
