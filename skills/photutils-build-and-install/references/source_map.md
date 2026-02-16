# photutils source map: Build and Install

Generated from source roots:
- `photutils`

Use this map only after exhausting the topic docs in `references/doc_map.md`.

## Topic query tokens
- `build`
- `deps`
- `epsf`
- `extras`
- `import`
- `install`
- `optional`
- `validation`

## Fast source navigation
- `rg -n "def |class " photutils/psf photutils/segmentation photutils/aperture photutils/datasets photutils/utils`
- `rg -n "optional|import|dependency|converged|read" photutils`
- `pytest -q <test_path> -k <keyword>`

## Function-level source entry points
- `photutils/__init__.py` | symbols: package import surface, `__version__` | behavior checks: `python -c "import photutils; print(photutils.__version__)"`
- `photutils/utils/_optional_deps.py` | symbols: optional dependency dispatch via `__getattr__` | behavior checks: `python -c "import photutils.utils._optional_deps as o; print(o.HAS_SCIPY)"`
- `photutils/aperture/converters.py` | symbols: `region_to_aperture`, `aperture_to_region` | behavior checks: `photutils/aperture/tests/test_converters.py`
- `photutils/segmentation/deblend.py` | symbols: `deblend_sources` (requires optional deps for some paths) | behavior checks: `photutils/segmentation/tests/test_deblend.py`
- `photutils/psf/epsf_builder.py` | symbols: `EPSFBuilder`, `EPSFBuildResult` | behavior checks: `photutils/psf/tests/test_epsf_builder.py`
- `photutils/psf/epsf_stars.py` | symbols: ePSF star extraction helpers | behavior checks: `photutils/psf/tests/test_epsf_stars.py`
- `photutils/psf/gridded_models.py` | symbols: `GriddedPSFModel`, `STDPSFGrid` | behavior checks: `photutils/psf/tests/test_gridded_models.py`
- `photutils/psf/model_io.py` | symbols: model serialization interfaces | behavior checks: `photutils/psf/tests/test_gridded_models.py`
- `photutils/datasets/load.py` | symbols: `get_path`, `load_*` helpers | behavior checks: `photutils/datasets/tests/test_load.py`
- `photutils/conftest.py` | symbols: pytest global settings and fixtures | behavior checks: `pytest -q photutils -k "not remote_data"`
