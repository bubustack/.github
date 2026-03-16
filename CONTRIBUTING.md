# Contributing to BubuStack

BubuStack is a Kubernetes-native automation stack composed of the **bobrapet** operator, the **bobravoz-grpc** transport plane, the **bubu-sdk-go**, and a growing catalog of Engrams and Impulses. Every repo follows the same principle: *DOTADIW (Do One Thing And Do It Well)* with declarative APIs, clean GitOps workflows, and production-grade reliability. Thank you for helping us keep that bar high.

## Choose the right home for your change

- Use the repository that matches your change (operator, transport, SDK, Engram/Impulse, docs, or examples). Repository-specific READMEs describe any extra steps.
- For cross-cutting proposals, start a thread in [org-wide Discussions](https://github.com/orgs/bubustack/discussions) so we can coordinate controller+SDK changes together.
- Security issues must follow the process in [SECURITY.md](./SECURITY.md); please do **not** open a public issue.

## Reporting bugs

1. Search the relevant repository issue tracker for existing reports.
2. When filing a new bug report, include:
   - Component (`bobrapet`, `http-request-engram`, `bubu-sdk-go`, etc.).
   - Kubernetes version and cluster type.
   - Custom Resources (`Story`, `StoryRun`, `Engram`, `Impulse`, `TransportBinding`, etc.) or sample manifests.
   - Controller/Engram pod logs (`kubectl logs`), SDK traces, or Stream payloads if applicable.
3. Tag issues with `kind/bug` and, if relevant, `area/operator`, `area/engram`, `area/sdk`, or `area/transport` to help us triage.

## Requesting features / new components

- Use the issue template to describe *why* the change is needed, not just the implementation. Helpful inputs include workload scale, latency budgets, tenancy constraints, and whether the change affects EngramTemplates, ImpulseTemplates, or SDK contracts.
- For brand-new Engram/Impulse ideas, share proposed `spec.with` fields alongside the Bobrapet Story snippet so we can validate the CRD shape before implementation.
- When asking for new transports, describe the streaming requirements (e.g., WebRTC, gRPC, or webhook semantics) so we can confirm they slot cleanly into the `bobravoz-grpc` surface.

## Pull requests

1. **Fork and branch** from `main`. Keep each PR focused on one change-set (e.g., a new Engram parameter or a controller reconciliation tweak).
2. **Discuss breaking changes early.** If you need to evolve CRDs or SDK types, open a design issue first so downstream integrations can prepare.
3. **Run the relevant quality gates** before opening the PR:
   - Operators / transport controller: `make lint`, `make test`, `make generate`, `make manifests`, and (optionally) `make deploy IMG=<registry>/bobrapet:dev`.
   - Engrams, impulses, SDK (Go): `make lint`, `make test`, `make docker-build IMG=<registry>/<component>:dev`.
   - TypeScript/Node repos (e.g., `bubustack/website` or agent samples): `pnpm install`, `pnpm lint`, `pnpm test`, `pnpm build`.
4. **Document user-facing changes.** Update README/CHANGELOG/CRD docs plus Engram or Impulse templates when you add fields or alter defaults.
5. **Link issues and test evidence** in the PR template. For controller work, include the `kubectl` commands or Kind/e2e scripts you ran.

## Development workflow

### Operators & controllers (bobrapet, bobravoz-grpc)

- **Prerequisites:** Go 1.25.1+, Docker or another OCI builder, `kubectl`, access to a Kubernetes cluster (Kind/Minikube is fine).
- **Common targets:** `make lint`, `make test`, `make test-e2e`, `make generate`, `make manifests`, `make deploy IMG=<registry>/<name>:tag`.
- **Samples:** `config/samples` contains CRDs that can be applied via `kubectl apply -k config/samples` to smoke-test Stories, StoryRuns, Engrams, and Impulses.
- **CRD changes:** Run `make generate` and `make manifests` to refresh `api/*` deep-copies and `config/crd/bases/*.yaml`.

### SDK + Engrams/Impulses (Go)

- **Prerequisites:** Go 1.25.1+, Docker, `make`.
- **Quality gates:** `make fmt`, `make lint`, `make test`, `make docker-build IMG=<registry>/<component>:dev`.
- **Runtime verification:** Use `kubectl apply -f Engram.yaml` (or Helm/Kustomize overlays) plus a test `Story` to validate overrides, streaming modes, and `BUBU_DEBUG` logging.

### JavaScript/TypeScript projects (website, agent starter kits)

- **Prerequisites:** Match the versions declared in each `package.json` (`node >=22` & `pnpm >=10` for the agent starter, `node >=20` for the docs site). Use the package manager the repo already uses (pnpm where a `pnpm-lock.yaml` exists, npm/yarn elsewhere).
- **Common scripts:** `pnpm install && pnpm lint && pnpm test && pnpm build` for pnpm-based repos, or `npm install && npm run build` for Docusaurus/docs.
- **Testing:** Keep E2E credentials out of commits; store secrets in `.env.local` and supply mock fixtures for CI.

### Documentation & community health

- Markdown files live alongside the code they describe. Run `pnpm format` or `make fmt` where provided to keep formatting consistent.
- Organization-wide policies (Code of Conduct, Security, Support) are sourced from this `.github` repository—update them here first, then sync downstream if needed.

## Commit style & reviews

- Follow [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) so release automation can build CHANGELOG entries.
- Rebase or merge `main` before requesting review when conflicts arise.
- Every PR must pass CI, include tests (or rationale when tests are not applicable), and leave the tree in a deployable state.

## Issue labels

All repositories sync a shared label taxonomy defined in `.github/labels.yml`. Please:

- Apply exactly one `kind/*` label (bug, feature, docs, refactor, tests, chore).
- Add one or more `area/*` labels (operator, transport, SDK, engram, impulse, docs) plus `priority/*` if known.
- Use `status/*` labels to reflect triage state (`status/triage`, `status/needs-info`, `status/in-progress`, `status/blocked`, `status/ready`).
- Leave the `dependencies` label on automation-driven PRs (e.g., Dependabot) so release tooling can batch them correctly.

If you introduce a new architectural surface, extend `.github/labels.yml` first so the taxonomy stays consistent before using bespoke labels in a single repo.

## Code of Conduct

Participation in any BubuStack space is governed by the [Contributor Covenant Code of Conduct](./CODE_OF_CONDUCT.md). Report unacceptable behaviour to [conduct@bubustack.com](mailto:conduct@bubustack.com) or via the org Discussions moderation form.
