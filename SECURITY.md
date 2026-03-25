# Security policy

## Supported versions

We prioritize security fixes for actively maintained components across the organization. As a general rule, we target the latest released minor and the immediately previous minor of core maintained repositories.

For Kubernetes-targeted components, we aim for N-2 upstream stable releases when feasible. Check each repository's release notes, configuration, and CI matrix for the exact compatibility guarantee.

## Reporting a vulnerability

The BubuStack Team and community take all security vulnerabilities seriously. We appreciate your efforts to responsibly disclose your findings, and will make every effort to acknowledge your contributions.

If you are unsure which repository is affected, please use the GitHub Security Advisory feature in this repository:

- https://github.com/bubustack/.github/security/advisories/new

If you already know the affected repository and it supports private advisories, you may report there instead.

**Please do not report security vulnerabilities through public GitHub issues.**

When reporting a vulnerability, please provide the following information:

- **A clear description** of the vulnerability and its potential impact.
- **Steps to reproduce** the vulnerability, including any example code, scripts, or configurations.
- **The affected component(s) and version(s)**.
- **Kubernetes, cloud, or runtime context** if it matters to the issue.
- **Your contact information** for us to follow up with you.

## Disclosure process

1. **Report**: You report the issue through a private GitHub Security Advisory.
2. **Review**: We review the report on a best-effort basis and may ask for more information.
3. **Coordination**: We determine the affected repository or repositories and coordinate remediation with the relevant maintainers.
4. **Fix**: We develop and validate a patch or mitigation.
5. **Disclosure**: When a fix is ready, we publish the advisory and release notes, and credit you unless you prefer to remain anonymous.

We do not currently offer formal security response SLAs. Acknowledgement and remediation timelines depend on severity, scope, and maintainer availability, but we will respond as quickly as we can.
