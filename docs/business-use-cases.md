# Business Use Cases Unlocked

This document outlines the potential business use cases that are generally enable by liquid stacking and liquid stacking derivatives.

# Individual/Trader

```mermaid
graph TB
    A[Individual's Assets] --> B[Stake Assets]
    B --> C[Liquid Staking Token]
    C --> D1[Trade on DEX]
    C --> D2[Use as Collateral]
    C --> D3[Yield Farming]
    C --> D4[Hedge & Diversify]

    D2 --> E1[Lend on Platform]
    D2 --> E2[Borrow Assets]
    D3 --> F1[Reinvest in Staked Asset]
    D3 --> F2[Double Dip Rewards]
```

**Liquidity Provision**

Liquid staking allows individuals to stake their assets and still have access to the liquidity in the form of a tokenized staked asset. This can be traded, used as collateral, or utilized in other decentralized finance (DeFi) applications.

Individuals can use these tokenized staked assets to enter into other investment opportunities without having to unstake or sell their primary staked asset.

```mermaid
sequenceDiagram
    participant I as Individual
    participant LS as Liquid Staking Protocol
    participant D as DeFi Application

    I->>LS: Stake assets
    LS->>I: Issue tokenized staked asset
    I->>D: Use tokenized asset (Trade, Collateral, etc.)
    D->>I: Provide liquidity or investment opportunity
    I-->>LS: Retain option to un-stake if needed
```

**Collateralization for loans**

Individuals can lend their tokenized staked assets on lending platforms to earn interest or use them as collateral to borrow other assets.

```mermaid
sequenceDiagram
    participant I as Individual (Borrower)
    participant LP as Lending Platform
		participant L as Individual (Lender)

    Note over I,L: Interest-bearing liquid staking derivatives:
		L->>LP: Lend tokenized staked asset
    LP->>L: Offer base interest earnings on the lent asset
		LP-->L: Offer additional interest from LSD yield

    I->>LP: Deposit tokenized staked asset as collateral
    LP->>I: Offer loan based on collateral

    alt Borrow with enhanced collateral
        I->>LP: Borrow additional funds due to enhanced collateral value
    else Use LSD interest to pay down principal
        I->>LP: Pay down principal with LSD interest
    end

    I->>LP: Repay remaining loan
    LP->>I: Return collateral (and any remaining interest on the derivative if used for pay down)
		LP->>L: Return the lent asset (with overall interest earned)
```

**Yield Farming**

Rewards earned from yield farming can be converted and reinvested into more of the original asset, which can then be staked again, creating a compounding effect.

By utilizing liquid staking derivatives in yield farming protocols, individuals can potentially earn additional rewards, effectively double-dipping.

```mermaid
sequenceDiagram
    participant I as Individual
    participant YF as Yield Farming Protocol
    participant LS as Liquid Staking Protocol

    I->>LS: Stake assets (if not already staked)
    LS->>I: Issue tokenized staked asset
    I->>YF: Deposit tokenized staked asset for farming
    YF->>I: Earn rewards
    I->>LS: Convert rewards to original asset & stake (optional for compounding)
```

**Hedging and Risk Management**

With the tokenized form of staked assets, individuals and institutions can easily trade or diversify their holdings. If they foresee a potential downturn or risk in one staked asset, they can exchange it for another without waiting for un-staking periods.

```mermaid
sequenceDiagram
    participant I as Individual/Institution
    participant DEX as Decentralized Exchange
    participant LS as Liquid Staking Protocol

		I->>LS: Stake asset
		LS->>I: Issue tokenized staked asset
    I->>DEX: Trade partial tokenized staked asset position for another asset
    DEX->>I: Provide diversified asset
    I-->>LS: Retain option to un-stake remaining position if needed
```

# Teams/Builders

```mermaid
graph TB
    A1[Builder's Platform] --> B1[Integrate Liquid Staking Tokens]
    A1 --> B2[Interoperability Solutions]
    A1 --> B3[Form Cross-Protocol Synergies]

    B1 --> C1[Yield Farming]
    B1 --> C2[Lending/Borrowing]
    B2 --> C3[Stake on Multiple Chains]
    B3 --> C4[Maximized Yield]
    B3 --> C5[Enhanced Liquidity]
```

**DeFi Integration**:

Builders can integrate liquid staking tokens into their DeFi applications, expanding the range of assets available for yield farming, lending, borrowing, and other DeFi activities.

```mermaid
sequenceDiagram
    participant B as Builder
    participant LS as Liquid Staking Protocol
    participant DA as DeFi Application
		participant U as User

    B->>DA: Integrate Liquid Staking into DeFi App
		U->>DA: Stake asset
		DA->>LS: Stake asset
		LS->>DA: Provides tokenized stake asset
    DA->>U: Provide tokenized application-specific postion
    DA->>DA: Use assets for Yield Farming, Lending, Borrowing, etc.
		DA-->U: Earns yield
```

**Interoperability Solutions**:

Builders can explore interoperability solutions that enable cross-chain liquid staking, allowing users to stake assets across different blockchains.

```mermaid
sequenceDiagram
    participant B as Builder
    participant IS as Interoperability Solution
    participant BC1 as Blockchain 1
    participant BC2 as Blockchain 2
    participant U as User

    B->>IS: Integrate Cross-chain Liquid Staking Solution
    U->>IS: Stake in cross-chain staking
    IS->>BC1: Interface with Blockchain 1 for staking
    IS->>BC2: Interface with Blockchain 2 for staking
    BC1-->>U: Reward for staking on Blockchain 1
    BC2-->>U: Reward for staking on Blockchain 2
```

**Cross-Protocol Synergies**

Developers can create partnerships or integrations with other DeFi protocols, leveraging the liquid staked assets to maximize yield for users. For instance, integrating a liquid staking platform with a yield aggregator can optimize returns for users.

```mermaid
sequenceDiagram
    participant D as Developer
    participant LSP as Liquid Staking Platform
    participant YA as Yield Aggregator
    participant DP as DeFi Protocol (Another)

    D->>LSP: Integrate Liquid Staking Platform
    D->>DP: Create partnership/integration with DeFi Protocol
    LSP->>YA: Provide liquid staked assets to Yield Aggregator
    DP->>YA: Optimize yields using combined assets
```

# Institutions

```mermaid
graph TB
    A2[Institution's Capital] --> B4[Liquid Stake Assets]
    B4 --> C5[Institutional Participation]
    B4 --> C6[Hedging & Risk Management]
    B4 --> C7[Liquidity Mining]
    B4 --> C8[Automated Portfolio Management]
    B4 --> C9[Create New Financial Products]
    B4 --> C10[Collateralization]
    B4 --> C11[Yield Farming]

    C6 --> D1[Short on Derivative]
    C6 --> D2[Long on Derivative]
    C7 --> D3[Enhanced Liquidity]
    C8 --> D4[Rebalance Assets]
    C10 --> D5[Novel Collateral Type]
    C11 --> D6[Revenue Diversification]
```

**Institutional Participation**

Liquid staking can offer a more attractive entry point for institutional investors. They can benefit from the potential rewards of staking while maintaining liquidity, which is often a requirement for institutional operations. (Looking at you, T-Bonds 👀)

```mermaid
sequenceDiagram
    participant Inst as Institution
    participant LS as Liquid Staking Protocol

    Inst->>LS: Stake assets
    LS->>Inst: Issue tokenized staked assets
    Note over Inst,LS: Institution maintains liquidity while generating yield
```

**Hedging and Risk Management**

With liquid staking derivatives available, it's possible for investors to hedge their positions. For instance, if one anticipates a decrease in rewards, they might take a short position on a liquid staking derivative. Conversely, if an investor expects the rewards to increase, they could take a long position on the derivative, thereby securing potential future gains.

```mermaid
sequenceDiagram
    participant I as Investor
    participant LSD as Liquid Staking Derivative

    Note over I,LSD: Investor anticipates market movement

    alt Anticipates Decrease in Rewards
        I->>LSD: Takes short position
        Note over I,LSD: Secures against potential loss
    else Anticipates Increase in Rewards
        I->>LSD: Takes long position
        Note over I,LSD: Secures potential future gains
    end
```

Suppose an investor has a long position in a certain asset, but they anticipate a potential decrease in its value. To hedge against this risk, they could use their liquid staking rewards to take a short position in a derivative of the same asset.

```mermaid
sequenceDiagram
    participant I as Investor
    participant A as Asset
    participant D as Derivative
    participant LS as Liquid Staking Protocol

    I->>A: Takes long position in asset
    I->>LS: Stakes assets and earns rewards
    LS->>I: Provides liquid staking rewards
    I->>D: Uses rewards to take short position in derivative
    Note over I,D: Hedge against potential loss in asset
```

This way, if the asset's value decreases, the loss in the long position would be offset by the gain in the short position. Conversely, if the asset's value increases, the gain in the long position would offset the loss in the short position.

**Liquidity Mining**

Protocols can incentivize stakers by offering additional rewards for those who stake and then use their liquid staking tokens in specific DeFi platforms or liquidity pools. This dual reward mechanism (staking rewards + liquidity mining rewards) can attract more capital and ensure a deeper liquidity for the token.

```mermaid
sequenceDiagram
    participant S as Staker
    participant Prot as Protocol

    S->>Prot: Stake assets
    Prot->>S: Issue liquid staking tokens

    Prot-->S: Provide staking + liquidity mining rewards
```

**Automated Portfolio Management**: 

With liquid staking tokens available, portfolio management tools could be build to automate certain strategies, like rebalancing between liquid assets and staking positions, to optimize returns

```mermaid
sequenceDiagram
    participant I as Institution
    participant LST as Liquid Staking Tokens

    I->>I: Evaluate current staking positions
    I->>LST: Rebalance assets and staking positions
    I-->LST: Optimization of returns
```

**New Financial Products**

Institutions can create new financial products around these tokenized staked assets, such as staking as a service, derivative products, or interest-bearing instruments.

**Collateralization**

For institutions dealing in DeFi lending and borrowing, tokenized staked assets can serve as a novel form of collateral, due to different risk-reward profiles compared to traditional assets.

**Yield Farming**

Institutions can diversify their revenue streams by not only earning from staking but also from yield farming using the tokenized staked assets. This can provide a competitive advantage in the DeFi landscape.

```mermaid
sequenceDiagram
    participant Inst as Institution
    participant YFPlatform as Yield Farming Platform

    Inst->>YFPlatform: Deposit tokenized staked assets
    YFPlatform->>Inst: Provide yield farming rewards
    Note over Inst,YFPlatform: Diversified revenue streams
```
