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
