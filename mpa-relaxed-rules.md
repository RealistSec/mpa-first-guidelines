# GitHub Copilot Instructions: MPA-First Mandate

## Core Philosophy

My primary goal is to build performant, resilient, and maintainable server-rendered **Multi-Page Applications (MPAs)**.

- **Prioritize the Platform:** Use HTML, CSS, and server-side logic (PHP) first.
- **Simplicity Over Complexity:** Choose simple, durable solutions over complex, trendy ones.
- **Progressive Enhancement:** JavaScript is an enhancement, not a requirement. Core functionality must work without it. I use **jQuery** to implement these enhancements.

---

## 1. PRIME DIRECTIVE: MPA-Only Architecture

- **You MUST build server-rendered MPAs.** Each distinct page or view is its own file (e.g., `.php`, `.html`) at a unique URL.
- **Navigation MUST use standard anchor links (`<a href="...">`)** that trigger a full page load.
- **Core functionality MUST work with JavaScript disabled.**

### 🚫 BANNED TECHNOLOGIES & PATTERNS

- **DO NOT** use or reference any Single-Page Application (SPA) frameworks or libraries. This includes **React, Angular, Vue, Svelte, Next.js, and Nuxt.js**.
- **DO NOT** use **JSX, TSX, or any form of client-side routing**.

---

## 2. JavaScript Rules (Progressive Enhancement with jQuery)

- **jQuery is the standard.** Use jQuery for all DOM manipulation, event handling, and AJAX requests.
- **Include jQuery from a CDN** in the base layout file, just before the closing `</body>` tag.
- **Write Unobtrusive JavaScript.** Always ensure the site is fully functional if JavaScript fails or is disabled.
- Wrap all jQuery code in `$(function() { ... });` to ensure the DOM is ready.
- Handle AJAX errors gracefully using `.done()`, `.fail()`, and `.always()`.

**Correct Pattern: Unobtrusive Toggle with jQuery**
```html
<!-- HTML works on its own -->
<a href="?show_details=true#details" class="toggle-link">Show Details</a>
<div id="details" style="display: none;">
    <p>Here are the details you requested.</p>
</div>
```
```javascript
// JS enhances the experience
$(function() {
  $('.toggle-link').on('click', function(event) {
    event.preventDefault();
    $('#details').slideToggle(300, () => {
      const isVisible = $('#details').is(':visible');
      $(this).text(isVisible ? 'Hide Details' : 'Show Details');
    });
  });
});
```

---

## 3. HTML Rules

- **Semantic HTML is Mandatory:** Use `<header>`, `<nav>`, `<main>`, `<article>`, `<footer>`, etc., correctly.
- **Accessibility (A11Y) is critical (WCAG 2.1 AA):**
  - All form inputs must have a `<label>`.
  - Use descriptive `alt` text for images. `alt=""` for decorative images.
- **Use Speculation Rules** in the `<head>` to prerender links for instant navigation.
  ```html
  <script type="speculationrules">
  { "prerender": [{"source": "document", "where": {"href_matches": "/*"}, "eagerness": "moderate"}] }
  </script>
  ```
- **SEO is a top priority.** Every page needs a complete `<head>` with `title`, `meta description`, `canonical` link, and Open Graph tags.

---

## 4. CSS Rules

- **Use Modern CSS:** Use Flexbox and Grid for all layouts.
- **Use Custom Properties (`--var-name`)** for theming and maintainability.
- **Use Native CSS View Transitions** for fluid "app-like" navigation.
  ```css
  @view-transition { navigation: auto; }

  ::view-transition-old(root),
  ::view-transition-new(root) {
    animation: fade-out 0.3s ease-out both;
  }

  @keyframes fade-out {
    from { opacity: 1; }
    to { opacity: 0; }
  }
  ```

---

## 5. PHP Rules

- **Target PHP 8.1+** and always start files with `declare(strict_types=1);`.
- **Adhere to PSR-12** for clean, standardized code.
- **Use modern PHP features:** constructor property promotion, `readonly` properties, `match` expressions, and enums.

**Correct Pattern: Modern PHP Class**
```php
<?php
declare(strict_types=1);
namespace App\Models;

readonly class User
{
    public function __construct(
        public int $id,
        public string $name,
    ) {}
}
```

---

## 6. Security Rules

- **Always use parameterized queries** to prevent SQL injection. No exceptions.
- **All POST forms must have CSRF protection.** Generate a token, store it in the session, and validate it on submission.
- **Implement a strict Content Security Policy (CSP).** Whitelist any CDNs you use (like for jQuery).

**Correct Pattern: CSP Header with jQuery CDN**
```php
<?php
$csp = "default-src 'self'; " .
       "script-src 'self' https://code.jquery.com; " . // Whitelist the CDN
       "style-src 'self'; " .
       "img-src 'self'; " .
       "form-action 'self'; " .
       "frame-ancestors 'none';";
header("Content-Security-Policy: " . $csp);
?>
```

---

## 7. Folder Structure

Follow this MVC-style folder structure for all projects.

```
project-root/
├── public/                # Web root
│   ├── assets/
│   │   ├── css/
│   │   ├── js/
│   └── index.php
├── src/                   # Application source code
│   ├── controllers/       # Handles user requests
│   ├── models/            # Business logic and data
│   ├── views/             # HTML templates/partials
└── vendor/                # Composer dependencies
```