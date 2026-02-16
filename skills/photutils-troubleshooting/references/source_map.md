# photutils source map: Troubleshooting

Generated from source roots:
- `photutils`

Use this map only after exhausting the topic docs in `references/doc_map.md`.

## Topic query tokens
- `deblend`
- `detect`
- `error`
- `faq`
- `failure`
- `isophote`
- `photometry`
- `regression`
- `threshold`
- `units`

## Fast source navigation
- `rg -n "def |class " photutils/detection photutils/segmentation photutils/psf photutils/isophote`
- `rg -n "ValueError|warning|npixels|threshold|unit|converged" photutils`
- `pytest -q <test_path> -k <keyword>`

## Function-level source entry points
- `photutils/detection/daofinder.py` | symbols: `DAOStarFinder` | behavior checks: `photutils/detection/tests/test_daofinder.py`
- `photutils/detection/irafstarfinder.py` | symbols: `IRAFStarFinder` | behavior checks: `photutils/detection/tests/test_irafstarfinder.py`
- `photutils/segmentation/detect.py` | symbols: `detect_threshold`, `detect_sources` | behavior checks: `photutils/segmentation/tests/test_detect.py`
- `photutils/segmentation/deblend.py` | symbols: `deblend_sources` | behavior checks: `photutils/segmentation/tests/test_deblend.py`
- `photutils/background/background_2d.py` | symbols: `Background2D` | behavior checks: `photutils/background/tests/test_background_2d.py`
- `photutils/aperture/converters.py` | symbols: `region_to_aperture`, `aperture_to_region` | behavior checks: `photutils/aperture/tests/test_converters.py`
- `photutils/psf/photometry.py` | symbols: `PSFPhotometry` | behavior checks: `photutils/psf/tests/test_photometry.py`
- `photutils/isophote/ellipse.py` | symbols: `Ellipse` | behavior checks: `photutils/isophote/tests/test_ellipse.py`
- `photutils/isophote/fitter.py` | symbols: `EllipseFitter`, `CentralEllipseFitter` | behavior checks: `photutils/isophote/tests/test_fitter.py`
- `photutils/isophote/sample.py` | symbols: `EllipseSample` | behavior checks: `photutils/isophote/tests/test_sample.py`
- `photutils/isophote/model.py` | symbols: `build_ellipse_model` | behavior checks: `photutils/isophote/tests/test_model.py`
- `photutils/utils/errors.py` | symbols: `calc_total_error` | behavior checks: `photutils/utils/tests/test_errors.py`
