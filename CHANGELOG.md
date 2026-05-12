# F1 Clash 2026 Setup Optimizer — Changelog

## v3.9 (May 2026)
- **Team Score in KPI bar** — now shows the real Team Score matching the game's "Puntuación de Equipo" (car stats + pit score + both drivers)
- **Pit Time → Score formula** — discovered and implemented: `PitScore = round(208.79 - 28.76 × PitTime)`. Verified against game data with max error of 1 point across 91 data points
- **Car Total in totals bars** — component totals now include pit score conversion (previously excluded)
- **AI Compare Team Score fixed** — your setup's Team Score now includes pit score, ranking correctly against bots
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
