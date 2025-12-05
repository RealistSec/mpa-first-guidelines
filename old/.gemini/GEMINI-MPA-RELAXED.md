# Project Context: MPA-First Development Mandate (Relaxed - jQuery Allowed)

## Core Philosophy

You are working on a server-rendered **Multi-Page Application (MPA)** project that prioritizes:
- **The Platform First:** HTML, CSS, and server-side logic (PHP)
- **Simplicity Over Complexity:** Simple, durable solutions over complex ones
- **Progressive Enhancement:** JavaScript is an enhancement, not a requirement. Core functionality must work without it. We use **jQuery** for progressive enhancement.

## 🚫 ABSOLUTE PROHIBITIONS

**You MUST NOT suggest, reference, or use:**
- React, Angular, Vue, Svelte, Next.js, Nuxt.js, or any SPA framework
- JSX, TSX, or any form of client-side routing

## Required Architecture

### Multi-Page Application Structure

1. **Each page is a separate file** (`.php`, `.html`) at a unique URL
2. **Navigation uses standard `<a href="...">` links** that trigger full page loads
3. **Core functionality MUST work with JavaScript disabled**

### Folder Structure

```
project-root/
├── public/                # Web root
│   ├── assets/
│   │   ├── css/
│   │   ├── js/
│   └── index.php
├── src/
│   ├── controllers/       # Request handlers
│   ├── models/            # Business logic and data
│   ├── views/             # HTML templates
└── vendor/                # Composer dependencies
```

## JavaScript Rules: Progressive Enhancement with jQuery

### jQuery is the Standard

- **Use jQuery** for all DOM manipulation, event handling, and AJAX requests
- **Include jQuery from a CDN** in the base layout file, before the closing `</body>` tag
- **Write Unobtrusive JavaScript** - site must be fully functional if JavaScript fails or is disabled

### jQuery Best Practices

1. Wrap all jQuery code in `$(function() { ... });` to ensure DOM is ready
2. Handle AJAX errors gracefully using `.done()`, `.fail()`, and `.always()`
3. Always provide fallback behavior for non-JavaScript users

### jQuery Pattern Example

HTML (works without JavaScript):
```html
<a href="?show_details=true#details" class="toggle-link">Show Details</a>
<div id="details" style="display: none;">
    <p>Here are the details you requested.</p>
</div>
```

JavaScript (enhances the experience):
```javascript
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

## HTML Requirements

### Semantic HTML (Mandatory)
- Use proper semantic elements: `<header>`, `<nav>`, `<main>`, `<article>`, `<footer>`, etc.

### Accessibility (WCAG 2.1 Level AA)
- All form inputs MUST have a `<label>`
- Use descriptive `alt` text for images (`alt=""` for decorative images)

### Speculation Rules for Instant Navigation
Include in `<head>`:
```html
<script type="speculationrules">
{ "prerender": [{"source": "document", "where": {"href_matches": "/*"}, "eagerness": "moderate"}] }
</script>
```

### SEO is a Top Priority
Every page needs a complete `<head>` with:
- Unique `<title>` and meta description
- Canonical link
- Open Graph tags

## CSS Requirements

### Modern CSS
- Use Flexbox and Grid for layouts
- Use Custom Properties (`--var-name`) for theming and maintainability

### CSS View Transitions
Use native View Transitions for fluid navigation:
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

## PHP Requirements

### Modern PHP 8.1+
- Always start files with `declare(strict_types=1);`
- Adhere to PSR-12 coding standards
- Use modern PHP features: constructor property promotion, `readonly` properties, `match` expressions, enums

### Example:
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

## Security Requirements

### Database Security
- **Always use parameterized queries** - NO exceptions
- Never concatenate user input into SQL

### CSRF Protection
- All POST forms MUST have CSRF protection
- Generate a token, store it in the session, and validate on submission

### Content Security Policy
Implement strict CSP, whitelisting jQuery CDN:
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

## Response Guidelines

When working on this project:
1. Always prioritize the platform (HTML, CSS, server-side logic) first
2. Use jQuery for progressive enhancement
3. Ensure core functionality works without JavaScript
4. Never suggest SPA frameworks or patterns
5. Always verify semantic HTML and accessibility
6. Check that SEO requirements are met

## Tools and Commands

- Use `pnpm` if package manager is needed
- Use Composer for PHP dependencies
- Include jQuery from CDN (e.g., https://code.jquery.com/jquery-3.7.1.min.js)
