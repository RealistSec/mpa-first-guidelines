# Project Context: MPA-First Development Mandate (Strict Rules)

## Architecture Philosophy

You are working on a project that strictly follows **Multi-Page Application (MPA)** architecture. This is a deliberate choice to prioritize performance, resilience, maintainability, SEO, and accessibility over the complexity of Single-Page Applications (SPAs).

### Core Principle: Use the Platform

We leverage the native strengths of HTML, CSS, and the browser itself. Modern web features like CSS View Transitions and Speculation Rules provide fluid user experiences without the performance penalty of heavy JavaScript frameworks.

## 🚫 ABSOLUTE PROHIBITIONS

**You MUST NOT suggest, reference, or use:**
- React, Angular, Vue, Svelte, Next.js, Nuxt.js, or any SPA framework
- JSX, TSX, or TypeScript-based routing
- Client-side routing of any kind
- jQuery or any JavaScript libraries/frameworks

## Required Architecture

### Multi-Page Application Structure

1. **Each page is a separate file** (`.html`, `.php`) served at a unique URL
2. **Navigation uses standard `<a href="...">` links** that trigger full page loads
3. **Core functionality MUST work with JavaScript disabled**
4. JavaScript is ONLY for progressive enhancement, never for core features

### Folder Structure

```
project-root/
├── public/                # Web root
│   ├── assets/
│   │   ├── css/
│   │   ├── js/
│   │   ├── images/
│   │   ├── fonts/
│   └── index.php
├── src/
│   ├── controllers/       # Request handlers
│   ├── models/            # Business logic and data
│   ├── views/             # HTML templates
│   └── utilities/
├── vendor/                # Composer dependencies
├── config/
├── tests/
└── docs/
```

## HTML Requirements

### Semantic HTML (Mandatory)
- Use proper semantic elements: `<header>`, `<nav>`, `<main>`, `<article>`, `<section>`, `<footer>`, `<aside>`
- This is non-negotiable for SEO and accessibility

### SEO Requirements

Every page MUST have:
1. Complete `<head>` section with:
   - Meta charset (UTF-8)
   - Viewport meta tag
   - Unique, descriptive `<title>` (50-60 chars)
   - Meta description (150-160 chars)
   - Canonical link (`<link rel="canonical">`)
   - Open Graph tags (og:title, og:description, og:type, og:url, og:image)
   - Twitter Card tags

2. JSON-LD structured data:
```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "BlogPosting",
  "headline": "Article Title",
  "datePublished": "2025-07-24T09:00:00Z",
  "author": {
    "@type": "Person",
    "name": "Author Name"
  },
  "publisher": {
    "@type": "Organization",
    "name": "Site Name"
  }
}
</script>
```

### Accessibility (WCAG 2.1 Level AA)
- All form inputs MUST have associated `<label>` elements
- All meaningful images MUST have descriptive `alt` text
- Decorative images MUST use `alt=""`
- Use ARIA roles only where semantic HTML is insufficient

### Speculation Rules (Performance)
Include in `<head>`:
```html
<script type="speculationrules">
{
  "prerender": [{
    "source": "document",
    "where": {"href_matches": "/*"},
    "eagerness": "moderate"
  }]
}
</script>
```

### Responsive Images
- Use `srcset` and `sizes` attributes
- Prefer modern formats (WebP, AVIF) with fallbacks

## CSS Requirements

### Modern CSS Only
- Use Flexbox and Grid for layouts
- Use CSS Custom Properties (variables) for theming
- NO preprocessors unless explicitly required

### CSS View Transitions (Critical)
Use native View Transitions for fluid navigation:
```css
@view-transition {
  navigation: auto;
}

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
- Use constructor property promotion
- Use `readonly` properties where appropriate
- Use `match` expressions instead of `switch`
- Use enums for fixed value sets
- Adhere to PSR-12 coding standards

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
        public UserStatus $status = UserStatus::Active,
    ) {}

    public function getProfileUrl(): string
    {
        return '/users/' . $this->id;
    }
}
```

## JavaScript Requirements (Progressive Enhancement ONLY)

### Vanilla JavaScript ES2020+
- NO libraries, NO frameworks, NO jQuery
- Use `async/await`, optional chaining (`?.`), `const`/`let`
- Handle errors with `try/catch`

### Unobtrusive Pattern
HTML must work without JavaScript:
```html
<a href="?show_details=true#details" class="toggle-link">Show Details</a>
```

JavaScript enhances:
```javascript
document.querySelector('.toggle-link')?.addEventListener('click', async (event) => {
  event.preventDefault();
  const details = document.querySelector('#details');
  if (details) {
    const isHidden = details.hidden;
    if (document.startViewTransition) {
      document.startViewTransition(() => {
        details.hidden = !isHidden;
        event.target.textContent = isHidden ? 'Hide Details' : 'Show Details';
      });
    } else {
      details.hidden = !isHidden;
      event.target.textContent = isHidden ? 'Hide Details' : 'Show Details';
    }
  }
});
```

## Database Requirements

1. **Always use parameterized queries** - NO exceptions
2. Use PDO for database access
3. Never concatenate user input into SQL
4. SQLite for simple sites, MySQL/PostgreSQL for high-concurrency

### Example:
```php
<?php
// Safe, parameterized query
$stmt = $pdo->prepare('SELECT * FROM users WHERE id = :id');
$stmt->execute(['id' => $_GET['id']]);
$user = $stmt->fetch();
```

## Security Requirements (Non-Negotiable)

### Input/Output Handling
- Never trust user-provided data
- Sanitize all inputs
- Escape all outputs for their context (HTML, SQL, etc.)

### CSRF Protection
- All state-changing requests (POST) MUST have CSRF tokens
- Generate: `bin2hex(random_bytes(32))`
- Store in session
- Validate with `hash_equals()`

### Content Security Policy
Implement strict CSP:
```php
<?php
$csp = "default-src 'self'; " .
       "img-src 'self' https://images.example.com; " .
       "style-src 'self'; " .
       "script-src 'self'; " .
       "form-action 'self'; " .
       "frame-ancestors 'none'; " .
       "object-src 'none'; " .
       "base-uri 'self';";

header("Content-Security-Policy: " . $csp);
```

## Documentation Standards

### PHPDoc (Required)
```php
/**
 * Retrieves a user from the database by their ID.
 *
 * @param PDO $pdo The database connection object.
 * @param int $userId The ID of the user to fetch.
 * @return array|false The user data or false if not found.
 * @throws InvalidArgumentException if the user ID is not positive.
 */
function findUserById(PDO $pdo, int $userId): array|false
{
    if ($userId <= 0) {
        throw new InvalidArgumentException('User ID must be a positive integer.');
    }
    $stmt = $pdo->prepare('SELECT * FROM users WHERE id = :id');
    $stmt->execute(['id' => $userId]);
    return $stmt->fetch(PDO::FETCH_ASSOC);
}
```

### JSDoc (Required for JavaScript)
Document all public functions with parameter and return types.

## Response Guidelines

When working on this project:
1. Always explain your understanding before implementing
2. Ask for clarification if requirements are ambiguous
3. Suggest MPA-appropriate solutions only
4. Verify progressive enhancement in all JavaScript
5. Check semantic HTML and accessibility
6. Ensure SEO requirements are met on all pages
7. Never compromise on security standards

## Tools and Commands

- Use `pnpm` if package manager is needed
- Use Composer for PHP dependencies
- Always run tests before committing
- Follow existing code formatting conventions
