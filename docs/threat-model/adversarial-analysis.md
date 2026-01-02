# Adversarial Analysis

## 1. Adversary Definition
The ARGON-V protocol assumes a **Sophisticated Rational Adversary** ($\mathcal{A}$). $\mathcal{A}$ has complete control over the client-side execution environment (the Prover) and is motivated by the utility $U$ of a successful forgery.

### 1.1 Adversarial Capabilities
* **Runtime Manipulation**: $\mathcal{A}$ can pause, modify, or replay JavaScript execution.
* **DOM Injection**: $\mathcal{A}$ can inject or hide elements within the Source ($\mathcal{S}$) to mimic a valid state.
* **Network Interception**: $\mathcal{A}$ can spoof API responses from $\mathcal{S}$ before they reach the observation agent.

## 2. The Economic Security Model
The ARGON-V protocol operates on the principle of **Deterministic Adversarial Friction**. This refers to the predictable increase in coordination cost imposed on an adversary as the number of required coherent observations $k$ grows. While the protocol acknowledges the inherent mutability of client-side runtimes, it enforces a security threshold where the cost of a coordinated forgery is mathematically decoupled from the ease of local manipulation.

Security is maintained via **Economic Exhaustion**:

$$C(\text{forgery}) > U(\text{forgery})$$

> **Security Invariant**: The cost ($C$) required to maintain a logically consistent state across $k$ surfaces must strictly exceed the utility ($U$) derived from the forged attestation.

By requiring $k$ independent surfaces to maintain semantic coherence under a server-issued challenge $\eta$, the protocol transforms a low-cost data injection attack into a high-complexity coordination problem. Independent surfaces are defined as observations that cannot be trivially derived from a single DOM mutation or API interception without maintaining cross-surface consistency.

## 3. Attack Vectors & Mitigations

### 3.1 The "Single Surface" Spoof
**Attack**: $\mathcal{A}$ modifies the HTML of a single page to show a false balance or status.  
**Mitigation**: **Multi-Surface Coherence ($k > 1$)**. The protocol requires $k$ independent surfaces. $\mathcal{A}$ must now coordinate the forgery across multiple URLs or UI states, exponentially increasing the complexity of the script required to maintain the lie.

### 3.2 Temporal Replay
**Attack**: $\mathcal{A}$ records a valid state from the past and attempts to re-submit it.  
**Mitigation**: **Ephemeral Nonce ($\eta$)**. The observation is cryptographically bound to a unique, time-sensitive challenge $\eta$. A captured state from $T_{-1}$ cannot satisfy the challenge for $T_{0}$ within the window $\Delta t$.

### 3.3 Semantic Dissonance
**Attack**: $\mathcal{A}$ fakes data that looks structurally correct but is logically impossible.  
**Mitigation**: **Constraint Set ($\mathcal{C}$)**. The Verifier enforces platform-specific invariants (e.g., "The sum of the ledger must equal the displayed balance"). 

## 4. Residual Risk & Scope
The protocol remains vulnerable to **Platform-Level Corruption**, where the Source $\mathcal{S}$ itself provides false data. ARGON-V makes no claims about detecting misinformation originating from a compromised or malicious platform; it verifies observation fidelity, not platform honesty. The protocol is designed to verify that "The Platform said X," not necessarily that "X is the ultimate truth of the universe."
