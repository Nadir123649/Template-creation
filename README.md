# Pro-Dent Club Email Templates

This workspace contains multiple Pro-Dent Club email layout variations and a welcome email design built for responsive HTML email rendering.

The templates are designed for email clients, especially Outlook and mobile clients, using table-based layout patterns with inline CSS and media-query fallbacks.

---

## Included Files

- `index.html` — base email layout / reference template
- `v1.html` — version 1 layout with 3-step process section
- `welcom.html` — welcome email version with warm card layout and rounded borders
- `final.html` — final revised version
- `second.html` — alternate layout
- `third.html` — alternate layout
- `variation-1.html` — variation 1
- `variation-2.html` — variation 2
- `variation-3.html` — variation 3
- `README.md` — project documentation

---

## Design Notes

- Email-first HTML structure using tables for compatibility
- Responsive behavior through media queries
- Pro-Dent Club branding colors and premium dental GPO styling
- Dark premium sections, gold accents, cream backgrounds, and warm neutral tones
- CTA buttons, partner cards, stats sections, and onboarding-style welcome copy

---

## Common Styling Approach

- Inline CSS for critical email rendering
- Hardcoded mobile padding and widths for Outlook-safe layouts
- Border radii and card containers for modern presentation
- Support for Microsoft Outlook via conditional comments and VML fallback

---

## Suggested Workflow

1. Open the needed version file in the browser or email preview tool.
2. Update copy, layout spacing, or styling as required.
3. Test in a mobile email preview and Outlook-compatible environment.
4. Copy the approved version into the final production file when needed.

---

## Git Usage

```bash
git add .
git commit -m "Update Pro-Dent Club email template"
git push origin main
```

---

© 2026 Pro-Dent Club. All Rights Reserved.
