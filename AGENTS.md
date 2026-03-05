# AGENTS.md - Developer Guide for This Hugo Site

## Overview

This is a **Hugo static site** using the **Blowfish theme**. The site uses TOML configuration and Hugo templating. No Node.js/npm needed for normal development.

---

## Build & Development Commands

### Building the Site

```bash
hugo                    # Build to ./public/
hugo --minify          # Build with minification
hugo --buildDrafts    # Include drafts
hugo --buildFuture    # Include future posts
```

### Development Server

```bash
hugo server                              # Live reload server
hugo server --buildDrafts --buildFuture # With drafts/future
hugo server -p 3000                     # Custom port (default: 1313)
```

### Validation

```bash
hugo config              # Validate configuration
hugo --check            # Check for broken links (after build)
hugo --printI18nWarnings --printPathWarnings  # List content issues
```

---

## Code Style Guidelines

### General Conventions

- **Indentation**: 2 spaces (soft tabs)
- **Line Endings**: LF (Unix-style)
- **Charset**: UTF-8
- **Trailing Whitespace**: Trim on save
- **Final Newline**: Always include

### Hugo Templates (Go Templates)

- Spaces between list items: `[1, 2, 3]` not `[1,2,3]`
- Spaces around operators: `1 + 1` not `1+1`
- Spaces inside Go templating tags: `{{< alert >}}` not `{{<alert>}}`
- Relative asset paths without leading slash: `static/img/` not `/static/img/`
- Folder paths with trailing slash: `static/img/`

### TOML Configuration

- 2-space indentation
- Format: `key = "value"`
- Booleans: `true` or `false` (no quotes)

### Content Files (Markdown)

- Front matter at top (YAML or TOML)
- Example:
  ```yaml
  ---
  title: "Your Title"
  date: 2024-01-15
  draft: false
  tags: ["tag1", "tag2"]
  categories: ["Technology"]
  ---
  ```

---

## Naming Conventions

### Files and Directories

- Lowercase letters, numbers, hyphens only
- Directory: `content/posts/my-new-post/`
- File: `content/posts/my-new-post/index.md`
- No spaces in filenames

### Front Matter

| Field | Convention | Example |
|-------|------------|---------|
| `title` | Title case | "My New Post" |
| `date` | ISO 8601 | 2024-01-15 |
| `tags` | lowercase, hyphens | `["web-dev"]` |
| `categories` | Title case | `["Tech"]` |
| `draft` | boolean | `false` |

---

## Project Structure

```
/home/david/Documents/workspace/personal/
├── config/_default/       # Hugo configuration
│   ├── hugo.toml         # Main config
│   ├── params.toml       # Theme parameters
│   ├── markup.toml       # Markdown settings
│   └── menus.en.toml     # Navigation
├── content/              # Site content (posts, pages)
├── layouts/             # Custom layouts (overrides theme)
├── assets/              # Static assets (images)
├── static/              # Static files (favicon)
├── themes/blowfish/     # Hugo theme (submodule)
└── public/              # Built output (DO NOT EDIT)
```

---

## Adding New Content

```bash
hugo new posts/my-new-post/index.md  # New post
hugo new about.md                     # New page
```

---

## Configuration Reference

### `config/_default/params.toml`

- `colorScheme`: "terminal"
- `defaultAppearance`: "light"
- `autoSwitchAppearance`: true/false
- `enableSearch`: true/false
- `enableCodeCopy`: true/false

### `config/_default/hugo.toml`

- `theme`: "blowfish"
- `defaultContentLanguage`: "en"
- `enableEmoji`: true
- Taxonomies: tags, categories, authors, series

### Markdown (`config/_default/markup.toml`)

- Goldmark parser settings
- Code highlighting
- Table of contents (levels 2-4)

---

## Error Handling

- **Template errors**: Run `hugo server` for real-time errors
- **Missing assets**: Check relative paths without leading slash
- **i18n issues**: Add keys to `i18n/` directory

### Debug Commands

```bash
hugo config                  # Show configuration
hugo --printTemplateWarnings # List templates
hugo -v                      # Verbose output
```

---

## Important Notes

1. **Do NOT edit `public/`** - generated and overwritten on build
2. **Use `layouts/` for customizations** - overrides theme templates
3. **Keep content in `content/`** - organize by type
4. **Test locally before deploying** - use `hugo server`
5. **Set `draft: true`** during development
