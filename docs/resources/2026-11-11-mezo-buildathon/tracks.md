# Tracks: Mezo Buildathon

Sources: event page body [P1] and Terms §2 [P3] (verbatim); Wave 1 judge reviews via the AKINDO API [P2]. See INDEX.md.
There are **two tracks and no per-track prize**: one points-proportional pool per wave across all eligible entries ($5,000 in Wave 2). "Pick one, or submit to both." Track is "multiple choice on the submission form" [P1 FAQ].

## Track 1: DeFi (Borrowing, Lending, Looping, and Yield) — TARGET

- **Challenge question (verbatim):** "How might we expand MUSD and MEZO utility as collateral and productive capital across DeFi?"
- **Framing (verbatim):** "Build protocols and strategies that make MUSD and MEZO a core building block in DeFi: composable collateral and yield-bearing capital."
- **Example projects (verbatim):**
  - "Lending protocols accepting MUSD/MEZO as collateral, single-chain or cross-chain"
  - "Looping strategies for MUSD/MEZO positions (leveraged yield farming)"
  - "Yield-generating vaults and auto-compounding strategies for MUSD/MEZO"
  - "MUSD/MEZO liquidity pools and DEX integrations on other chains"
  - "Staking derivatives for MUSD/MEZO"
- **Requirement (verbatim):** "Requirement: MUSD/MEZO integration."
- **Terms wording [P3]:** "(1) DeFi — Borrowing, Lending, Looping, and Yield, focused on building protocols and strategies that make MUSD and MEZO core building blocks for composable collateral, productive capital, and yield generation, including lending protocols, looping strategies, yield-generating vaults, liquidity pools, DEX integrations, and staking derivatives".
- **Minimum bar to qualify (all tracks, event.md §3):** MUSD and/or MEZO integration · a working deployment on Mezo (testnet OK), Ethereum, Base, or BNB Chain · built during the event or a new extension · public repo, deck, 2-minute video and live link.
- **Required tech:** none mandated beyond the integration. In practice it means Solidity on Mezo (EVM, chain 31611/31612) against MUSD's Liquity-style contracts, Mezo Pools (Solidly/Aerodrome-style plus CL), veBTC/veMEZO gauges, and the sMUSD Savings Vault. See sponsors/.
- **Domain constraint to keep in mind:** on Mezo, MUSD's own CDP takes **BTC only** as collateral (openTrove is `payable`, native BTC). So "MUSD/MEZO as collateral" means building a new market or venue that accepts them (as Mezodot and Baserate did), not posting them into MUSD's troves. See sponsors/mezo-musd.md §Claims.

## Track 2: Access and Distribution for MUSD/MEZO (prior-art context only)

- **Challenge question (verbatim):** "How might we make MUSD and MEZO easier to discover, access, and use?"
- **Framing (verbatim):** "Build the tools, bots, and interfaces that reduce friction for users interacting with Mezo's ecosystem, meeting users where they already are."
- **Example projects (verbatim):** "Telegram or WhatsApp bots for MUSD/MEZO transactions and monitoring" · "Matching and discovery platforms" · "Marketplaces and aggregators for Mezo ecosystem products" · "Cross-platform wallets and interfaces that simplify MUSD/MEZO access"
- **Requirement (verbatim):** "Requirement: MUSD or MEZO integration."

## What the judges' principles reward (applies to both tracks)

Published principles (verbatim, [P1]): "Integration is mandatory" · "Extend, don't detour. Projects that extend the reach and utility of existing Mezo products are prioritized over unrelated standalone apps." · "Composability wins. Projects that plug into existing DeFi infrastructure (lending markets, DEXs, vote-escrow systems) score higher than isolated consumer apps." · "Long-term commitment counts."

What the Wave 1 scoring shows ([P2]; detail in prior-art.md):
- **Integration depth is scored on a 5-rung ladder** (cosmetic → transactional → protocol-aware → composing → top). Reaching the top needs several Mezo primitives exercised **on chain** (troves via BorrowerOperations, Mezo Pools/gauges, sMUSD, veBTC/veMEZO voters, PriceFeed), not only in fork tests, plus usage beyond your own wallets.
- **Track 1 lanes earned more than Track 2 lanes in Wave 1.** Mean award: lending/credit 25.6 USDT (max 80), ve/boost markets 20.0 (max 69), loan protection 15.9, vaults 14.3, versus payments 10.9 and agents/x402 8.7. Mean Integration value: about 7.3 for lending and loan protection, about 4.5 for most Track 2 lanes.
- **The top five Wave 1 awards all composed Mezo's own primitives deeply:** veBTC custody and voting (Doji, Surety, Janus, Keel) or real troves behind a product (Mezonk). Reviews of entries that read the protocol without transacting through it named the cap explicitly ("protocol-aware (L3)").
- **Wave 2 is relative:** "we'll rank projects against each other … more "complete" and "ready" projects will get better points" (official comment, 2026-11-06).
- **Viability (30%) is scored against the chosen track's question.** Reviews repeatedly ask for a stated revenue/fee model, unit economics, who pays for keepers and infrastructure, and a first pilot or outside users.
