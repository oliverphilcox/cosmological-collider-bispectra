# Cosmological Collider Bispectra

Interactive explorer for weakly-mixed massive scalar exchange bispectrum shapes from cosmological collider physics.

**[Launch the app](https://oliverphilcox.github.io/cosmological-collider-bispectra/)**

## Parameters

| Parameter | Description |
|-----------|-------------|
| log₁₀ cπ | Inflaton sound speed |
| c̃₃(cπ⁻²−1) | Cubic self-interaction coupling |
| μ | Mass of the exchanged scalar (in units of H) |
| log₁₀ cσ | Scalar field sound speed |
| ρ | π̇σ mixing coupling |
| ρ̃ | π̇²σ interaction coupling |

## Features

- 1D squeezed-limit plot: S(x,1)/x showing self-interaction, weak mixing, and total contributions
- 2D shape map: full bispectrum shape S(x,y) with RdBu colorscale
- Toggle between linear and logarithmic y-axis
- All computation runs client-side in JavaScript

## Local development

Serve locally with any static file server:
```bash
python -m http.server 8000
```
Then open http://localhost:8000.

## Data

The binary data file `shape_data.bin` (6.7 MB) contains pre-computed bootstrap exchange shapes and k-space binning.
