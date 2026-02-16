---
name: photutils-build-and-install
description: This skill should be used when users ask about build and install in photutils; it prioritizes documentation references and then source inspection only for unresolved details.
---

# photutils: Build and Install

## High-Signal Playbook
### Route conditions
- Route to `photutils-getting-started` for first analysis workflows after installation.
- Route to `photutils-api-and-scripting` for symbol-level API usage after environment is working.
- Route to `photutils-developer-guide` for contributor/release governance and milestone flow.
- Route to `photutils-whats-new` for migration checks when upgrading across versions.

### Triage questions
- Which Python and package manager are being used (`pip`, `conda`, source checkout)?
- Is this a released install, pre-release wheel, or editable development install?
- Are optional features needed (`regions`, `scikit-image`, `gwcs`, `tqdm`, etc.)?
- Is install falling back to source build (no wheel available)?
- Are tests being used as installation validation?
- Is the task maintainer release packaging versus user installation?

### Canonical workflow
1. Verify interpreter/dependency floors (Python 3.11+, NumPy 2.0+, SciPy 1.13+, Astropy 6.1.4+) from `docs/getting_started/install.rst`.
2. Install with `pip`/`conda`; include extras when feature-complete environments are needed (`docs/getting_started/install.rst`).
3. For development installs, clone and run `python -m pip install ".[all]"` (`docs/getting_started/install.rst`).
4. If building from source, ensure compiler/toolchain prerequisites are present (`docs/getting_started/install.rst`).
5. Validate install with `pytest --pyargs photutils` (`docs/getting_started/install.rst`, `docs/whats_new/1.13.rst`).
6. For release packaging, run tox checks, build sdist, and twine validation (`docs/development/releasing.rst`).

### Minimal working example
```bash
python -m pip install "photutils[all]"
pytest --pyargs photutils
```

```bash
git clone https://github.com/astropy/photutils.git
cd photutils
python -m pip install ".[all]"
pytest --pyargs photutils
```

### Pitfalls and fixes
- Missing optional dependencies silently remove capabilities (e.g., deblending requires `scikit-image`, region workflows require `regions`): install extras (`docs/getting_started/install.rst`).
- Very new Python/platform may force source builds: install C compiler/toolchain first (`docs/getting_started/install.rst`).
- `photutils.test()` was removed: use `pytest --pyargs photutils` (`docs/whats_new/1.13.rst`).
- Upgrades to 3.0 require newer NumPy/SciPy/Matplotlib/scikit-image minimum versions (`docs/whats_new/3.0.rst`).
- ePSF build API changed from tuple-only style to `EPSFBuildResult`: prefer `result.epsf`, `result.converged`, etc. (`docs/whats_new/3.0.rst`).
- Poor star sample quality in ePSF building yields noisy/holed models: use bright, isolated stars and subtract background before extraction (`docs/user_guide/epsf_building.rst`).

### Convergence/validation checks
- Confirm `import photutils` works and version is expected.
- Run `pytest --pyargs photutils` as baseline runtime validation (`docs/getting_started/install.rst`).
- If ePSF workflow is involved, verify `EPSFBuildResult.converged`, `iterations`, and `final_center_accuracy` (`docs/whats_new/3.0.rst`).
- Spot-check optional features after extras install (deblend, regions conversion, progress bars).
- For release artifacts, run `python -m build --sdist .` and `python -m twine check --strict dist/*` (`docs/development/releasing.rst`).

## Scope
- Handle questions about build, installation, compilation, and environment setup.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `docs/whats_new/2.1.rst`
- `docs/getting_started/install.rst`
- `docs/whats_new/3.0.rst`
- `docs/whats_new/1.13.rst`
- `docs/user_guide/epsf_building.rst`

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
- `photutils/__init__.py`
- `photutils/psf/epsf_builder.py`
- `photutils/psf/epsf_stars.py`
- `photutils/psf/simulation.py`
- `photutils/psf/model_io.py`
- `photutils/psf/model_helpers.py`
- `photutils/segmentation/core.py`
- `photutils/datasets/__init__.py`
- `photutils/datasets/load.py`
- `photutils/datasets/images.py`
- `photutils/conftest.py`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" photutils`).
