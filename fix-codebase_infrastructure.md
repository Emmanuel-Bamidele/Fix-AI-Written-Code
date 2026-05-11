# fix-codebase_infrastructure.md

Use this prompt to repair Docker, deployment, cloud configuration, permissions, and runtime safety.

## Goal

Make infrastructure reproducible, least-privilege, secure, and operable.

## Agent instructions

Inspect:

- Dockerfiles
- Compose files
- Kubernetes manifests
- Terraform/OpenTofu/Pulumi/CDK
- GitHub Actions deploy workflows
- Environment variables
- Secret handling
- IAM permissions
- Storage buckets
- Network exposure
- Runtime resource limits
- Backup configuration

## Docker checklist

- [ ] Base images are pinned.
- [ ] Multi-stage build is used where appropriate.
- [ ] Runtime image excludes dev dependencies.
- [ ] Container does not run as root.
- [ ] Secrets are not baked into image.
- [ ] Health check exists.
- [ ] Ports are explicit.
- [ ] Build context excludes unnecessary files.
- [ ] Image is scanned.

## Cloud/IAM checklist

- [ ] Least-privilege roles.
- [ ] No wildcard admin permissions unless justified.
- [ ] Public buckets are intentional.
- [ ] Databases are not publicly exposed.
- [ ] Secrets are stored in a secret manager.
- [ ] Logs have retention.
- [ ] Backups are enabled.
- [ ] Encryption is enabled where appropriate.
- [ ] Production changes are auditable.

## Deployment checklist

- [ ] Deployment requires passing CI.
- [ ] Rollback path exists.
- [ ] Migrations are ordered safely.
- [ ] Health checks gate rollout.
- [ ] Environment variables are documented.
- [ ] Production config does not use dev defaults.

## Required output

```md
# Infrastructure Repair Summary

## Infrastructure files inspected

## Docker risks

## Secret/config risks

## IAM risks

## Deployment risks

## Fixes made

## Remaining infrastructure risks
```
