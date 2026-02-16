---
name: photutils-getting-started
description: This skill should be used when users ask about getting started in photutils; it prioritizes documentation references and then source inspection only for unresolved details.
---

# photutils: Getting Started

## High-Signal Playbook
### Route conditions
- Route to `photutils-build-and-install` for environment setup, dependency failures, wheel/source build issues, or packaging commands.
- Route to `photutils-api-and-scripting` for symbol-level API questions, return-table schema details, and version-specific API deltas.
- Route to `photutils-whats-new` for migration questions across releases.
- Route to `photutils-parallel-hpc` for performance/scaling/HPC scheduler concerns.
- Route to `photutils-advanced-topics` for changelog-wide archaeology, datasets API-only questions, or isophote test-data provenance.

### Triage questions
- What kind of data is this (2D image, units attached, WCS available)?
- Are sources point-like, extended, or both?
- Is the background approximately constant or spatially varying?
- Do you need only detection, or also photometry/centroids/morphology?
- Are blended sources expected, requiring deblending?
- What source scale do you expect (FWHM, minimum connected pixels)?
- Do you need region conversions/deblending features that require optional deps (`regions`, `scikit-image`)?

### Canonical workflow
1. Confirm install/import style and load data (`docs/getting_started/install.rst`, `docs/getting_started/importing.rst`).
2. Align coordinates with Photutils pixel conventions before measurements (`docs/getting_started/pixel_conventions.rst`).
3. Estimate and subtract background using sigma-clipped stats or `Background2D` (`docs/user_guide/background.rst`).
4. Detect sources with `DAOStarFinder` (point-like) or segmentation (`detect_sources`) for general extraction (`docs/user_guide/detection.rst`, `docs/user_guide/segmentation.rst`).
5. Deblend only when overlaps are merged and reuse matching `convolved_data`/`npixels` settings (`docs/user_guide/segmentation.rst`).
6. Run photometry (`aperture_photometry` or segmentation catalogs) on background-subtracted data (`docs/user_guide/aperture.rst`, `docs/user_guide/segmentation.rst`).
7. Validate counts/fluxes/positions, then tune threshold, kernel, and `npixels`.

### Minimal working example
```python
from astropy.convolution import convolve
from photutils.background import Background2D, MedianBackground
from photutils.datasets import make_100gaussians_image
from photutils.segmentation import detect_sources, make_2dgaussian_kernel

data = make_100gaussians_image()
bkg = Background2D(data, (50, 50), filter_size=(3, 3),
                   bkg_estimator=MedianBackground())
data = data - bkg.background
threshold = 1.5 * bkg.background_rms

kernel = make_2dgaussian_kernel(3.0, size=5)
convolved = convolve(data, kernel)
segment_map = detect_sources(convolved, threshold, npixels=10)
print(segment_map.nlabels)
```

### Pitfalls and fixes
- `import photutils; photutils.CircularAperture(...)` fails because tools are no longer exported at top-level: import from subpackages (`docs/getting_started/importing.rst`).
- Importing private/internal modules (e.g., `photutils.aperture.circle`) is unstable: import from public package namespaces (`docs/getting_started/importing.rst`).
- Using FITS/IRAF 1-based coordinates directly causes offsets: convert to Photutils 0-based, pixel-center convention (`docs/getting_started/pixel_conventions.rst`).
- Aperture photometry on non-background-subtracted data biases flux high: subtract background first (`docs/user_guide/aperture.rst`, `docs/user_guide/background.rst`).
- Deblending with different `convolved_data`/`npixels` than detection destabilizes labels: keep them consistent (`docs/user_guide/segmentation.rst`).
- Plain median/std background estimates are source-biased: use sigma clipping and masks (`docs/user_guide/background.rst`).

### Convergence/validation checks
- Re-run background stats after masking and verify mean/median/std stabilize (`docs/user_guide/background.rst`).
- Perturb threshold slightly (for example 1.5-sigma to 2-sigma) and confirm source counts are not wildly unstable.
- Check segmentation overlays for obvious merged/split pathologies.
- Verify output centroids stay inside frame bounds and on-source.
- Confirm aperture sums scale sensibly with radius for bright isolated sources (`docs/user_guide/aperture.rst`).

## Scope
- Handle questions about initial setup, quickstarts, and core concepts.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `docs/index.rst`
- `docs/getting_started/overview.rst`
- `docs/getting_started/index.rst`
- `docs/user_guide/segmentation.rst`
- `docs/user_guide/psf_matching.rst`
- `docs/user_guide/psf.rst`
- `docs/user_guide/profiles.rst`
- `docs/user_guide/background.rst`
- `docs/user_guide/aperture.rst`
- `docs/user_guide/detection.rst`
- `docs/whats_new/1.1.rst`
- `docs/user_guide/morphology.rst`

## Workflow
- Start with the primary references above.
- If details are missing, inspect `references/doc_map.md` for the complete topic document list.
- Use tutorials/examples as executable usage patterns when available.
- Use tests as behavior or regression references when available.
- If ambiguity remains after docs, inspect `references/source_map.md` and start with the ranked source entry points.
- Cite exact documentation file paths in responses.

## Tutorials and examples
- `docs/getting_started`
- `docs/user_guide`

## Test references
- `photutils/tests`
- `photutils/aperture/tests`
- `photutils/background/tests`
- `photutils/centroids/tests`
- `photutils/datasets/tests`
- `photutils/detection/tests`
- `photutils/geometry/tests`
- `photutils/isophote/tests`
- `photutils/morphology/tests`
- `photutils/profiles/tests`
- `photutils/psf/tests`
- `photutils/psf_matching/tests`
- `photutils/segmentation/tests`
- `photutils/utils/tests`

## Optional deeper inspection
- `photutils`

## Source entry points for unresolved issues
- `photutils/segmentation/core.py`
- `photutils/segmentation/utils.py`
- `photutils/detection/core.py`
- `photutils/background/background_2d.py`
- `photutils/background/core.py`
- `photutils/aperture/core.py`
- `photutils/aperture/photometry.py`
- `photutils/psf_matching/fourier.py`
- `photutils/psf_matching/windows.py`
- `photutils/psf/simulation.py`
- `photutils/profiles/core.py`
- `photutils/morphology/core.py`
- `photutils/isophote/model.py`
- `photutils/isophote/geometry.py`
- `photutils/datasets/images.py`
- `photutils/datasets/noise.py`
- `photutils/datasets/load.py`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" photutils`).
