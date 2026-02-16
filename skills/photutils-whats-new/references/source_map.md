# photutils source map: Whats New

Generated from source roots:
- `photutils`

Use this map only after exhausting the topic docs in `references/doc_map.md`.

## Topic query tokens
- `deprecation`
- `imports`
- `migration`
- `release`
- `regression`
- `upgrade`
- `whats-new`

## Fast source navigation
- `rg -n "def |class " photutils/aperture photutils/detection photutils/segmentation photutils/profiles photutils/psf`
- `rg -n "deprecated|removed|npixels|theta|min_separation|converged" photutils`
- `pytest -q <test_path> -k <keyword>`

## Function-level source entry points
- `photutils/aperture/converters.py` | symbols: `region_to_aperture`, `aperture_to_region` | behavior checks: `photutils/aperture/tests/test_converters.py`
- `photutils/aperture/photometry.py` | symbols: `aperture_photometry` | behavior checks: `photutils/aperture/tests/test_photometry.py`
- `photutils/detection/daofinder.py` | symbols: `DAOStarFinder` | behavior checks: `photutils/detection/tests/test_daofinder.py`
- `photutils/detection/irafstarfinder.py` | symbols: `IRAFStarFinder` | behavior checks: `photutils/detection/tests/test_irafstarfinder.py`
- `photutils/segmentation/finder.py` | symbols: `SourceFinder` | behavior checks: `photutils/segmentation/tests/test_finder.py`
- `photutils/segmentation/deblend.py` | symbols: `deblend_sources` | behavior checks: `photutils/segmentation/tests/test_deblend.py`
- `photutils/profiles/radial_profile.py` | symbols: `RadialProfile` | behavior checks: `photutils/profiles/tests/test_radial_profile.py`
- `photutils/profiles/curve_of_growth.py` | symbols: `CurveOfGrowth` | behavior checks: `photutils/profiles/tests/test_curve_of_growth.py`
- `photutils/psf/epsf_builder.py` | symbols: `EPSFBuilder`, `EPSFBuildResult` | behavior checks: `photutils/psf/tests/test_epsf_builder.py`
- `photutils/psf/photometry.py` | symbols: `PSFPhotometry` | behavior checks: `photutils/psf/tests/test_photometry.py`
- `photutils/background/background_2d.py` | symbols: `Background2D` | behavior checks: `photutils/background/tests/test_background_2d.py`
- `photutils/utils/_optional_deps.py` | symbols: `__getattr__` for optional dependency gating | behavior checks: `python -c "import photutils.utils._optional_deps as o; print(hasattr(o, 'HAS_SCIPY'))"`
