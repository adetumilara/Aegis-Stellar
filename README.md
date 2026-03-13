# Aegis Stellar: Decentralized Smart Contract Insurance

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Stellar](https://img.shields.io/badge/Stellar-Soroban-14B8A6)](https://soroban.stellar.org)
[![Status](https://img.shields.io/badge/status-Active-4F46E5)](https://testnet.stellar.org)

Aegis Stellar is a mutual insurance protocol built on Soroban that provides a decentralized safety net for the Stellar ecosystem. It allows users and developers to hedge against smart contract vulnerabilities, logic failures, or protocol hacks through a community-driven risk pooling mechanism.

---

## 🌟 Overview

As the Soroban ecosystem grows, so does the complexity of DeFi protocols. Aegis Stellar decentralizes risk by pooling capital from "Risk Underwriters" to provide coverage for "Policy Holders." If a covered contract is exploited, the pool compensates the victims, ensuring the ecosystem remains resilient.

### The Mission

Our mission is to make the Stellar DeFi ecosystem more secure and trustworthy by providing reliable insurance coverage for smart contracts. We believe that insurance is a critical piece of DeFi infrastructure that protects users and encourages broader adoption.

### Why Aegis Stellar?

- **Decentralized**: No central authority; all decisions are made through community governance
- **Transparent**: All claims, premiums, and payouts are verifiable on-chain
- **Automated**: Smart contracts handle premium calculations and claim payouts
- **Community-Driven**: Aegis token holders govern the protocol

---

## 🚀 Features

### 1. Risk Pools (Underwriting)

- **Liquidity Provision**: Users deposit $USDC$ or $XLM$ into specific risk pools (e.g., "AMM Pool" or "Lending Pool") to earn premiums
- **Staking Rewards**: Underwriters earn a percentage of all policy premiums paid by users seeking coverage
- **Pool Diversification**: Multiple specialized pools for different protocol types
- **Auto-Compounding**: Rewards are automatically reinvested

### 2. Dynamic Policy Minting

- **Custom Coverage**: Users can purchase "Coverage NFTs" that represent a claim right for a specific contract address over a set duration
- **Risk-Based Pricing**: Premiums are calculated on-chain based on the pool's total liquidity vs. the total active coverage (Utilization Ratio)
- **Flexible Terms**: Choose coverage duration from 7 days to 1 year
- **Instant Coverage**: Policies are minted immediately upon payment

### 3. Decentralized Claims Processing

- **Evidence Submission**: Policyholders submit on-chain proof of a hack or failure
- **Governance Assessment**: Aegis token holders (or a specialized "Claims DAO") vote on the validity of the claim using the Vora voting logic
- **Automated Payouts**: Once a claim is approved, the Soroban contract automatically releases funds to the policyholder's wallet
- **Fast Resolution**: Target claim resolution within 7 days

### 4. Incident Oracle Integration

- Integration with external security oracles to pause premium payments or flag high-risk contracts in real-time
- Real-time risk assessment updates
- Automatic policy suspension for flagged contracts

### 5. Governance

- **Aegis Token**: Native governance token for protocol decisions
- **Proposal System**: Token holders can propose changes to protocol parameters
- **Delegated Voting**: Stake your tokens or delegate to trusted representatives

---

## 🏗 Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                        Frontend (Next.js)                       │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────────────────┐ │
│  │   Dashboard │  │ Buy Coverage│  │  Underwriting Portal    │ │
│  └─────────────┘  └─────────────┘  └─────────────────────────┘ │
└────────────────────────────┬────────────────────────────────────┘
                             │ Soroban RPC
┌────────────────────────────┴────────────────────────────────────┐
│                     Smart Contracts Layer                        │
│  ┌──────────────┐  ┌────────────────┐  ┌──────────────────────┐ │
│  │  Vault       │  │ Policy Engine  │  │   Claims Manager    │ │
│  │  Contract    │  │    Contract    │  │     Contract        │ │
│  └──────────────┘  └────────────────┘  └──────────────────────┘ │
│  ┌──────────────┐  ┌────────────────┐                            │
│  │  Governance  │  │   Oracle       │                            │
│  │  Contract    │  │   Adapter      │                            │
│  └──────────────┘  └────────────────┘                            │
└──────────────────────────────────────────────────────────────────┘
                             │
┌────────────────────────────┴────────────────────────────────────┐
│                        Data Layer                                │
│  ┌──────────────┐  ┌────────────────┐  ┌──────────────────────┐   │
│  │ Stellar      │  │  Mercury       │  │   Off-chain         │   │
│  │ Ledger       │  │  Indexer       │  │   Storage           │   │
│  └──────────────┘  └────────────────┘  └──────────────────────┘   │
└──────────────────────────────────────────────────────────────────┘
```

### System Components

| Component             | Description                                                |
| --------------------- | ---------------------------------------------------------- |
| **Capital Pool**      | Holds the underlying assets ($XLM/USDC$)                   |
| **Policy Factory**    | Mints the insurance policy terms as a Soroban ledger entry |
| **Claims Manager**    | The logic gate that evaluates and executes payouts         |
| **Governance Module** | Handles voting and proposal execution                      |
| **Oracle Adapter**    | Connects to external security oracles                      |

---

## 🛠 Tech Stack

### Smart Contracts

- **Language**: Rust
- **Framework**: Soroban SDK
- **Target**: WASM (`wasm32-unknown-unknown`)

### Frontend

- **Framework**: Next.js 14
- **Styling**: Tailwind CSS
- **UI Components**: Shadcn/UI
- **State Management**: React Query + Zustand

### Wallet & Authentication

- **Wallet**: Freighter Wallet (Stellar)
- **Authentication**: Wallet-based session management

### Indexing & Data

- **Indexer**: Mercury or Stellar RPC
- **Historical Data**: Event indexing for claim tracking

### Development Tools

- **CLI**: Stellar CLI
- **Testing**: Rust testing framework + Soroban test utils
- **Package Manager**: npm/pnpm

---

## 🚦 Getting Started

### Prerequisites

Before you begin, ensure you have the following installed:

| Tool            | Version | Installation                     |
| --------------- | ------- | -------------------------------- |
| **Stellar CLI** | Latest  | `cargo install stellar_cli`      |
| **Rust**        | 1.70+   | [rustup.rs](https://rustup.rs)   |
| **Node.js**     | 18+     | [nodejs.org](https://nodejs.org) |
| **npm/pnpm**    | Latest  | `npm install -g pnpm`            |

#### Install Rust WASM Target

```bash
rustup target add wasm32-unknown-unknown
```

#### Install Additional Tools

```bash
# Install wasm-bindgen-cli (required for Soroban)
cargo install wasm-bindgen-cli

# Install stellar-cli for contract deployment
cargo install stellar-cli
```

### Installation

1. **Clone the Repository**

```bash
git clone https://github.com/aegis-stellar/aegis-stellar.git
cd aegis-stellar
```

2. **Install Dependencies**

```bash
# Install frontend dependencies
cd frontend && pnpm install && cd ..

# Or using npm
npm install
```

3. **Build Smart Contracts**

```bash
# Build all contracts
stellar contract build

# Build specific contract
cd contracts/vault && stellar contract build
```

4. **Configure Environment**

```bash
# Copy environment template
cp frontend/.env.example frontend/.env.local

# Edit with your configuration
# - Stellar Network (testnet/mainnet)
# - Contract Addresses
# - RPC Endpoints
```

### Development

#### Running Local Development Server

```bash
# Start the frontend development server
cd frontend
pnpm dev
```

The application will be available at `http://localhost:3000`

#### Running Tests

```bash
# Run all contract tests
cd contracts
cargo test

# Run specific contract tests
cd contracts/vault
cargo test

# Run frontend tests
cd frontend
pnpm test
```

#### Deploying to Testnet

```bash
# Deploy vault contract
stellar contract deploy \
  --wasm target/wasm32-unknown-unknown/release/aegis_vault.wasm \
  --source-account YOUR_SECRET \
  --network testnet

# Deploy policy engine
stellar contract deploy \
  --wasm target/wasm32-unknown-unknown/release/aegis_policy_engine.wasm \
  --source-account YOUR_SECRET \
  --network testnet

# Deploy claims manager
stellar contract deploy \
  --wasm target/wasm32-unknown-unknown/release/aegis_claims_manager.wasm \
  --source-account YOUR_SECRET \
  --network testnet
```

---

## 📂 Project Structure

```
aegis-stellar/
├── contracts/                    # Soroban smart contracts
│   ├── vault/                    # Manages deposits and withdrawals
│   │   ├── src/
│   │   │   ├── lib.rs           # Contract interface
│   │   │   ├── deposit.rs       # Deposit logic
│   │   │   ├── withdraw.rs      # Withdrawal logic
│   │   │   └── pool.rs          # Pool management
│   │   ├── Cargo.toml
│   │   └── Makefile
│   ├── policy_engine/            # Calculates premiums and mints coverage
│   │   ├── src/
│   │   │   ├── lib.rs           # Contract interface
│   │   │   ├── pricing.rs       # Premium calculation
│   │   │   ├── policy.rs        # Policy minting
│   │   │   └── types.rs         # Data structures
│   │   ├── Cargo.toml
│   │   └── Makefile
│   ├── claims_manager/           # Logic for voting on and executing payouts
│   │   ├── src/
│   │   │   ├── lib.rs           # Contract interface
│   │   │   ├── claims.rs        # Claim processing
│   │   │   ├── voting.rs        # Governance voting
│   │   │   └── payout.rs        # Payout execution
│   │   ├── Cargo.toml
│   │   └── Makefile
│   └── governance/               # Protocol governance
│       ├── src/
│       │   ├── lib.rs
│       │   ├── proposal.rs
│       │   └── voting.rs
│       └── Cargo.toml
├── frontend/                     # Next.js application
│   ├── app/                     # App Router pages
│   │   ├── page.tsx             # Landing page
│   │   ├── dashboard/           # User dashboard
│   │   ├── buy/                 # Buy coverage page
│   │   ├── underwrite/          # Underwriting page
│   │   └── layout.tsx           # Root layout
│   ├── components/              # Reusable components
│   │   ├── ui/                  # Base UI components
│   │   ├── dashboard/           # Dashboard components
│   │   ├── insurance/           # Insurance-specific components
│   │   └── charts/              # Data visualization
│   ├── hooks/                   # Custom React hooks
│   │   ├── useSoroban.ts       # Soroban wallet integration
│   │   ├── useContracts.ts      # Contract interactions
│   │   └── useClaims.ts         # Claims management
│   ├── lib/                     # Utility functions
│   │   ├── soroban.ts          # Soroban client
│   │   ├── contracts/           # Contract ABIs and interfaces
│   │   └── utils.ts            # Helper functions
│   ├── public/                  # Static assets
│   ├── tailwind.config.ts      # Tailwind configuration
│   ├── next.config.js          # Next.js configuration
│   └── package.json
├── tests/                       # Integration tests
│   ├── contracts/              # Contract simulation tests
│   └── frontend/               # Frontend tests
├── scripts/                     # Deployment and utility scripts
├── docs/                        # Documentation
├── README.md
├── CONTRIBUTING.md
├── LICENSE
└── package.json                 # Root package.json (workspaces)
```

---

## 📜 Smart Contracts

### Vault Contract

The Vault contract manages all deposits and withdrawals for underwriters.

#### Key Functions

```rust
// Deposit funds into a risk pool
fn deposit(env: Env, pool_id: u32, amount: i128) -> bool

// Withdraw funds from a pool
fn withdraw(env: Env, pool_id: u32, amount: i128) -> bool

// Get user's balance in a pool
fn get_balance(env: Env, user: Address, pool_id: u32) -> i128

// Get total pool liquidity
fn get_total_liquidity(env: Env, pool_id: u32) -> i128
```

### Policy Engine Contract

The Policy Engine calculates premiums and mints insurance policies.

#### Key Functions

```rust
// Calculate premium for coverage
fn calculate_premium(env: Env, coverage_amount: i128, duration: u32, pool_id: u32) -> i128

// Mint a new policy
fn mint_policy(env: Env, user: Address, coverage_amount: i128, duration: u32, target_contract: Address) -> u64

// Get policy details
fn get_policy(env: Env, policy_id: u64) -> Policy

// Check if a contract is covered
fn is_covered(env: Env, contract_address: Address) -> bool
```

### Claims Manager Contract

The Claims Manager handles claim submission, voting, and payouts.

#### Key Functions

```rust
// Submit a new claim
fn submit_claim(env: Env, policy_id: u64, evidence: ClaimEvidence) -> u64

// Vote on a claim
fn vote(env: Env, claim_id: u64, approve: bool) -> bool

// Execute payout for approved claim
fn execute_payout(env: Env, claim_id: u64) -> bool

// Get claim status
fn get_claim_status(env: Env, claim_id: u64) -> ClaimStatus
```

---

## 💻 Frontend Application

### Pages

| Route         | Description                         |
| ------------- | ----------------------------------- |
| `/`           | Landing page with protocol overview |
| `/dashboard`  | User portfolio and positions        |
| `/buy`        | Purchase insurance coverage         |
| `/underwrite` | Provide liquidity to pools          |
| `/claims`     | View and manage claims              |
| `/governance` | Participate in governance           |

### Key Components

- **PoolCard**: Displays pool statistics and APR
- **PolicyForm**: Multi-step form for purchasing coverage
- **ClaimCard**: Shows claim status and voting progress
- **RiskChart**: Visualizes pool utilization and risk metrics
- **WalletButton**: Freighter wallet connection

### State Management

The frontend uses a combination of:

- **React Query**: Server state and contract queries
- **Zustand**: Client-side UI state
- **Context**: Theme and wallet providers

---

## 🧪 Testing

### Running Tests

```bash
# Run all contract tests
cd contracts
cargo test

# Run tests with output
cargo test -- --nocapture

# Run specific test
cargo test test_deposit

# Run frontend tests
cd frontend
pnpm test
```

### Test Coverage

- **Unit Tests**: Individual contract functions
- **Integration Tests**: Cross-contract interactions
- **Simulation Tests**: End-to-end scenarios
- **Property Tests**: Invariant verification

### Writing Tests

```rust
#[test]
fn test_deposit() {
    // Arrange
    let env = Env::default();
    env.ledger().set_sequence_number(100);

    // Act
    // ...

    // Assert
    assert_eq!(balance, expected_balance);
}
```

---

## 🚀 Deployment

### Mainnet Deployment

1. **Audit Contracts**: Complete security audits
2. **Set Parameters**: Configure governance parameters
3. **Deploy Contracts**: Deploy to Stellar mainnet
4. **Initialize Pools**: Create initial risk pools
5. **Verify**: Run integration tests against mainnet

### Network Configuration

| Network | RPC URL                               | Network Passphrase                               |
| ------- | ------------------------------------- | ------------------------------------------------ |
| Testnet | `https://soroban-testnet.stellar.org` | `Test SDF Network ; September 2015`              |
| Mainnet | `https://soroban.stellar.org`         | `Public Global Stellar Network ; September 2014` |

### Contract Upgrade Process

1. Deploy new contract WASM
2. Submit upgrade proposal to governance
3. Vote and approve upgrade
4. Execute upgrade transaction

---

## ⚙️ Configuration

### Environment Variables

```env
# Frontend (.env.local)
NEXT_PUBLIC_STELLAR_NETWORK=testnet
NEXT_PUBLIC_RPC_URL=https://soroban-testnet.stellar.org
NEXT_PUBLIC_VAULT_CONTRACT_ADDRESS=CA...
NEXT_PUBLIC_POLICY_CONTRACT_ADDRESS=CA...
NEXT_PUBLIC_CLAIMS_CONTRACT_ADDRESS=CA...

# Contract (contracts/vault/.env)
NETWORK=testnet
SOURCE_ACCOUNT=S...
```

### Contract Parameters

| Parameter       | Description                 | Default        |
| --------------- | --------------------------- | -------------- |
| `MIN_DEPOSIT`   | Minimum deposit amount      | 10 USDC        |
| `MAX_COVERAGE`  | Maximum coverage per policy | 1,000,000 USDC |
| `CLAIM_PERIOD`  | Time to submit claims       | 7 days         |
| `VOTING_PERIOD` | Time to vote on claims      | 3 days         |
| `QUORUM`        | Minimum votes for validity  | 51%            |

---

## 📚 API Reference

### Contract Interfaces

#### Vault Contract

```typescript
interface Vault {
  deposit(poolId: number, amount: BigNumber): Promise<Transaction>;
  withdraw(poolId: number, amount: BigNumber): Promise<Transaction>;
  getBalance(user: string, poolId: number): Promise<BigNumber>;
  getTotalLiquidity(poolId: number): Promise<BigNumber>;
}
```

#### Policy Engine

```typescript
interface PolicyEngine {
  calculatePremium(
    coverageAmount: BigNumber,
    duration: number,
    poolId: number,
  ): Promise<BigNumber>;
  mintPolicy(
    coverageAmount: BigNumber,
    duration: number,
    targetContract: string,
  ): Promise<number>;
  getPolicy(policyId: number): Promise<Policy>;
  isCovered(contractAddress: string): Promise<boolean>;
}
```

#### Claims Manager

```typescript
interface ClaimsManager {
  submitClaim(policyId: number, evidence: ClaimEvidence): Promise<number>;
  vote(claimId: number, approve: boolean): Promise<boolean>;
  executePayout(claimId: number): Promise<boolean>;
  getClaimStatus(claimId: number): Promise<ClaimStatus>;
}
```

---

## 🤝 Contributing

We welcome contributions! Please see our [Contributing Guide](CONTRIBUTING.md) for details.

### Development Workflow

1. **Fork** the repository
2. **Clone** your fork
3. **Create** a feature branch
4. **Make** your changes
5. **Test** thoroughly
6. **Commit** with clear messages
7. **Push** to your fork
8. **Submit** a Pull Request

### Code Style

- **Rust**: Follow `rustfmt` and clippy guidelines
- **TypeScript**: Follow ESLint and Prettier rules
- **Commits**: Use conventional commits format

---

## 🗺️ Roadmap

### Phase 1: Core Protocol (Completed)

- [x] Vault contract implementation
- [x] Policy engine with premium calculation
- [x] Basic claims submission

### Phase 2: Governance (In Progress)

- [x] Claims DAO voting mechanism
- [ ] Delegated voting
- [ ] Proposal system

### Phase 3: Features

- [ ] Multi-chain support
- [ ] Advanced risk modeling
- [ ] Flash loans for coverage
- [ ] Secondary market for policies

### Phase 4: Ecosystem

- [ ] Integration with major DeFi protocols
- [ ] Cross-chain insurance
- [ ] Institutional coverage options

---

## ❓ FAQ

### General

**What is Aegis Stellar?**
Aegis Stellar is a decentralized insurance protocol built on Soroban that protects DeFi users against smart contract failures and hacks.

**How does the protocol work?**
Underwriters deposit capital into risk pools. Policy holders pay premiums for coverage. If a covered event occurs, claims are voted on by the community and payouts are made from the pool.

**What tokens are supported?**
Currently $XLM$ and $USDC$. Support for more assets coming soon.

### For Underwriters

**How do I earn rewards?**
Deposit funds into a risk pool. You'll earn a share of all premiums paid by policy holders in your pool.

**What's the risk of underwriting?**
Your deposited funds can be used to pay out claims. The risk is mitigated by diversification across pools and over-collateralization.

**Can I withdraw anytime?**
Yes, subject to the pool's liquidity. Some pools may have a withdrawal delay for added security.

### For Policy Holders

**What does insurance cover?**
Coverage includes smart contract exploits, logic errors, and protocol hacks that result in loss of funds.

**How are premiums calculated?**
Premiums are based on: coverage amount, duration, pool utilization ratio, and historical claim history.

**How do I file a claim?**
Submit a claim through the frontend with proof of the exploit. The Claims DAO will vote on its validity.

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

