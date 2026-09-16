# balccon-2k26-badge

Design assets for the BalCCon 2k26 PCB-style pin/badge.


### The board

The front carries the silkscreen artwork only — no components. Everything
gets soldered to the back.

| Front | Back  |
| --- | --- |
| ![Front of the PCB](photos/front-PCB-render.png) | ![Back of the PCB](photos/back-PCB-render.png) |


### Electronics components

| Qty | Ref | Part | Package / Value |
| --- | --- | --- | --- |
| 1 | BT1 | Coin cell holder | CR2032 |
| 11 | D1,D5-D14 | LED | 0805| 
| 1 | D2| LED | 0603| 
| 1 | D3| LED | 0402| 
| 1 | D4| LED | 0201| 
| 14 | R1–R14 | 1kΩ | 0805 |
| 1 | SW1 | Slide switch, SPDT | PCM12 |


### Schematic

![LED + resistor branch](photos/simple-schematic-led-resistor.png)

Each of the 14 LEDs is wired the same way: **VCC → resistor → LED → GND**,
one branch per LED, all 14 branches in parallel. A couple of basics explain
why it's built this way:

- **Voltage** is the electrical "push" between two points — here, the ~3V
  the CR2032 battery provides between VCC and GND. **Current** is the actual
  flow of electrons through the circuit, driven by that voltage.
- An LED only conducts one way, and left unchecked it will pull more current
  than it can handle and burn out. The resistor limits the current to a safe
  level (1kΩ per branch) so the LED just lights up instead.
- Each LED has its own resistor, so the 14 branches are independent — one
  LED (or a joint that isn't soldered yet) doesn't affect the others.

BT1 (the coin cell) is what supplies VCC to all of this, and SW1 sits
between the battery and the rest of the board — flipping it is what turns
the whole badge on and off.

## Assembly Instructions

General rule: solder the smallest / lowest-profile components first, so
taller parts don't block your iron from reaching the rest.

### Step 1 — Resistors (R1–R14)

TODO — solder all 14 1kΩ 0805 resistors.

### Step 2 — LEDs (D1–D14): the solder challenge

TODO — solder the LEDs in order, D1 down to D4 last — packages shrink from
0805 to 0603 to 0402 to 0201 as you go.

### Step 3 — Switch (SW1)

TODO — solder the slide switch.

### Step 4 — Battery holder (BT1)

TODO — solder the coin cell holder last; it's the tallest part on the board.

### Step 5 — Power on

TODO — insert the CR2032 battery, flip the switch, and verify all 14 LEDs
light up.

## Repository Layout

- `photos/` — renders/photos of the board and badge, used in the assembly instructions above
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
