# AI Coding Agent Guidelines: The MPA-First Mandate

---

## Introduction: Why We Build This Way

For over a decade, web development has trended towards complex, JavaScript-heavy Single-Page Applications (SPAs). The promise was a slick, "app-like" user experience. The reality, in most cases, has been bloated, fragile, and over-engineered websites that are slow to load, difficult to maintain, and hostile to users and search engines.

This document outlines a return to a more resilient, performant, and durable web. We are intentionally choosing a **Multi-Page Application (MPA)** architecture. The guiding principle is to **use the platform**. We build upon the native strengths of HTML, CSS, and the browser itself, which have evolved significantly. Modern features like CSS View Transitions and Speculation Rules now provide the fluid user experience that once required megabytes of JavaScript, but without the performance penalty.

We are choosing simplicity, speed, and maintainability over unnecessary complexity. We build for users and outcomes, not for developer experience (DX) or architectural novelty. JavaScript is a powerful tool for progressive enhancement, not the default foundation for every page.

---

## PRIME DIRECTIVE: MPA-Only Architecture

- You **MUST** create server-rendered, multi-page websites (MPAs). Each distinct page or view must be its own unique file (e.g., `.html`, `.php`) served at a distinct URL.
- Navigation **MUST** use standard anchor links (`<a href="...">`) that trigger a full page navigation. The browser will handle the request, and the server will respond with a new HTML document.
- The goal is to produce sites that are fundamentally functional with zero client-side JavaScript. JS should only be used to enhance, not to enable, core functionality.

### 🚫 BANNED TECHNOLOGIES & PATTERNS

- **DO NOT** use or reference any Single-Page Application (SPA) frameworks, libraries, or patterns.
  - This includes, but is not limited to: React, Angular, Vue, Svelte, Next.js, Nuxt.js.
- **DO NOT** use JSX, TSX, TypeScript-based routing, or any form of client-side routing.

---

## Guiding Complex Changes

When approaching a complex change or refactoring a large file, prioritize clarity and communication:

1. **Outline a Plan:** Before diving in, briefly describe your approach. What is the goal? Which parts of the code will you touch?
2. **Communicate as You Go:** Explain your changes in small, logical steps. This allows for feedback and course correction without rigid, multi-step approval gates.
3. **Focus on Conceptual Changes:** Group your edits logically. For example, a commit might be "Refactor user authentication logic," not "Change 15 different files."

---

## Folder Structure

This structure promotes a clean separation of concerns and follows the Model-View-Controller (MVC) architectural pattern:

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

---

## SEO Best Practices: A Top Priority

Excellent SEO is not an afterthought; it's a direct result of building a clean, semantic, and performant MPA.

### 1. The Head is Everything

Ensure every page has a comprehensive and valid `<head>` section:

**Example: Detailed `<head>` for a Blog Post**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>It's Time for Modern CSS to Kill the SPA | My Awesome Blog</title>
    <meta name="description" content="Native CSS transitions have quietly killed the strongest argument for client-side routing. Learn how to build faster, simpler websites.">

    <link rel="canonical" href="https://www.example.com/blog/css-kills-spa">

    <meta property="og:title" content="It's Time for Modern CSS to Kill the SPA">
    <meta property="og:description" content="Native CSS transitions have quietly killed the strongest argument for client-side routing. Learn how to build faster, simpler websites.">
    <meta property="og:type" content="article">
    <meta property="og:url" content="https://www.example.com/blog/css-kills-spa">
    <meta property="og:image" content="https://www.example.com/assets/images/blog/og-image-css-spa.jpg">
    <meta property="og:image:width" content="1200">
    <meta property="og:image:height" content="630">
    <meta property="og:site_name" content="My Awesome Blog">

    <meta name="twitter:card" content="summary_large_image">
    <meta name="twitter:site" content="@MyAwesomeBlog">
    <meta name="twitter:title" content="It's Time for Modern CSS to Kill the SPA">
    <meta name="twitter:description" content="Native CSS transitions have quietly killed the strongest argument for client-side routing.">
    <meta name="twitter:image" content="https://www.example.com/assets/images/blog/twitter-card-css-spa.jpg">
</head>
<body>
</body>
</html>
```

### 2. Structured Data with JSON-LD

Embed structured data to help search engines understand your content. This is critical for rich results (reviews, recipes, events, etc.):

**Example: JSON-LD for an Article**

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "BlogPosting",
  "headline": "It's Time for Modern CSS to Kill the SPA",
  "datePublished": "2025-07-24T09:00:00Z",
  "dateModified": "2025-07-25T10:30:00Z",
  "author": {
    "@type": "Person",
    "name": "Jono Alderson",
    "url": "https://www.example.com/authors/jono-alderson"
  },
  "image": {
    "@type": "ImageObject",
    "url": "https://www.example.com/assets/images/blog/og-image-css-spa.jpg",
    "width": 1200,
    "height": 630
  },
  "publisher": {
    "@type": "Organization",
    "name": "My Awesome Blog",
    "logo": {
      "@type": "ImageObject",
      "url": "https://www.example.com/assets/images/logo.png",
      "width": 600,
      "height": 60
    }
  },
  "description": "Native CSS transitions have quietly killed the strongest argument for client-side routing. Learn how to build faster, simpler websites.",
  "mainEntityOfPage": {
    "@type": "WebPage",
    "@id": "https://www.example.com/blog/css-kills-spa"
  }
}
</script>
```

---

## HTML Requirements

- **Semantic HTML is Mandatory:** Use `<header>`, `<nav>`, `<main>`, `<article>`, `<section>`, `<footer>`, `<aside>`, etc., correctly. This is foundational for accessibility and SEO.
- **Accessibility (A11Y):** Adhere to WCAG 2.1 Level AA.
  - All form inputs must have a corresponding `<label>`.
  - Provide descriptive alt text for all meaningful images (`alt=""` for decorative ones).
  - Use ARIA roles where semantic HTML isn't sufficient.
- **Responsive Images:** Use `srcset` and `sizes` to serve appropriately sized images. Use modern formats like WebP or AVIF with a fallback.
- **Prerender for Instant Navigation:** Use Speculation Rules to make navigation feel instantaneous.

**Example: Instant Prerendering with Speculation Rules**

```html
<script type="speculationrules">
{
  "prerender": [{
    "source": "document",
    "where": {
      "href_matches": "/*"
    },
    "eagerness": "moderate"
  }]
}
</script>
```

---

## CSS Requirements

- **Embrace Modern CSS:** Use Flexbox and Grid for layouts. Use Custom Properties for theming and maintainability.
- **Native View Transitions:** This is our primary tool for creating "app-like" fluid navigation without JavaScript.

**Example: Cross-Page Fade Transition**

```css
/* Add to every page for a simple, elegant fade */
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

---

## PHP Requirements

- **Modern & Strict:** Target PHP 8.1+. Always start files with `declare(strict_types=1);`.
- **Clean Code:** Adhere to a standard like PSR-12. Prefer composition over inheritance. Use exceptions for error handling.
- **Leverage Modern Features:** Use constructor property promotion, `match` expressions, enums, and the nullsafe operator.

**Example: Modern PHP Class**

```php
<?php
declare(strict_types=1);

namespace App\Models;

use App\Db;
use App\Enums\UserStatus;

readonly class User
{
    public function __construct(
        private Db $db,
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

---

## JavaScript Requirements (Progressive Enhancement Only)

- **Vanilla JS ONLY:** NO libraries or frameworks (including jQuery).
- **Unobtrusive:** Assume JS might fail or be disabled. Core functionality must not depend on it.
- **Modern & Safe:** Use ES2020+ features like `async/await`, optional chaining (`?.`), and `const`/`let`. Handle errors gracefully with `try/catch`.

**Example: Unobtrusive JS for a Toggle Button**

HTML (works without JS):

```html
<a href="?show_details=true#details" class="toggle-link">Show Details</a>
```

JavaScript (enhances the experience if it runs):

```javascript
document.querySelector('.toggle-link')?.addEventListener('click', async (event) => {
  event.preventDefault(); // Prevent default navigation
  const details = document.querySelector('#details');
  if (details) {
    const isHidden = details.hidden;
    // Use a View Transition for a smooth reveal if available
    if (document.startViewTransition) {
        document.startViewTransition(() => {
            details.hidden = !isHidden;
            event.target.textContent = isHidden ? 'Hide Details' : 'Show Details';
        });
    } else {
        // Fallback for older browsers
        details.hidden = !isHidden;
        event.target.textContent = isHidden ? 'Hide Details' : 'Show Details';
    }
  }
});
```

---

## General Considerations

### 1. Database

Choose a database appropriate for the project's needs. SQLite is excellent for many sites due to its simplicity. For high-concurrency writes, consider MySQL or PostgreSQL. Regardless of the choice, always use **parameterized queries** to prevent SQL injection.

**Example: Secure Parameterized Query in PHP (PDO)**

```php
<?php
// Unsafe query (vulnerable to SQL injection)
// $statement = $pdo->query("SELECT * FROM users WHERE id = " . $_GET['id']);

// Safe, parameterized query
$stmt = $pdo->prepare('SELECT * FROM users WHERE id = :id');
$stmt->execute(['id' => $_GET['id']]);
$user = $stmt->fetch();
```

### 2. Documentation

Consistent documentation is crucial. Follow established standards like PHPDoc for PHP and JSDoc for JavaScript to describe what a function does, its parameters, and what it returns:

**Example: Documenting a PHP Function (PHPDoc style)**

```php
<?php
/**
 * Retrieves a user from the database by their ID.
 *
 * @param PDO $pdo The database connection object.
 * @param int $userId The ID of the user to fetch.
 * @return array|false The user data as an associative array, or false if not found.
 * @throws InvalidArgumentException if the user ID is not a positive integer.
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

### 3. Security

Security is a prerequisite, not a feature:

- **Sanitize Inputs, Escape Outputs:** Never trust user-provided data. Sanitize it on input and always escape it for the specific context of its output (e.g., HTML, SQL).
- **CSRF Protection:** All state-changing requests (e.g., forms submitted via POST) must be protected against Cross-Site Request Forgery.
- **Content Security Policy (CSP):** Implement a strict CSP to mitigate the risk of XSS and data injection attacks.

**Example: Basic CSRF Token Implementation**

```php
<?php
// In the script that displays the form:
session_start();
if (empty($_SESSION['csrf_token'])) {
    $_SESSION['csrf_token'] = bin2hex(random_bytes(32));
}
?>
<form action="/submit" method="post">
    <input type="hidden" name="csrf_token" value="<?= htmlspecialchars($_SESSION['csrf_token']) ?>">
    <button type="submit">Submit</button>
</form>

<?php
// In the /submit script that processes the form:
session_start();
if (!isset($_POST['csrf_token']) || !hash_equals($_SESSION['csrf_token'], $_POST['csrf_token'])) {
    // Token is invalid or missing, reject the request.
    http_response_code(403);
    die('CSRF validation failed.');
}
// Proceed with processing the form...
// Note: Do NOT unset the token here. Reusing the same token for the
// user's session is more robust and prevents issues with multiple
// tabs or the back button.
?>
```

**Example: Setting a Strict Content Security Policy Header in PHP**

```php
<?php
// This is a strict policy. It requires that all CSS and JavaScript
// be loaded from external files hosted on the same domain.
// No inline styles or scripts are allowed.
$csp = "default-src 'self'; " .
       "img-src 'self' https://images.example.com; " .
       "style-src 'self'; " .
       "script-src 'self'; " .
       "form-action 'self'; " .
       "frame-ancestors 'none'; " .
       "object-src 'none'; " .
       "base-uri 'self';";

header("Content-Security-Policy: " . $csp);
?>
```

---

## A Living Document

These guidelines are a starting point. The web platform evolves, and so should our practices. The core philosophy—simplicity, performance, and leveraging the native power of the web—remains constant. We champion this approach to build a better, faster, and more accessible web for everyone.
