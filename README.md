# 🏛️ BINST — Bitcoin Institutions Protocol

**Decentralized Institutional Design & Operations on Bitcoin**

> *Institutions are the main vehicle of power under the current world order. BINST aims to redesign them — transparently, immutably, and protected by Bitcoin's censorship resistance.*

---

## 🎯 Vision

Institutions shape every aspect of modern life — from governments and courts to corporations and financial systems. Yet their inner workings are opaque, their processes can be rigged, and their designs often serve dominant minorities at the expense of everyone else.

**BINST (Bitcoin Institutions)** is a protocol for creating, governing, and operating **on-chain institutions** anchored to Bitcoin — the most secure, decentralized, and censorship-resistant network in existence. By encoding institutional processes as smart contracts and linking them to formally defined institutions, BINST makes the design of power structures transparent, auditable, and tamper-proof.

Where traditional institutions rely on trust in people, BINST relies on **trust in math**.

---

## 💡 Added Value

| Problem Today | BINST Solution |
|---|---|
| Institutional processes are opaque and can be manipulated | Processes are deployed as **immutable smart contracts** with full on-chain audit trails |
| Institutional design is controlled by insiders | Institutions are **defined by constellations of smart contracts**, openly inspectable by anyone |
| DAOs rely on wealth-based voting (token staking) | BINST favors **meritocratic selection** — the most efficient processes win by adoption/usage (consensus), not capital |
| Privacy is sacrificed for transparency, or vice-versa | **Fully Homomorphic Encryption (FHE)** enables private institutional processes where needed, without sacrificing verifiability |
| Bitcoin's limited scripting prevents complex applications | **BitVM** enables Turing-complete verification on Bitcoin without consensus changes; **Covenants** will unlock trustless native contracts |
| Bridges between Bitcoin and programmable layers require trust in multisigs | **BitVM Bridge** (3rd gen) reduces trust to a single honest participant; **Covenant-based bridges** (4th gen) will be fully trustless |

---

## 🏗️ Architecture

BINST builds on two foundational layers:

### 1. Process Layer — Inherited from [DeBu Studio](https://github.com/diegobianqui/DeBu_studio)

DeBu Studio is a blockchain-based platform for designing, deploying, and executing standardized processes on-chain. BINST reuses and extends this framework:

- **Process Templates** — Immutable blueprints defining multi-step workflows (forms, approvals, payments, etc.) deployed as smart contracts
- **Process Instances** — Running executions of a template with full state tracking, actor recording, and timestamps
- **Process Deployer** — Factory contract maintaining a registry of all institutional processes
- **Browse & Discovery** — On-chain catalog of all deployed processes, filterable by institution, category, or address

### 2. Institution Layer — The BINST Addition

BINST adds the **institutional wrapper** that DeBu lacks:

- **Institution Contracts** — Smart contracts that formally define an institution: its mandate, governance rules, and the processes it hosts
- **Process-Institution Binding** — Every process deployed through the protocol is cryptographically linked to its parent institution
- **Institutional Registry** — On-chain registry of all institutions created via the protocol, enabling transparent discovery and accountability
- **Meritocratic Governance** — Process efficiency is measured by adoption and usage (consensus), not by staking or wealth-based voting

---

## 🔧 Core Technologies

### BitVM — Turing-Complete Verification on Bitcoin

[BitVM](https://bitvm.org/) enables arbitrary computation to be **verified** on Bitcoin without any changes to the network's consensus rules. Rather than executing computations on Bitcoin, they are merely verified — similarly to optimistic rollups. A prover makes a claim, and if false, anyone can perform a **fraud proof** and punish the prover.

- **BitVM2** — Implements a Groth16 SNARK verifier executable via the optimistic BitVM paradigm on Bitcoin. Enables trust-minimized Bitcoin bridges with ~1-of-N security (only one honest participant needed). On-chain cost: ~$15,000 per dispute; settlement: ~7.5 hours.
- **BitVM3** — Dramatically reduces costs and latency. On-chain fees drop below **$50**, settlement happens in **the next block**, and transactions are standard-sized. This makes BitVM practical for individual users, not just high-value bridge operations. Enables **trustless BTC vaults** for lending, borrowing, and DeFi without counterparty risk.

**Why this matters for BINST:** BitVM is the foundational technology that allows complex institutional logic to be verified against Bitcoin's security, enabling trust-minimized bridges to move assets between Bitcoin and the programmable layers where BINST institutions operate.

### Bitcoin Covenants — Spending Constraints for Smart Contracts

[Covenants](https://bitcoincovenants.com/) are hypothetical Bitcoin scripts that constrain how UTXOs can be spent — for example, restricting destination addresses or enforcing transaction templates. Key proposals include:

- **OP_CHECKTEMPLATEVERIFY (CTV / BIP-119)** — Commits to a specific transaction template, enabling congestion control, vaults, and payment trees
- **SIGHASH_ANYPREVOUT (APO / BIP-118)** — Allows signatures that don't commit to inputs, enabling Eltoo and advanced state channels
- **OP_CAT** — Concatenates stack elements, enabling Merkle tree verification, Schnorr signature tricks, and generalized covenants
- **OP_VAULT (BIP-345)** — Purpose-built for secure custody with clawback mechanisms

**Why this matters for BINST:** Native covenants are the prerequisite for **4th-generation trustless Bitcoin bridges** — where funds are managed by covenant-style smart contracts inheriting Bitcoin's native security model with zero external trust assumptions. This is BINST's end goal for maximum decentralization.

### Bridge Generations — The Path to Trustlessness

| Generation | Trust Model | Examples |
|---|---|---|
| **1st** — Centralized custodians | Single entity or fixed group controls funds | wBTC, MPC bridges |
| **2nd** — Distributed custodians | Random selection from a pool with staking penalties | tBTC (Keep Network) |
| **3rd** — BitVM smart contracts | Trust-minimized: only 1-of-N honest participant needed | BitVM Bridge (current) |
| **4th** — Covenant-based | **Fully trustless**: native Bitcoin script enforcement | Requires covenant soft fork (future) |

### SNARK Verification on Bitcoin

The [SNARK verifier in Bitcoin Script](https://bitvm.org/snark.html) enables zero-knowledge proof verification directly within Bitcoin's scripting environment. This uses Groth16 proofs over the BN254 curve, split into chunks that fit within Bitcoin's 4 MB block size limit. Combined with BitVM's optimistic protocol, this allows computations of up to **8–12 GB** to be verified on Bitcoin.

### Privacy — Fully Homomorphic Encryption (FHE)

Some institutional processes require confidentiality — personnel decisions, sealed-bid procurement, medical records, legal proceedings. BINST integrates **FHE** to allow computations on encrypted data without ever revealing the plaintext. Combined with ecash-style privacy layers (Fedimint, Cashu), BINST can serve institutions that need both transparency of structure and privacy of operations.

---

## 🗺️ Roadmap

### Phase 1 — Contribute & Build (Current)

> *Help develop the needed technologies by collaborating on open-source projects*

- [ ] Contribute to [BitVM](https://github.com/BitVM/BitVM) development (Rust, SNARK verifiers, bridge components)
- [ ] Participate in Bitcoin Core covenant discussions and review ([OP_CTV](https://github.com/bitcoin/bips/blob/master/bip-0119.mediawiki), [APO](https://anyprevout.xyz/), [OP_CAT](https://bitcoinops.org/en/topics/op_cat/))
- [ ] Evaluate and select the best Bitcoin L2/sidechain/rollup for initial deployment based on:
  - ZK proof support
  - SNARK validation capability
  - FHE integration potential
  - BitVM Alliance membership
- [ ] Adapt the [DeBu Studio](https://github.com/diegobianqui/DeBu_studio) smart contracts for the selected L2
- [ ] Design and implement the Institution Layer contracts

**L2 Candidates Under Investigation:**

| Project | Notes |
|---|---|
| [Alpen](https://x.com/AlpenLabs) | BitVM Alliance member; working on Glock (DV-SNARK for BitVM3) |
| [Babylon](https://x.com/babylonlabs_io) | BitVM Alliance member; pioneering BTC staking & trustless vaults |
| [Bitlayer](https://x.com/BitlayerLabs) | BitVM Alliance member; building the BitVM Bridge |
| [BOB](https://x.com/build_on_bob) | BitVM Alliance member; Bitcoin-Ethereum hybrid L2 |
| [Citrea](https://x.com/citrea_xyz) | BitVM Alliance member; ZK rollup on Bitcoin |
| [Element](https://x.com/element_labs42) | BitVM Alliance member |
| [Fiamma](https://x.com/fiamma_labs) | BitVM Alliance member; ZK verification infrastructure |
| [GOAT Network](https://www.goat.network/) | BitVM Alliance member |
| [{ ideal }](https://ideal.group/) | BitVM Alliance member |
| [ZeroSync](https://x.com/ZeroSync_) | BitVM Alliance member; nonprofit umbrella for BitVM development |

### Phase 2 — Deploy on Available L2 (Short-Mid Term)

> *Build the protocol on the best available rollup/sidechain/L2*

- [ ] Deploy Process Template and Instance contracts on selected L2
- [ ] Deploy Institution Registry and governance contracts
- [ ] Build frontend for institutional process design, deployment, and execution
- [ ] Integrate FHE for privacy-sensitive institutional processes
- [ ] Launch pilot institutions (e.g., transparent procurement, community governance, dispute resolution)
- [ ] Establish the meritocratic process selection mechanism (adoption-based ranking)

### Phase 3 — Evolve Toward Trustlessness (Mid-Long Term)

> *Move the protocol to newer versions as technologies become available*

- [ ] Migrate bridge infrastructure from BitVM2 to **BitVM3** (lower cost, faster settlement)
- [ ] Integrate **covenant-based 4th-generation bridges** once Bitcoin soft fork is activated
- [ ] Move critical institutional verification logic closer to Bitcoin L1
- [ ] Implement cross-institutional interoperability (institutions interacting through shared processes)
- [ ] Scale to support complex institutional ecosystems (federations of institutions, hierarchical governance)

---

## 🏛️ Use Cases

- **Public Administration** — Transparent permit applications, license renewals, civic processes with on-chain audit trails
- **Private Sector** — HR workflows, approval chains, procurement processes, compliance — all verifiable
- **Legal & Dispute Resolution** — Contract workflows, arbitration, compliance processes with immutable records
- **Finance** — Trust-minimized BTC lending, treasury management, budget approvals (enabled by BitVM3 vaults)
- **Community Governance** — DAOs reimagined: governance by process adoption rather than token wealth
- **Supply Chain** — Product tracking, quality checks, handoff procedures across institutional boundaries
- **Privacy-Sensitive Institutions** — Medical boards, sealed-bid procurement, personnel committees — using FHE for confidential operations

---

## 🤝 How to Contribute

BINST is an open-source project. We welcome contributions across multiple fronts:

1. **Bitcoin Core & Covenant Research** — Review and contribute to covenant proposals (CTV, APO, OP_CAT)
2. **BitVM Development** — Contribute to the [BitVM repository](https://github.com/BitVM/BitVM) (Rust)
3. **Protocol Design** — Help design the Institution Layer smart contracts and governance mechanisms
4. **L2 Evaluation** — Research and benchmark candidate L2s for BINST deployment
5. **Frontend Development** — Build the institutional process design and execution interface
6. **FHE Integration** — Research and implement privacy-preserving institutional computations

Join the [BitVM Telegram group](https://t.me/bitVM_chat) to connect with the broader BitVM community.

---

## 📚 Key References

| Topic | Resource |
|---|---|
| BitVM Overview | [bitvm.org](https://bitvm.org/) |
| BitVM Repository | [github.com/BitVM/BitVM](https://github.com/BitVM/BitVM) |
| BitVM Bridge (3rd Gen) | [Bitlayer article](https://blog.bitlayer.org/introducing_bitvm_bridge/) |
| BitVM3 Advances | [L2IV Research](https://l2ivresearch.substack.com/p/the-power-of-bitvm3) |
| Emulated vs Native Covenants | [ZK Security article](https://blog.zksecurity.xyz/posts/bitvm/) |
| Covenants Programmability | [HashKey Capital](https://medium.com/hashkey-capital-insights/covenants-programmability-of-bitcoin-0e646510b197) |
| Bitcoin Covenants Compilation | [bitcoincovenants.com](https://bitcoincovenants.com/) |
| Covenant PRs in Bitcoin Core | [GitHub search](https://github.com/search?q=repo%3Abitcoin%2Fbitcoin+covenants&type=pullrequests) |
| SNARK Verifier in Bitcoin Script | [bitvm.org/snark](https://bitvm.org/snark.html) |
| ZK Proofs on Bitcoin (Paper) | [ePrint 2025/1271](https://eprint.iacr.org/2025/1271.pdf) |
| Ecash & Bitcoin Privacy | [Bitcoin Magazine](https://bitcoinmagazine.com/technical/why-ecash-coffee-day-is-no-longer-just-a-celebration-but-a-call-to-action) |
| DeBu Studio (Base Protocol) | [github.com/diegobianqui/DeBu_studio](https://github.com/diegobianqui/DeBu_studio) |

---

## 📝 License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

<p align="center">
  <em>Decentralizing not only operations, but the very definition of institutions.</em><br/>
  <strong>Built on Bitcoin. Verified by math. Governed by consensus.</strong>
</p>
