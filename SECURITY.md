# Security Policy

## Responsible Disclosure

As an adversarial-resistant protocol, ARGON-V takes security and integrity with the utmost seriousness. We appreciate the efforts of security researchers in identifying vulnerabilities and practicing responsible disclosure.

## Reporting a Vulnerability

If you discover a security vulnerability within the ARGON-V protocol specification or its reference implementations, please do not use the public issue tracker. Instead, send a detailed report to the maintainer.

**Current Reporting Channel:** [dante@youroasis.ai](mailto:dante@youroasis.ai)

Please include the following in your report:
- A description of the vulnerability.
- The specific stage of the pipeline affected (e.g., Stage III: Consistency).
- A proof-of-concept (PoC) or theoretical walkthrough of the exploit.
- Potential impact and suggested mitigations.

## Scope

During the current **Pre-Birth/Drafting** phase, we are specifically looking for feedback on:
- **Logical Flaws**: Bypasses in the five-stage pipeline logic.
- **Economic Attacks**: Methods to lower the cost of forgery without breaking semantic coherence.
- **Protocol Invariants**: Contradictions in the formal specification (`SPEC.md`).

## Our Commitment

If you follow these guidelines, we commit to:
- Acknowledging receipt of your report within 48-72 hours.
- Working with you to understand and validate the issue.
- Providing credit in our security advisories once the issue is resolved.

## Non-Disclosure Policy

We ask that you do not disclose any vulnerability publicly until a fix has been developed and deployed, or until the protocol has reached a stable version 1.0 release.
