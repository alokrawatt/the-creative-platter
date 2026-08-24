# Development, Design & Deployment Guidelines — The Creative Platter

## 1. Unified Brand Design System

All sections, templates, and components across the website must strictly adhere to the unified typography hierarchy and color palette:

### 1.1 Typography Tokens
| Token / Role | Font Family | Usage |
| :--- | :--- | :--- |
| **Editorial Serif** | `'Cormorant Garamond', Georgia, serif` | Hero titles, section headings, quote banners, legacy expressions |
| **Modern Clean Sans** | `'Plus Jakarta Sans', -apple-system, sans-serif` | Body text, descriptions, navigation, buttons, specs |
| **Brand Tracking Sans** | `'Raleway', sans-serif` | Eyebrows, all-caps pills, badges (`letter-spacing: 2px–3.5px`) |
| **Accent Script** | `'Sacramento', cursive` | Organic cursive subtitles (*"the"*, *"The Legacy Collection"*, *"crafted with patience"*) |

```css
:root {
  --font-serif: 'Cormorant Garamond', Georgia, serif;
  --font-sans: 'Plus Jakarta Sans', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
  --font-brand: 'Raleway', sans-serif;
  --font-script: 'Sacramento', cursive;
  --ease-fluid: cubic-bezier(0.16, 1, 0.3, 1);
}
```

---

### 1.2 Color Palette Tokens
| Token / Role | Hex Code | Description & Usage |
| :--- | :--- | :--- |
| **Pure White** | `#FFFFFF` | Primary background for all pages, header, clean containers |
| **Warm Sand Card** | `#FAF7F2` / `#FBF9F5` | Secondary surface background, testimonial cards, swatch containers |
| **Charcoal Body** | `#545454` | Main reading text (softer than harsh pure black) |
| **Deep Charcoal / Heading** | `#2D2A27` / `#1F1D1B` | High-contrast headings, dark closing banners, button backgrounds |
| **Primary Gold** | `#fcce3a` / `#A6732E` / `#C29B38` | Accent pills, decorative divider bars, active links, primary CTA |
| **Gold Hover / Dark** | `#8C5F22` / `#e5b92e` | Interactive button hover and focus states |
| **Muted Grey** | `#8E8981` / `#7A746D` | Subtitles, secondary captions, metadata tags |
| **Subtle Border** | `#ECE7DF` / `#F0ECE6` | Section divider lines, card borders, subtle grid separators |

```css
:root {
  --tcp-white: #FFFFFF;
  --tcp-sand: #FAF7F2;
  --tcp-stone: #FBF9F5;
  --tcp-grey-body: #545454;
  --tcp-grey-dark: #2D2A27;
  --tcp-grey-muted: #8E8981;
  --tcp-gold: #fcce3a;
  --tcp-gold-accent: #fcce3a;
  --tcp-gold-hover: #8C5F22;
  --tcp-border: #ECE7DF;
}
```

---

## 2. Standardized Editorial Hero Architecture

The standard Hero section across core pages (`shop`, `pushpa-collection`, etc.) must follow the unified full-background editorial structure:

- **Background**: Full-bleed responsive image (`object-fit: cover`) with directional gradient overlay (90° desktop / 180° mobile).
- **Layout**: Left-aligned content container with max-width `540px`.
- **Content Hierarchy**:
  1. `tcp-hero__pill`: All-caps tracking eyebrow in `Raleway` (`#fcce3a`).
  2. `tcp-hero__title`: Large display title in `Cormorant Garamond` with gold accent period dot `<span class="dot">.</span>`.
  3. `tcp-hero__script`: Elegant cursive subtitle in `Sacramento`.
  4. `tcp-hero__desc`: Editorial description in `Cormorant Garamond` / `Plus Jakarta Sans`.
  5. `tcp-hero__actions`: Primary gold CTA button (`#A6732E`) + Secondary inline arrow link.

---

## 3. Safety & Settings Preservation Rules

- **Live Customizer Authority**: `config/settings_data.json` is strictly controlled by the live Shopify Theme Customizer.
- **Never Overwrite `settings_data.json`**: We will not manually edit or force-push `config/settings_data.json` so that all merchant customizer settings, uploaded assets, and navigation selections remain intact.
- **Theme Backups**: Full theme backups are archived in `backups/` before major updates.

---

## 4. Development & Deployment Procedures

### 4.1 Preview First (Theme Dev)
Always preview and validate changes using a development/test server before pushing to live:
```bash
shopify theme dev --store th9mw0-ry.myshopify.com
```

### 4.2 Targeted Push (Edited Files Only)
When pushing updates to the live theme (`Atelier` `#188298068248`), push only the specific modified files (e.g., sections, templates, or snippets) using `--only`:
```bash
shopify theme push --theme 188298068248 --store th9mw0-ry.myshopify.com --only sections/section-pushpa-dinner-sets.liquid --allow-live
```
