
# MPA Mandate, Rules & Guidelines for AI-Assisted Development Tools
Copilot Instructions: MPA-First Development Mandate | Guiding principles for building performant, resilient Multi-Page Applications. Focus on native web platform strengths, minimal JS, and robust SEO.

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

## 🚀 How to Guide Your AI Agent with These Rules

To ensure your AI agent (e.g., GitHub Copilot, Cursor, Claude Code, Gemini CLI) or IDE's code generation strictly adheres to the MPA-First Mandate, follow these steps:

<details>
<summary>1. 📋 **Copy the rules**</summary>

* **For GitHub Copilot (IDE Integration):** Copy the full content of `mpa-rules.md` into a file named `.github/copilot-instructions.md` at the root of your repository. This is where Copilot looks for project-specific instructions.
* **For Other AI Agents/CLIs:** Paste the core content of these rules directly into your agent's designated "system prompt," "custom instructions," or "knowledge base" file/section.
</details>

<details>
<summary>2. 🔗 **Explicitly Instruct/Reference Your AI**</summary>

* **Within `.github/copilot-instructions.md`:** Ensure your `copilot-instructions.md` includes a clear directive at the top, like:
    ```markdown
    ---
    description: All code generation and suggestions must strictly follow the MPA-First Development Mandate detailed in this repository.
    applyTo: "**"
    ---
    ```


* **In AI Chat Prompts:** When interacting directly with your AI agent, reinforce the mandate early in your conversation or prompt. For example:

    ```
    "Please generate [X feature] code, strictly adhering to the MPA-First rules from our project's `.github/copilot-instructions.md` (or the linked `mpa-rules.md`). Remember, no SPA frameworks, vanilla JS for enhancement only, and server-rendered HTML."
    ```
    * **Tip:** The more explicit you are in your prompts, the better the AI will align with your desired output.

</details>

This uses `details`/`summary` for collapsibility, bolding, code blocks for clarity, and a `Tip` for extra advice. The language is more direct and action-oriented.

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
