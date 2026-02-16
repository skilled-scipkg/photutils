# photutils source map: Getting Started

Generated from source roots:
- `photutils`

Use this map only after exhausting the topic docs in `references/doc_map.md`.

## Topic query tokens
- `aperture`
- `background`
- `centroid`
- `datasets`
- `detection`
- `photometry`
- `profiles`
- `segmentation`
- `simulation`

## Fast source navigation
- `rg -n "def |class " photutils/background photutils/detection photutils/segmentation photutils/aperture photutils/centroids photutils/datasets`
- `rg -n "threshold|npixels|background|mask|flux|centroid" photutils`
- `pytest -q <test_path> -k <keyword>`

## Function-level source entry points
- `photutils/background/background_2d.py` | symbols: `Background2D` | behavior checks: `photutils/background/tests/test_background_2d.py`
- `photutils/background/core.py` | symbols: `MedianBackground`, `SExtractorBackground` | behavior checks: `photutils/background/tests/test_core.py`
- `photutils/detection/daofinder.py` | symbols: `DAOStarFinder` | behavior checks: `photutils/detection/tests/test_daofinder.py`
- `photutils/segmentation/detect.py` | symbols: `detect_threshold`, `detect_sources` | behavior checks: `photutils/segmentation/tests/test_detect.py`
- `photutils/segmentation/deblend.py` | symbols: `deblend_sources` | behavior checks: `photutils/segmentation/tests/test_deblend.py`
- `photutils/segmentation/catalog.py` | symbols: `SourceCatalog` | behavior checks: `photutils/segmentation/tests/test_catalog.py`
- `photutils/aperture/photometry.py` | symbols: `aperture_photometry` | behavior checks: `photutils/aperture/tests/test_photometry.py`
- `photutils/aperture/stats.py` | symbols: `ApertureStats` | behavior checks: `photutils/aperture/tests/test_stats.py`
- `photutils/centroids/core.py` | symbols: `centroid_sources`, `centroid_com` | behavior checks: `photutils/centroids/tests/test_core.py`
- `photutils/morphology/core.py` | symbols: `data_properties` | behavior checks: `photutils/morphology/tests/test_core.py`
- `photutils/profiles/radial_profile.py` | symbols: `RadialProfile` | behavior checks: `photutils/profiles/tests/test_radial_profile.py`
- `photutils/psf_matching/fourier.py` | symbols: `make_kernel` | behavior checks: `photutils/psf_matching/tests/test_fourier.py`
- `photutils/datasets/images.py` | symbols: `make_model_image` | behavior checks: `photutils/datasets/tests/test_images.py`
- `photutils/datasets/noise.py` | symbols: `make_noise_image` | behavior checks: `photutils/datasets/tests/test_noise.py`
