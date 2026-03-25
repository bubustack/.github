<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://bubustack.io/img/banner.png">
  <source media="(prefers-color-scheme: light)" srcset="https://bubustack.io/img/banner.png">
  <img alt="BubuStack" src="https://bubustack.io/img/banner.png" width="640">
</picture>

### Kubernetes-native workflow runtime for batch DAGs and streaming pipelines.

[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![Kubernetes](https://img.shields.io/badge/Kubernetes-1.29+-326CE5?logo=kubernetes&logoColor=white)](https://kubernetes.io)
[![Go](https://img.shields.io/badge/Go-1.25+-00ADD8?logo=go&logoColor=white)](https://go.dev)

---

BubuStack is an open-source toolkit for declarative, composable workflows on Kubernetes. Define workflows as CRDs, review and promote them through pull requests, and run them with durable execution semantics for batch automation and streaming workloads.

## Why BubuStack

- **GitOps-native** - Workflows are CRDs. Version, review, and promote them through pull requests like any other infrastructure.
- **Durable execution** - StoryRun and StepRun resources give you retries, timeouts, status, and observability at the workflow level.
- **Composable building blocks** - Reusable Engrams (tasks) and Impulses (triggers) let you package common behavior without coupling everything into one controller.
- **Batch + streaming in one model** - Use the same Story abstraction for DAG-style batch jobs and transport-backed streaming pipelines.

## Quickstart

```bash
# Install the operator
helm install bubustack oci://ghcr.io/bubustack/charts/bubustack

# Deploy a hello-world Story
kubectl apply -f https://raw.githubusercontent.com/bubustack/examples/main/batch/hello-world/bootstrap.yaml
kubectl apply -f https://raw.githubusercontent.com/bubustack/examples/main/batch/hello-world/engrams.yaml
kubectl apply -f https://raw.githubusercontent.com/bubustack/examples/main/batch/hello-world/story.yaml

# Trigger a run and watch it execute
kubectl apply -f https://raw.githubusercontent.com/bubustack/examples/main/batch/hello-world/storyrun.yaml
kubectl get storyruns,stepruns -n hello-world -w
```

## Repositories

| Repository | Description |
|:-----------|:------------|
| [`bobrapet`](https://github.com/bubustack/bobrapet) | Story, StoryRun, Engram, and Impulse controllers — the core operator |
| [`core`](https://github.com/bubustack/core) | Shared contracts, templating engine, transport runtime, and identity helpers |
| [`bobravoz-grpc`](https://github.com/bubustack/bobravoz-grpc) | Transport operator for streaming workloads with hub and peer-to-peer topologies |
| [`bubu-sdk-go`](https://github.com/bubustack/bubu-sdk-go) | Go SDK for building Engrams and Impulses with streaming, retries, and observability |
| [`tractatus`](https://github.com/bubustack/tractatus) | Canonical protobuf definitions and multi-language transport artifacts |
| [`examples`](https://github.com/bubustack/examples) | Runnable examples for batch and streaming workflows |
| [`website`](https://github.com/bubustack/website) | Public documentation site and product pages |
| [`bubuilder`](https://github.com/bubustack/bubuilder) | UI and API work for browsing runs, stories, and engrams |
| [`bubu-registry`](https://github.com/bubustack/bubu-registry) | Registry and packaging work for sharing Engrams and Impulses |
| [`helm-charts`](https://github.com/bubustack/helm-charts) | Helm charts for bobrapet, bobravoz-grpc, and bubuilder |
| [`engrams/*`](https://github.com/orgs/bubustack/repositories?q=engram) | First-party Engrams — HTTP, OpenAI, LiveKit, MCP, VAD, and more |
| [`impulses/*`](https://github.com/orgs/bubustack/repositories?q=impulse) | First-party Impulses — Cron, GitHub webhooks, Kubernetes events, LiveKit webhooks |

## Examples

| Example | Pattern | What it shows |
|:--------|:--------|:--------------|
| [Hello World](https://github.com/bubustack/examples/tree/main/batch/hello-world) | Batch | Zero-dependency quickstart - parallel steps, DAG dependencies, template expressions |
| [Scheduled Health Check](https://github.com/bubustack/examples/tree/main/batch/scheduled-health-check) | Batch | Cron triggers, parallel fan-out, `allowFailure`, AI-powered summarization |
| [Map-Reduce Summarizer](https://github.com/bubustack/examples/tree/main/batch/map-reduce-summarizer) | Batch | Dynamic parallelism with sub-stories, map-reduce adapter, result aggregation |
| [Content Digest (Simple)](https://github.com/bubustack/examples/tree/main/batch/content-digest-simple) | Batch | RSS to AI extraction to newsletter to Discord via MCP adapter |
| [Content Digest (Advanced)](https://github.com/bubustack/examples/tree/main/batch/content-digest-advanced) | Batch | Multi-feed fan-out with map-reduce, combined digest, Discord notification |
| [Multi-Model Consensus](https://github.com/bubustack/examples/tree/main/batch/multi-model-consensus) | Batch | Same template with different configs, fan-in judge pattern, structured output |
| [GitHub PR Review](https://github.com/bubustack/examples/tree/main/batch/github-pr-review) | Batch | AI-powered PR review - GitHub webhooks, diff analysis, automated comments |
| [Materialize Demo](https://github.com/bubustack/examples/tree/main/batch/materialize-demo) | Batch | Offloaded data handling - storage refs, materialization, controller-mode resolution |
| [Pod Crash Notifier](https://github.com/bubustack/examples/tree/main/realtime/pod-crash-notifier) | Streaming | Kubernetes event watch, AI crash analysis, Discord alerts |
| [LiveKit Voice Assistant](https://github.com/bubustack/examples/tree/main/realtime/livekit-voice) | Streaming | Voice and chat dual-mode - VAD, STT, LLM, TTS with a parallel chat path |
| [LiveKit Text Chat](https://github.com/bubustack/examples/tree/main/realtime/livekit-chat) | Streaming | Text-only chat assistant via LiveKit data channels |

## Contributing

We welcome contributions of all kinds — bug fixes, new Engrams, documentation, and feature proposals.

- **Star** the repos and watch releases
- **Build** an Engram or Impulse using the [Go SDK](https://github.com/bubustack/bubu-sdk-go)
- **Report** bugs and request features in the [affected repository](https://github.com/orgs/bubustack/repositories)
- **Pick up** a [`good first issue`](https://github.com/orgs/bubustack/issues?q=is%3Aopen+label%3A%22good+first+issue%22) or [`help wanted`](https://github.com/orgs/bubustack/issues?q=is%3Aopen+label%3A%22help+wanted%22)
- **Discuss** architecture and roadmap in [Discussions](https://github.com/orgs/bubustack/discussions)

Read the full [Contributing Guide](https://github.com/bubustack/.github/blob/main/CONTRIBUTING.md) to get started.

## Community

- [Documentation](https://bubustack.io/docs) — Guides, API reference, and architecture deep dives
- [GitHub Discussions](https://github.com/orgs/bubustack/discussions) — Questions, proposals, and community conversations
- [Security Policy](https://github.com/bubustack/.github/blob/main/SECURITY.md) — Responsible disclosure process
- [Code of Conduct](https://github.com/bubustack/.github/blob/main/CODE_OF_CONDUCT.md) — Contributor Covenant 3.0

---

<sub>Apache 2.0 Licensed. Built for platform engineers, AI/ML teams, and anyone who believes workflows belong in Git.</sub>
