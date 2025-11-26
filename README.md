
# MPA Mandate, Rules & Guidelines for AI-Assisted Development Tools

Guiding principles for building performant, resilient Multi-Page Applications. Focus on native web platform strengths, minimal JS, and robust SEO.

## 💡 The Problem

Modern AI code generation tools (like GitHub Copilot, Cursor, Claude Code, Gemini CLI, etc.) and models (Claude Sonnet/Opus, Gemini Pro, GPT-4o, etc.) are primarily trained on the prevailing web development paradigm: **complex, JavaScript-heavy Single-Page Applications (SPAs)**. This often leads to generated code that is bloated, fragile, and contrary to principles of performance, resilience, and maintainability.

## ✨ The Solution: An MPA-First Philosophy

This repository provides a concise set of development rules championing a **Multi-Page Application (MPA) architecture**. We advocate leveraging the native strengths of HTML, PHP, CSS, and the browser itself, treating JavaScript as a tool for **progressive enhancement** only. This approach aims for:

* **Optimal Performance:** Faster load times and smoother navigation.
* **Enhanced Resilience:** Less dependency on complex client-side logic.
* **Superior Maintainability:** Simpler architecture, fewer moving parts.
* **Inherent SEO & Accessibility:** Built upon web standards.

## 💡 Quick Start

1. **Choose your AI assistant** from the setup instructions below
2. **Choose your version**: Strict (vanilla JS) or Relaxed (jQuery allowed)
3. **Copy/configure** the appropriate file for your tool
4. **Start coding** with MPA-First principles enforced by your AI assistant


### 📝 Two Versions Available

Each AI assistant has **two versions** of the MPA guidelines:

1. **Strict Rules** - Vanilla JavaScript ES2020+ only, no libraries or frameworks
2. **Relaxed Rules** - Allows jQuery for progressive enhancement

Choose the version that best fits your project requirements.

## 🚀 Setup Instructions for Your AI Assistant

### Getting Started

<details>
<summary><strong>First, clone this repository to get all the MPA-First guideline files:</strong></summary>

```sh
git clone https://github.com/RealistSec/mpa-first-guidelines.git
cd mpa-first-guidelines
```

</details>


### Then choose your AI assistant below and follow the specific setup instructions.

### For GitHub Copilot IDE Integration

1. Copy the appropriate agent file to `.github/agents/` in your project root:

   ```sh
   # For strict rules
   cp mpa-strict-agent.md .github/agents/mpa-strict-agent.md

   # For relaxed rules (jQuery allowed)
   cp mpa-relaxed-agent.md .github/agents/mpa-relaxed-agent.md
   ```

2. Add a reference to the agent file in your `.github/copilot-instructions.md` (create the file if it doesn't exist):

   ```markdown
   # MPA-First Guidelines Reference

   For MPA-first development guidelines, reference the agent file:
   - Strict rules: @mpa-strict-agent
   - Relaxed rules: @mpa-relaxed-agent

   This ensures GitHub Copilot uses MPA-first principles throughout your project.
   ```

   > If `.github/copilot-instructions.md` already contains custom instructions, **append** the agent reference instead of overwriting.

<details>
<summary><strong>For GitHub Copilot CLI setup</strong></summary>

1. clone this repo or copy the appropriate agent file to your project:

   ```sh
   # For strict rules place the file
   cp .github/agents/mpa-strict-agent.md .github/agents/mpa-strict-agent.md

   # For relaxed rules
   cp .github/agents/mpa-relaxed-agent.md .github/agents/mpa-relaxed-agent.md
   ```
   
The agent files are now in place in `.github/agents/`
2. To use the coding agent:

   ```bash
   # For strict rules
   gh copilot agent @mpa-strict-agent
   
   # For relaxed rules (jQuery)
   gh copilot agent @mpa-relaxed-agent

   # To remove all instruction sets 
   ```

</details>

### For Cursor IDE

<details>
<summary><strong>Expand for Cursor IDE setup</strong></summary>

1. The rules are already in place in `.cursor/rules/`
2. Cursor will automatically detect and use these `.mdc` files
3. Choose which rule to apply:
   * **Strict**: Use `mpa-strict-rules.mdc` (always applied)
   * **Relaxed**: Use `mpa-relaxed-rules.mdc` (manually applied with `@mpa-relaxed-rules`)

</details>

### For Windsurf IDE

<details>
<summary><strong>Expand for Windsurf IDE setup</strong></summary>

1. Copy the appropriate file to your project root:

   ```sh
   # For strict rules (overwrites existing)
   cp .windsurf/mpa-strict-rules.md .windsurfrules

   # For relaxed rules (appends, preserves existing)
   cat .windsurf/mpa-relaxed-rules.md >> .windsurfrules
   # Or, on Windows/PowerShell:
   Get-Content .windsurf/mpa-relaxed-rules.md | Add-Content .windsurfrules
   ```

   > If `.windsurfrules` already contains custom instructions, **append** new rules instead of overwriting.
2. Or edit workspace rules via: Settings > Set Workspace AI Rules > Edit Rules

</details>

### For Gemini CLI

<details>
<summary><strong>Expand for Gemini CLI setup</strong></summary>

1. Copy the appropriate file to your Gemini CLI context directory:

   ```sh
   # For strict rules (overwrites existing)
   cp .gemini/GEMINI-MPA-STRICT.md ~/.gemini/GEMINI.md

   # For relaxed rules (appends, preserves existing)
   cat .gemini/GEMINI-MPA-RELAXED.md >> ~/.gemini/GEMINI.md
   # Or, on Windows/PowerShell:
   Get-Content .gemini/GEMINI-MPA-RELAXED.md | Add-Content ~/.gemini/GEMINI.md
   ```

   > If `GEMINI.md` already contains custom instructions, **append** new rules instead of overwriting.
2. Or place at project root: `.gemini/GEMINI.md`

</details>

### For Claude Desktop / Claude Projects

<details>
<summary><strong>Expand for Claude Desktop/Projects setup</strong></summary>

1. Open your Claude Project settings
2. Copy the content from the appropriate file:
   * **Strict**: `.claude/mpa-strict-instructions.md`
   * **Relaxed**: `.claude/mpa-relaxed-instructions.md`
3. Paste into the "Custom Instructions" section of your Claude Project.
   > If you already have custom instructions, **merge** the new rules with your existing content—do not overwrite.

</details>

### For GPT-5 / OpenAI Codex

<details>
<summary><strong>Expand for GPT-5/OpenAI Codex setup</strong></summary>

1. Copy the content from the appropriate file:
   * **Strict**: `GPT-5_and_GPT-5-Codex/mpa-strict-system-prompt.md`
   * **Relaxed**: `GPT-5_and_GPT-5-Codex/mpa-relaxed-system-prompt.md`
2. Use as your system prompt in:
   * ChatGPT Custom GPT instructions
   * OpenAI API system message
   * Any GPT-4 based coding assistant configuration
   * Any GPT-5 based coding as assistant configuration
   > If you already have custom instructions, **merge** the new rules with your existing content—do not overwrite.

</details>

**Quick cleanup:** After cloning, you can remove unneeded assistant folders with:

```sh
# Unix/Linux/macOS/Windows(Current version) (Bash/Zsh/PowerShell 7.4+) - Keep only what you need, remove the rest
rm -r -force .cursor/ .windsurf/ .gemini/ .claude/ GPT-5_and_GPT-5-Codex/ .github/ 
```


## 📁 Repository Structure

This repository contains MPA-First guidelines formatted specifically for each major AI coding assistant:

```text
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
├── GPT-5_and_GPT-5-Codex/
│   ├── mpa-strict-system-prompt.md     # GPT-5/Codex (strict)
│   └── mpa-relaxed-system-prompt.md    # GPT-5/Codex (relaxed)
├── mpa-rules.md                         # Original strict rules
├── mpa-relaxed-rules.md                 # Original relaxed rules (jQuery)
└── README.md
```

## 📖 Original Rules Documents

* [`mpa-rules.md`](./mpa-rules.md) - Original comprehensive strict rules
* [`mpa-relaxed-rules.md`](./mpa-relaxed-rules.md) - Original relaxed rules with jQuery

These documents contain the full, detailed guidelines. The assistant-specific versions are formatted adaptations of these core rules.

---


## 🙏 Inspiration

These rules were heavily inspired by the insightful perspectives of **Jono Alderson**, particularly his compelling blog post, ["It's Time for Modern CSS to Kill the SPA"](https://www.jonoalderson.com/conjecture/its-time-for-modern-css-to-kill-the-spa), which we discovered via the [TLDR Newsletter](https://refer.tldr.tech/557b5919/).

Jono's work deeply resonates with my aim for a more resilient and performant web. We also recommend his equally thought-provoking piece, ["JavaScript Broke The Web And Called It Progress"](https://www.jonoalderson.com/conjecture/javascript-broke-the-web-and-called-it-progress/), for further reading on the philosophy behind building a better web.

Also the tweet that triggered my curiosity into non-SPA - ["@levelsio not knowing what state is in react."](https://x.com/levelsio/status/1945542563521249659)

---

One day I plan to make a companion doc: "Landscape of PHP" - a concise orientation debunking the "PHP is dying" myth [(it still powers ~74% of the known server-side of the web /2025)](https://w3techs.com/technologies/overview/programming_language) and mapping its vibrant subcultures (WordPress pragmatists, Laravel evangelists, strict type/standards purists) to contextualize architectural choices.

---

## 🤝 Contributing

These rules are a living document. We welcome suggestions, improvements, and discussions.

---

## 📝 License

This project is open-sourced under the MIT License. See the `LICENSE` file for more details.
