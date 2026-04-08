## 2023-10-24 - Resolving Ambiguous Link Context
**Learning:** Found a recurring pattern in the app cards where identical link text ("Google Play", "Privacidad") was used across multiple sections. This creates a confusing experience for screen reader users navigating a list of links without surrounding context.
**Action:** Always add descriptive `aria-label` attributes (e.g., `aria-label="Descargar BrainFit en Google Play"`) to generic links inside repeated components like cards.

## 2023-10-24 - Resolving Ambiguous Link Context

**Learning:** Found a recurring pattern in the app cards where identical link text ("Google Play", "Privacidad") was used across multiple sections. This creates a confusing experience for screen reader users navigating a list of links without surrounding context.

**Action:** Always add descriptive `aria-label` attributes (e.g., `aria-label="Descargar BrainFit en Google Play"`) to generic links inside repeated components like cards.
