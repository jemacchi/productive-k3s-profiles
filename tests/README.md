# Profiles Test Runner

This repository exposes content-focused tests that run public profiles and scenarios against a chosen version of the `productive-k3s-infra` engine.

Supported suites:

- `static`
- `contract`
- `live`

Recommended usage:

```bash
make test-static PROFILE=multipass-1-server-2-agents
make test-contract PROFILE=aws-single-node-basic INFRA_VERSION=0.9.62-0.9.4
make test-live PROFILE=on-prem-basic INFRA_VERSION=0.9.62-0.9.4
PRODUCTIVE_K3S_INFRA_REPO_URL="https://github.com/jemacchi/productive-k3s-infra.git" PRODUCTIVE_K3S_INFRA_REPO_REF="development" make test-matrix
make test-matrix
```

`test-matrix` runs only `static + contract`.

`live` is intended for manual validation before push, not for default CI.

Resolution order for the Infra engine:

- `PRODUCTIVE_K3S_INFRA_REPO_DIR`
- `PRODUCTIVE_K3S_INFRA_REPO_URL` + `PRODUCTIVE_K3S_INFRA_REPO_REF`
- `INFRA_VERSION`
- latest released `productive-k3s-infra`
