# UI/UX Wireframe & Dashboard Generation Skill

## Purpose
Enforce strict architectural discipline, spatial hierarchy, and visual restraint when generating wireframes, schematics, or tactical dashboard mockups. Prevents compositional drift into photorealism, visual clutter, or repetitive illustrative assets.

---

## Core Rules & Constraints
1. **Medium Enforcement:** Always specify the style as a flat 2D vector schematic, technical UI wireframe, or low-fidelity CAD blueprint. Never allow photorealistic textures, organic debris, or 3D terrain renders in wireframe requests.
2. **Negative Space Priority:** Reserve dedicated margin padding and high-contrast bounding boxes around interactive elements.
3. **Deterministic Spatial Mapping:** Anchor interface elements strictly to screen positions using a 5-zone layout:
   - **Header:** Global states, time, system status, communications.
   - **Left Panel:** Primary operational telemetry, active agents, trees/lists.
   - **Center Viewport:** Primary canvas (tactical map, data graph, primary workspace).
   - **Right Panel:** Auxiliary data, resource meters, secondary metrics.
   - **Footer/Dock:** Action bars, multi-channel feeds, contextual logs.
4. **Numbered Section Anchoring:** Explicitly bind bracketed numeric callouts (`[1]`, `[2]`, `[3]`) directly to designated spatial zones to maintain clear visual documentation.
5. **No Visual Redundancy:** Limit entity markers to single, canonical instances unless multi-instance data points are explicitly quantified.

---

## Structured Prompt Template

```text
As a UI Designer, assmeble a clean, minimalist, high-contrast flat UI/UX wireframe schematic of a [INTERFACE TYPE], designed as a technical blueprint with labeled numeric callouts [1] through [N].

Style: Flat 2D vector UI, technical schematic, clean line work on dark slate background, no 3D textures, no organic visual clutter.

Spatial Breakdown:
- View Space: [TotalWidth] x [TotalHeight]
- [1] TOP PANEL: Size: [Width] x [Height] [Global controls, system telemetry, status bars]
- [2] LEFT SIDEBAR: Size: [Width] x [Height] [Operational lists, active unit statuses, telemetry metrics]
- [3] CENTER VIEWPORT: Size: [Width] x [Height] [Primary canvas/map, bounding zones, isolated key targets]
- [4] RIGHT SIDEBAR: Size: [Width] x [Height] [Resource monitors, logistics meters, secondary analytical data]
- [5] BOTTOM DOCK: Size: [Width] x [Height] [Side-by-side equal-width feeds/viewports labeled sequentially]

Visual Tone: High scannability, uniform borders, precise data density, presentation-ready.

Ask for details on the controls, telemetry, contents of each numbered section if not provided with this prompt. 

Context: [Context of what the dashboard is for]