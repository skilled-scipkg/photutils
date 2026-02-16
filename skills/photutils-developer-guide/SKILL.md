---
name: photutils-developer-guide
description: Use this skill for Photutils contribution and maintainer workflows (bug triage, test-first fixes, release execution, and cross-subpackage regression checks).
---

# photutils: Developer Guide

## High-Signal Playbook
### Route conditions
- Route to `photutils-build-and-install` for environment/bootstrap issues before contribution work.
- Route to `photutils-api-and-scripting` for end-user API usage questions.
- Route to `photutils-whats-new` for migration triage tied to concrete release deltas.
- Route to `photutils-getting-started` for non-maintainer, first-analysis workflows.

### Triage questions
- Is the task a bug fix, feature PR, or release operation?
- Is there a minimal reproducer and complete traceback?
- Which branch is targeted (`main` vs maintenance branch)?
- Which tests prove the bug and guard the fix?
- Does the change require updates to `CHANGES.rst` and a concrete file in `docs/whats_new/`?
- Is maintainer access available for tagging and publishing?

### Canonical workflow
1. Start with reproducible bug report + environment snapshot (`docs/development/contributing.rst`).
2. Add/adjust targeted tests before changing behavior.
3. Implement fix in the narrowest module and run focused pytest targets.
4. Run local quality gates (`tox -e test-alldeps`, docs, linkcheck).
5. Update `CHANGES.rst` and the relevant `docs/whats_new/*.rst` file.
6. For releases, tag/push and verify artifact publication (`docs/development/releasing.rst`).

### Minimal working example
```bash
pytest -q photutils/segmentation/tests/test_detect.py -k mask
pytest -q photutils/psf/tests/test_photometry.py -k basic
tox -e test-alldeps -- --remote-data
tox -e build_docs
tox -e linkcheck
```

```bash
ls docs/whats_new/*.rst | tail -n 5
git tag -a <X.Y.Z> -m '<X.Y.Z>'
git push upstream <X.Y.Z>
```

### Pitfalls and fixes
- Missing repro scripts slow issue triage: require minimal failing code and environment details.
- Skipping targeted tests increases regression risk: always add/modify tests with behavior changes.
- Releasing without updated `CHANGES.rst` and `docs/whats_new/*.rst` leaves incomplete release metadata.
- Tagging before CI/docs pass can publish broken artifacts: gate on green checks.
- Assuming publish permissions without maintainer rights blocks release flow.

### Convergence/validation checks
- Reproducer fails before fix and passes after fix.
- Focused tests and full tox targets pass.
- `CHANGES.rst` and release notes reflect shipped behavior.
- Release tags and distribution checks (`twine check`) succeed.

## Scope
- Handle contributor and maintainer workflows with test-backed implementation checks.
- Prioritize deterministic validation over broad architectural commentary.

## Primary documentation references
- `docs/development/index.rst`
- `docs/development/contributing.rst`
- `docs/development/releasing.rst`
- `docs/release_notes/index.rst`
- `docs/development/license.rst`
- `docs/development/contributors.rst`

## Workflow
- Start with the primary references above.
- If details are missing, inspect `references/doc_map.md` for the complete topic document list.
- Use `references/source_map.md` to jump to implementation modules and matching tests.
- Prefer narrow pytest targets first, then full tox quality gates.
- Cite exact documentation/source paths in responses.

## Source entry points for unresolved issues
- `photutils/conftest.py`
- `photutils/segmentation/detect.py`
- `photutils/segmentation/deblend.py`
- `photutils/psf/photometry.py`
- `photutils/background/background_2d.py`
- `photutils/aperture/photometry.py`
- `photutils/detection/daofinder.py`
- `photutils/isophote/fitter.py`
- `photutils/utils/errors.py`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" photutils`).
