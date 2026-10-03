# Bose–Einstein Condensation, Interactively

An interactive, single-page web demo of Bose–Einstein condensation: how a gas of identical bosons with a fixed number of atoms abruptly piles into its ground state below a critical temperature, and why the explanation lies in counting arrangements of identical particles.

Created by **Claude Opus 5.5**, based on the lecture notes by **Sang Hoon Lee** (Chapter 7, Quantum Statistics; Section 7.6, Bose–Einstein Condensation). It is a companion to the demos for Sections 7.1 to 7.5 (the grand canonical ensemble, bosons and fermions, degenerate Fermi gases, blackbody radiation, and the Debye theory of solids).

## What's inside

**Bosons whose number is fixed.** Why μ ≠ 0 for atoms, the ground-state energy ε<sub>0</sub> = 3h²/8mL², and why N<sub>0</sub> ≈ k<sub>B</sub>T/(ε<sub>0</sub> − μ) forces μ just below ε<sub>0</sub>.

**Finding the chemical potential.** The density of states g(ε) ∝ √ε, the failed guess μ = 0 that defines the condensation temperature

```
k_B T_c = 0.527 (h²/2πm) (N/V)^(2/3)
```

and the results N<sub>excited</sub> = (T/T<sub>c</sub>)<sup>3/2</sup> N and N<sub>0</sub> = [1 − (T/T<sub>c</sub>)<sup>3/2</sup>] N below T<sub>c</sub>. A three-panel figure, after the one in the lecture, multiplies the density of states by the Bose–Einstein distribution to give the particle distribution at any T/T<sub>c</sub>, with the condensate shown as a separate bar at ε = 0. Above T<sub>c</sub>, μ is found numerically.

**A phase transition.** Charts of N<sub>0</sub>/N, N<sub>excited</sub>/N, and μ/k<sub>B</sub>T<sub>c</sub> against T/T<sub>c</sub> show the kink at T<sub>c</sub>. A further chart takes up the notes' remark that the simple picture is inaccurate just below T<sub>c</sub> for a finite number of atoms (Problem 7.66): it sums exactly over the box states for 100 to 100,000 atoms, solving for μ at each temperature. Condensation sets in above T<sub>c</sub> and the curve sharpens only slowly toward 1 − (T/T<sub>c</sub>)<sup>3/2</sup>; at T = T<sub>c</sub> the condensate fraction is still about 20% for 10,000 atoms.

**How cold is cold enough?** A calculator for T<sub>c</sub> (rubidium-87, sodium-23, or helium-4, at any density) together with a logarithmic energy axis that draws the actual single-particle levels of the box and the hierarchy (ε<sub>0</sub> − μ) ≪ ε<sub>0</sub> ≪ k<sub>B</sub>T<sub>c</sub>, with k<sub>B</sub>T<sub>c</sub>/ε<sub>0</sub> ≈ 0.22 N<sup>2/3</sup>. Rubidium-87 at 10<sup>19</sup> atoms per m³ gives T<sub>c</sub> ≈ 86 nK; liquid helium-4 gives about 3.1 K, near its actual superfluid transition at 2.17 K.

**Why does it happen?** The lecture's argument: for distinguishable particles the Z<sub>1</sub><sup>N</sup> arrangements of excited particles overwhelm the Boltzmann factor e<sup>−N</sup>, but identical bosons have only C(N + Z<sub>1</sub> − 1, N) arrangements, too few when Z<sub>1</sub> ≪ N. A toy model with one ground state and Z<sub>1</sub> excited states is solved exactly for both kinds of particle, showing the full probability distribution of the ground-state population, and a picture after the lecture's Figure 7.36 draws randomly sampled system states. The lecture example (N = 100, Z<sub>1</sub> = 25) gives e<sup>−100</sup> ≈ 4 × 10<sup>−44</sup> against 3 × 10<sup>25</sup> boson arrangements; about 86% of the bosons condense, against 10% of distinguishable particles.

**A truly quantum phenomenon.** Why the conclusion rests on bosons being truly identical.

## Running it

There is nothing to build or install. The whole demo is one self-contained file, `index.html`, with all CSS and JavaScript inline.

Open it locally by double-clicking `index.html`, or serve the folder:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

### Publishing with GitHub Pages

1. Push this repository to GitHub.
2. Go to **Settings → Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**, select your main branch and the `/ (root)` folder, then save.
4. After a minute or so, the demo will be live at `https://<your-username>.github.io/<repository-name>/`.

## Technical notes

- Plain HTML, CSS, and vanilla JavaScript drawn on `<canvas>`. No frameworks, no build step.
- Above T<sub>c</sub>, μ is found by bisection on the Bose–Einstein number integral, evaluated with Simpson's rule.
- The finite-N calculation groups the box states (n<sub>x</sub>² + n<sub>y</sub>² + n<sub>z</sub>², with degeneracies) and solves for μ exactly at each temperature. It runs in the browser on first use: under half a second for 10,000 atoms and about two seconds for 100,000.
- The toy model uses exact binomial probabilities computed with logarithms, so the counts remain accurate far beyond double-precision range.
- Equations are typeset with [MathJax 3](https://www.mathjax.org/) (SVG output, loaded from cdnjs), so they need no extra web fonts.
- The only other external resources are the Newsreader and Instrument Sans fonts from Google Fonts, with system font fallbacks if they fail to load.
- Opening the page requires an internet connection for MathJax; offline, the equations appear as raw TeX.
- Supports light and dark mode via `prefers-color-scheme`, and is responsive down to phone widths.
- Constants used: h = 6.626 × 10<sup>−34</sup> J s, k<sub>B</sub> = 1.381 × 10<sup>−23</sup> J/K, ζ(3/2) = 2.612.

## Caveats

- The T<sub>c</sub> calculator uses the box formula from the lecture. Real atom-trap experiments, such as the rubidium-87 images in the lecture (Wieman, 1996), use harmonic traps, so the calculator gives only an order-of-magnitude estimate for them. The densities in the presets are representative, not taken from the lecture.
- Liquid helium-4 is a strongly interacting liquid, not an ideal gas; the agreement with its superfluid transition is suggestive, not exact.
- The toy model puts all Z<sub>1</sub> excited states at a single energy ε, a simplification of the lecture's argument (E ~ k<sub>B</sub>T).

## Credits

- Demo: Claude Opus 5.5
- Physics content and examples: lecture notes by Sang Hoon Lee
- The lecture follows Daniel V. Schroeder, *An Introduction to Thermal Physics* (Section 7.6 and Problem 7.66), which quotes David J. Griffiths, *Introduction to Quantum Mechanics*.

## License

No license has been chosen yet. Add a `LICENSE` file (for example, MIT or CC BY 4.0) before sharing or reusing this project publicly, and confirm that any use of the lecture material is permitted by its author.
