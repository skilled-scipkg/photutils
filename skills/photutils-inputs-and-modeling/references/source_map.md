# photutils source map: Inputs and Modeling

Generated from source roots:
- `photutils`

Use this map only after exhausting the topic docs in `references/doc_map.md`.

## Topic query tokens
- `geometry`
- `inputs`
- `model`
- `npixels`
- `overlap`
- `psf`
- `segmentation`
- `units`

## Fast source navigation
- `rg -n "def |class " photutils/geometry photutils/psf photutils/segmentation photutils/datasets`
- `rg -n "overlap|model|npixels|nlevels|oversampling|bounds" photutils`
- `pytest -q <test_path> -k <keyword>`

## Function-level source entry points
- `photutils/geometry/circular_overlap.pyx` | symbols: `circular_overlap_grid` | behavior checks: `photutils/geometry/tests/test_circular_overlap_grid.py`
- `photutils/geometry/elliptical_overlap.pyx` | symbols: `elliptical_overlap_grid` | behavior checks: `photutils/geometry/tests/test_elliptical_overlap_grid.py`
- `photutils/geometry/rectangular_overlap.pyx` | symbols: `rectangular_overlap_grid` | behavior checks: `photutils/geometry/tests/test_rectangular_overlap_grid.py`
- `photutils/datasets/model_params.py` | symbols: `make_model_params`, `make_random_models_table`, `params_table_to_models` | behavior checks: `photutils/datasets/tests/test_model_params.py`
- `photutils/datasets/images.py` | symbols: `make_model_image` | behavior checks: `photutils/datasets/tests/test_images.py`
- `photutils/segmentation/finder.py` | symbols: `SourceFinder` | behavior checks: `photutils/segmentation/tests/test_finder.py`
- `photutils/segmentation/deblend.py` | symbols: `deblend_sources` | behavior checks: `photutils/segmentation/tests/test_deblend.py`
- `photutils/psf/functional_models.py` | symbols: `GaussianPSF`, `CircularGaussianPRF`, `MoffatPSF` | behavior checks: `photutils/psf/tests/test_functional_models.py`
- `photutils/psf/model_helpers.py` | symbols: `make_psf_model`, `grid_from_epsfs` | behavior checks: `photutils/psf/tests/test_model_helpers.py`
- `photutils/psf/image_models.py` | symbols: `ImagePSF` | behavior checks: `photutils/psf/tests/test_image_models.py`
- `photutils/psf/gridded_models.py` | symbols: `GriddedPSFModel`, `STDPSFGrid` | behavior checks: `photutils/psf/tests/test_gridded_models.py`
- `photutils/isophote/model.py` | symbols: `build_ellipse_model` | behavior checks: `photutils/isophote/tests/test_model.py`
