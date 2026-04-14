# Sommerfeld Factor Data

Ancillary data for the paper:

> **Gravitational Sommerfeld Factor for Scalar Perturbations with Tidal Effects**

This repository provides high-precision perturbative data for the gravitational Sommerfeld enhancement factor $\mathcal{S}_\ell$ for scalar scattering off a Schwarzschild black hole, computed to $\mathcal{O}(G^{10})$ for partial waves $\ell = 0, 1, 2$.

## Files

| File | Partial wave | Description |
|------|:---:|-------------|
| `l0Data.m` | $\ell = 0$ | Sommerfeld factor data |
| `l1Data.m` | $\ell = 1$ | Sommerfeld factor data |
| `l2Data.m` | $\ell = 2$ | Sommerfeld factor data |

## Data Format

Each file is a Mathematica `Association` that can be loaded with

```mathematica
data = Get["l1Data.m"];
```

The keys are:

| Key | Description |
|-----|-------------|
| `"|S|"` | Magnitude $\|\mathcal{S}_\ell\|$ as a list of coefficients in $x = G M \omega$, expanded in the paper variables $L = \log(4\omega^2/\bar\mu^2)$ |
| `"Arg[S]"` | Phase $\arg\mathcal{S}_\ell$ (same expansion) |
| `"phaseShift"` | Scattering phase shift $\delta_\ell$ (same expansion); equals $\arg\mathcal{S}_\ell$ when the tidal response is conservative |
| `"|Srem|"` | Resummation remainder $\|\mathcal{S}_{\rm rem}\|$ after factoring out $\|\mathcal{S}_{\rm IR}\|\,\|\mathcal{S}_{\rm run}\|$ |
| `"\[Gamma]"` | Anomalous dimension matrix $\gamma$ for the radiative multipole / tidal system |

Each entry is a list of coefficients `{c0, c1, c2, ...}` where `c_k` is the coefficient of $x^k$ (i.e., $G^k$ after the substitution $G \to x/\omega$).

## Conventions

- $x = G M \omega$ with $M = 1$.
- $L = \log(4\omega^2/\bar\mu^2)$ where $\bar\mu^2 = 4\pi\, e^{-\gamma_E}\, \mu^2$ (MS-bar scheme).
- $L_{\rm IR} = \log(4\omega^2/\mu_{\rm IR}^2)$ (raw IR scale, not MS-bar).
- Wilson coefficients of the tidal response $F_\ell(\omega) = G^{2\ell+1}\sum_n c_{\ell,n}\,(i G\omega)^n$ are denoted `c[l, n]` in the data files.

## Usage Example

```mathematica
data = Get["l1Data.m"];

(* Magnitude of the Sommerfeld factor at O(x^2) for l=1 *)
data["|S|"][[3]]
(* Output: 413/50 - (19 L)/15 + Pi^2/6 *)

(* Phase shift at O(x^1) for l=1 *)
data["phaseShift"][[2]]
(* Output: -3 + 2 EulerGamma + LIR *)
```

## Citation

If you use this data, please cite the accompanying paper.

## License

This data is released under the [MIT License](https://opensource.org/licenses/MIT).
