# balccon-2k26-badge

Design assets for the BalCCon 2k26 PCB-style pin/badge.

## Assembly Instructions

> **Skeleton — work in progress.** Photos of the real board and finished
> badge will replace the placeholders below once boards and parts are in
> hand. Quantities/values are pulled from the KiCad board file; double-check
> them against the actual kit before publishing this for real.

### The board

| Front (artwork side) | Back (component side) |
| --- | --- |
| TODO: photo — see `svg/pcb-only.svg` / `png/colors/` for the artwork in the meantime | TODO: photo |

The front carries the silkscreen artwork only — no components. Everything
gets soldered to the back.

### What's in the kit

| Qty | Ref | Part | Package / Value | Notes |
| --- | --- | --- | --- | --- |
| 1 | BT1 | Coin cell holder | Keystone 3002 (CR2032, 1x) | |
| 14 | D1–D14 | LED | mostly 0805 — **D2 is 0603, D3 is 0402, D4 is 0201** | ⚠️ confirm this size mix is intentional before ordering parts |
| 14 | R1–R14 | Resistor, 1kΩ | 0805 | LED current-limiting resistors |
| 1 | SW1 | Slide switch, SPDT | PCM12 | power switch |
| 1 | — | CR2032 coin cell battery | 3V | not on the PCB — needed to power the badge, order separately |

### Tools needed

- TODO (soldering iron + fine tip, solder, tweezers, flux, etc.)

### Steps

1. TODO — solder resistors (R1–R14)
2. TODO — solder LEDs (D1–D14), watch orientation and package size per part above
3. TODO — solder the switch (SW1)
4. TODO — solder the battery holder (BT1)
5. TODO — insert the CR2032 battery, flip the switch, verify all LEDs light up

## Repository Layout

- `svg/` — vector source files (Inkscape)
  - `pcb-only.svg` — final PCB-only artwork
  - `logo2k26_08.08-original.svg` — original full logo artwork
  - `pcb-assets.svg`, `pcb-decomposed.svg` — decomposed/layered PCB artwork elements
- `png/colors/` — rendered color variants (black, blue, green, purple, red, white, yellow)
- `png/swatches/` — small reference color swatches (FR4 board color, grey)
- `balccon-2k26-hardware/` — KiCad project for the physical pin/badge PCB (schematic, board, routed and with silkscreen finished)
  - `pcb-svg/` — SVG layers exported from KiCad (`copper.svg`, `mask-front.svg`, `mask-back.svg`, `silkscreen-front.svg`, `edge-cuts.svg`, `hex.svg`, `log.svg`, `date.svg`)
  - `fabrication/` — Gerber and drill files exported for board fabrication (gitignored; regenerate via KiCad's Plot dialog)
  - `orders/` — `fabrication-YYYY-MM-DD.zip` snapshots of `fabrication/` at the time an order was placed, kept as a record of what was actually sent to the fab
