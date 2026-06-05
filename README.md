# Cosmological Collider Bispectra

Interactive explorer for massive scalar exchange bispectrum shapes from cosmological collider physics.
A toggle at the top switches the whole page between two regimes:

- **Weak mixing** — perturbative (small-ρ) exchange; self-interaction + weak-mixing contributions.
- **General mixing** — non-perturbative ρ (the general collider); shapes tabulated on a 3D
  (log₁₀ρ, m, log₁₀c_rel) grid, decomposed into single / double / triple exchange.

**[Launch the app](https://oliverphilcox.github.io/cosmological-collider-bispectra/)**

## Parameters

**Weak mixing**

| Parameter | Description |
|-----------|-------------|
| log₁₀ cπ | Goldstone (inflaton) sound speed |
| c̃₃ | π̇³ self-interaction coupling |
| m/H | Mass of the exchanged scalar (in units of H) |
| log₁₀ cσ | Scalar field sound speed |
| ρ | π̇σ mixing coupling |
| Δρ | π̇²σ weak-mixing coupling (Δρ=0 is boost-invariant) |

**General mixing** (adds the non-perturbative ρ axis and the higher σ vertices)

| Parameter | Description |
|-----------|-------------|
| m/H | Mass of the exchanged scalar |
| log₁₀ cπ, log₁₀ cσ | Goldstone / scalar sound speeds |
| log₁₀ ρ | Mixing strength (non-perturbative) |
| Δρ | π̇²σ exchange coupling |
| c̃₃ | π̇³ self-interaction coupling |
| α | π̇σ² exchange coupling |
| μ | σ³ exchange coupling |

The mass parameter ν = √(m²/H² − 9/4) used for the shape grid is computed internally.

## Features

- 1D squeezed-limit plot: S(x,1)/x showing the per-order contributions and total
- 2D shape map: full bispectrum shape S(x,y) with RdBu colorscale
- Weak ↔ general toggle, linear/log y-axis, divide-by-x
- All computation runs client-side in JavaScript

## Local development

Serve locally with any static file server:
```bash
python -m http.server 8000
```
Then open http://localhost:8000.

## Data

- `shape_data.bin` (13 MB) — pre-computed bootstrap exchange shapes for the **weak** model + k-space binning.
- `strong_shape_data.bin` (6.3 MB) + `strong_factor_coefs.json` — merged, renormalized cosmoflow shapes
  (7 operators on the 3D grid) and the Chebyshev factor coefficients for the **general** model.

The general-mixing shapes reproduce `Strong-Exchange-Clean.ipynb` (`signal()`) up to the data whitening.
