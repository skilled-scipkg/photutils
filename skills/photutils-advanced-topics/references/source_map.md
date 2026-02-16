# photutils source map: Advanced Topics

Generated from source roots:
- `photutils`

Use this map only after exhausting the topic docs in `references/doc_map.md`.

## Topic query tokens
- `changelog`
- `datasets`
- `isophote`
- `release`
- `simulation`
- `user-guide`

## Fast source navigation
- `rg -n "def |class " photutils/datasets photutils/isophote photutils/psf`
- `rg -n "load_|make_|ellipse|harmonic|simulation" photutils`
- `pytest -q <test_path> -k <keyword>`

## Function-level source entry points
- `photutils/datasets/load.py` | symbols: `get_path`, `load_spitzer_image`, `load_irac_psf` | behavior checks: `photutils/datasets/tests/test_load.py`
- `photutils/datasets/images.py` | symbols: `make_model_image` | behavior checks: `photutils/datasets/tests/test_images.py`
- `photutils/datasets/noise.py` | symbols: `make_noise_image`, `apply_poisson_noise` | behavior checks: `photutils/datasets/tests/test_noise.py`
- `photutils/datasets/wcs.py` | symbols: `make_wcs`, `make_gwcs` | behavior checks: `photutils/datasets/tests/test_wcs.py`
- `photutils/datasets/model_params.py` | symbols: `make_model_params` | behavior checks: `photutils/datasets/tests/test_model_params.py`
- `photutils/psf/simulation.py` | symbols: `make_psf_model_image` | behavior checks: `photutils/psf/tests/test_simulation.py`
- `photutils/isophote/ellipse.py` | symbols: `Ellipse` | behavior checks: `photutils/isophote/tests/test_ellipse.py`
- `photutils/isophote/fitter.py` | symbols: `EllipseFitter` | behavior checks: `photutils/isophote/tests/test_fitter.py`
- `photutils/isophote/model.py` | symbols: `build_ellipse_model` | behavior checks: `photutils/isophote/tests/test_model.py`
- `photutils/isophote/sample.py` | symbols: `EllipseSample` | behavior checks: `photutils/isophote/tests/test_sample.py`
