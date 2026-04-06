# 🏛️ BINST — Bitcoin Institutions Protocol

**Bitcoin-Sovereign Institutional Design & Operations**

> *Your institution's identity lives on Bitcoin. Its authority is rooted in Bitcoin keys. Its activity is Bitcoin-verifiable.*

---

## 🎯 Vision

Institutions shape every aspect of modern life — from governments and courts to corporations and financial systems. Yet their inner workings are opaque, their processes can be rigged, and their designs often serve dominant minorities at the expense of everyone else.

**BINST (Bitcoin Institutions)** is a protocol for creating, governing, and operating **on-chain institutions** anchored to Bitcoin — the most secure, decentralized, and censorship-resistant network in existence.

BINST introduces a **Bitcoin-sovereign authority model**: every institution's identity is inscribed on Bitcoin L1, its membership is managed through Runes, and its operational logic runs on a portable processing layer. The Bitcoin key is the root of all authority — everything else is a delegate.

Where traditional institutions rely on trust in people, BINST relies on **trust in math**.

---

## 💡 The Problem We Solve

| Problem Today | BINST Solution |
|---|---|
| Institutional processes are opaque and manipulable | Processes run as **immutable on-chain contracts** with full audit trails |
| Institutional design is controlled by insiders | Institutions are **defined by open, inspectable contracts** — not by who you know |
| DAOs rely on wealth-based voting (token staking) | BINST favors **meritocratic selection** — the most efficient processes win by adoption |
| Institutional identity depends on centralized registries | Identity is **inscribed on Bitcoin L1** — sovereign, censorship-resistant, permanent |
| L2 lock-in: migrating chains means losing everything | The **Bitcoin key is the root of authority** — the processing layer is replaceable |
| Privacy vs. transparency is a false choice | **FHE** enables private institutional processes without sacrificing verifiability |
| Bitcoin bridges require trusting a custodian or operator | **BitVMX** minimizes trust today; **covenant soft forks** will make bridges fully trustless |

---

## 🏗️ Architecture — Three Layers of Sovereignty

BINST is structured around a clear hierarchy: Bitcoin L1 is the source of truth, a smart-contract layer handles execution, and a verification layer progressively closes every remaining trust gap.

```
┌──────────────────────────────────────────┐
│          BITCOIN L1  (Authority)         │
│  Institutional identity · Membership     │
│  Asset custody · Root of all authority   │
└──────────────────┬───────────────────────┘
                   │ anchors
┌──────────────────▼───────────────────────┐
│      PROCESSING LAYER  (Delegate)        │
│  Smart contracts · Workflow execution    │
│  Portable across any compatible L2       │
└──────────────────┬───────────────────────┘
                   │ verified by
┌──────────────────▼───────────────────────┐
│     VERIFICATION LAYER  (Trust Minimizer)│
│  BitVMX fraud proofs · Covenant vaults   │
│  ZK proofs · FHE (long term)             │
└──────────────────────────────────────────┘
```

**The key principle:** the Bitcoin key is permanent. The processing layer is a portable delegate — if a better L2 emerges, BINST migrates its contracts while the Bitcoin-anchored identity remains unchanged.

---

## 🔭 Long-Term Vision — Maximum Bitcoin Sovereignty

BINST's north star is an institution whose entire lifecycle — identity, membership, governance, asset custody, and process verification — is enforced by Bitcoin consensus, with zero trust in any third party.

### Sovereignty Stack

| Layer | Mechanism | Trust model |
|---|---|---|
| **Identity** | Ordinals inscriptions on Bitcoin L1 | Trustless — permanently anchored |
| **Membership & roles** | Runes tokens on Bitcoin L1 | Trustless — Bitcoin-native |
| **Asset custody** | Bitcoin tapscript vaults → covenant vaults | Trustless — consensus-enforced (covenant soft fork required) |
| **Execution** | L2 smart contracts (portable) | Delegated — operator trust, mitigated by ZK proofs |
| **Execution verification** | BitVMX fraud proofs on Bitcoin L1 | Trust-minimized — 1-of-N honest |
| **ZK proof verification** | BitVMX garbled-circuit verifier on Bitcoin | Trustless — on-chain math |
| **Privacy** | FHE on encrypted process data | Confidential without sacrificing verifiability |

### Bitcoin-Native Technologies

These are the building blocks that progressively move BINST toward full sovereignty:

**BitVMX** — optimistic computation verification on Bitcoin using fraud proofs and challenge-response protocols. No consensus changes required. BINST's Phase 4 verification layer is built around BitVMX and its ecosystem protocols: TOOP for trustless inscription transfer, ESSPI for Schnorr-signed program inputs, and FLEX for capital-efficient dispute bonds.

**Bitcoin Covenants** — proposed Bitcoin script extensions that let UTXOs constrain their own future spending, without trusted intermediaries. Several proposals are relevant to BINST:

| Proposal | What it enables for BINST |
|---|---|
| **CTV** (BIP-119) | Inscription vaults where the recovery path is enforced by consensus — no committee multi-sig needed |
| **OP_CAT** (BIP-347) | Recursive vault covenants, on-Script membership proofs, BitVMX setup simplification |
| **APO** (BIP-118) | Lightning-compatible governance microchannels for institutional microtransactions |
| **OP_VAULT model** (BIP-443 direction) | Trigger-delay-recover custody: a governance window to interrupt unauthorized inscription moves |

*All covenant proposals require a Bitcoin soft fork. BINST tracks them and will adopt whichever activates.*

**FHE** — fully homomorphic encryption for institutional processes that require confidentiality (personnel decisions, sealed-bid procurement, legal proceedings) without sacrificing on-chain verifiability.

---

## 🗺️ Roadmap

### Phase 1 — Pilot ✅ (Completed)
> *Prove the Bitcoin-sovereign institutional model works end-to-end*

See [Phase 1 details below](#-phase-1-pilot--what-was-built).

### Phase 2 — Harden the Pilot (Current)
> *Strengthen and expand the Bitcoin-native foundations*

- [ ] Deploy tapscript vault on Bitcoin testnet with real UTXO management
- [ ] Implement Runes-based membership and role tokens
- [ ] Build institutional discovery and browsing interface
- [ ] Expand Bitcoin state correlation across all protocol layers

### Phase 3 — Multi-Chain Presence & Usability (Short Term)
> *Make BINST usable by real institutions*

- [ ] Launch Runes-based membership system (issuance, transfer, revocation)
- [ ] Cross-chain identity sync via messaging protocols (read-only mirrors on other L2s)
- [ ] Web frontend for institutional design, deployment, and process execution
- [ ] On-chain institutional registry with discovery and meritocratic process ranking
- [ ] Launch pilot institutions (procurement, governance, dispute resolution)

### Phase 4 — BitVMX Verification (Mid Term)
> *Close the trust gap between L2 execution and Bitcoin L1*

- [ ] Integrate BitVMX fraud-proof verification for institutional state transitions
- [ ] Adopt TOOP for trustless cross-chain inscription transfers (no custodian)
- [ ] Adopt ESSPI for Schnorr-signed program inputs (leveraging existing BTC key binding)
- [ ] Capital-efficient dispute infrastructure via FLEX on-demand bonds
- [ ] Single-wallet UX with Schnorr-verified sessions

### Phase 5 — Covenant Migration & Full Sovereignty (Long Term)
> *Achieve maximum trustlessness as Bitcoin evolves*

- [ ] Replace committee multi-sig vault backstop with covenant-enforced recovery path
- [ ] On-Bitcoin ZK proof verification via BitVMX garbled-circuit verifier
- [ ] Trigger-delay-recover governance windows for inscription custody (OP_VAULT model)
- [ ] FHE integration for privacy-sensitive institutional processes
- [ ] Federated institutional ecosystems with hierarchical governance

---

## 🧭 Strategy

BINST follows a pragmatic three-horizon strategy:

- **Short term** — Prove the Bitcoin-sovereign model with the pilot. Contribute to open-source ecosystems (BitVMX, Fairgate protocols, Bitcoin covenants, L2 tooling).
- **Mid term** — Build on the best available L2, integrate BitVMX fraud-proof verification, and adopt TOOP + ESSPI as the inscription transfer and authorization primitives.
- **Long term** — Evolve as Bitcoin-native technologies mature (BitVMX garbled circuits, covenant soft forks, FHE), progressively eliminating every remaining trust assumption until BINST operates at maximum Bitcoin sovereignty.

---

## 🏛️ Use Cases

- **Public Administration** — Transparent permit applications, license renewals, civic processes with on-chain audit trails
- **Private Sector** — HR workflows, approval chains, procurement processes — all verifiable
- **Legal & Dispute Resolution** — Contract workflows, arbitration, compliance with immutable records
- **Finance** — Trust-minimized treasury management and budget approvals
- **Community Governance** — DAOs reimagined: governance by process adoption rather than token wealth
- **Supply Chain** — Product tracking and handoff procedures across institutional boundaries
- **Privacy-Sensitive Institutions** — Medical boards, sealed-bid procurement, personnel committees — using FHE for confidential operations

---

## 🚀 Phase 1 Pilot — What Was Built

The [BINST Pilot](https://github.com/Bitcoin-Institutions/binst-pilot) is the first working implementation of the Bitcoin-sovereign institutional model. It validates the core architecture with real deployments on Bitcoin testnet4 and Citrea testnet (Chain 5115).

### Components

**Smart Contracts (Citrea):** `Institution.sol`, `ProcessTemplate.sol`, `ProcessInstance.sol`, `BINSTDeployer.sol` — together defining an institution, its workflow blueprints, and running process executions.

**BINST Protocol (Rust, 79 tests):** Four crates for decoding `binst` metaprotocol inscriptions from Bitcoin witness data, parsing Ordinals envelopes, reading Citrea DA batch proofs, and scanning nodes for BINST state.

**Pilot Webapp (Rust/WASM, 66 tests):** Browser-based UI with dual-wallet support (UniSat, SafePal BTC, MetaMask, SafePal EVM), L1 inscription stack for PSBT review, and L2 EVM queue for per-call approval.

**`binst` Metaprotocol Schema:** Formal JSON schema for inscription-based institution, template, instance, and step-execution entities.

### Key Achievement

The first BINST inscription was created on Bitcoin testnet4 — an institutional identity permanently anchored to Bitcoin L1. This proves the core thesis: **institutional identity can live on Bitcoin, with L2 as a portable processing delegate.**

---

## 🤝 How to Contribute

1. **Pilot Development** — Extend the [BINST Pilot](https://github.com/Bitcoin-Institutions/binst-pilot) (Solidity, Rust, TypeScript)
2. **Protocol Design** — Help design governance mechanisms and the meritocratic selection model
3. **Bitcoin Covenant Research** — Review and contribute to covenant proposals (CTV, APO, OP_CAT)
4. **BitVM Development** — Contribute to the [BitVMX](https://bitvmx.org/) and [BitVM](https://github.com/BitVM/BitVM) ecosystems
5. **Frontend Development** — Build the institutional process design and execution interface
6. **FHE Integration** — Research privacy-preserving institutional computations

---

## 📚 Key References

| Topic | Resource |
|---|---|
| **BINST Pilot** | [github.com/Bitcoin-Institutions/binst-pilot](https://github.com/Bitcoin-Institutions/binst-pilot) |
| BitVMX | [bitvmx.org](https://bitvmx.org/) |
| BitVM Repository | [github.com/BitVM/BitVM](https://github.com/BitVM/BitVM) |
| Citrea (Current L2) | [citrea.xyz](https://citrea.xyz/) |
| Bitcoin Covenants | [bitcoincovenants.com](https://bitcoincovenants.com/) |
| Ordinals Protocol | [docs.ordinals.com](https://docs.ordinals.com/) |
| Runes Protocol | [docs.ordinals.com/runes](https://docs.ordinals.com/runes/) |
| ZK Proofs on Bitcoin | [ePrint 2025/1271](https://eprint.iacr.org/2025/1271.pdf) |

---

## 📝 License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

<p align="center">
  <em>Decentralizing not only operations, but the very definition of institutions.</em><br/>
  <strong>Inscribed on Bitcoin. Processed on L2. Verified by math. Governed by consensus.</strong>
</p>
