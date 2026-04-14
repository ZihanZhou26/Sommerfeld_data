# Ancillary Data

Ancillary data for the paper:

> **Gravitational Sommerfeld Effects: Formalism, Renormalization, and Perturbation to $\mathcal{O}(G^{10})$**
>
> Chih-Hao Chang, Chia-Hsien Shen, Zihan Zhou

## Overview

In the effective field theory (EFT) description of compact binary inspirals, the radiated gravitational waveform receives universal corrections from the gravitational background — the so-called "tail" effects — that resum into the Sommerfeld factor. This repository provides the perturbative data for the gravitational Sommerfeld enhancement factor for scalar perturbations of a Schwarzschild black hole, computed to $\mathcal{O}(G^{10})$ for partial waves $\ell = 0, 1, 2$, including the tidal response kept symbolic in the Wilson coefficients $c_{\ell,n}$.

## Files

| File | Partial wave |
|------|:---:|
| `l0Data.m` | $\ell = 0$ |
| `l1Data.m` | $\ell = 1$ |
| `l2Data.m` | $\ell = 2$ |

## Data Format

Each file is a Mathematica `Association` loadable via

```mathematica
data = Get["l1Data.m"];
```

The keys are:

| Key | Symbol | Description |
|-----|--------|-------------|
| `"\|S\|"` | $\|\mathcal{S}_\ell\|$ | Magnitude of the Sommerfeld factor |
| `"Arg[S]"` | $\mathrm{Arg}\,\mathcal{S}_\ell$ | Phase of the Sommerfeld factor |
| `"phaseShift"` | $\delta_\ell$ | Scattering phase shift; equals $\mathrm{Arg}\,\mathcal{S}_\ell$ when the tidal response is conservative |
| `"\|Srem\|"` | $\|\mathcal{S}_{\mathrm{rem}}\|$ | Resummation remainder after factoring out $\|\mathcal{S}_{\mathrm{IR}}\|\,\|\mathcal{S}_{\mathrm{run}}\|$ |
| `"\[Gamma]"` | $\gamma$ | Anomalous dimension matrix for the radiative multipole / tidal system |

Each entry (except `"\[Gamma]"`) is a list `{c0, c1, c2, ...}` where `ck` is the coefficient of $x^k$ in the expansion parameter $x = G M \omega$.

The tidal response function is parameterized as
$$\bar{F}_{\ell,0}(\omega) = (GM)^{2\ell+1} \sum_{n=0}^{\infty} c_{\ell,n}(\mu_0)\,(i\,GM\omega)^n$$
and the Wilson coefficients $c_{\ell,n}$ appear symbolically as `c[l, n]` in the data.

## Conventions

| Symbol | Definition |
|--------|------------|
| $x$ | $GM\omega$ with $M = 1$ |
| $L$ | $\log(4\omega^2/\bar{\mu}^2)$, where $\bar{\mu}^2 = 4\pi\, e^{-\gamma_E}\,\mu_0^2$ (MS-bar) |
| $L_{\mathrm{IR}}$ | $\log(4\omega^2/\bar{\mu}_{\mathrm{IR}}^2)$, where $\bar{\mu}_{\mathrm{IR}}^2 = 4\pi\, e^{\gamma_E - 1}\,\mu_{\mathrm{IR}}^2$ |

These follow the conventions in the Supplemental Material of the paper (Sec. VII).

## Usage Example

```mathematica
data = Get["l1Data.m"];

(* Magnitude of the Sommerfeld factor at O(x^2) for l=1 *)
data["|S|"][[3]]
(* 413/50 - (19 L)/15 + Pi^2/6 *)

(* Phase shift at O(x^1) for l=1 *)
data["phaseShift"][[2]]
(* -3 + 2 EulerGamma + LIR *)
```

## Citation

If you use this data, please cite the accompanying paper.

## License

This data is released under the [MIT License](https://opensource.org/licenses/MIT).
