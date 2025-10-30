
# MPA Mandate, Rules & Guidelines for AI-Assisted Development Tools

Guiding principles for building performant, resilient Multi-Page Applications. Focus on native web platform strengths, minimal JS, and robust SEO.

<details>
<summary><h2>💡 The Problem</h2></summary>

Modern AI code generation tools (like GitHub Copilot, Cursor, Claude Code, Gemini CLI, etc.) and models (Claude Sonnet/Opus, Gemini Pro, GPT-4o, etc.) are primarily trained on the prevailing web development paradigm: **complex, JavaScript-heavy Single-Page Applications (SPAs)**. This often leads to generated code that is bloated, fragile, and contrary to principles of performance, resilience, and maintainability.

</details>

<details>
<summary><h2>✨ The Solution: An MPA-First Philosophy</h2></summary>

This repository provides a concise set of development rules championing a **Multi-Page Application (MPA) architecture**. We advocate leveraging the native strengths of HTML, CSS, and the browser itself, treating JavaScript as a tool for **progressive enhancement** only. This approach aims for:
* **Optimal Performance:** Faster load times and smoother navigation.
* **Enhanced Resilience:** Less dependency on complex client-side logic.
* **Superior Maintainability:** Simpler architecture, fewer moving parts.
* **Inherent SEO & Accessibility:** Built upon web standards.

</details>

## 📁 Repository Structure

This repository contains MPA-First guidelines formatted specifically for each major AI coding assistant:

```
mpa-first-guidelines/
├── .cursor/
│   └── rules/
│       ├── mpa-strict-rules.mdc        # Cursor IDE (strict: vanilla JS only)
│       └── mpa-relaxed-rules.mdc       # Cursor IDE (relaxed: jQuery allowed)
├── .windsurf/
│   ├── mpa-strict-rules.md             # Windsurf IDE (strict)
│   └── mpa-relaxed-rules.md            # Windsurf IDE (relaxed)
├── .gemini/
│   ├── GEMINI-MPA-STRICT.md            # Gemini CLI (strict)
│   └── GEMINI-MPA-RELAXED.md           # Gemini CLI (relaxed)
├── .claude/
│   ├── mpa-strict-instructions.md      # Claude Desktop/Projects (strict)
│   └── mpa-relaxed-instructions.md     # Claude Desktop/Projects (relaxed)
├── .github/
│   └── agents/
│       ├── mpa-strict-agent.md         # GitHub Copilot CLI Agent (strict)
│       └── mpa-relaxed-agent.md        # GitHub Copilot CLI Agent (relaxed)
├── gpt4-codex/
│   ├── mpa-strict-system-prompt.md     # GPT-4/Codex (strict)
│   └── mpa-relaxed-system-prompt.md    # GPT-4/Codex (relaxed)
├── mpa-rules.md                         # Original strict rules
├── relaxed-mpa-rules.md                 # Original relaxed rules (jQuery)
└── README.md
```

### 📝 Two Versions Available

Each AI assistant has **two versions** of the MPA guidelines:

1. **Strict Rules** - Vanilla JavaScript ES2020+ only, no libraries or frameworks
2. **Relaxed Rules** - Allows jQuery for progressive enhancement

Choose the version that best fits your project requirements.

## 🚀 Setup Instructions for Your AI Assistant

### For Cursor IDE

1. The rules are already in place in `.cursor/rules/`
2. Cursor will automatically detect and use these `.mdc` files
3. Choose which rule to apply:
   - **Strict**: Use `mpa-strict-rules.mdc` (always applied)
   - **Relaxed**: Use `mpa-relaxed-rules.mdc` (manually applied with `@mpa-relaxed-rules`)

### For Windsurf IDE

1. Copy the appropriate file to your project root:
   ```bash
   # For strict rules
   cp .windsurf/mpa-strict-rules.md .windsurfrules
   
   # For relaxed rules (jQuery)
   cp .windsurf/mpa-relaxed-rules.md .windsurfrules
   ```
2. Or edit workspace rules via: Settings > Set Workspace AI Rules > Edit Rules

### For Gemini CLI

1. Copy the appropriate file to your Gemini CLI context directory:
   ```bash
   # For strict rules
   cp .gemini/GEMINI-MPA-STRICT.md ~/.gemini/GEMINI.md
   
   # For relaxed rules (jQuery)
   cp .gemini/GEMINI-MPA-RELAXED.md ~/.gemini/GEMINI.md
   ```
2. Or place at project root: `.gemini/GEMINI.md`

### For Claude Desktop / Claude Projects

1. Open your Claude Project settings
2. Copy the content from the appropriate file:
   - **Strict**: `.claude/mpa-strict-instructions.md`
   - **Relaxed**: `.claude/mpa-relaxed-instructions.md`
3. Paste into the "Custom Instructions" section of your Claude Project

### For GitHub Copilot CLI

1. The agent files are already in place in `.github/agents/`
2. To use the coding agent:
   ```bash
   # For strict rules
   gh copilot agent @mpa-strict-agent
   
   # For relaxed rules (jQuery)
   gh copilot agent @mpa-relaxed-agent
   ```

### For GitHub Copilot IDE Integration

1. Copy the appropriate original file to `.github/copilot-instructions.md`:
   ```bash
   # For strict rules
   cp mpa-rules.md .github/copilot-instructions.md
   
   # For relaxed rules (jQuery)
   cp relaxed-mpa-rules.md .github/copilot-instructions.md
   ```
2. GitHub Copilot will automatically use this file for context

### For GPT-4 / OpenAI Codex

1. Copy the content from the appropriate file:
   - **Strict**: `gpt4-codex/mpa-strict-system-prompt.md`
   - **Relaxed**: `gpt4-codex/mpa-relaxed-system-prompt.md`
2. Use as your system prompt in:
   - ChatGPT Custom GPT instructions
   - OpenAI API system message
   - Any GPT-4 based coding assistant configuration

## 💡 Quick Start

1. **Choose your AI assistant** from the setup instructions above
2. **Choose your version**: Strict (vanilla JS) or Relaxed (jQuery allowed)
3. **Copy/configure** the appropriate file for your tool
4. **Start coding** with MPA-First principles enforced by your AI assistant

## 📖 Original Rules Documents

- [`mpa-rules.md`](./mpa-rules.md) - Original comprehensive strict rules
- [`relaxed-mpa-rules.md`](./relaxed-mpa-rules.md) - Original relaxed rules with jQuery

These documents contain the full, detailed guidelines. The assistant-specific versions are formatted adaptations of these core rules.

---

## 🙏 Inspiration

These rules were heavily inspired by the insightful perspectives of **Jono Alderson**, particularly his compelling blog post, ["It's Time for Modern CSS to Kill the SPA"](https://www.jonoalderson.com/conjecture/its-time-for-modern-css-to-kill-the-spa), which we discovered via the [TLDR Newsletter](https://refer.tldr.tech/557b5919/).

Jono's work deeply resonates with my aim for a more resilient and performant web. We also recommend his equally thought-provoking piece, ["JavaScript Broke The Web And Called It Progress"](https://www.jonoalderson.com/conjecture/javascript-broke-the-web-and-called-it-progress/), for further reading on the philosophy behind building a better web.

Also the tweet that triggered my curiosity into non-SPA - ["@levelsio not knowing what state is in react."](https://x.com/levelsio/status/1945542563521249659)

---

##  🤝Contributing
These rules are a living document. We welcome suggestions, improvements, and discussions.

---

## 📝 License
This project is open-sourced under the MIT License. See the `LICENSE` file for more details.
