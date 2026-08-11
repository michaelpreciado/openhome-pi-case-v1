# OpenHome Dev Kit — Raspberry Pi Top Shroud

A cover for the exposed Pi 4 + OpenHome HAT stack that sits on top of the printed
speaker enclosure. Open bottom, drops straight over the stack, rests on the
enclosure's top face. Nothing about the existing enclosure changes.

## Files

| File | What it is |
|---|---|
| `OpenHome_Pi_Lid_PreciadoTech.stl` | Ready to slice, "PRECIADO TECH" debossed on top |
| `OpenHome_Pi_Lid_BLANK.stl` | Same part, no text — add your own in the slicer |
| `openhome_pi_lid.scad` | Parametric source. Change one line to rename it. |

## Size

- Outside: **96.8 × 66.8 × 32.4 mm**
- Interior cavity: 92 × 62 × 30 mm
- Walls 2.4 mm, top 2.4 mm, 3 mm corner radius
- ~26 cm³ of plastic → roughly **30–35 g** at normal wall/infill settings

The enclosure's top face is 100 × 95 mm, so this sits inside that footprint with
a small margin all the way around.

## What's on it

- **Ethernet + 4× USB-A** — one large 54 × 23.5 mm window on the short end
- **USB-C power, 2× micro-HDMI, 3.5 mm jack** — 58 × 19 mm window on the long side
- **microSD** — 16 × 12 mm slot on the opposite short end
- **Wire exit notch** — 15 mm notch at the top of the back long side for the
  speaker/GPIO leads
- **Side grills** — vertical slots on three sides, bottom 5 mm left solid so the
  rim stays stiff
- **Top grill** — six rows of slots either side of the name

(No standoff pass-through holes — the standoffs stay under the lid. If you ever
want them back, set `STANDOFF_HOLES = true` in the .scad.)

The big side window and the top slots give a straight convection path — cool air
in low through the grills, hot air out the top.

## Printing

**Print it upside down — top face flat on the plate.** The STL is already
oriented that way, so just drop it in and slice.

- No supports needed anywhere
- 0.2 mm layers, 3 walls, 15% infill
- The debossed name prints against the build plate, so it comes out crisp

If you want the text in a second color, add a filament change at ~0.6 mm.

## Changing the name

Open `openhome_pi_lid.scad` and edit the first line:

```
NAME_TEXT = "PRECIADO TECH";
```

It auto-shrinks to fit, so longer names still work. `SUB_TEXT` adds a smaller
second line under it. Or just use the blank STL and add text with the slicer's
text tool.

## Before you print — two numbers worth checking

I built this from your approximate 90 × 60 × 27 mm plus margin. Measure your
actual stack from the enclosure's top face:

- `STACK_H` (currently **30**) — top face to the tallest thing on the stack.
  If the lid bottoms out before it seats, raise this.
- `STACK_L` / `STACK_W` (currently **92 / 62**) — the footprint including how far
  the USB and Ethernet jacks hang past the board edge.

Everything else keys off those three numbers, so a re-export takes seconds.
Also worth a dry check: the port windows are deliberately tall so the exact
height of the Pi above the face doesn't have to be exact — but confirm the
USB-C plug clears the bottom edge of its window.
