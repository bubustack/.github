# Security policy

## Supported versions

We provide security updates for the latest released minor of every actively maintained component (bobrapet, bobravoz-grpc, bubu-sdk-go, and first-party Engrams/Impulses). Please ensure you are using a supported version to receive security patches. We generally support the latest minor and the immediately previous minor for each repo.

Supported Kubernetes versions: we aim to support N-2 of upstream stable releases across the operators and Engrams. For example, when Kubernetes 1.31 is current, we target 1.31, 1.30, 1.29. See each repository’s `config/` directory and CI matrices for exact compatibility guarantees.

## Reporting a vulnerability

The BubuStack Team and community take all security vulnerabilities seriously. We appreciate your efforts to responsibly disclose your findings, and will make every effort to acknowledge your contributions.

To report a security vulnerability, please use the GitHub Security Advisory feature in this repository:

- https://github.com/bubustack/.github/security/advisories/new

**Please do not report security vulnerabilities through public GitHub issues.**

When reporting a vulnerability, please provide the following information:

- **A clear description** of the vulnerability and its potential impact.
- **Steps to reproduce** the vulnerability, including any example code, scripts, or configurations.
- **The version(s) of the component (operator, transport, SDK, Engram, or Impulse)** affected.
- **Your contact information** for us to follow up with you.

## Disclosure process

1.  **Report**: You report the vulnerability through the GitHub Security Advisory feature.
2.  **Confirmation**: We will acknowledge your report within 48 hours.
3.  **Investigation**: We will investigate the vulnerability and determine its scope and impact. We may contact you for additional information during this phase.
4.  **Fix**: We will develop a patch for the vulnerability.
5.  **Disclosure**: We will create a security advisory, issue a CVE (if applicable), and release a new version with the patch. We will credit you for your discovery unless you prefer to remain anonymous.

We aim to resolve high severity vulnerabilities within 30 days, medium within 60 days, and low within 90 days, subject to complexity and scope. We'll keep you informed of progress.

We aim to resolve all vulnerabilities as quickly as possible. The timeline for a fix and disclosure will vary depending on the complexity and severity of the vulnerability. We will keep you informed of our progress throughout the process.
