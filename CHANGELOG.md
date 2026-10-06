# F1 Clash 2026 Setup Optimizer — Changelog

## v4.1 (October 2026)
- **Driver Series tiers corrected** — fixed Grand Prix suggestions dropping high-stat drivers because their `series` value was a placeholder, not their real unlock tier. The GP filter excludes any driver whose `series` > the category cap (Junior=3, Challenger=6, Contender=9, Champions=12), so wrong series = wrongly hidden (or wrongly shown).
  - **Legendary** (was `0` → always passed every cap): set to real tiers — Junior/3: Fisichella, McLaren, G.Villeneuve, Herbert · Challenger/6: Webber, Massa, Coulthard, Rindt, Berger · Contender/9: Hunt, J.Villeneuve, Andretti, Button, D.Hill, Mansell · Champion/12: Senna, G.Hill, Fittipaldi, Lauda, Brabham, Fangio, Prost, Schumacher.
  - **Paddock Pick** (was `13` → always hidden, exceeded max cap 12): Junior/3: Piastri, Colapinto · Challenger/6: Lindblad, Gasly · Contender/9: Antonelli, Bortoleto, Bearman, Hadjar.
  - **Paddock Pick Turbo** (was `14` → always hidden): all 8 → Champion/12.
  - **Data drift resolved — Excel is now the single source again.** Previously Paddock Pick/Turbo and Legendary "Herbert" existed ONLY in `drivers.json` (hand-added, bypassing the pipeline). All of them were added into `Stats.xlsx` (Drivers sheet): Herbert (7 levels, series 3) and all 16 Paddock drivers with FULL level 1–7 stats (the v4.0 "intermediate levels TBD" gap is now filled) and correct series. Rarity strings use the exact `Paddock Pick` / `Paddock Pick Turbo` spelling the app's CSS keys on. `export-stats.py` re-run cleanly regenerates all JSON from the Excel (drivers.json now 889 rows). Re-exporting is now safe — no JSON-only drivers remain. Backups saved as `drivers.json.bak` / `Stats.xlsx.bak`.

## v4.0 (August 2026)
- **Paddock Pick Drivers** — new Special Edition tier with Normal and Turbo variants
  - 8 drivers: Piastri, Colapinto, Lindblad, Gasly, Bortoleto, Bearman, Hadjar, Antonelli
  - Normal (silver badge) + Turbo (turquoise badge) shown in a single combined inventory section
  - Max level 7, stats at Level 1 and Level 7 (intermediate levels TBD)
- **Johnny Herbert added to Legendary Drivers** — full Level 1-7 progression
- **Legendary max level corrected** — now 7 (was incorrectly set to 5)
- **Rarity CSS helper** — supports rarity names with spaces (future-proof)

## v3.9.1 (May 2026)
- **GP Weight sliders now work** — fixed bug where Component Weights and Driver Weights on the Grand Prix tab had no effect on the Suggested GP Setup. Sliders were being ignored in favor of hardcoded track-focus weights or the Results tab weights. Now the user's GP slider values are always used, with track focus multiplied on top when a location is selected.

## v3.9 (May 2026)
- **Team Score in KPI bar** — now shows the real Team Score matching the game's "Puntuación de Equipo" (car stats + pit score + both drivers)
- **Pit Time → Score formula** — discovered and implemented: `PitScore = round(208.79 - 28.76 × PitTime)`. Verified against game data with max error of 1 point across 91 data points
- **Car Total in totals bars** — component totals now include pit score conversion (previously excluded)
- **AI Compare Team Score fixed** — your setup's Team Score now includes pit score, ranking correctly against bots. OT Mode excluded from AI Compare for fair comparison (bot data doesn't include OT)
- **AI Compare OT disclaimer** — note below section title explaining OT Mode exclusion
- **Race Boosts clarified** — boosts are race-time mechanics only, do NOT affect Team Score. Removed all boost effects from displayed stats (bold indicators, label, stat modifications). Boost section remains for informational purposes
- **Unweighted drivers** — top 2 drivers by raw stat total (OV + DEF + QUAL + RS + TYRE) shown below unweighted component table
- **"Reset to 1" buttons** — next to Component Weights and Driver Weights headers, resets all sliders to 1 for the active tab
- **"Inspired by TR The Flash's work"** — credit text added to header (italic, top-right)
- **Bug / Suggestion button** — moved next to PayPal button (#DA5A0C burnt orange), links to GitHub Issues

## v3.8 (May 2026)
- **Separate weights for Results vs Grand Prix** — each tab now has independent Component and Driver Weight sliders, persisted separately
- **Legendary driver toggle** — checkbox on GP tab to include/exclude Legendary drivers from suggestions
- **Race Boost stats in dropdown** — boost options now show all affected stats inline (e.g., `Ballast · RS+5 CRN+10 PIT+5`)
- **Auto-select on focus** — clicking a level input highlights the number for quick editing
- **Level input styling** — wider, larger font, more readable
- **Icon consistency** — ⚡ = Race Boost, 🚀 = Event Boost throughout
- **Report a Bug / Suggestions** — link to GitHub Issues for community feedback
- **Light mode fixes** — AI Compare column headers (OV, DEF, QUAL, RS, TYRE, SPD, CRN, PU, PIT) now readable in both themes
- **Totals bar light mode** — Total KPI stays red with white text in light mode

## v3.7 (April 2026)
- **Component sort by Series** — inventory sorted by Series number (ascending), Starter always first
- **Driver uniqueness** — top 2 driver recommendations always unique by name (can't use same driver at different rarities)
- **Responsive CSS** — 3 breakpoints (900px, 600px, 400px) for tablet and mobile use
- **PayPal support button** — below Driver Weights in left panel

## v3.6 and earlier
- Component/Driver inventory with localStorage persistence
- Weight² optimization engine
- Event Boost % applied to checked items
- Race Boost selector
- OT Mode (#00B0F0) support
- AI Compare (Series) — compare your setup against bots
- Grand Prix tab — category-based setup with track auto-weights
- Upgrade Advisor — shows which upgrades give the most weighted score gain
- Day/Night theme toggle
- All data loaded from JSON files (components, drivers, boosts, AI compare, GP compare, track stats)
