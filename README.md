# BRZ Maintenance Calculator

Single-page static calculator for **Subaru BRZ 1st gen (FA20, ZC6, 2013–2020)** maintenance intervals.

Type your current odometer (km) → pick a schedule → see two cards: the **last service milestone** you passed (or are currently at) and the **next** one coming up. Each card shows replace items with OEM part numbers (Subaru / Toyota / OEM-supplier — Denso, Exedy, Aisin, KYB, NGK, Akebono, NTN, Bando) and a plain checklist of inspect items.

## Run it

Open `index.html` in any browser. No build step, no dependencies — Tailwind loads from CDN.

```sh
open index.html        # macOS
xdg-open index.html    # Linux
```

To deploy: drop the single file anywhere that serves static HTML (GitHub Pages, Vercel, Netlify, S3, your own server).

## Scope

Locked to the **Israeli-market BRZ Limited**:

- Engine oil: Subaru by Motul 5W-30 (Israel hot-climate spec, not 0W-20)
- Engine air filter: pre-facelift PNs (Israeli market kept this spec through 2020)
- Brakes: 294 mm Brembo (Limited trim)

## Schedules

Three independently selectable views:

1. **Subaru Factory** — the OEM owner's-manual schedule (replace + all the "inspect" items)
2. **CSG Street** — CounterSpace Garage's recommended schedule for street-driven cars
3. **CSG Track / Boosted** — CSG's tighter schedule for cars seeing track use or forced induction

CSG's published schedule is replacement-focused (it doesn't enumerate every factory "inspect" bullet). On the two CSG views, the Subaru inspect items are overlaid with their intervals scaled to CSG's faster rhythm (×0.67 for street, ×0.42 for track, rounded to 1,000 km) so they land naturally between fluid changes instead of slipping by 50%+.

## Data sources

- [CSG maintenance guide](https://www.counterspacegarage.com/blog/toyota-86-subaru-brz/recommended-maintenance-guide-for-toyota-86-subaru-brz/)
- [cars101 Subaru schedule pages](https://www.cars101.com/subaru/maintenance-2018.html) (factory schedule cross-reference)
- [FT86Club OEM PN megathread](https://www.ft86club.com/forums/showthread.php?t=79867)
- [GR86.org maintenance & part-numbers thread](https://www.gr86.org/threads/gr86-brz-basic-maintenance-fluid-specs-and-part-numbers.7905/)
- [Subaru by Motul 5W-30](https://www.motul.com/en-HR/products/60350) (Motul SKU 103172)
- partsouq.com, parts.subaru.com, parts.toyota.com (dealer PN cross-references)

## Caveats

- Part numbers were collected from public sources. Verify with a Subaru/Toyota dealer using your VIN before ordering — especially for items with year/trim splits (front struts split at the 2017 facelift, etc.).
- The "current" milestone is the most recent km on the schedule that's ≤ your odometer, "next" is the smallest > your odometer. Multiple items naturally cluster on the same milestone (e.g., at 48,000 km the Subaru schedule hits oil + air filter + brake fluid + clutch fluid + many inspects together).
- Time-based triggers (brake fluid every 2 years, coolant every 6 years, cabin filter annually) are shown as text chips but not computed against a date. Reset the clock yourself.

## Out of scope

- 2nd-gen GR86 / BRZ (ZD8, FA24) — schedule differs slightly; explicitly first-gen only.
- localStorage / persistence — refresh forgets everything.
- Authenticated services, server-side anything — pure static HTML.

## License

[WTFPL v2](LICENSE). Do what the fuck you want to.
