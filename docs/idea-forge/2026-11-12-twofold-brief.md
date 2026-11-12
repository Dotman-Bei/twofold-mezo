# Idea Forge Brief — Twofold: 2× Bitcoin as one token, run on one shared MUSD trove

> Working title "Twofold" (token symbol `BTC2x`) is provisional; the builder may rename. `BTC2x` is a
> descriptive placeholder: Index Coop already markets a BTC2X token on other chains, so pick a distinct
> symbol before launch. This brief is the single source of truth handed to the architect (Step 1). It
> is a brief, not a spec: it fixes *what* and *why*, not *how*.

## Event + constraints

- **Date written:** 2026-11-12
- **Hackathon:** Mezo Buildathon (AKINDO WaveHack), Wave 2. Event page: https://app.akindo.io/wave-hacks/ovoo0gdrvu8379d10
- **Resource pack (pre-verified, read first):** `docs/resources/2026-11-11-mezo-buildathon/` · tollgate report `docs/tollgate/2026-11-11-tollgate.md`
- **Working deadline (inert calendar fact; idea-forge did not gate on it):** 2026-11-15 15:00 UTC = 16:00 WAT. The builder's internal stop is 10:00 WAT that day.
- **Deployment target:** Mezo testnet (chain 31611), which the event accepts. No mainnet funds, partnerships, approvals or gated contract addresses are assumed.
- **Team:** one human plus the autonomous pool (architect → executor pool → reviewer).
- **Target track:** Track 1: DeFi (Borrowing, Lending, Looping, and Yield). Track 1 only.
- **Risk posture:** safe-feasible.
- **Submission items the plan must leave room for (event.md §3):** live testnet link, public GitHub repo, project deck, a video of about 2 minutes or less, and the AKINDO form fields. A missing deck caps Materials at the lowest level; a video over about 2:15 caps it too.

## Problem

Leveraged BTC on Mezo means running your own MUSD trove loop, and that has three costs.

1. **A size floor.** MUSD requires at least 1,800 MUSD of net debt plus a 200 MUSD gas deposit per trove. At 2× leverage, debt equals your own equity, so a personal loop needs roughly $2,000 of BTC (about 0.027 BTC at the testnet oracle price on 2026-11-12). Smaller holders cannot open one at all.
2. **A babysitting job.** Each looper carries their own liquidation, redemption and Recovery Mode risk, and either watches the trove or pre-signs a stop-loss for a keeper.
3. **A dead-end position.** The exposure is locked in one address. It cannot be transferred, pooled as liquidity, or used as collateral.

Every leverage product filed in the buildathon so far wraps one trove per user, so each inherits all three.

## Solution (one line)

Twofold is a vault that runs one pooled, self-rebalancing 2× BTC loop on a real MUSD trove and issues it as `BTC2x`, a token anyone can mint or redeem with any amount of BTC in one transaction.

## Must-have demo features

1. **The `BTC2x` vault (the one custom on-chain core).** Mint with any BTC amount and redeem for BTC, each in one transaction, against a single vault-owned trove: collateral and debt move through `BorrowerOperations`, the MUSD-to-BTC leg swaps on the Mezo Pools MUSD/BTC pool with a bound taken from Mezo's `PriceFeed`, and each minter or redeemer bears the cost of their own swap, so existing holders are not diluted. The vault carries MUSD's debt floor and gas deposit once, for everyone.
2. **A risk engine anyone can run.** A permissionless `rebalance` (with a capped bounty) pulls leverage back into its band when BTC moves. The vault keeps a MUSD reserve in Mezo's Savings Vault (sMUSD). The reserve lets the vault cut leverage by repayment alone, which still works in Recovery Mode when collateral withdrawals are blocked, and its real yield is claimed by a permissionless `harvest` and used to repay trove debt.
3. **The app, plus `BTC2x` liquidity on Mezo Pools.** One screen to mint and redeem, with live leverage, trove ICR, system TCR and Recovery Mode state, an explorer link for every leg, and Rebalance and Harvest buttons a judge can press. A `BTC2x` pool is created through Mezo's `PoolFactory` and seeded, so the token has a second exit when redemptions are paused. A small keeper script runs `rebalance` and `harvest` on a schedule.

## Target sponsor track(s)

**Track 1: DeFi.** It answers the challenge question ("expand MUSD and MEZO utility as collateral and productive capital") through the official example "Looping strategies for MUSD/MEZO positions", and turns the looped position into a composable token rather than a private trove. MUSD is the funding leg of every `BTC2x` minted, and the vault's reserve is MUSD held in sMUSD.

## Judging criteria (published)

Mezo Integration **30%** · Product & Business Viability **30%** · Technical Implementation **20%** · User Experience **10%** · Submission Materials Quality **10%** (event.md §4).

How they are applied, from the pack: Wave 2 entries are ranked against each other across both tracks and paid by points share; "more complete and ready projects will get better points". Integration is graded on a five-rung ladder: read-only use caps at level 3, and the top needs several Mezo primitives exercised on chain (not only in fork tests) plus users beyond the builder's own wallets. Viability is read against the Track 1 question and reviews ask for a stated fee model and who pays the keeper.

## Why it wins

**White space.** Two groups of the 148 AKINDO products sit either side of this, and none combines them. Every leverage entry (Coil twice, MezoRoute's Wave 2 Leverage, Pylon, Morbit's loop factory, Mezodot's one-transaction long, Beam's LeveragedLoop) opens a separate position for each user. The pooled-trove entries issue a token for something else: LP yield (mbLP), savings yield (Feasy) or small loans (TinyVault, Spend, Microtrove). Unlike both, Twofold makes the leveraged position itself the pooled, fungible token. The live Wave 2 list was re-fetched on 2026-11-12 (still 45 products, none new), and a sweep of the testnet explorer's token index found no working equivalent: only `mlBTC` ("MezoLoop Leveraged BTC"), two unverified deployments from 2026-10-01 with 0 holders and no activity since.

**Head-to-head.** Against MezoRoute (the strongest live leverage entry: Wave 1 scores 8/8/8/8/6, mainnet, Wave 2 adds one-transaction leverage) and Pylon, Twofold wins on **Product & Business Viability**: their positions inherit MUSD's per-trove floor (1,800 MUSD net debt plus a 200 MUSD gas deposit, confirmed on chain) and need a keeper or signature per user, while `BTC2x` mints from any amount, is one transferable ERC-20, and is protected by one shared rebalance. On **Mezo Integration** it is a tie, not a win: all three compose troves and Mezo Pools on chain (Twofold adds sMUSD and its own Mezo pool). It loses on mainnet proof, which is not a published criterion; testnet is accepted. Wave 1 leaders can still refile before the deadline.

## Demo money shot (~15 seconds)

A wallet holding 0.001 test BTC tries the direct route first: opening its own trove reverts with Mezo's own message, "BorrowerOps: Trove's net debt must be greater than minimum". The same wallet then mints `BTC2x` with that 0.001 BTC in one transaction; the explorer shows the vault's trove taking collateral, borrowing MUSD and swapping on Mezo Pools, and the wallet now holds a 2× BTC position it can transfer.

If there is room for a second beat: anyone presses Harvest, and real Savings Vault yield repays trove debt on screen.

## Out of scope (explicit)

- **No mainnet and no other chain.** Mezo testnet only. (MUSD does not exist on BNB Chain; only MEZO does.)
- **One vault, one multiple (2×).** No 3× tier, no below-1× "BTC plus savings" tier, no short token.
- **No per-user troves.** No `BorrowerOperationsSignatures` flows, no pre-signed stop-losses, no trove NFTs.
- **No Stability Pool.** Its withdrawals pause while any trove is under 110% and deposits can be converted to BTC, so the reserve sits in sMUSD only.
- **No veBTC, veMEZO, gauges or bribes.** Reward claims need an epoch flip, and the next one after 2026-11-12 is 2026-11-19 00:00 UTC, after the deadline.
- **No lending market that accepts `BTC2x` as collateral.** A future milestone, not this build.
- **No mock tokens and no custom oracle.** Canonical testnet MUSD, BTC and `PriceFeed` only (a self-deployed MUSD fails the judges' integration gate).
- **No indexer or subgraph.** Read the chain and the explorer API directly.
- **No AI agent, Telegram bot, cross-chain bridge, points or token incentives.**

## Feasibility notes for the architect (primitives, not design)

Addresses and signatures in A to D are transcribed from the resource pack (`sponsors/mezo-musd.md`, `sponsors/mezo-earn-pools-mezo.md`, `sponsors/mezo-network.md`). Items marked **[verified 2026-11-12]** were checked by idea-forge against primary sources: `mezo-org/musd` at `main` = `da7888a10949c8a5d3f884454cec8978cfa87e48`, verified contract sources on the testnet explorer API (`https://api.explorer.test.mezo.org/api/v2/`), and read-only `eth_call` on `https://rpc.test.mezo.org` near block 16,723,300.

### A. Network

Chain ID `31611` · RPC `https://rpc.test.mezo.org` · WSS `wss://rpc-ws.test.mezo.org` · explorer https://explorer.test.mezo.org (Blockscout, Sourcify-backed verification) · faucet https://faucet.test.mezo.org/ · dApp https://testnet.mezo.org. Gas token is BTC, native, 18 decimals, also visible as an ERC-20 at `0x7b7C000000000000000000000000000000000000`. viem chain config: `mezo-org/chains`. Wallet connection: `@mezo-org/passport` (RainbowKit-based; judges asked other teams for it).

### B. MUSD contracts on testnet (31611)

| Contract | Address |
|---|---|
| MUSD (token, 18 dp) | `0x118917a40FAF1CD7a13dB0Ef56C86De7973Ac503` |
| BorrowerOperations | `0xCdF7028ceAB81fA0C6971208e83fa7872994beE5` |
| TroveManager | `0xE47c80e8c23f6B4A1aE41c34837a0599D5D16bb0` |
| HintHelpers | `0x4e4cBA3779d56386ED43631b4dCD6d8EacEcBCF6` |
| SortedTroves | `0x722E4D24FD6Ff8b0AC679450F3D91294607268fA` |
| PriceFeed | `0x86bCF0841622a5dAC14A313a15f96A95421b9366` |
| InterestRateManager | `0xD4D6c36A592A2c5e86035A6bca1d57747a567f37` |
| PCV | `0x4dDD70f4C603b6089c07875Be02fEdFD626b80Af` |
| CollSurplusPool | `0xB4C35747c26E4aB5F1a7CdC7E875B5946eFa6fa9` |
| ActivePool | `0x143A063F62340DA3A8bEA1C5642d18C6D0F7FF51` |
| StabilityPool (not used) | `0x1CCA7E410eE41739792eA0A24e00349Dd247680e` |
| BorrowerOperationsSignatures (not used) | `0xD757e3646AF370b15f32EB557F0F8380Df7D639e` |

All are proxies and upgradable by Mezo.

### C. Trove entry points

`BorrowerOperations` (cross-checked against `IBorrowerOperations.sol` at `da7888a`):

```solidity
function openTrove(uint256 _debtAmount, address _upperHint, address _lowerHint) external payable; // BTC as msg.value
function addColl(address _upperHint, address _lowerHint) external payable;
function withdrawColl(uint256 _amount, address _upperHint, address _lowerHint) external;
function withdrawMUSD(uint256 _amount, address _upperHint, address _lowerHint) external;
function repayMUSD(uint256 _amount, address _upperHint, address _lowerHint) external;
function adjustTrove(uint256 _collWithdrawal, uint256 _debtChange, bool _isDebtIncrease, address _upperHint, address _lowerHint) external payable;
function closeTrove() external;
function refinance(address _upperHint, address _lowerHint) external;
function claimCollateral() external;
function getBorrowingFee(uint256 _debt) external view returns (uint);
function minNetDebt() external view returns (uint256);
```

`TroveManager`: `getEntireDebtAndColl(address)` returns `(coll, principal, interest, pendingCollateral, pendingPrincipal, pendingInterest)` · `getCurrentICR(address, uint256 price)` · `getTCR(uint256 _price)` · `checkRecoveryMode(uint256 _price)` · `getTroveMaxBorrowingCapacity(address)` · `getTroveStatus(address)` · `updateSystemInterest()` · `MUSD_GAS_COMPENSATION()`.
`HintHelpers`: `getApproxHint(uint256 _CR, uint256 _numTrials, uint256 _inputRandomSeed) returns (address hintAddress, uint256 diff, uint256 latestRandomSeed)`.
`SortedTroves`: `findInsertPosition(uint256 _NICR, address _prevId, address _nextId) returns (address, address)` · `getLast()`.
`PriceFeed`: `fetchPrice() external view returns (uint)` (BTC/USD, 18 dp).

Hint pattern from the Mezo docs (verbatim):

```typescript
const gasCompensation = await contracts.troveManager.MUSD_GAS_COMPENSATION();
const expectedFee = await contracts.borrowerOperations.getBorrowingFee(debtAmount);
const expectedTotalDebt = debtAmount + expectedFee + gasCompensation;
const nicr = (assetAmount * BigInt(1e20)) / expectedTotalDebt;
const { '0': approxHint } = await contracts.hintHelpers.getApproxHint(nicr, 15, 42);
const { '0': upperHint, '1': lowerHint } =
  await contracts.sortedTroves.findInsertPosition(nicr, approxHint, approxHint);
await contracts.borrowerOperations.connect(wallet)
  .openTrove(debtAmount, upperHint, lowerHint, { value: assetAmount });
```

A contract can own a trove. The direct entry points pass `msg.sender` as borrower, caller and recipient, so MUSD is minted to the calling contract, and collateral comes back through `_recipient.call{value: _amount}("")`, so the vault needs a payable receive path. **[verified 2026-11-12]**

### D. Mezo Pools on testnet

| Contract | Address |
|---|---|
| Router | `0x9a1ff7FE3a0F69959A3fBa1F1e5ee18e1A9CD7E9` |
| PoolFactory | `0x4947243CC818b627A5D06d14C4eCe7398A23Ce1A` |
| MUSD/BTC pool (volatile; token0 MUSD, token1 BTC) | `0xd16A5Df82120ED8D626a1a15232bFcE2366d6AA9` |

The pack flagged the router ABI as a gap. It is now read from the verified explorer source: **[verified 2026-11-12]**

```solidity
// Route = (address from, address to, bool stable, address factory)
function swapExactTokensForTokens(uint256 amountIn, uint256 amountOutMin, Route[] routes, address to, uint256 deadline) returns (uint256[]);
function getAmountsOut(uint256 amountIn, Route[] routes) view returns (uint256[]);
function addLiquidity(address tokenA, address tokenB, bool stable, uint256 amountADesired, uint256 amountBDesired, uint256 amountAMin, uint256 amountBMin, address to, uint256 deadline) returns (uint256, uint256, uint256);
function removeLiquidity(address tokenA, address tokenB, bool stable, uint256 liquidity, uint256 amountAMin, uint256 amountBMin, address to, uint256 deadline) returns (uint256, uint256);
// PoolFactory
function createPool(address tokenA, address tokenB, bool stable) returns (address);
function getPool(address tokenA, address tokenB, bool stable) view returns (address);
function getFee(address pool, bool _stable) view returns (uint256);
// Pool
function swap(uint256 amount0Out, uint256 amount1Out, address to, bytes data); // calls IPoolCallee(to).hook(...) when data is non-empty
function getAmountOut(uint256 amountIn, address tokenIn) view returns (uint256);
function getReserves() view returns (uint256, uint256, uint256);
```

- The router has no native-BTC variants. BTC is swapped as the ERC-20 at `0x7b7C…0000` (contract `BTCCaller`: `approve`, `transferFrom`, `permit`). Its `balanceOf` equals the native balance (checked on the pool and the faucet). **[verified 2026-11-12]**
- `PoolFactory.createPool` is permissionless: a simulated call from an arbitrary address returned a pool address, and other teams' receipt tokens already have pools. **[verified 2026-11-12]**
- Read fees on chain, not from the docs: `volatileFee()` = 4 and `stableFee()` = 1 on testnet (basis points; the router's quote for 100 MUSD matches a 0.04% fee), while the docs say 0.30% and 0.02%. Do not hard-code.

### E. Savings Vault (sMUSD) on testnet: the pack gap, closed

- **Address:** `0x6f461c68B2c5492C0F5CCEc5a264d692aA7A8e16`. It is what `PCV.feeRecipient()` returns on 31611, so it is the canonical vault. `name()` "MUSD Savings Rate", `symbol()` "sMUSD", 18 decimals; proxy to implementation `0x92d12f0a60906b39d81acd9bf8977b6c824cd98c`, verified on the explorer as `MUSDSavingsRate`. **[verified 2026-11-12]** The Mezo judge's own Wave 1 reviews of AjoCircle and Agentfloat name the same address ("Mezo's sMUSD vault, which does exist on testnet at 0x6f46…8e16"), so the pack already held it inside prior-art-detail.md.
- **Interface (not ERC-4626):** `deposit(uint256 amount)` mints sMUSD 1:1 · `withdraw(uint256 amount)` burns 1:1 and also pays out the caller's yield · `claimYield() returns (uint256)` · `claimableYield(address)` · `yieldIndex()` · `receiveProtocolYield(uint256)`. Principal never changes value; yield is separate, claimable MUSD tracked by an index.
- **Yield is real and can be triggered on demand.** `PCV.distributeMUSD()` has no access modifier and sends `feeSplitPercentage` (50) percent of the PCV's MUSD to the vault; `TroveManager.updateSystemInterest()` is public and mints accrued interest to the PCV first. Both simulate without revert from an arbitrary address. On testnet the vault's own `pcv()` and `vaultGauge()` are the zero address, so deposits do not trigger a distribution by themselves; call the PCV directly. **[verified 2026-11-12]**
- **Measured rate:** `yieldIndex` rose by 0.0823 MUSD per sMUSD over 9.63 days (blocks 16,523,306 to 16,723,306), about 0.85% a day, arriving in discrete distributions. The PCV held about 17,839 undistributed MUSD at the probe. This is a testnet figure (large system debt, small vault) and must not be presented as a mainnet rate.

### F. Mechanics that bite (hard constraints)

- **BTC-only collateral.** MUSD troves take native BTC only. MUSD and MEZO cannot be posted into a trove.
- **Debt floor.** Net debt must stay at or above 1,800 MUSD (`minNetDebt`, governable), and 200 MUSD is added as a gas deposit, so a trove opens with at least 2,000 MUSD of debt. A repayment that would leave net debt under the floor reverts; the only way lower is `closeTrove`. The pooled trove therefore needs a seed that never leaves, and a wind-down path for the last holders. Reviews asked other pooled products "who funds the anchor".
- **One trove per address.** The vault contract is the borrower. A second vault needs its own address and its own floor.
- **`maxBorrowingCapacity`.** Set at open to `coll * price / 1.1`. Adding collateral does **not** raise it; withdrawing collateral can only lower it; any debt increase must satisfy `maxBorrowingCapacity >= debt + increase`. Only `refinance` recomputes it from current collateral and price. Refinance costs 0.02% of net debt, resets the trove's interest rate to the current global rate, and is blocked in Recovery Mode. A growing vault must refinance to keep borrowing (`BorrowerOperations.sol` L692–L698, L879–L899, L1012–L1105, L1358–L1365).
- **Recovery Mode (system TCR under 150%).** No collateral withdrawal at all; a debt increase needs the new ICR at or above 150% and not below the old ICR; `closeTrove` and `refinance` revert. Pure repayment and pure top-up still work. Liquidation is under 110% in every mode. In normal mode every adjustment must also leave system TCR at or above 150%.
- **`adjustTrove` cannot add and withdraw collateral in one call.** It can add collateral and borrow, or withdraw collateral and repay.
- **Fees.** 0.1% issuance fee on every debt increase (`borrowingRate`, governable), fixed interest set at open (100 bps on testnet now), 0.75% redemption fee.
- **Accounting.** `getEntireDebtAndColl` already folds pending interest into `interest`; adding it again misprices shares (a named finding in Wave 1 reviews).
- **Redemptions.** They hit the lowest-ICR troves first. A fully redeemed trove is closed and its leftover BTC waits in `CollSurplusPool` for `claimCollateral()`.
- **Stability Pool withdrawal pause.** `withdrawFromSP` with a non-zero amount reverts while the lowest trove is under 110%. This is the reason the reserve is not kept there.
- **MUSD is absent on BNB Chain.** It exists on Mezo, Ethereum and Base only.
- **Do not hard-code MUSD at $1 for anything shown as a dollar value.** A Pyth MUSD/USD feed exists (Pyth `0x2880aB155794e7179c9eE2e38200202908C17B43`, feed id `0x0617a9b725011a126a2b9fd53563f4236501f32cf76d877644b943394606c6de`).

### G. Live testnet state (measured 2026-11-12, will drift)

| Item | Value |
|---|---|
| `PriceFeed.fetchPrice()` | $73,794.69 |
| System TCR / Recovery Mode | 264.95% / false |
| Troves / lowest ICR | 362 / 118.3% (nothing is liquidatable; the Stability Pool is not frozen) |
| Interest rate / issuance fee / min net debt | 100 bps / 0.1% / 1,800 MUSD |
| MUSD/BTC pool reserves | 102.43M MUSD / 1,305.0 BTC |
| **Pool price vs oracle** | The pool trades BTC at about 78,490 MUSD, **6.4% above** the oracle price. A swap bounded tightly against `PriceFeed` will revert on testnet, so the bound's tolerance must be a per-deployment setting. Entry and exit are symmetric: a minter gets fewer BTC for borrowed MUSD, a redeemer needs fewer BTC to repay it. Show users the realizable exit value. |
| Faucet | 0.05 test BTC per request (35 of the distributor's last 50 transfers were exactly 0.05 BTC). One request opens a minimum trove: `openTrove` with 0.05 BTC and 2,000 MUSD simulates without revert. |

### H. Testing reality

A plain `anvil` fork of 31611 does **not** emulate Mezo's precompiles: on the fork `BTC.balanceOf`, `PriceFeed.fetchPrice()` and `openTrove` all revert, while the same calls succeed on the live RPC. **[verified 2026-11-12]** Fork tests therefore need shims (for example `vm.etch` or `vm.mockCall` over the BTC token at `0x7b7C…0000` and the price source), and the real precompile paths can only be proven on live testnet. The upside is that a mocked price lets fork tests stage what testnet cannot: a crash, a liquidation, Recovery Mode and a redemption of the vault's trove. Those paths will be fork-only; say so in the materials rather than claim them on chain.

### I. What the judges punished in adjacent products

Take these as acceptance checks. They are quoted or summarized from Wave 1 reviews of pooled-trove and leverage entries (prior-art-detail.md).

- Swap minimums taken from the pool's spot quote instead of `PriceFeed` (Coil); a keeper able to sandwich the pool (Coil).
- No exit or defined behavior in Recovery Mode (Coil, mbLP, TinyVault, Spend).
- No handling of redemption or liquidation of the shared trove, leaving user BTC frozen (Spend, TinyVault); no `claimCollateral` path (Coil, AgentVault).
- `maxBorrowingCapacity` ignored, so deposits sat idle (mbLP).
- Double-counted pending interest in share pricing (mbLP, Pylon, Sternpost).
- Owner functions that can redirect funds without a timelock (Lockless, MUSD Yield Vault, Pylon). Each High finding capped Technical.
- Unverified contracts, features that ran only in fork tests, usage only from the builder's own wallets, no stated fee model or keeper funding, no deck, a video over 2:15.

### J. Day-1 dependency

Test BTC from the faucet (Cloudflare-gated, so a human step): enough requests for the trove seed, the `BTC2x` pool liquidity and a second wallet that acts as an outside user. Outside testers are a human task too; dust-size mints are what make recruiting them cheap.

### K. Integration model and the longest pole

Solidity with Foundry against the canonical testnet contracts above; a TypeScript and React app using viem with `mezo-org/chains`; a small Node keeper. Pin tool and SDK versions and re-check the Mezo docs before coding, because the docs' own example links are dead and their pool fees differ from the chain. The longest pole, and the task that deserves the highest effort and the most review, is the vault's accounting across mint, redeem, rebalance, refinance and wind-down. Everything else talks to fixed, already-deployed interfaces.

## Rubric mapping (why this won, for the record)

Weights, re-mapped from the kit default (35/25/20/20) to the event's published criteria with buildability kept highest: **Intrinsic buildability 40** (includes the +5 safe-feasible shift) · **Theme and sponsor-track fit 30** (the event's Integration and Viability criteria, scored as the mean of the two) · **Demo WOW and story 15** · **Novelty 15** (after the −5 safe-feasible shift).

Twofold scored **415 of 500** (buildability 4, fit 4.5, WOW 4, novelty 4). The field was 28 candidates plus 8 bolder rewrites: 9 were knocked out at the gate and 27 were scored. Next best were a BTC-plus-savings index token and a yield-to-BTC savings vault (380 each), then a per-user loop router and a PriceFeed-settled prediction market (365 each, both duplicates of filed entries).

The highest raw score, fixed-rate savings by splitting sMUSD into principal and yield tokens (425), fell to 335 at the head-to-head. Three teams already have it deployed on testnet: Tenor (contracts verified on 2026-11-09, 14 principal-token holders, its own Mezo pools), "Fixed MUSD", and "Prism" (possibly the Wave 1 entry PRISM Teleport). Tenor and Fixed MUSD are not on the AKINDO list yet.

Knocked out at the buildability gate and never scored: ideas whose money shot needs a governance rate change, a liquidation or a live price gap (the lowest testnet ICR is 118% and the builder cannot move the oracle); a hedge that needs a short venue Mezo lacks; cross-chain builds that need mainnet funds or testnet bridge routes the pack could not confirm; and every vote-escrow reward product, because a reward claim needs an epoch flip and the next one (2026-11-19 00:00 UTC) falls after submissions close.
