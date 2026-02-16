---
name: photutils-api-and-scripting
description: This skill should be used when users ask about api and scripting in photutils; it prioritizes documentation references and then source inspection only for unresolved details.
---

# photutils: API and Scripting

## High-Signal Playbook
### Route conditions
- Route to `photutils-build-and-install` for missing dependencies, environment bootstrap, or packaging commands.
- Route to `photutils-getting-started` for first-pass workflow design (background -> detection -> photometry).
- Route to `photutils-whats-new` for upgrade/migration diffs across versions.
- Route to `photutils-developer-guide` for release process and contribution workflow.

### Triage questions
- Which exact symbol(s) are needed (class/function/method)?
- Which Photutils version is the target runtime?
- Which subpackage is in scope (`aperture`, `segmentation`, `psf`, `psf_matching`, etc.)?
- Are inputs plain arrays or quantity/unit-bearing arrays?
- Is output schema compatibility required (table columns/flags/units)?
- Is this a behavior question needing source inspection versus documented API lookup?

### Canonical workflow
1. Identify the subpackage from `docs/reference/index.rst` and open its API page.
2. Confirm the import path from subpackage namespace (not package top-level).
3. Check release notes for API breaks/deprecations before scripting fixes (`docs/whats_new/1.6.rst`, `docs/whats_new/1.8.rst`, `docs/whats_new/2.0.rst`, `docs/whats_new/2.1.rst`).
4. Build a minimal script with only required symbols and synthetic data.
5. If docs are insufficient, inspect ranked source entry points in `references/source_map.md`.
6. Validate outputs (shape, units, table columns, flag semantics).

### Minimal working example
```python
import numpy as np
from photutils.psf import CircularGaussianSigmaPRF
from photutils.psf_matching import make_kernel, make_wiener_kernel

yy, xx = np.mgrid[0:51, 0:51]
src = CircularGaussianSigmaPRF(flux=1, x_0=25, y_0=25, sigma=3)(xx, yy)
tgt = CircularGaussianSigmaPRF(flux=1, x_0=25, y_0=25, sigma=5)(xx, yy)

kernel = make_kernel(src, tgt, otf_threshold=1e-4)
wkernel = make_wiener_kernel(src, tgt, penalty='laplacian')
print(kernel.shape, float(kernel.sum()), float(wkernel.sum()))
```

### Pitfalls and fixes
- Importing public tools from `photutils` top-level no longer works: import from subpackages (`docs/whats_new/2.0.rst`, `docs/getting_started/importing.rst`).
- PSF matching is not imported from `photutils.psf`: use `photutils.psf_matching` (and compatibility namespace `photutils.psf.matching`) per current docs and release notes (`docs/whats_new/2.0.rst`, `docs/user_guide/psf_matching.rst`).
- `RadialProfile`/`CurveOfGrowth` bin API changed and old constructor style breaks: pass explicit radial-bin edges (`docs/whats_new/1.8.rst`, `docs/user_guide/profiles.rst`).
- Star-finder threshold now needs compatible units when data carry units (`docs/whats_new/1.13.rst`).
- `DAOStarFinder`/`IRAFStarFinder` interval-end inclusivity changed and can alter counts at boundaries (`docs/whats_new/2.1.rst`).
- Release-note examples are frozen to historical API state: validate against current user/API docs before final fixes (`docs/release_notes/index.rst`).

### Convergence/validation checks
- Verify each imported symbol resolves from its documented subpackage page.
- For PSF matching, ensure kernel sums near 1 and inspect warnings for off-center PSFs (`docs/user_guide/psf_matching.rst`, `docs/whats_new/3.0.rst`).
- For detection workflows, verify threshold units match data units (`docs/whats_new/1.13.rst`).
- Compare output table columns and units against release-note changes for the target version.
- Re-run a minimal synthetic script after each migration edit.

## Scope
- Handle questions about language bindings, APIs, and programmatic interfaces.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `docs/reference/index.rst`
- `docs/whats_new/1.6.rst`
- `docs/development/releasing.rst`
- `docs/whats_new/1.8.rst`
- `docs/reference/utils_api.rst`
- `docs/reference/segmentation_api.rst`
- `docs/reference/psf_matching_api.rst`
- `docs/reference/psf_api.rst`
- `docs/reference/profiles_api.rst`
- `docs/reference/morphology_api.rst`
- `docs/reference/isophote_api.rst`
- `docs/reference/detection_api.rst`

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
- `photutils/psf_matching/fourier.py`
- `photutils/psf_matching/windows.py`
- `photutils/psf_matching/utils.py`
- `photutils/psf/matching/__init__.py`
- `photutils/segmentation/core.py`
- `photutils/segmentation/catalog.py`
- `photutils/detection/core.py`
- `photutils/psf/photometry.py`
- `photutils/psf/functional_models.py`
- `photutils/psf/gridded_models.py`
- `photutils/profiles/core.py`
- `photutils/morphology/core.py`
- `photutils/isophote/model.py`
- `photutils/centroids/core.py`
- `photutils/background/background_2d.py`
- `photutils/aperture/photometry.py`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" photutils`).
