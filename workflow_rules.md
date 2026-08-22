# Development & Deployment Guidelines — The Creative Platter

## 1. Safety & Settings Preservation Rules
- **Live Customizer Authority**: `config/settings_data.json` is controlled by the live Shopify Theme Customizer.
- **Never Overwrite `settings_data.json`**: We will not manually edit or force-push `config/settings_data.json` so that all merchant customizer settings and image uploads remain intact.
- **Theme Backups**: Full theme backups are archived in `backups/` before major updates.

## 2. Preview First (Theme Dev)
- Always preview and validate changes using a development/test server before pushing to live:
  ```bash
  shopify theme dev --store th9mw0-ry.myshopify.com
  ```
  *(Creates a temporary development theme for live preview without affecting live customers).*

## 3. Targeted Push (Edited Files Only)
- When pushing updates to the live theme (`Atelier` #`188298068248`), push only the specific modified files (e.g. sections, templates, or snippets) using `--only`:
  ```bash
  shopify theme push --theme 188298068248 --store th9mw0-ry.myshopify.com --only sections/section-pushpa-dinner-sets.liquid --allow-live
  ```
