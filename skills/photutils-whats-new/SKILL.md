---
name: photutils-whats-new
description: Use this skill for Photutils upgrade and migration work across releases. It maps behavior/import/dependency changes to concrete release notes, source entry points, and validation checks.
---

# photutils: Whats New

## High-Signal Playbook
### Route conditions
- Route to `photutils-build-and-install` when migration blockers are dependency or environment related.
- Route to `photutils-api-and-scripting` for symbol-level rewrites after identifying version deltas.
- Route to `photutils-getting-started` for non-migration workflow guidance.
- Route to `photutils-advanced-topics` for full changelog archaeology beyond release highlights.

### Triage questions
- What exact source and target versions are involved?
- Which subpackages fail after upgrade (`aperture`, `detection`, `segmentation`, `profiles`, `psf`)?
- Are failures import-related, behavior-related, or output-schema-related?
- Are arrays unit-bearing or region/deblending features in use?
- Do failing tests map to specific release note sections?

### Canonical workflow
1. Identify version jump and open concrete files under `docs/whats_new/` (for example `docs/whats_new/2.0.rst`, `docs/whats_new/2.2.rst`, `docs/whats_new/3.0.rst`).
2. Apply import/dependency changes first (major blockers in 2.0 and 3.0).
3. Update behavior-sensitive paths (finder limits, profile bins, aperture conversions, PSF/ePSF results).
4. Run synthetic mini-scripts per touched subsystem.
5. Reconcile table columns/units/flags against release notes.
6. Escalate to `references/source_map.md` when notes are ambiguous.

### Minimal working example
```python
from photutils.aperture import CircularAperture, aperture_to_region

aper = CircularAperture((10.0, 20.0), r=4.0)
region = aperture_to_region(aper)
print(type(region).__name__)
```

```bash
pytest -q photutils/aperture/tests/test_converters.py -k region
pytest -q photutils/profiles/tests/test_radial_profile.py -k edge
```

### Pitfalls and fixes
- 2.0 import policy requires subpackage-qualified imports (`docs/whats_new/2.0.rst`).
- 3.0 raises minimum dependency versions and can break stale environments (`docs/whats_new/3.0.rst`).
- `RadialProfile`/`CurveOfGrowth` constructor semantics changed to radial-edge inputs (`docs/whats_new/1.8.rst`).
- `DAOStarFinder`/`IRAFStarFinder` endpoint inclusivity changed and affects boundary detections (`docs/whats_new/2.1.rst`).
- Pixel-aperture `theta` became an angular quantity object (`docs/whats_new/2.2.rst`).
- Release-note examples are historical snapshots; confirm current behavior with tests.

### Convergence/validation checks
- Migration scripts run without deprecation warnings.
- Imports resolve from documented namespaces.
- Table schemas/units match expected release deltas.
- Focused tests for touched subpackages pass.

## Scope
- Handle release-to-release migration analysis and concrete remediation steps.
- Prioritize reproducible checks over broad historical summary.

## Primary documentation references
- `docs/whats_new/2.0.rst`
- `docs/whats_new/2.1.rst`
- `docs/whats_new/2.2.rst`
- `docs/whats_new/3.0.rst`
- `docs/whats_new/1.8.rst`
- `docs/release_notes/index.rst`

## Workflow
- Start with the primary references above.
- If details are missing, inspect `references/doc_map.md` for the complete topic document list.
- Use `references/source_map.md` for function-level module and test entry points.
- Re-run focused tests after each migration edit.
- Cite exact documentation/source file paths in responses.

## Source entry points for unresolved issues
- `photutils/aperture/converters.py`
- `photutils/aperture/photometry.py`
- `photutils/detection/daofinder.py`
- `photutils/detection/irafstarfinder.py`
- `photutils/segmentation/finder.py`
- `photutils/segmentation/deblend.py`
- `photutils/profiles/radial_profile.py`
- `photutils/profiles/curve_of_growth.py`
- `photutils/psf/epsf_builder.py`
- `photutils/psf/photometry.py`
- `photutils/background/background_2d.py`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" photutils`).
