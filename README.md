# 🏛️ BINST — Bitcoin Institutions Protocol

**Bitcoin-Sovereign Institutional Design & Operations**

> *Your institution's identity lives on Bitcoin. Its authority is rooted in Bitcoin keys. Everything else is a delegate.*

---

## 🎯 Vision

Institutions shape every aspect of modern life — from governments and courts to corporations and financial systems. Yet their inner workings are opaque, their processes can be rigged, and their designs often serve dominant minorities at the expense of everyone else.

**BINST (Bitcoin Institutions)** is a protocol for creating, governing, and operating **on-chain institutions** anchored to Bitcoin — the most secure, decentralized, and censorship-resistant network in existence.

BINST introduces a **Bitcoin-sovereign authority model**: every institution's identity is inscribed on Bitcoin L1 using Ordinals, its membership is managed through Runes, and its operational logic runs on a portable L2 processing layer. The Bitcoin key is the root of all authority — L2 contracts are delegates, not owners.

Where traditional institutions rely on trust in people, BINST relies on **trust in math**.

---

## 💡 Added Value

| Problem Today | BINST Solution |
|---|---|
| Institutional processes are opaque and manipulable | Processes are deployed as **immutable smart contracts** with full on-chain audit trails |
| Institutional design is controlled by insiders | Institutions are **defined by constellations of smart contracts**, openly inspectable by anyone |
| DAOs rely on wealth-based voting (token staking) | BINST favors **meritocratic selection** — the most efficient processes win by adoption, not capital |
| Institutional identity depends on centralized registries | Identity is **inscribed on Bitcoin L1** — sovereign, censorship-resistant, and permanent |
| L2 lock-in: migrating between chains means losing everything | The **Bitcoin key is the root of authority** — L2 contracts are portable delegates, not the source of truth |
| Privacy is sacrificed for transparency, or vice-versa | **FHE** enables private institutional processes without sacrificing verifiability |
| Bitcoin's limited scripting prevents complex applications | **BitVM** enables Turing-complete verification on Bitcoin; **Covenants** will unlock trustless native contracts |
| Bridges between Bitcoin and programmable layers require trust | **BitVM Bridge** (3rd gen) reduces trust to 1-of-N; **Covenant bridges** (4th gen) will be fully trustless |

---

## 🏗️ Architecture — The Bitcoin-Sovereign Model

BINST's architecture is built on a three-layer sovereignty model, proven by the Phase 1 pilot:

```
┌─────────────────────────────────────────────────┐
│              BITCOIN L1 (Authority)              │
│                                                  │
│  Ordinals Inscriptions ─── Institutional Identity│
│  Runes Tokens ──────────── Membership & Roles    │
│  Tapscript Vault ────────── UTXO Safety Layer    │
│  BTC Key ────────────────── Root of All Authority│
└──────────────────────┬──────────────────────────┘
                       │ anchors
┌──────────────────────▼──────────────────────────┐
│           L2 PROCESSING LAYER (Delegate)         │
│           Currently: Citrea (Chain 5115)         │
│                                                  │
│  Institution.sol ────── On-chain institution def │
│  ProcessTemplate.sol ── Immutable workflow logic │
│  ProcessInstance.sol ── Running execution + state│
│  BINSTDeployer.sol ──── Factory & registry       │
└──────────────────────┬──────────────────────────┘
                       │ future
┌──────────────────────▼──────────────────────────┐
│         VERIFICATION LAYER (Future)              │
│                                                  │
│  BitVM ──────── Fraud-proof verification on BTC  │
│  BitVMX ─────── RISC-V execution verification    │
│  Covenants ──── Native BTC spending constraints  │
│  SNARK ──────── ZK proof verification on BTC     │
└─────────────────────────────────────────────────┘
```

### Authority Model

| Layer | Technology | Role | Status |
|---|---|---|---|
| **Identity** | Ordinals Inscriptions | Permanent institutional identity on Bitcoin | ✅ Proven |
| **Membership** | Runes Protocol | Token-based roles and membership | 🔜 Phase 3 |
| **Safety** | Tapscript Vault | UTXO protection with timelocked recovery | 🔜 Phase 2 |
| **Processing** | L2 Smart Contracts | Operational logic execution (currently Citrea) | ✅ Proven |
| **Verification** | BitVM / Covenants | Trust-minimized verification on Bitcoin L1 | 🔮 Phase 5+ |

### Key Principle: L2 Portability & Cross-Chain Presence

The Bitcoin key is the **root of all authority**. L2 contracts are delegates — they can be redeployed on any EVM chain without losing institutional identity. If a better L2 emerges, BINST migrates its processing layer while the Bitcoin-anchored identity remains unchanged.

Beyond portability, BINST supports **multi-chain presence** via a dual-channel sync model:

- **LayerZero V2** syncs identity and membership across L2s in real-time (Citrea endpoint live: Chain ID 4114)
- **Bitcoin DA** provides trustless execution state verification via ZK batch proofs

Mirror contracts on other L2s (BOB, Rootstock, etc.) provide read-only identity and membership verification. Process execution stays on the home chain — **single-writer per process instance** prevents concurrent mutation conflicts across chains.

---

## 🚀 Phase 1 — The Pilot (Completed)

The [BINST Pilot](https://github.com/Bitcoin-Institutions/binst-pilot) is the first working implementation of the Bitcoin-sovereign institutional model. It validates the core architecture with real deployments on Bitcoin testnet4 and Citrea testnet.

### What Was Built

**4 Solidity Contracts** (Citrea Testnet — Chain 5115, Shanghai EVM, Solidity 0.8.24):

| Contract | Purpose |
|---|---|
| `Institution.sol` | Defines an institution with BTC anchoring (taproot address, inscription ID) |
| `ProcessTemplate.sol` | Immutable multi-step workflow blueprints |
| `ProcessInstance.sol` | Running process executions with full state tracking |
| `BINSTDeployer.sol` | Factory & registry for all institutional components |

**4 Rust Crates** (Taproot Reader — 28 tests passing):

| Crate | Purpose |
|---|---|
| `binst-decoder` | Decodes BINST metaprotocol inscriptions from witness data |
| `binst-inscription` | Creates and manages inscription envelopes |
| `citrea-decoder` | Reads Citrea L2 state and correlates with BTC anchors |
| `cli` | Command-line tool for scanning and decoding inscriptions |

**6 TypeScript Scripts**:

| Script | Purpose |
|---|---|
| `demo-flow.ts` | End-to-end institutional lifecycle demonstration |
| `inscribe-binst.ts` | Creates BINST inscriptions on Bitcoin testnet4 |
| `bitcoin-awareness.ts` | L2 contracts reading Bitcoin state via Citrea's light client |
| `finality-monitor.ts` | Monitors Bitcoin finality for L2 transactions |
| `taproot-vault.ts` | Tapscript vault with timelocked recovery paths |
| `test-protocol.ts` | Full protocol deployment and testing |

**`binst` Metaprotocol Schema**: A formal JSON schema for the `binst` inscription protocol, with entity types for institutions, process templates, instances, and step executions.

### Key Achievement

The first BINST inscription was created on Bitcoin testnet4 — an institutional identity permanently anchored to Bitcoin L1. This proves the core thesis: **institutional identity can live on Bitcoin, with L2 as a portable processing delegate.**

### Origin

BINST builds upon [DeBu Studio](https://github.com/diegobianqui/DeBu_studio), a blockchain-based platform for designing and executing standardized processes on-chain, presented at the ETHGlobal 2025 hackathon in Buenos Aires. BINST extends DeBu's process framework with the institutional wrapper and Bitcoin-sovereign authority model.

---

## 🔧 Core Technologies

### BitVM — Beyond Bridges: A Turing-Complete Paradigm for Bitcoin

[BitVM](https://bitvm.org/) is more than a bridge technology — it represents a broader paradigm for Turing-complete computation verification on Bitcoin without consensus changes. Created by [ZeroSync](https://zerosync.org/) and supported by the [BitVM Alliance](https://bitvm.org/#about-bitvm-alliance), it encompasses:

- **BitVM2** — Groth16 SNARK verifier on Bitcoin via optimistic fraud proofs. Enables trust-minimized bridges with 1-of-N security. On-chain cost: ~$15,000 per dispute; settlement: ~7.5 hours.
- **BitVM3** — Dramatically reduces costs (<$50) and latency (next block settlement). Enables trustless BTC vaults for lending, borrowing, and DeFi.
- **Stateful Contracts** — Using Lamport/Winternitz one-time signatures, BitVM enables contracts that maintain state across Bitcoin transactions — a building block for on-chain institutional logic.
- **BitVMX** — RISC-V program execution verification on Bitcoin. Any program compiled to RISC-V can be optimistically verified on L1.
- **Tree++** — A future high-level scripting language for writing Bitcoin smart contracts that compile to BitVM circuits.

**Why this matters for BINST:** BitVM is a complementary verification layer. BINST uses inscriptions for identity and L2 for processing *today*. In the future, BitVM can verify that L2 state transitions are correct — adding a fraud-proof layer between institutional operations and Bitcoin's security. BitVMX could eventually verify entire institutional process executions against Bitcoin L1.

### Bitcoin Covenants — Native Spending Constraints

[Covenants](https://bitcoincovenants.com/) are proposed Bitcoin script extensions that constrain how UTXOs can be spent:

- **OP_CHECKTEMPLATEVERIFY (CTV / BIP-119)** — Transaction template commitments for vaults, payment trees, congestion control
- **SIGHASH_ANYPREVOUT (APO / BIP-118)** — Input-agnostic signatures for Eltoo and advanced state channels
- **OP_CAT** — Stack concatenation enabling Merkle verification, Schnorr tricks, and generalized covenants
- **OP_VAULT (BIP-345)** — Purpose-built secure custody with clawback mechanisms

**Why this matters for BINST:** Covenants are the prerequisite for **4th-generation fully trustless Bitcoin bridges** and enhanced tapscript vaults. They represent BINST's long-term path to maximum sovereignty.

### Bridge Generations — The Path to Trustlessness

| Generation | Trust Model | Examples |
|---|---|---|
| **1st** — Centralized | Single entity controls funds | wBTC, MPC bridges |
| **2nd** — Distributed | Random selection with staking penalties | tBTC (Keep Network) |
| **3rd** — BitVM | 1-of-N honest participant needed | Citrea Clementine Bridge (current) |
| **4th** — Covenant-based | **Fully trustless**: native BTC script enforcement | Requires covenant soft fork (future) |

### SNARK Verification on Bitcoin

The [SNARK verifier in Bitcoin Script](https://bitvm.org/snark.html) enables zero-knowledge proof verification within Bitcoin's scripting environment using Groth16 proofs over BN254, split into chunks fitting Bitcoin's 4 MB limit. Combined with BitVM's optimistic protocol, computations of up to **8–12 GB** can be verified on Bitcoin.

### Privacy — Fully Homomorphic Encryption (FHE)

Some institutional processes require confidentiality — personnel decisions, sealed-bid procurement, medical records, legal proceedings. BINST plans to integrate **FHE** to allow computations on encrypted data without revealing plaintext. Combined with ecash privacy layers (Fedimint, Cashu), BINST can serve institutions needing both structural transparency and operational privacy.

---

## 🗺️ Roadmap

### Phase 1 — Pilot ✅ (Completed)

> *Prove the Bitcoin-sovereign institutional model with a working implementation*

- [x] Design and implement the Bitcoin-sovereign authority model
- [x] Deploy 4 institutional smart contracts on Citrea testnet (Chain 5115)
- [x] Build Taproot Reader (4 Rust crates, 28 tests) for decoding `binst` inscriptions
- [x] Create the `binst` metaprotocol inscription schema
- [x] Inscribe the first BINST institutional identity on Bitcoin testnet4
- [x] Implement Bitcoin-awareness in L2 contracts via Citrea's Bitcoin Light Client
- [x] Design tapscript vault with timelocked recovery paths
- [x] Build end-to-end demo flow and protocol test scripts

### Phase 2 — Expand the Pilot (Current)

> *Harden the protocol and add Bitcoin-native features*

- [ ] Deploy tapscript vault on testnet4 with real UTXO management
- [ ] Implement Runes-based membership and role tokens
- [ ] Build institutional discovery and browsing interface
- [ ] Add Bitcoin finality tracking to L2 contract state
- [ ] Expand Taproot Reader with full Citrea state correlation
- [ ] Comprehensive test suite across all layers

### Phase 3 — Runes, Cross-Chain Sync & Frontend (Short Term)

> *Make the protocol usable by real institutions across multiple L2s*

- [ ] Launch Runes-based membership system (issuance, transfer, revocation)
- [ ] Implement cross-chain state sync via LayerZero V2 (`BINSTRelay.sol` OApp + `InstitutionMirror.sol` read-only mirrors)
- [ ] Build web frontend for institutional design, deployment, and process execution
- [ ] Implement on-chain institutional registry with search and filtering
- [ ] Establish meritocratic process selection (adoption-based ranking)
- [ ] Batch Bitcoin-side operations (inscribe + etch in fewer transactions)
- [ ] Launch pilot institutions (transparent procurement, community governance, dispute resolution)

### Phase 4 — BitVM Verification & Unified Wallet (Mid Term)

> *Add trust-minimized verification and streamlined UX*

- [ ] Integrate BitVM fraud-proof verification for critical institutional state transitions
- [ ] Explore BitVMX for verifying process execution proofs on Bitcoin L1
- [ ] Migrate bridge infrastructure from BitVM2 to BitVM3 (lower cost, faster settlement)
- [ ] Implement cross-institutional interoperability (shared processes across institutions)
- [ ] Single-wallet UX via Schnorr-verified sessions and account abstraction
- [ ] Cross-chain process state verification via Bitcoin DA batch proof reads

### Phase 5 — Covenant Migration & Full Sovereignty (Long Term)

> *Achieve maximum trustlessness as Bitcoin evolves*

- [ ] Integrate covenant-based 4th-generation trustless bridges once soft fork activates
- [ ] Move critical institutional verification logic to Bitcoin L1 via covenants
- [ ] Implement FHE for privacy-sensitive institutional processes
- [ ] Scale to complex institutional ecosystems (federations, hierarchical governance)
- [ ] Evaluate Tree++ for writing institutional logic that compiles to BitVM circuits

---

## 🧭 Strategy

BINST follows a pragmatic three-horizon strategy:

- **Short term** — Help develop the needed technologies by collaborating on open-source projects (BitVM, covenants, L2 ecosystems)
- **Mid term** — Build the protocol on the best available L2, proving the model with real institutional use cases
- **Long term** — Evolve to newer versions as Bitcoin-native technologies mature (BitVM3, covenants, FHE), progressively moving toward full Bitcoin sovereignty

---

## 🏛️ Use Cases

- **Public Administration** — Transparent permit applications, license renewals, civic processes with on-chain audit trails
- **Private Sector** — HR workflows, approval chains, procurement processes, compliance — all verifiable
- **Legal & Dispute Resolution** — Contract workflows, arbitration, compliance with immutable records
- **Finance** — Trust-minimized BTC lending, treasury management, budget approvals (enabled by BitVM3 vaults)
- **Community Governance** — DAOs reimagined: governance by process adoption rather than token wealth
- **Supply Chain** — Product tracking, quality checks, handoff procedures across institutional boundaries
- **Privacy-Sensitive Institutions** — Medical boards, sealed-bid procurement, personnel committees — using FHE for confidential operations

---

## 🤝 How to Contribute

BINST is an open-source project. We welcome contributions across multiple fronts:

1. **Pilot Development** — Extend the [BINST Pilot](https://github.com/Bitcoin-Institutions/binst-pilot) (Solidity, Rust, TypeScript)
2. **Bitcoin Core & Covenant Research** — Review and contribute to covenant proposals (CTV, APO, OP_CAT)
3. **BitVM Development** — Contribute to the [BitVM repository](https://github.com/BitVM/BitVM) (Rust)
4. **Protocol Design** — Help design governance mechanisms and the meritocratic selection model
5. **Frontend Development** — Build the institutional process design and execution interface
6. **Inscription Tooling** — Improve the Taproot Reader and `binst` metaprotocol tooling
7. **FHE Integration** — Research privacy-preserving institutional computations

---

## 📚 Key References

| Topic | Resource |
|---|---|
| **BINST Pilot** | [github.com/Bitcoin-Institutions/binst-pilot](https://github.com/Bitcoin-Institutions/binst-pilot) |
| **DeBu Studio (Origin)** | [github.com/diegobianqui/DeBu_studio](https://github.com/diegobianqui/DeBu_studio) |
| BitVM Overview | [bitvm.org](https://bitvm.org/) |
| BitVM Repository | [github.com/BitVM/BitVM](https://github.com/BitVM/BitVM) |
| BitVMX | [bitvmx.org](https://bitvmx.org/) |
| Awesome BitVM | [github.com/pankajjagtappp/awesome-bitvm](https://github.com/pankajjagtappp/awesome-bitvm) |
| ZeroSync | [zerosync.org](https://zerosync.org/) |
| BitVM3 Advances | [L2IV Research](https://l2ivresearch.substack.com/p/the-power-of-bitvm3) |
| Citrea (Current L2) | [citrea.xyz](https://citrea.xyz/) |
| LayerZero V2 (Cross-Chain) | [layerzero.network](https://layerzero.network/) |
| Bitcoin Covenants | [bitcoincovenants.com](https://bitcoincovenants.com/) |
| SNARK Verifier on Bitcoin | [bitvm.org/snark](https://bitvm.org/snark.html) |
| ZK Proofs on Bitcoin | [ePrint 2025/1271](https://eprint.iacr.org/2025/1271.pdf) |
| Ordinals Protocol | [docs.ordinals.com](https://docs.ordinals.com/) |
| Runes Protocol | [docs.ordinals.com/runes](https://docs.ordinals.com/runes/) |

---

## 📝 License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

<p align="center">
  <em>Decentralizing not only operations, but the very definition of institutions.</em><br/>
  <strong>Inscribed on Bitcoin. Processed on L2. Verified by math. Governed by consensus.</strong>
</p>
