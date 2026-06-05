# General Collider (Strong Mixing) — Bispectrum Shape Explorer (prototype)

Analog of the weak-mixing site (`cosmological-collider-bispectra`), but for the **general
collider with strong mixing**: ρ is non-perturbative, so shapes are tabulated on a 3D
`(log₁₀ρ, μ, log₁₀c_rel)` grid over 7 operators.

Shapes reproduce `scripts/Strong-Exchange-Clean.ipynb` (`signal()`, cell 17) **up to the data
whitening** — same `factors()` interpolation-conditioning (cell 14) and same `get_f_pi`
normalization.

## Files
- `index.html` — the explorer (Plotly + MathJax from CDN; needs internet in-browser).
- `strong_shape_data.bin` — 6.5 MB. Conditioned shape cubes `cond = shapes_full / factors(grid)`
  (float32) + `cond_ratio` for `get_f_pi`.
- `strong_factor_coefs.json` — 45 kB. Chebyshev factor coefficients (norm ranges, degs,
  per-operator + ratio c1/c2/e1/e2) so the browser reproduces `factors()`/`factor_ratio()`.
- `prepare_web_data_strong.py` — builds the two data files from
  `all_shapes_clean_production_full.npz` + `strong_factor_coefs.npz`.
- `verify_pipeline.py` — validates packed path vs source npz (node-exact, 6e-8) + finite signal.
- `_node_test.js` — runs the *actual* index.html JS in Node and matches the Python pipeline.

## View locally
```bash
cd scripts/strong_collider_explorer
python -m http.server 8000      # then open http://localhost:8000  (use SSH port-forward if remote)
```

## Sliders
- **Background**: μ (−1.49…5, <0 = complementary), log₁₀c_π, log₁₀c_σ, log₁₀ρ (−4…3).
- **Operator couplings** (Δρ², c̃₃, ρ²α, ρ³μ_σ): shown in **units of their natural
  perturbativity bound** (`get_bounds`, type='general'), so ±1 ≈ an O(1) physical coupling.

## Known limitations (prototype)
- Grid is coarse in c_rel (7 pts, 0.01–10) and μ (15 pts); interpolation can look chunky.
- Slider ranges keep c_rel ∈ [0.01, 10] (the tabulated range); outside is not modelled.
- Not pushed anywhere; local prototype only.
