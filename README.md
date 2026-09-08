# Phosphene

A music visualizer for altered states. One HTML file, WebGL2 and Web Audio, no build step
and no dependencies. Open `index.html` in Chrome or Safari, or use the link above.

## What it does

**Key is colour.** A chroma analysis finds the song's key and maps it onto the circle of
fifths. C is red, G orange, D yellow, A green, E cyan, B blue, F♯ violet. A key change turns
the whole field over slowly.

**It listens deep.** Two FFTs run at once: an 8192-point window for key and a 256-band log
spectrum, a 1024-point window for transients. Both the spectrum and the raw waveform reach
the shader as a texture. Each ring of the field is a frequency band, low in the centre. The
waveform traces the mirror edges. A beat tracker locks the pulse by autocorrelation and
flips the spin every bar. Build, drop and breakdown are detected from sixteen seconds of
energy history. Kick, snare and hats drive separate signals. Spectral flatness makes tonal
passages flow and noisy ones fracture. Stereo width pulls the two halves apart.

## Modes

Seven presets, keys `1`–`7`. Each sets mirror count, palette, trail length, melt, tunnel
pull and detail.

| mode | character |
|---|---|
| Sober | A fixation dot and a constant spiral. Stare for a minute, then look at a wall: it breathes. A real motion aftereffect, for people who took nothing. |
| Cannabis | Warm and soft, bass-led, short trails. |
| Psilocybin | Organic. Everything melts and breathes. Earth colour under the key. |
| LSD | Geometry. Saturated, long tracers, fine lace that never stops turning. |
| DMT | Maximum mirrors, folds inside folds, fast jewel colour. |
| MDMA | Rose and gold, glowing, nothing sharp. |
| Ketamine | Slow, deep, grey-blue. The field falls away from you. |

## Shape and deformers

The row under the modes folds the whole field onto a **circle, triangle, square, pentagon,
hexagon, star or flower**, changing the geometry everything else is built on.

**Twist** rotates the field more the further out you go. **Bulge** swells the centre, or
pinches it left of zero. **Ripple** runs concentric waves outward. All three rest at zero in
the middle of their travel and take the music with them.

**A 3D file.** Press **Load 3D** and choose an `.obj` or `.stl`. The mesh is drawn off screen
every frame and the field is refracted through its surface normals and depth, so the
kaleidoscope behaves as though lit through a glass version of your object. **Knot** is built
in, to see the effect without a file. **Scroll to dolly**: the camera physically moves toward
the object, so perspective opens up as you approach. It is a dolly, not a zoom, and the focal
length never changes.

## Dials

`depth` trail length · `drift` rotation · `react` how hard the music moves the image ·
`bass` how far the low end bends the deep background · `spiral` vortex speed · `zoom` the
endless log-polar fall · `twist` `bulge` `ripple` the deformers · `model` how hard the 3D
object bites.

## Hands

The field leans toward the cursor. Click for a ripple. Hold for a gravity well. Drag to spin
or dive. Ctrl-scroll to add mirrors. Double-click for fullscreen.

## Anchor

Press **Anchor**, or `A`, at any time. Everything slows to a warm, steady eight-fold mandala
with a breath pacer at 5.5 breaths a minute, the real clock, and one grounding line. It damps
the mouse and the deformers too, so a hand on the trackpad cannot disturb it. Press again to
return.

## Safety

Nothing here strobes. Every audio value passes an envelope follower and a feedback buffer, so
brightness changes are smoothed rather than switched. If you are photosensitive, keep `depth`
low and the room lit.

## Feeding it sound

- **Drop a song** anywhere on the page, or use **Open a song**.
- **Microphone** hears the room. On a Mac, route your player through a virtual device
  (BlackHole, Loopback) and pick it here to visualise anything playing on the machine.
- **A browser tab** captures the audio of one Chrome tab. Tick "Share tab audio".
- **MIDI** takes a drum kit or controller directly, so every hit is exact.

Microphone, tab audio and MIDI need a secure origin and a real click.

## Performance

Renders at full device pixels. A frame-time governor lowers resolution only when the refresh
budget is missed and raises it back when it is met, carrying the trails across the change so
nothing flashes. The help panel has a lock for full resolution.

## Debugging

`window.PHOSPHENE.state` · `.loadArrayBuffer(ab)` · `.setMode(name)` · `.setShape(key)` ·
`.readModelMask()` prints the loaded mesh's coverage as an ASCII grid.

Built with Claude Code.
