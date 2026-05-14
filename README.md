# Raup's Morphospace — The Shells That Were Never Born

**Week 8 Vibe Code**  
HIST 17514 / HIPS 18504 / SOC 20526: Computation, Culture & Society  
University of Chicago · Spring 2026

---

## What is this?

An interactive implementation of the geometric shell model developed by paleontologist **David M. Raup** in his 1966 paper:

> Raup, D.M. "Geometric Analysis of Shell Coiling: General Problems."  
> *Journal of Paleontology* 40(5): 1178–1190.

Raup showed that nearly all coiled invertebrate shells can be described using three geometric parameters, which together define a **morphospace** — a complete map of every shell that *could* theoretically exist. The striking finding: **actual organisms occupy only a tiny fraction of this space.** The rest is geometrically valid but biologically empty — a void of shells the biosphere never made.

---

## Parameters

| Symbol | Name | What it controls |
|--------|------|-----------------|
| **W** | Whorl Expansion Rate | How much each coil grows relative to the last. Low W = tight nautilus; high W = rapidly opening spiral. Math: r(θ) = W^(θ/2π) |
| **D** | Umbilical Ratio | Inner edge of the tube as a fraction of the outer radius. D≈0: whorls touch the axis; D≈1: thin hollow tube. |
| **T** | Translation Rate | Rate of movement along the coiling axis. T=0: flat ammonite disc; T→1: tall gastropod spire (displayed as foreshortening). |

The shell is drawn as a cross-sectional polygon: the outer logarithmic spiral traced forward from θ=0 to θ=4×2π (4 whorls), then the inner spiral (scaled by D) traced backward — forming a closed region that represents the shell material.

---

## How to use

1. **Drag the sliders** (W, D, T) — the shell redraws live.
2. **Preset buttons** jump to known organism geometries: ammonite, gastropod, bivalve, brachiopod.
3. **"Enter the Void"** places you in an unoccupied region of morphospace. Each click picks a different void location.
4. The **organism badge** identifies which taxonomic group (if any) matches your current parameters.
5. The **morphospace minimap** (bottom left) shows W vs D, with colored ellipses for organism zones and a gold dot for your current position.

---

## Deploying on GitHub Pages

1. **Create a new GitHub repository** (e.g., `raup-morphospace`).
2. **Upload `index.html`** to the repository root (or paste the code directly into the GitHub web editor).
3. Go to **Settings → Pages**.
4. Under **Source**, set Branch to `main` and folder to `/ (root)`.
5. Click **Save**. GitHub will provision a URL like:  
   `https://yourusername.github.io/raup-morphospace/`
6. Share that URL as your **live artifact link**.

*No build tools, no npm, no server required — it's a single self-contained HTML file.*

---

## Running locally

```bash
# Option 1: Just open the file
open index.html   # macOS
start index.html  # Windows

# Option 2: Serve with Python (avoids any CORS issues)
python3 -m http.server 8080
# Then open http://localhost:8080 in your browser
```

---

## Connection to Week 8 readings

| Reading | Connection |
|---------|-----------|
| **Raup (1966)** | Directly implements his three-parameter shell geometry model. |
| **Wigner (1959)** | The same logarithmic spiral mathematics that describes galaxy arms and population curves describes shell growth — reasonably effective or mysteriously so? |
| **Edwards (2010)** | The model doesn't just *describe* nature; it defines what counts as *possible*, structuring what questions we can even ask. |
| **Kozlowski & Evans (2025)** | Like AI stand-ins for human subjects, the shell model is both powerful and bounded — it generates more than it can validate, and its "void" is as meaningful as its occupied regions. |

---

## Reflection hook

> *"This artifact shows that the model generates more than nature ever built — which makes evolution's choices visible as choices."*

---

## Technical notes

- Single HTML file, ~350 lines including CSS and JavaScript.
- Uses **HTML5 Canvas** for all rendering — no external graphics libraries.
- **IM Fell English** and **Crimson Pro** fonts loaded from Google Fonts (requires internet; falls back to Georgia).
- Shell drawing: closed polygon path, radial gradient fill, suture lines at whorl boundaries, gold aperture dot.
- Morphospace map: organism zones drawn as scaled ellipses based on Raup's text-figure 4.
- "Void" presets are hand-curated points outside all four organism zones, with small random jitter per click.

---

*Built for CCS 2026. Single-file HTML/CSS/JS. No frameworks.*
