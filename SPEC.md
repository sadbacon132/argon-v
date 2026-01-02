# ARGON-V Protocol Specification (v0.1-draft)

## 1. Introduction
The ARGON-V protocol defines a method for a Verifier ($V$) to obtain a high-confidence attestation of state $\sigma$ from a third-party Platform (hereafter referred to as the **Source** $\mathcal{S}$) via an untrusted Prover $\mathcal{A}$ (the adversarial client). The protocol operates under the assumption that $\mathcal{A}$ has full control over the local execution environment and may attempt to present a forged state.

## 2. Protocol Invariants
For any attestation to be considered valid, it must satisfy the following invariants:

1.  **Freshness**: The observation must be cryptographically bound to an ephemeral, server-issued nonce $\eta$.
2.  **Coherence**: The set of extracted facts $F = \{f_1, f_2, ..., f_k\}$ across $k$ surfaces must maintain logical consistency. Coherence is evaluated against verifier-defined semantic constraints $\mathcal{C}$, which are necessarily incomplete and platform-specific.
3.  **Immutability**: Once an observation is canonicalized, its Merkle root $R$ must be signed by $V$ to prevent post-facto tampering.

## 3. The Five-Stage Pipeline

### Stage I: Challenge (Temporal Binding)
The Verifier issues a single-use, high-entropy nonce $\eta$. This nonce must be embedded into the observation environment to prove the observation occurred *after* $\eta$ was issued and within the validity window $\Delta t$.

### Stage II: Observation (Multi-Surface Capture)
The Prover $\mathcal{A}$ captures $k$ independent surfaces from the Source $\mathcal{S}$. Each surface $s_i \in \{s_1, ..., s_k\}$ contributes to the total evidence pool.

### Stage III: Consistency (Semantic Validation)
The system evaluates the captured surfaces for cross-surface invariants. If surface $s_1$ represents a summary and $s_2$ represents a detailed ledger, the protocol enforces that $s_1 \equiv s_2$ according to the verifier-defined constraints $\mathcal{C}$.



### Stage IV: Canonicalization (Deterministic Mapping)
Raw captured data is stripped of non-deterministic artifacts (e.g., timestamps, session IDs) and mapped into a strictly typed schema. This ensures that equivalent platform states deterministically map to identical cryptographic representations.

### Stage V: Verification (Finality)
The canonical state is inserted into a Merkle-based accumulator. The Verifier signs the Merkle root $R$, issuing a "Verifiable Attestation" that can be audited by third parties—provided they trust $V$’s public key and the constraint set $\mathcal{C}$—without re-running the extraction pipeline.

## 4. Error States and Termination
If any invariant is violated during Stages I-III, the protocol must terminate immediately with a `NULL_COMMITMENT`. The protocol prioritizes **Safety** (preventing false positives) over **Liveness** (guaranteeing a result).
