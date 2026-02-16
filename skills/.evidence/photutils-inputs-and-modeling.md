# Evidence: photutils-inputs-and-modeling

## Primary docs
- `docs/whats_new/2.0.rst`
- `docs/whats_new/1.9.rst`
- `docs/whats_new/1.11.rst`
- `docs/whats_new/1.10.rst`
- `docs/reference/geometry_api.rst`

## Primary source entry points
- `skills/photutils-inputs-and-modeling/references/doc_map.md`
- `photutils/geometry/__init__.py`
- `photutils/isophote/geometry.py`
- `photutils/geometry/core.pyx`
- `photutils/geometry/core.pxd`
- `photutils/geometry/rectangular_overlap.pyx`
- `photutils/geometry/elliptical_overlap.pyx`
- `photutils/geometry/circular_overlap.pyx`
- `photutils/psf/model_plotting.py`
- `photutils/psf/model_io.py`
- `photutils/psf/model_helpers.py`
- `photutils/isophote/model.py`
- `photutils/isophote/ellipse_model.pyx`
- `photutils/datasets/model_params.py`
- `photutils/psf/image_models.py`
- `photutils/psf/gridded_models.py`
- `photutils/psf/functional_models.py`

## Extracted headings
- (none extracted)

## Executable command hints
- (none extracted)

## Warnings and pitfalls
- allow the input of error arrays, which will be used as weights in the
- * Fit warnings are not emitted for each source. A single warning is emitted at the end of fitting.
