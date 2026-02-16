---
name: photutils-inputs-and-modeling
description: This skill should be used when users ask about inputs and modeling in photutils; it prioritizes documentation references and then source inspection only for unresolved details.
---

# photutils: Inputs and Modeling

## High-Signal Playbook
### Route conditions
- Route to `photutils-getting-started` for end-to-end beginner workflows.
- Route to `photutils-api-and-scripting` for symbol-level API behavior and method signatures.
- Route to `photutils-whats-new` for release migration and deprecation handling.
- Route to `photutils-build-and-install` for dependency/toolchain blockers.

### Triage questions
- Is the request about aperture overlap geometry, PSF model fitting, or segmentation model controls?
- Are inputs unit-bearing arrays or plain NumPy arrays?
- Is exact overlap required, or is approximate/subsampled overlap acceptable?
- Are you using `SourceFinder`/deblending and needing separate detection vs deblend `npixels`?
- Are you upgrading old imports or deprecated modeling classes?
- Are memory/performance constraints important for gridded PSF models?

### Canonical workflow
1. Select the modeling path: high-level aperture tools, segmentation controls, or PSF-model fitting (`docs/reference/geometry_api.rst`, `docs/whats_new/1.9.rst`, `docs/whats_new/1.11.rst`).
2. Normalize import paths to subpackage namespaces (`docs/whats_new/2.0.rst`).
3. If geometry overlap detail is needed, inspect low-level overlap functions; otherwise stay on `photutils.aperture` (`docs/user_guide/geometry.rst`).
4. Configure source-detection/deblend controls (`npixels`, `nlevels`, `contrast`) with explicit intent (`docs/whats_new/1.11.rst`).
5. For PSF photometry, choose model/fitter defaults and bounds appropriate to crowding (`docs/whats_new/1.9.rst`, `docs/whats_new/2.0.rst`).
6. Validate behavior with a synthetic mini-case before scaling.

### Minimal working example
```python
from photutils.geometry import circular_overlap_grid

grid = circular_overlap_grid(-1.0, 1.0, -1.0, 1.0,
                             200, 200, 0.4, 1, 5)
print(grid.shape, float(grid.max()))
```

```python
from photutils.segmentation import SourceFinder

finder = SourceFinder(npixels=(10, 5), nlevels=32, contrast=0.001,
                      progress_bar=False)
```

### Pitfalls and fixes
- Legacy import style (`from photutils import ...`) fails in modern versions: import from explicit subpackages (`docs/whats_new/2.0.rst`).
- Treating low-level geometry as public user API increases fragility: prefer `photutils.aperture` for production workflows (`docs/user_guide/geometry.rst`).
- `Background2D` behavior changed (caching removal and deprecations like `edge_method='crop'`): align configs to current defaults (`docs/whats_new/2.0.rst`).
- `SourceFinder` can use tuple `npixels` for detect/deblend stages; single value may over/under-split in mixed fields (`docs/whats_new/1.11.rst`).
- `DAOStarFinder`/`IRAFStarFinder` gained `min_separation`, which changes blend handling if left implicit (`docs/whats_new/1.10.rst`).
- Gridded PSF memory/performance changed over releases; benchmark after upgrade (`docs/whats_new/1.10.rst`, `docs/whats_new/1.11.rst`).

### Convergence/validation checks
- For overlap grids, verify fully enclosed pixels reach near-1.0 overlap (`photutils/geometry/tests/test_circular_overlap_grid.py`).
- Run parameter sweeps for `npixels`/`nlevels` and ensure source counts are stable in expected ranges.
- Check PSF-fitting outputs for non-finite parameters/flags before downstream use.
- Profile memory with gridded PSF workflows on representative source counts.
- Confirm no deprecation warnings remain in migration targets.

## Scope
- Handle questions about inputs, system setup, models, and physical parameterization.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `docs/whats_new/2.0.rst`
- `docs/whats_new/1.9.rst`
- `docs/whats_new/1.11.rst`
- `docs/whats_new/1.10.rst`
- `docs/reference/geometry_api.rst`

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
- `photutils/geometry/__init__.py`
- `photutils/geometry/core.pyx`
- `photutils/geometry/core.pxd`
- `photutils/geometry/circular_overlap.pyx`
- `photutils/geometry/elliptical_overlap.pyx`
- `photutils/geometry/rectangular_overlap.pyx`
- `photutils/geometry/tests/test_circular_overlap_grid.py`
- `photutils/geometry/tests/test_elliptical_overlap_grid.py`
- `photutils/geometry/tests/test_rectangular_overlap_grid.py`
- `photutils/psf/model_helpers.py`
- `photutils/psf/model_io.py`
- `photutils/psf/model_plotting.py`
- `photutils/psf/gridded_models.py`
- `photutils/psf/image_models.py`
- `photutils/psf/functional_models.py`
- `photutils/isophote/model.py`
- `photutils/isophote/ellipse_model.pyx`
- `photutils/datasets/model_params.py`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" photutils`).
