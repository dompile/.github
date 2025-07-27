# dompile

A modern static site generator with Apache SSI-style includes, live development server, and DOM-based templating.

## Overview

dompile is a static site generator designed for developers who want the simplicity of HTML with the power of includes and live development features. It processes HTML files with server-side includes, supports Markdown content with layouts, and provides instant browser reload during development.

## Key Features

- **Apache SSI-style includes** - `<!--#include virtual="/includes/header.html" -->`
- **DOM-based templating** - Modern `<template>` and `<slot>` syntax
- **Markdown processing** - YAML frontmatter, layouts, and automatic ToC generation
- **Live development server** - Instant browser reload with Server-Sent Events
- **Incremental builds** - Smart dependency tracking for fast rebuilds
- **Security-first** - Path traversal prevention and input validation
- **Zero client-side JavaScript** - Pure static output

## Packages

This monorepo contains:

- **[@dompile/cli](cli/)** - Core static site generator CLI
- **[create-dompile-site](create-dompile-site/)** - Project scaffolding tool
- **[starter-kit](starter-kit/)** - Template repository for new projects
- **[vscode-extension](vscode-extension/)** - VS Code extension for dompile development

## Quick Start

```bash
# Create a new site
npm create dompile-site my-site
cd my-site

# Start development server
npx dompile serve

# Build for production
npx dompile build
```

## Example Usage

**HTML with includes:**
```html
<!DOCTYPE html>
<html>
<head>
    <!--#include virtual="/includes/head.html" -->
</head>
<body>
    <!--#include virtual="/includes/header.html" -->
    <main>
        <h1>Welcome to my site</h1>
    </main>
    <!--#include virtual="/includes/footer.html" -->
</body>
</html>
```

**Markdown with layout:**
```markdown
---
layout: blog
title: My Blog Post
---

# Hello World

This content will be inserted into the `{{ content }}` slot in `blog.html`.
```

## Architecture

dompile follows a simple processing pipeline:

1. **Include Processing** - Resolves `<!--#include -->` directives
2. **Head Injection** - Auto-discovers and injects head content
3. **Markdown Processing** - Converts Markdown with layout support
4. **Asset Tracking** - Copies only referenced assets
5. **Dependency Tracking** - Enables incremental builds

## Development

```bash
# Clone and setup
git clone https://github.com/your-username/dompile.git
cd dompile/cli
npm install

# Run tests
npm test

# Link for global testing
npm link
```

## License

CC0-1.0 (Public Domain)