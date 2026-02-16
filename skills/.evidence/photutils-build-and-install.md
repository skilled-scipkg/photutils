# Evidence: photutils-build-and-install

## Primary docs
- `docs/whats_new/2.1.rst`
- `docs/getting_started/install.rst`
- `docs/whats_new/3.0.rst`
- `docs/whats_new/1.13.rst`
- `docs/user_guide/epsf_building.rst`

## Primary source entry points
- `skills/photutils-build-and-install/references/doc_map.md`
- `photutils/psf/epsf_builder.py`
- `photutils/psf/epsf_stars.py`
- `photutils/__init__.py`
- `photutils/psf/simulation.py`
- `photutils/utils/__init__.py`
- `photutils/segmentation/__init__.py`
- `photutils/psf_matching/__init__.py`
- `photutils/psf/__init__.py`
- `photutils/profiles/__init__.py`
- `photutils/morphology/__init__.py`
- `photutils/isophote/__init__.py`
- `photutils/geometry/__init__.py`
- `photutils/detection/__init__.py`
- `photutils/datasets/__init__.py`
- `photutils/centroids/__init__.py`
- `photutils/background/__init__.py`
- `photutils/aperture/__init__.py`
- `photutils/psf/matching/__init__.py`
- `photutils/conftest.py`

## Extracted headings
- Old (deprecated)
- New

## Executable command hints
- python -m pip install photutils
- python -m pip install "photutils[all]"
- python -m pip install ".[all]"
- python -m pip install --upgrade --extra-index-url https://pypi.anaconda.org/astropy/simple "photutils[all]" --pre

## Warnings and pitfalls
- error. This situation can occur when the local background estimator
- * PSFs should be centered (a warning is issued if not)
- convergence accuracy. Please see the :class:`~photutils.psf.EPSFBuilder`
