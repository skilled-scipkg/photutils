---
name: photutils-advanced-topics
description: This skill should be used for low-volume advanced topics consolidated from one-doc skills (changelog, datasets API, user-guide index routing, and isophote test-data notes).
---

# photutils: Advanced Topics

## Scope
- Consolidated router for low-signal one-doc topics.
- `docs/changelog.rst` (full change ledger)
- `docs/reference/datasets_api.rst` (datasets/simulation API landing page)
- `docs/user_guide/index.rst` (user-guide table of contents)
- `photutils/isophote/tests/data/README.rst` (isophote test-data provenance note)

## Route the request
- Use this skill for changelog lookup, release archaeology, or broad diff tracing across many versions.
- Use this skill for quick datasets API entrypoint lookup before drilling into `photutils.datasets` source.
- Use this skill to route users from a generic "user guide" request into concrete subtopics.
- Use this skill for isophote test-data README context; route functional isophote fitting/API questions to `photutils-api-and-scripting` after initial triage.

## Primary documentation references
- `docs/changelog.rst`
- `docs/reference/datasets_api.rst`
- `docs/user_guide/index.rst`
- `photutils/isophote/tests/data/README.rst`

## Workflow
- Start with the exact doc file that matches the request subtype.
- If the request needs actionable workflow details, route to a core skill (`photutils-getting-started`, `photutils-api-and-scripting`, or `photutils-whats-new`).
- If docs remain ambiguous, inspect `references/source_map.md` entry points for concrete implementation details.
- Cite exact file paths in responses.

## Source entry points for unresolved issues
- `photutils/datasets/__init__.py`
- `photutils/datasets/images.py`
- `photutils/datasets/noise.py`
- `photutils/datasets/wcs.py`
- `photutils/datasets/load.py`
- `photutils/datasets/model_params.py`
- `photutils/datasets/examples.py`
- `photutils/psf/simulation.py`
- `photutils/isophote/ellipse.py`
- `photutils/isophote/isophote.py`
- `photutils/isophote/sample.py`
- `photutils/isophote/integrator.py`
- `photutils/isophote/model.py`
- `photutils/isophote/geometry.py`
- `photutils/isophote/ellipse_model.pyx`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" photutils`).
