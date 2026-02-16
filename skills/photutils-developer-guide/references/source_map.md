# photutils source map: Developer Guide

Generated from source roots:
- `photutils`

Use this map only after exhausting the topic docs in `references/doc_map.md`.

## Topic query tokens
- `contributing`
- `coverage`
- `deprecation`
- `developer`
- `regression`
- `release`
- `tests`
- `triage`

## Fast source navigation
- `rg -n "def |class " photutils`
- `rg -n "deprecated|warning|TODO|FIXME|converged|npixels" photutils`
- `pytest -q <test_path> -k <keyword>`

## Function-level source entry points
- `photutils/conftest.py` | symbols: pytest fixtures/markers setup | behavior checks: `pytest -q photutils -k "not remote_data"`
- `photutils/segmentation/detect.py` | symbols: `detect_threshold`, `detect_sources` | behavior checks: `photutils/segmentation/tests/test_detect.py`
- `photutils/segmentation/deblend.py` | symbols: `deblend_sources` | behavior checks: `photutils/segmentation/tests/test_deblend.py`
- `photutils/segmentation/catalog.py` | symbols: `SourceCatalog` | behavior checks: `photutils/segmentation/tests/test_catalog.py`
- `photutils/background/background_2d.py` | symbols: `Background2D` | behavior checks: `photutils/background/tests/test_background_2d.py`
- `photutils/aperture/photometry.py` | symbols: `aperture_photometry` | behavior checks: `photutils/aperture/tests/test_photometry.py`
- `photutils/detection/daofinder.py` | symbols: `DAOStarFinder` | behavior checks: `photutils/detection/tests/test_daofinder.py`
- `photutils/psf/photometry.py` | symbols: `PSFPhotometry` | behavior checks: `photutils/psf/tests/test_photometry.py`
- `photutils/psf/epsf_builder.py` | symbols: `EPSFBuilder`, `EPSFBuildResult` | behavior checks: `photutils/psf/tests/test_epsf_builder.py`
- `photutils/isophote/fitter.py` | symbols: `EllipseFitter`, `CentralEllipseFitter` | behavior checks: `photutils/isophote/tests/test_fitter.py`
- `photutils/isophote/model.py` | symbols: `build_ellipse_model` | behavior checks: `photutils/isophote/tests/test_model.py`
- `photutils/utils/errors.py` | symbols: `calc_total_error` | behavior checks: `photutils/utils/tests/test_errors.py`
