## 2025-04-07 - Disabled Anchor Tags

**Learning:** Styling an `<a>` tag to look disabled (e.g., using `pointer-events: none` and visual opacity) is not enough for keyboard and screen reader accessibility. Because it remains natively focusable, users tabbing through the page will land on a visually "dead" link, causing confusion and trapping focus.

**Action:** Whenever a link acts as a button and needs to be disabled, always add `aria-disabled="true"` to signal its state to assistive technologies and `tabindex="-1"` to explicitly remove it from the keyboard focus order.