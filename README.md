
# MPA Mandate, Rules & Guidelines for AI-Assisted Development Tools v2
   >  **<center>AI-Assisted & Agent Development guiding principles for building performant, resilient Multi-Page Applications .</br>
   </br>AI coding tools default to SPAs. This <ins>changes</ins> that.</center>**</br>
   These guiding principles restore the native strengths of HTML, CSS, and server-rendered architecture, capabilities the platform has quietly perfected.
   JavaScript is for enhancement, not enablement. Core functionality works without it.
   Designed for seamless integration with GitHub Copilot, Cursor, Claude, and other AI assistants.
   > Designed for seamless integration with major AI coding assistants to enforce MPA-first development practices automatically.
>
**Changelog:**  
   Last Update: Dec 2025
###
   v2 Changes:

- Major assistant-specific instruction formats added
- See repository structure for new subfolder organization and integration steps
- Wording refinements for clarity and emphasis of MPA-first philosophy.

## 🌐 Overview
For over a decade, web development has trended towards complex, JavaScript-heavy Single-Page Applications (SPAs). The promise was a slick, "app-like" user experience. The reality, in most cases, has been bloated, fragile, and over-engineered websites that are slow to load, difficult to maintain, and hostile to users and search engines.

This document outlines a return to a more resilient, performant, and durable web. We are intentionally choosing a **Multi-Page Application (MPA)** architecture. The guiding principle is to **use the platform**. We build upon the native strengths of HTML, CSS, and the browser itself, which have evolved significantly. Modern features like CSS View Transitions and Speculation Rules now provide the fluid user experience that once required megabytes of JavaScript, but without the performance penalty.

We are choosing simplicity, speed, and maintainability over unnecessary complexity. We build for users and outcomes, not for developer experience (DX) or architectural novelty. JavaScript is a powerful tool for progressive enhancement, not the default foundation for every page.

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

### For Claude Code CLI

<details>
<summary><strong>Expand for Claude Code CLI setup</strong></summary>

1. Copy the appropriate file to your project root as `CLAUDE.md`:

   ```sh
   # For strict rules
   cp claude-code/CLAUDE-MPA-STRICT.md CLAUDE.md

   # For relaxed rules (jQuery allowed)
   cp claude-code/CLAUDE-MPA-RELAXED.md CLAUDE.md
   ```

2. Claude Code will automatically read `CLAUDE.md` from your project root.

</details>

### For OpenAI Codex CLI

<details>
<summary><strong>Expand for OpenAI Codex CLI setup</strong></summary>

1. Copy the appropriate file to your project root as `AGENTS.md`:

   ```sh
   # For strict rules
   cp openai-codex/AGENTS-MPA-STRICT.md AGENTS.md

   # For relaxed rules (jQuery allowed)
   cp openai-codex/AGENTS-MPA-RELAXED.md AGENTS.md
   ```

2. OpenAI Codex will automatically read `AGENTS.md` from your project root.

</details>

### For Cline

<details>
<summary><strong>Expand for Cline setup</strong></summary>

1. Copy the appropriate file to your project root:

   ```sh
   # For strict rules
   cp .cline/mpa-strict.md .clinerules

   # For relaxed rules (jQuery allowed)
   cp .cline/mpa-relaxed.md .clinerules
   ```

2. Or create a `.clinerules/` directory for multiple rule files.

</details>

### For Roo Code

<details>
<summary><strong>Expand for Roo Code setup</strong></summary>

1. Copy the rules to your project:

   ```sh
   # For strict rules
   mkdir -p .roo/rules
   cp .roo/rules/mpa-strict.md .roo/rules/

   # For relaxed rules (jQuery allowed)
   mkdir -p .roo/rules
   cp .roo/rules/mpa-relaxed.md .roo/rules/
   ```

2. Or use a single `.roorules` file in your project root.

</details>

### For JetBrains AI Assistant

<details>
<summary><strong>Expand for JetBrains AI Assistant setup</strong></summary>

1. Open your JetBrains IDE (IntelliJ IDEA, WebStorm, PhpStorm, etc.)
2. Go to **Settings → Tools → AI Assistant → Prompt Library**
3. Copy prompts from `jetbrains-ai/mpa-prompts.md`
4. Add them to your prompt library

</details>

### For Augment Code / Kilo Code / Kiro / Qwen Coder

<details>
<summary><strong>Expand for other AI assistants setup</strong></summary>

Copy the appropriate instructions file to your project and configure according to each tool's documentation:

- **Augment Code**: `augment-code/mpa-strict.md` or `mpa-relaxed.md`
- **Kilo Code**: `kilo-code/mpa-strict.md` or `mpa-relaxed.md`
- **Kiro**: `kiro/mpa-strict.md` or `mpa-relaxed.md`
- **Qwen Coder**: `qwen-coder/mpa-strict.md` or `mpa-relaxed.md`

</details>

### For Bolt.new / Lovable / V0.app / Replit

<details>
<summary><strong>Expand for system prompt-based tools setup</strong></summary>

1. Copy the content from the appropriate file:
   * **Strict**: `system-prompts/mpa-strict-system-prompt.md`
   * **Relaxed**: `system-prompts/mpa-relaxed-system-prompt.md`
2. Paste as your system prompt or custom instructions in the platform's settings.

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
│
├── .github/                              # GitHub Copilot (Source of Truth)
│   ├── agents/
│   │   ├── mpa-strict-agent.md          # Copilot Coding Agent (strict)
│   │   └── mpa-relaxed-agent.md         # Copilot Coding Agent (relaxed)
│   └── copilot-instructions.md          # Copilot IDE instructions
│
├── .cursor/                              # Cursor IDE
│   └── rules/
│       ├── mpa-strict-rules.mdc         # .mdc format (strict)
│       └── mpa-relaxed-rules.mdc        # .mdc format (relaxed)
│
├── .windsurf/                            # Windsurf IDE
│   ├── mpa-strict-rules.md              # .windsurfrules format (strict)
│   └── mpa-relaxed-rules.md             # .windsurfrules format (relaxed)
│
├── .gemini/                              # Gemini CLI
│   ├── GEMINI-MPA-STRICT.md             # GEMINI.md format (strict)
│   └── GEMINI-MPA-RELAXED.md            # GEMINI.md format (relaxed)
│
├── .claude/                              # Claude Desktop/Projects
│   ├── mpa-strict-instructions.md       # Custom instructions (strict)
│   └── mpa-relaxed-instructions.md      # Custom instructions (relaxed)
│
├── .cline/                               # Cline
│   ├── mpa-strict.md                    # .clinerules format (strict)
│   └── mpa-relaxed.md                   # .clinerules format (relaxed)
│
├── .roo/                                 # Roo Code
│   └── rules/
│       ├── mpa-strict.md                # .roorules format (strict)
│       └── mpa-relaxed.md               # .roorules format (relaxed)
│
├── claude-code/                          # Claude Code CLI
│   ├── CLAUDE-MPA-STRICT.md             # CLAUDE.md format (strict)
│   └── CLAUDE-MPA-RELAXED.md            # CLAUDE.md format (relaxed)
│
├── openai-codex/                         # OpenAI Codex CLI
│   ├── AGENTS-MPA-STRICT.md             # AGENTS.md format (strict)
│   └── AGENTS-MPA-RELAXED.md            # AGENTS.md format (relaxed)
│
├── GPT-5_and_GPT-5-Codex/                # GPT-5/ChatGPT
│   ├── mpa-strict-system-prompt.md      # System prompt (strict)
│   └── mpa-relaxed-system-prompt.md     # System prompt (relaxed)
│
├── jetbrains-ai/                         # JetBrains AI Assistant
│   └── mpa-prompts.md                   # Prompt library templates
│
├── augment-code/                         # Augment Code
│   ├── mpa-strict.md                    # Instructions (strict)
│   └── mpa-relaxed.md                   # Instructions (relaxed)
│
├── kilo-code/                            # Kilo Code
│   ├── mpa-strict.md                    # Rules (strict)
│   └── mpa-relaxed.md                   # Rules (relaxed)
│
├── kiro/                                 # Kiro
│   ├── mpa-strict.md                    # Instructions (strict)
│   └── mpa-relaxed.md                   # Instructions (relaxed)
│
├── qwen-coder/                           # Qwen Coder
│   ├── mpa-strict.md                    # Instructions (strict)
│   └── mpa-relaxed.md                   # Instructions (relaxed)
│
├── system-prompts/                       # Generic System Prompts
│   ├── mpa-strict-system-prompt.md      # For Bolt.new, Lovable, V0.app, Replit
│   └── mpa-relaxed-system-prompt.md     # For Bolt.new, Lovable, V0.app, Replit
│
├── mpa-rules.md                          # Original strict rules
├── mpa-relaxed-rules.md                  # Original relaxed rules (jQuery)
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
