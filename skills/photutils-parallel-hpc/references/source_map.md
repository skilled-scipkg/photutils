# photutils source map: Parallel and HPC

Generated from source roots:
- `photutils`

Use this map only after exhausting the topic docs in `references/doc_map.md`.

## Topic query tokens
- `batch`
- `benchmark`
- `deblend`
- `memory`
- `parallel`
- `performance`
- `photometry`
- `scaling`
- `segmentation`
- `throughput`

## Fast source navigation
- `rg -n "def |class " photutils/segmentation photutils/psf photutils/background photutils/datasets`
- `rg -n "npixels|nlevels|progress_bar|oversampling|threshold" photutils`
- `pytest -q <test_path> -k <keyword>`

## Function-level source entry points
- `photutils/segmentation/detect.py` | symbols: `detect_threshold`, `detect_sources` | behavior checks: `photutils/segmentation/tests/test_detect.py`
- `photutils/segmentation/deblend.py` | symbols: `deblend_sources` | behavior checks: `photutils/segmentation/tests/test_deblend.py`
- `photutils/segmentation/finder.py` | symbols: `SourceFinder` | behavior checks: `photutils/segmentation/tests/test_finder.py`
- `photutils/segmentation/catalog.py` | symbols: `SourceCatalog` | behavior checks: `photutils/segmentation/tests/test_catalog.py`
- `photutils/background/background_2d.py` | symbols: `Background2D` | behavior checks: `photutils/background/tests/test_background_2d.py`
- `photutils/psf/photometry.py` | symbols: `PSFPhotometry` | behavior checks: `photutils/psf/tests/test_photometry.py`
- `photutils/psf/iterative.py` | symbols: `IterativePSFPhotometry` | behavior checks: `photutils/psf/tests/test_iterative.py`
- `photutils/psf/gridded_models.py` | symbols: `GriddedPSFModel`, `STDPSFGrid` | behavior checks: `photutils/psf/tests/test_gridded_models.py`
- `photutils/psf/simulation.py` | symbols: `make_psf_model_image` | behavior checks: `photutils/psf/tests/test_simulation.py`
- `photutils/datasets/images.py` | symbols: `make_model_image` | behavior checks: `photutils/datasets/tests/test_images.py`
- `photutils/datasets/noise.py` | symbols: `make_noise_image`, `apply_poisson_noise` | behavior checks: `photutils/datasets/tests/test_noise.py`
- `photutils/utils/_convolution.py` | symbols: `_filter_data` | behavior checks: `photutils/utils/tests/test_convolution.py`
