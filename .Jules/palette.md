## 2023-10-24 - Resolving Ambiguous Link Context
**Learning:** Found a recurring pattern in the app cards where identical link text ("Google Play", "Privacidad") was used across multiple sections. This creates a confusing experience for screen reader users navigating a list of links without surrounding context.
**Action:** Always add descriptive `aria-label` attributes (e.g., `aria-label="Descargar BrainFit en Google Play"`) to generic links inside repeated components like cards.

## 2023-10-24 - Resolving Ambiguous Link Context

**Learning:** Found a recurring pattern in the app cards where identical link text ("Google Play", "Privacidad") was used across multiple sections. This creates a confusing experience for screen reader users navigating a list of links without surrounding context.

**Action:** Always add descriptive `aria-label` attributes (e.g., `aria-label="Descargar BrainFit en Google Play"`) to generic links inside repeated components like cards.

## 2024-04-09 - Improving Keyboard Navigation & Color Contrast for App Cards

**Learning:** Hover effects on cards (like the lift and glow animation on `.app-card`) are often missed by keyboard users, making the interface feel less responsive when tabbing. Additionally, white text on bright accent colors (like emerald `#10b981`) often fails WCAG contrast standards.

**Action:** Ensure interactive components or their containers have `:focus-within` styles that mirror `:hover` styles to provide equivalent feedback to keyboard users. Always check the contrast ratio for text on bright accent backgrounds, opting for dark colors (like `#022c22`) instead of white when necessary.

## 2024-05-18 - Accessibility Compliance with Reduced Motion Fallbacks

**Learning:** This static app heavily relies on continuous or triggered CSS animations and hover transitions to bring attention to interactive components like app cards. For users with vestibular motion disorders, these animations can cause discomfort or nausea. We need to respect the OS-level "reduced motion" preference natively.

**Action:** Whenever custom CSS animations or `transform`-based hover transitions are added in `<style>` blocks, ensure an `@media (prefers-reduced-motion: reduce)` block is included. Set `animation-duration: 0.01ms !important;` and remove transformative hover states (`transform: none`) to keep the static app accessible to all users.

## 2024-05-24 - Disabled Button UX & `pointer-events`

**Learning:** Using `pointer-events: none` on disabled visual elements (like the "Próximamente" button) ruins the user experience because it prevents the OS-level `cursor: not-allowed` from displaying and stops native `title` tooltips from rendering on hover. Users receive no interactive feedback as to why the button is unresponsive.

**Action:** When creating visually disabled buttons, avoid `pointer-events: none`. Instead, rely on `cursor: not-allowed`, add a helpful `title` tooltip explaining the disabled state, and use semantic attributes like `aria-disabled="true"` to ensure screen readers provide correct context.

## 2026-04-13 - Focusable Disabled States

**Learning:** Removing `pointer-events: none` from disabled elements only solves the issue for mouse users; keyboard users cannot reach disabled `<a>` elements without an `href` (e.g. if using `tabindex="-1"`). This causes them to completely miss the context and tooltip.

**Action:** Ensure disabled interactive elements like `<a>` tags have `tabindex="0"` and `role="button"` (if they act like buttons) along with `aria-disabled="true"`. This makes them keyboard focusable and correctly announced by screen readers without being interactive.

## 2026-04-14 - Adding Skip-to-Content Links
**Learning:** Screen reader and keyboard users navigate visually complex or long pages linearly. Without a way to bypass repetitive top-level navigation, ambient animations, or headers, reaching the main content is tedious. Adding a `skip-link` that is visually hidden but appears on `focus` creates an immediate accessibility win without compromising the visual design.
**Action:** Ensure that apps with rich headers or repeating navigation include a `.skip-link` right after the `<body>` tag pointing directly to the `<main>` content id.

## 2026-04-15 - Refining Skip-to-Content UX (Smooth Scroll & Focus Outline)
**Learning:** While skip-to-content links require `tabindex="-1"` on the target container (like `<main>`) to programmatically receive focus, this causes browsers to render a massive, visually jarring focus ring around the entire content area. Also, an instantaneous jump can be disorienting.
**Action:** Always add `#main-content:focus { outline: none; }` to hide the jarring focus ring on the main container when the skip link is used. Additionally, consider `html { scroll-behavior: smooth; }` to make the jump visually smooth, but ensure it respects `prefers-reduced-motion: reduce`.

## 2024-05-25 - External Link Context Switching
**Learning:** Links that open in a new tab (`target="_blank"`) can be disorienting for users, especially those using screen readers or those with cognitive disabilities, as the sudden context switch is unexpected and they might struggle to return to the original page.
**Action:** Always append ` (abre en una pestaña nueva)` to the `aria-label` of external links and include a visual indicator (like an external link SVG icon) to warn users visually and programmatically about the context switch.
