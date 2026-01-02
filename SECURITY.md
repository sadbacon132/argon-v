# Security Policy

## Responsible Disclosure

ARGON-V is an adversarial-resistant protocol, and security and integrity are treated as first-class design goals. We welcome and appreciate responsible disclosure from security researchers, protocol analysts, and systems engineers.

At this stage, ARGON-V is an early protocol and systems design (v0.1). Security reports may concern logical flaws, economic attacks, invariant violations, or weaknesses in the formal specification, in addition to issues in any reference implementations.

---

## Reporting a Vulnerability

If you identify a potential security issue in the ARGON-V protocol specification or its reference implementations, please do **not** use the public issue tracker.

Instead, report the issue privately to the maintainer:

**Reporting channel:** dante@youroasis.ai

Please include, where applicable:

- A clear description of the issue or vulnerability  
- The affected protocol stage (e.g., Stage III: Semantic Intersection)  
- A proof-of-concept, attack sketch, or theoretical walkthrough  
- Potential impact on correctness, security, or economic guarantees  
- Suggested mitigations or design alternatives (if available)

---

## Scope of Security Review

During the current **Pre-Birth / Specification Drafting** phase, we are particularly interested in reports covering:

- **Logical flaws** — Bypasses or inconsistencies in the five-stage pipeline  
- **Economic attacks** — Techniques that reduce the cost of forgery without violating semantic coherence  
- **Protocol invariants** — Contradictions or weaknesses in the formal specification (`SPEC.md`)  
- **Adversarial assumptions** — Gaps or unrealistic constraints in the threat model  

---

## Our Commitment

If you follow the responsible disclosure process outlined above, we commit to:

- Acknowledging receipt of your report within **48–72 hours**  
- Working with you to understand, validate, and reproduce the issue  
- Crediting you in security advisories or specification revisions, where appropriate  

---

## Non-Disclosure Policy

We ask that reported issues are not disclosed publicly until they have been addressed in the specification or resolved in a subsequent protocol revision. This policy is intended to support responsible discussion during early development and does not preclude future public disclosure once the protocol reaches a stable release.
