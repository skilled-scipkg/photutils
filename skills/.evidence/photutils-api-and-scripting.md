# Evidence: photutils-api-and-scripting

## Primary docs
- `docs/reference/index.rst`
- `docs/whats_new/1.6.rst`
- `docs/development/releasing.rst`
- `docs/whats_new/1.8.rst`
- `docs/reference/utils_api.rst`
- `docs/reference/segmentation_api.rst`
- `docs/reference/psf_matching_api.rst`
- `docs/reference/psf_api.rst`
- `docs/reference/profiles_api.rst`
- `docs/reference/morphology_api.rst`
- `docs/reference/isophote_api.rst`
- `docs/reference/detection_api.rst`

## Primary source entry points
- `skills/photutils-api-and-scripting/references/doc_map.md`
- `photutils/psf_matching/utils.py`
- `photutils/psf_matching/__init__.py`
- `photutils/psf/matching/__init__.py`
- `photutils/psf_matching/windows.py`
- `photutils/psf_matching/fourier.py`
- `photutils/segmentation/utils.py`
- `photutils/psf/utils.py`
- `photutils/psf/functional_models.py`
- `photutils/psf/simulation.py`
- `photutils/segmentation/__init__.py`
- `photutils/psf/__init__.py`
- `photutils/profiles/__init__.py`
- `photutils/morphology/__init__.py`
- `photutils/isophote/__init__.py`
- `photutils/detection/__init__.py`
- `photutils/centroids/__init__.py`
- `photutils/background/__init__.py`
- `photutils/aperture/__init__.py`
- `photutils/segmentation/core.py`

## Extracted headings
- (none extracted)

## Executable command hints
- python -m build --sdist .
- python -m twine check --strict dist/*

## Warnings and pitfalls
- #. Remove any untracked files (**WARNING: this will permanently remove
