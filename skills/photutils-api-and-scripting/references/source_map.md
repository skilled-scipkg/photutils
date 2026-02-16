# photutils source map: API and Scripting

Generated from source roots:
- `photutils`

Use this map only after exhausting the topic docs in `references/doc_map.md`.

## Topic query tokens
- `aperture`
- `background`
- `centroid`
- `detection`
- `isophote`
- `morphology`
- `profiles`
- `psf`
- `segmentation`
- `units`

## Fast source navigation
- `rg -n "def |class " photutils/aperture photutils/background photutils/centroids photutils/detection photutils/segmentation photutils/psf photutils/profiles photutils/morphology photutils/isophote`
- `rg -n "deprecated|threshold|npixels|unit|catalog|kernel" photutils`
- `pytest -q <test_path> -k <keyword>`

## Function-level source entry points
- `photutils/aperture/photometry.py` | symbols: `aperture_photometry` | behavior checks: `photutils/aperture/tests/test_photometry.py`
- `photutils/background/core.py` | symbols: `MedianBackground`, `SExtractorBackground`, background RMS estimators | behavior checks: `photutils/background/tests/test_core.py`
- `photutils/background/background_2d.py` | symbols: `Background2D` | behavior checks: `photutils/background/tests/test_background_2d.py`
- `photutils/centroids/core.py` | symbols: `centroid_com`, `centroid_quadratic`, `centroid_sources` | behavior checks: `photutils/centroids/tests/test_core.py`
- `photutils/detection/daofinder.py` | symbols: `DAOStarFinder` | behavior checks: `photutils/detection/tests/test_daofinder.py`
- `photutils/detection/irafstarfinder.py` | symbols: `IRAFStarFinder` | behavior checks: `photutils/detection/tests/test_irafstarfinder.py`
- `photutils/segmentation/detect.py` | symbols: `detect_threshold`, `detect_sources` | behavior checks: `photutils/segmentation/tests/test_detect.py`
- `photutils/segmentation/finder.py` | symbols: `SourceFinder` | behavior checks: `photutils/segmentation/tests/test_finder.py`
- `photutils/segmentation/catalog.py` | symbols: `SourceCatalog` | behavior checks: `photutils/segmentation/tests/test_catalog.py`
- `photutils/psf/photometry.py` | symbols: `PSFPhotometry` | behavior checks: `photutils/psf/tests/test_photometry.py`
- `photutils/psf_matching/fourier.py` | symbols: `make_kernel`, `make_wiener_kernel` | behavior checks: `photutils/psf_matching/tests/test_fourier.py`
- `photutils/psf_matching/windows.py` | symbols: window classes (`HanningWindow`, `TukeyWindow`, `TopHatWindow`) | behavior checks: `photutils/psf_matching/tests/test_windows.py`
- `photutils/profiles/radial_profile.py` | symbols: `RadialProfile` | behavior checks: `photutils/profiles/tests/test_radial_profile.py`
- `photutils/profiles/curve_of_growth.py` | symbols: `CurveOfGrowth` | behavior checks: `photutils/profiles/tests/test_curve_of_growth.py`
- `photutils/morphology/core.py` | symbols: `data_properties` | behavior checks: `photutils/morphology/tests/test_core.py`
- `photutils/isophote/ellipse.py` | symbols: `Ellipse` | behavior checks: `photutils/isophote/tests/test_ellipse.py`
