# Windsurf Workspace Rules - MPA-First Development (Strict)

## Version
v1.0

## Core Configuration
- Architecture: Multi-Page Application (MPA)
- Code Style: clean_and_maintainable
- JavaScript: Vanilla ES2020+ only (NO frameworks, NO jQuery)
- Server-Side: PHP 8.1+ with strict types
- CSS: Modern CSS with Flexbox/Grid and View Transitions

## Prime Directive: MPA-Only Architecture

1. **MUST** create server-rendered, multi-page websites (MPAs). Each distinct page or view must be its own unique file (e.g., `.html`, `.php`) served at a distinct URL.
2. Navigation **MUST** use standard anchor links (`<a href="...">`) that trigger a full page navigation.
3. Sites **MUST** be fundamentally functional with zero client-side JavaScript. JS should only enhance, not enable, core functionality.

## 🚫 BANNED TECHNOLOGIES & PATTERNS

- **DO NOT** use or reference any Single-Page Application (SPA) frameworks, libraries, or patterns
- This includes: React, Angular, Vue, Svelte, Next.js, Nuxt.js
- **DO NOT** use JSX, TSX, TypeScript-based routing, or any form of client-side routing
- **DO NOT** use jQuery or any JavaScript libraries/frameworks

## Folder Structure Requirements

```
project-root/
├── public/                # Web root, all publicly accessible files
│   ├── assets/
│   │   ├── css/
│   │   ├── js/
│   │   ├── images/
│   │   ├── fonts/
│   └── index.php          # Or index.html
├── src/                   # Application source code
│   ├── controllers/       # Handles user requests
│   ├── models/            # Business logic and data interaction
│   ├── views/             # HTML templates/partials
│   └── utilities/         # Helper functions, etc.
├── vendor/                # Composer dependencies
├── config/                # Configuration files
├── tests/                 # Automated tests
└── docs/                  # Project documentation
```

## SEO Standards

### Required `<head>` Elements
1. Meta charset UTF-8
2. Viewport meta tag
3. Unique, descriptive title (50-60 chars)
4. Meta description (150-160 chars)
5. Canonical link
6. Open Graph tags (og:title, og:description, og:type, og:url, og:image)
7. Twitter Card tags
8. JSON-LD structured data where appropriate

### Structured Data
- Use JSON-LD format for structured data
- Include appropriate schema.org types (Article, BlogPosting, Organization, etc.)
- Always include publisher, author, datePublished, and image information

## HTML Standards

1. **Semantic HTML is Mandatory**
   - Use `<header>`, `<nav>`, `<main>`, `<article>`, `<section>`, `<footer>`, `<aside>` correctly
   - This is foundational for accessibility and SEO

2. **Accessibility (A11Y) - WCAG 2.1 Level AA**
   - All form inputs must have a corresponding `<label>`
   - Provide descriptive alt text for all meaningful images
   - Use `alt=""` for decorative images
   - Use ARIA roles where semantic HTML isn't sufficient

3. **Responsive Images**
   - Use `srcset` and `sizes` attributes
   - Use modern formats (WebP, AVIF) with fallbacks

4. **Speculation Rules**
   - Include in `<head>` for instant navigation
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

## CSS Standards

1. **Use Modern CSS Features**
   - Flexbox and Grid for all layouts
   - Custom Properties (CSS variables) for theming
   - NO preprocessors unless project-specific requirement

2. **CSS View Transitions**
   - Use native View Transitions for fluid navigation
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

## PHP Standards

1. **Modern PHP 8.1+**
   - Always start files with `declare(strict_types=1);`
   - Use constructor property promotion
   - Use `readonly` properties where appropriate
   - Use `match` expressions instead of `switch`
   - Use enums for fixed sets of values

2. **Code Quality**
   - Adhere to PSR-12 coding standards
   - Prefer composition over inheritance
   - Use exceptions for error handling
   - Always type hint parameters and return types

3. **Example Modern PHP Class**
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
   }
   ```

## JavaScript Standards (Progressive Enhancement Only)

1. **Vanilla JS ONLY**
   - NO libraries or frameworks whatsoever
   - NO jQuery

2. **Unobtrusive JavaScript**
   - Assume JS might fail or be disabled
   - Core functionality must not depend on it
   - Always provide fallback behavior

3. **Modern ES2020+ Features**
   - Use `async/await` for asynchronous operations
   - Use optional chaining (`?.`)
   - Use `const` and `let` (never `var`)
   - Handle errors gracefully with `try/catch`

4. **View Transitions in JavaScript**
   - Check for support: `if (document.startViewTransition)`
   - Always provide fallback for unsupported browsers

## Database Standards

1. **Always use parameterized queries** - NO exceptions
2. SQLite for simple sites, MySQL/PostgreSQL for high-concurrency
3. Use PDO for database access in PHP
4. Never concatenate user input into SQL queries

## Security Requirements

1. **Input Sanitization & Output Escaping**
   - Never trust user-provided data
   - Sanitize on input
   - Escape for context on output (HTML, SQL, etc.)

2. **CSRF Protection**
   - All state-changing requests must have CSRF tokens
   - Generate tokens with `bin2hex(random_bytes(32))`
   - Store in session and validate on submission
   - Use `hash_equals()` for comparison

3. **Content Security Policy (CSP)**
   - Implement strict CSP headers
   - No inline scripts or styles
   - Whitelist only necessary external domains

## Documentation Standards

1. **PHPDoc for PHP**
   - Document all public methods
   - Include @param, @return, @throws tags
   - Describe what functions do, not how

2. **JSDoc for JavaScript**
   - Document all public functions
   - Include parameter types and return types

## AI Assistant Behaviors

1. Explain understanding of requirements before coding
2. Ask for clarification when requirements are ambiguous
3. Suggest MPA-appropriate solutions, never SPA patterns
4. Always check for proper progressive enhancement
5. Verify semantic HTML and accessibility standards
6. Ensure SEO requirements are met for all pages
