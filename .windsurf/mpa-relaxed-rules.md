# Windsurf Workspace Rules - MPA-First Development (Relaxed - jQuery Allowed)

## Version
v1.0

## Core Configuration
- Architecture: Multi-Page Application (MPA)
- Code Style: clean_and_maintainable
- JavaScript: jQuery for progressive enhancement
- Server-Side: PHP 8.1+ with strict types
- CSS: Modern CSS with Flexbox/Grid and View Transitions

## Prime Directive: MPA-Only Architecture

1. **MUST** build server-rendered MPAs. Each distinct page or view is its own file (e.g., `.php`, `.html`) at a unique URL.
2. Navigation **MUST** use standard anchor links (`<a href="...">`) that trigger a full page load.
3. **Core functionality MUST work with JavaScript disabled.**

## 🚫 BANNED TECHNOLOGIES & PATTERNS

- **DO NOT** use or reference any Single-Page Application (SPA) frameworks or libraries
- This includes: **React, Angular, Vue, Svelte, Next.js, and Nuxt.js**
- **DO NOT** use **JSX, TSX, or any form of client-side routing**

## JavaScript Rules (Progressive Enhancement with jQuery)

1. **jQuery is the standard** for all DOM manipulation, event handling, and AJAX requests
2. **Include jQuery from a CDN** in the base layout file, just before the closing `</body>` tag
3. **Write Unobtrusive JavaScript** - site must be fully functional if JavaScript fails or is disabled
4. Wrap all jQuery code in `$(function() { ... });` to ensure DOM is ready
5. Handle AJAX errors gracefully using `.done()`, `.fail()`, and `.always()`

### jQuery Pattern Example
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

## HTML Standards

1. **Semantic HTML is Mandatory**
   - Use `<header>`, `<nav>`, `<main>`, `<article>`, `<footer>`, etc., correctly

2. **Accessibility (A11Y) - WCAG 2.1 Level AA**
   - All form inputs must have a `<label>`
   - Use descriptive `alt` text for images (`alt=""` for decorative images)

3. **Speculation Rules for Instant Navigation**
   ```html
   <script type="speculationrules">
   { "prerender": [{"source": "document", "where": {"href_matches": "/*"}, "eagerness": "moderate"}] }
   </script>
   ```

4. **SEO is a top priority**
   - Every page needs a complete `<head>` with `title`, `meta description`, `canonical` link, and Open Graph tags

## CSS Standards

1. **Use Modern CSS**
   - Flexbox and Grid for all layouts
   - Custom Properties (`--var-name`) for theming

2. **Native CSS View Transitions**
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

## PHP Standards

1. **Target PHP 8.1+** and always start files with `declare(strict_types=1);`
2. **Adhere to PSR-12** for clean, standardized code
3. **Use modern PHP features**: constructor property promotion, `readonly` properties, `match` expressions, and enums

### Modern PHP Example
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

## Security Standards

1. **Always use parameterized queries** to prevent SQL injection - NO exceptions
2. **All POST forms must have CSRF protection**
   - Generate a token, store it in the session, validate on submission
3. **Implement a strict Content Security Policy (CSP)**
   - Whitelist any CDNs you use (like for jQuery)

### CSP Header Example with jQuery CDN
```php
<?php
$csp = "default-src 'self'; " .
       "script-src 'self' https://code.jquery.com; " .
       "style-src 'self'; " .
       "img-src 'self'; " .
       "form-action 'self'; " .
       "frame-ancestors 'none';";
header("Content-Security-Policy: " . $csp);
?>
```

## Folder Structure

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

## AI Assistant Behaviors

1. Always prioritize the platform (HTML, CSS, server-side logic) first
2. Use jQuery for progressive enhancement
3. Ensure core functionality works without JavaScript
4. Never suggest SPA frameworks or patterns
5. Always verify semantic HTML and accessibility
6. Check that SEO requirements are met
