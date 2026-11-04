# Beacon release review

## Pipeline audit
Gap: production could run without the validation job completing first.
Risk: an unvalidated release could reach the production review stage.
Fix: `production` now uses `needs: validate` in `.github/workflows/release.yml`.
Approval remains required in the production environment; this local check does not prove approval or deployment.

## Image and rollback audit
Gap: deployment used mutable `latest`, and rollback pointed to the candidate image.
Risk: the deployed image could change unexpectedly, and rollback could repeat the failed release.
Fix: deployment is pinned to `beacon-service:v2.3.1`; rollback targets known-good `beacon-service:v2.3.0`.

## Traceability
Why PATCH is appropriate:
Candidate image and annotated Git tag:
Record tag -> code commit in PDF using git rev-parse commands.
Image-tag mutability limitation:

## Incident recovery
Evidence and rollback vs forward decision:
Known-good target:
Proposed kubectl command (not executed):
Recovery checks after action:

## Release note and decision
Change scope:
Local validation proof:
Open risk / owner / mitigation:
Current production decision and blocker:
Terraform vs Kubernetes responsibilities:
