# Evidence: photutils-getting-started

## Primary docs
- `docs/index.rst`
- `docs/getting_started/overview.rst`
- `docs/getting_started/index.rst`
- `docs/user_guide/segmentation.rst`
- `docs/user_guide/psf_matching.rst`
- `docs/user_guide/psf.rst`
- `docs/user_guide/profiles.rst`
- `docs/user_guide/background.rst`
- `docs/user_guide/aperture.rst`
- `docs/user_guide/detection.rst`
- `docs/whats_new/1.1.rst`
- `docs/user_guide/morphology.rst`

## Primary source entry points
- `skills/photutils-getting-started/references/doc_map.md`
- `photutils/psf_matching/utils.py`
- `photutils/psf_matching/__init__.py`
- `photutils/psf/matching/__init__.py`
- `photutils/isophote/geometry.py`
- `photutils/psf_matching/windows.py`
- `photutils/psf_matching/fourier.py`
- `photutils/segmentation/utils.py`
- `photutils/psf/utils.py`
- `photutils/psf/simulation.py`
- `photutils/segmentation/__init__.py`
- `photutils/psf/__init__.py`
- `photutils/profiles/__init__.py`
- `photutils/morphology/__init__.py`
- `photutils/isophote/__init__.py`
- `photutils/geometry/__init__.py`
- `photutils/detection/__init__.py`
- `photutils/datasets/__init__.py`
- `photutils/centroids/__init__.py`
- `photutils/background/__init__.py`

## Extracted headings
- Initialize figure
- Create a 2-row, 6-column grid
- First row: 3 plots, each spanning 2 columns
- Second row: 2 plots, centered (occupying columns 1-2 and 3-4)
- Plot using the OO interface
- create an artificial single source
- find the source centroid
- create the radial profile
- plot the radial profile

## Executable command hints
- (none extracted)

## Warnings and pitfalls
- .. admonition:: Important
- areas you think API stability is important, please let us know as part
- The error columns are NaN because we did not input an error array (see
- *total* error array, i.e., the background-only error plus Poisson noise
- function can be used to calculate the total error array from a
- background-only error array and an effective gain.
- :func:`~photutils.utils.calc_total_error` to calculate the total error
- class. When a total ``error`` is input, the
- instrumental flux and propagated flux error within the source segments:
- >>> error = calc_total_error(data, bkg.background_rms, effective_gain)
- >>> cat = SourceCatalog(data, segm_deblend, error=error)
- should be at the center of the array. A warning will be issued if
