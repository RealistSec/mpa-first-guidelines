# Copilot Instructions: MPA-First Guidelines Repository

## Repository Purpose

This is a **reference documentation repository** containing MPA (Multi-Page Application) development guidelines for AI coding agents. Users copy these guidelines into their own projects to teach AI tools (GitHub Copilot, Cursor, Claude, Codex, etc.) to generate MPA-first code instead of defaulting to SPA frameworks.

## Key Files & Their Roles

- **`mpa-rules.md`** - Comprehensive, strict MPA-first mandate with strict PHP & vanilla JS only. This is the primary reference document.
- **`relaxed-mpa-rules.md`** - Variant ruleset allowing full use of PHP & jQuery for progressive enhancement while maintaining MPA architecture.
- **`README.md`** - User-facing documentation explaining the problem, solution, and how to integrate these rules into AI coding workflows.

## Writing Style & Tone

When editing these guidelines:

- **Be authoritative and prescriptive** - Use "MUST" and "DO NOT" language. These are rules, not suggestions.
- **Provide concrete examples** - Every principle should have a code snippet showing the correct pattern.
- **Explain the "why"** - Help developers understand the philosophy, not just the mechanics.
- **Stay opinionated** - The entire premise is rejecting the SPA-default paradigm. Don't hedge or equivocate.

## Content Maintenance Patterns

### Adding New Rules or Sections

1. **Keep examples realistic** - Use patterns that would appear in actual projects
2. **Maintain parallelism** - Both `mpa-rules.*` and `relaxed-mpa-rules.*` should cover the same topics in the same order
3. **Update the table of contents** - If you add major sections, ensure navigation is clear

### Updating Existing Content

- **Preserve the document structure** - The current flow (Prime Directive → HTML → CSS → PHP → JS → Security) is intentional
- **Keep code examples modern** - Target current 2025-26 web standards (PHP 8.1+, ES2020+, modern CSS)
- **Maintain accessibility focus** - A11Y is not optional in these guidelines

## Technical Constraints

- **Markdown formatting** - All rule files use standard markdown with fenced code blocks
- **No dependencies** - This is a pure documentation repository with no build tools or runtime
- **Git-friendly** - Keep line lengths reasonable for clean diffs

## Philosophy to Preserve

This repository champions:

1. **Platform-first thinking** - HTML, CSS, PHP, and browser APIs over JavaScript frameworks
2. **Progressive enhancement** - Core functionality works without JS
3. **Performance as a feature** - Fast load times from server-rendered HTML
4. **SEO & accessibility by default** - Not bolted on as afterthoughts
5. **Simplicity over novelty** - Boring, proven technology over the latest trends

## Common Edits & How to Handle Them

### "Should we add framework X?"
No. If it's a client-side SPA framework (React, Vue, Svelte, etc.), it's explicitly banned. Even if "everyone uses it."

### "Can we include framework-based SSR?"
No. Next.js, Nuxt, SvelteKit, etc. are still SPA architectures at their core. True MPAs use traditional server-side rendering (PHP, Node.js + templates, Ruby, Python, etc.).

### "What about Htmx/Alpine.js/other minimal JS libraries?"
These could be mentioned as acceptable enhancement tools since they embrace progressive enhancement, but only in the relaxed variant. The strict `mpa-rules.md` stays vanilla-only.

## When Users Request Changes

If a user wants to add content:
- Ask what problem they're solving
- Ensure it aligns with MPA-first principles
- Add concrete examples, not abstract advice
- Update both variants if applicable

If a user wants to make rules more lenient:
- Consider whether it compromises the MPA architecture (banned)
- Or just adds a helpful tool for enhancement (potentially allowed in relaxed variant)

## Documentation Standards

- **Use semantic HTML examples** - Always show proper `<header>`, `<main>`, `<article>`, etc.
- **Include accessibility attributes** - `alt` text, `aria-label`, proper `<label>` associations
- **Show security patterns** - CSRF tokens, parameterized queries, CSP headers
- **Demonstrate modern CSS** - Grid, Flexbox, Custom Properties, View Transitions
