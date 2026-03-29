# GSoC 2026 Project 4 Track B PoC

This branch contains a small multi-tenant security hardening slice for Kubeflow Pipelines frontend artifact proxy handling.

## What this track demonstrates

Track B is about turning tenant-boundary assumptions into explicit allow and deny behavior.

This branch focuses on the namespaced artifact proxy path. The change makes the handler reject invalid namespace inputs before constructing or calling the namespaced proxy target.

## What changed

- Added namespace syntax validation in `frontend/server/handlers/artifacts.ts`
- Expanded `frontend/server/integration-tests/artifact-proxy.test.ts`
- Added deny cases for invalid namespaces with:
  - dot-separated namespace values
  - uppercase namespace values
- Added assertions that the proxy target function is not called on rejected input

## Quick local check

```bash
cd frontend/server
npm test -- integration-tests/artifact-proxy.test.ts
```

## What is intentionally not included

- broader identity-aware authorization redesign
- cross-component changes outside the artifact proxy slice
- Track A scalability changes
- Track C manifests routing changes
- Track D Trainer zero-trust validation helpers

This branch is intentionally narrow. It shows a concrete security hardening unit with direct regression coverage.
