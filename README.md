# Casa Nira · Villa C5 — Upgraded Inventory

A single self-contained web page (`index.html`) showing the FF&E upgrade inventory and
custom-branding catalog for **Villa C5 · Lara · The Sanctuary** (3BR, 160 sqm).
Built on the shared Casa Nira inventory template.

## Baseline verification
The retained/upgraded rows were checked line-by-line against Annex I ("Spesifikasi Villa
dan Daftar Perabot") of **`C5_Furniture Agreement_Lara Bakker.pdf`**
(CN-C5-FURN-001, signed 25 July 2025).

- **83 / 83 baseline items matched** on quantity and location
- **0 discrepancies** between the agreement's `Ex:` brands and the page's `prevBrand`

C5's Annex I is item-for-item identical to C1's (same quantities, locations, and brands,
including the C1-specific splits: AC 1.5 PK ×4 in Dining + Bedrooms, Iron ×1, TV Stand ×1,
TV Cabinet/Shelving ×3, Wall Shelving All Bedrooms ×2, Outdoor Dining Chair ×3, and the
"Glassware Set" / "Pool Towel Set" naming). The page was therefore derived from C1's with
identity changes only.

### Open items to confirm with the team
- Owner display name is shown as **"Lara"** (from the document filename; the contracting
  entity is PT Citra Rasa Rijckholt, represented for Lara Iris Rijckholt Bakker). Confirm
  the preferred display name.
- Five linen/kitchen rows carried from the shared upgrade programme are **not itemised in
  C5's Annex I**: Spatula & Cooking Spoon Set, Flat Sheet, Duvet Cover, Waterproof
  Mattress Protector, Duvet Insert. They are shown as *As Is* (same as C1).
- Annex I lists the bathtub and bathroom mirrors under *Master Bedroom* / *All Bedrooms*;
  the page uses *Master Bathroom* / *All Bathrooms* for clarity.
- "The Sanctuary" estate name follows the C-block convention (not stated in the agreement).

## Structure
Everything lives in **`index.html`** — HTML, CSS, and JS in one file, no build step and no
dependencies (fonts load from Google Fonts).

- **`ITEMS`** — the inventory (136 rows): `{ cat, name, location, status, qty, prevBrand, newBrand, note? }`
  - `status`: `"Upgrade"` (gold ribbon, prev → new brand), `"New"` (green ribbon), `"As Is"`.
- **`BRANDED`** — shared custom-branding catalog (In-Room Amenities + Signage) with
  material/finish/dimension specs and Google Drive asset links.

Counts: **136 total · 28 upgraded · 41 new · 67 retained**, plus 21 branding assets.

## Run locally
```bash
python3 -m http.server 4173      # then open http://localhost:4173
```

## Deploy
No build step — fully static. Import the repo at vercel.com/new (Framework: **Other**, no
build command), or run `npx vercel --prod`.

## Notes
- The source agreement (furniture PDF) is git-ignored — not published.
- "Last updated" shows the current month automatically.
