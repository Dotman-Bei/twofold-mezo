# Mezo, part 1 of 3: MUSD (borrowing, troves, Stability Pool, redemptions)

Sponsor: Mezo (Thesis) / Supernormal Foundation. Parts 2 and 3: `mezo-earn-pools-mezo.md` (sMUSD, Pools, veBTC/veMEZO, MEZO, oracles) and `mezo-network.md` (chain params, RPCs, cross-chain tokens, bridges, Passport, x402, repos).

Sources (fetched 2026-11-11/12, see INDEX.md):
[D-MUSD] https://mezo.org/docs/developers/musd ·
[D-RED] https://mezo.org/docs/developers/musd/musd-redemptions ·
[D-FEES] https://mezo.org/docs/users/borrow/fees ·
[D-LIQ] https://mezo.org/docs/users/borrow/liquidation-mechanics ·
[GH] https://github.com/mezo-org/musd (`main`: `solidity/contracts/*.sol`, `solidity/artifacts/deployments/{mainnet,matsnet}/*.json`) ·
[CHAIN] the extractor's read-only JSON-RPC probes, 2026-11-12 (`eth_getCode` / `eth_call` on `rpc.test.mezo.org` and `mezo-mainnet.boar.network`; raw output in `../data/chainprobe-2026-11-12.json`) ·
[REV] Wave 1 judge reviews (AKINDO API).

## What MUSD is

- [D-MUSD] verbatim: "MUSD is a collateralized debt position (CDP) based on Threshold USD, which is a fork of Liquity." · "A user opens up a position by calling `BorrowerOperations.openTrove`, providing BTC, and requesting MUSD. The BTC is routed to the `ActivePool`".
- Peg: "price floor of $1" via redemption at 1:1 (`TroveManager.redeemCollateral`); "price ceiling of $1.10 via the minimum 110% collateralization ratio".
- Key changes from THUSD (verbatim): "Fixed-Interest Borrowing: Interest rates are fixed when a trove is opened and can be refinanced." · "Protocol Controlled Value (PCV)" · "EIP-712 Signature Verification: Allows for gasless transaction authorizations." · "No Special Recovery Mode Liquidations: Liquidations follow a single process."
- Stability Pool bootstrap (verbatim): "MUSD's Stability Pool is initially populated with a bootstrapping loan. This MUSD can only be used for liquidations." There are no token rewards for SP depositors described in the docs.
- Upgradability (verbatim): "MUSD smart contracts are upgradable to allow for fixes." All listed addresses are proxies ([D-RED]: "All addresses are proxy contracts.").

## Contract addresses (mainnet 31612 and testnet 31611)

From [GH] deployment artifacts (`mainnet` = 31612, `matsnet` = 31611; `.chainId` files read). Where marked ✓, [CHAIN] confirmed the code exists (bytes; 1159 = proxy). [D-RED] lists the same six addresses for TroveManager, HintHelpers, SortedTroves, BorrowerOperations, PriceFeed and MUSD (all match).

| Contract | Mainnet (31612) | Testnet (31611) |
|---|---|---|
| MUSD (token) | `0xdD468A1DDc392dcdbEf6db6e34E89AA338F9F186` ✓ 6436 B | `0x118917a40FAF1CD7a13dB0Ef56C86De7973Ac503` ✓ 6437 B |
| BorrowerOperations | `0x44b1bac67dDA612a41a58AAf779143B181dEe031` ✓ | `0xCdF7028ceAB81fA0C6971208e83fa7872994beE5` ✓ |
| BorrowerOperationsSignatures | `0xB57ab578BF20b3e318f3EFAA587C51DBccE5df7a` | `0xD757e3646AF370b15f32EB557F0F8380Df7D639e` ✓ |
| TroveManager | `0x94AfB503dBca74aC3E4929BACEeDfCe19B93c193` ✓ | `0xE47c80e8c23f6B4A1aE41c34837a0599D5D16bb0` ✓ |
| StabilityPool | `0x73245Eff485aB3AAc1158B3c4d8f4b23797B0e32` ✓ | `0x1CCA7E410eE41739792eA0A24e00349Dd247680e` ✓ |
| HintHelpers | `0xD267b3bE2514375A075fd03C3D9CBa6b95317DC3` | `0x4e4cBA3779d56386ED43631b4dCD6d8EacEcBCF6` ✓ |
| SortedTroves | `0x8C5DB4C62BF29c1C4564390d10c20a47E0b2749f` | `0x722E4D24FD6Ff8b0AC679450F3D91294607268fA` ✓ |
| PriceFeed | `0xc5aC5A8892230E0A3e1c473881A2de7353fFcA88` | `0x86bCF0841622a5dAC14A313a15f96A95421b9366` ✓ |
| InterestRateManager | `0x4a453700d157717Fe02fB62E7700ED7845048285` | `0xD4D6c36A592A2c5e86035A6bca1d57747a567f37` ✓ |
| ActivePool | `0x3012C2fE1240e3754E5C200A0946bb0E07474876` | `0x143A063F62340DA3A8bEA1C5642d18C6D0F7FF51` ✓ |
| DefaultPool | `0xE4B5913C0c82dB2eFC553b95c0173efb90a07c8B` | `0x59851D252090283f9367c159f0C9036e75483300` |
| CollSurplusPool | `0xBF51807ACb3394B8550f0554FB9098856Ef5F491` | `0xB4C35747c26E4aB5F1a7CdC7E875B5946eFa6fa9` |
| GasPool | `0x3EB418BdBE95b4b9cf465ecfBD8424685ACD1Bc1` | `0x8fa3EF45137C3AFF337e42f98023C1D7dd3666C0` |
| PCV | `0x391EcC7ffEFc48cff41D0F2Bb36e38b82180B993` | `0x4dDD70f4C603b6089c07875Be02fEdFD626b80Af` ✓ |
| GovernableVariables | `0x560AC4Ea44Fb7EB2D4d3c00608CB1CAb2613d389` | `0x6552059B6eFc6aA4AE3ea45f28ED4D92acE020cD` |

Note: the mainnet GasPool address `0x3EB4…1Bc1` equals the **Base** MUSD NTT Manager address in the docs' contracts reference (same deployer nonce on different chains). It's harmless, but don't confuse the two.

## Constants and live values ([GH] source + [CHAIN] reads, 2026-11-12)

| Item | Source value | On-chain read |
|---|---|---|
| `MCR` (min collateral ratio) | `1.1e18` "110%" (LiquityBase.sol L22) | testnet `TM.MCR()` = 1.1e18 |
| `CCR` (Recovery Mode threshold) | `1.5e18` "150%" (L25) | testnet `TM.CCR()` = 1.5e18 |
| `MUSD_GAS_COMPENSATION` | `200e18` (L28) | testnet BO and TM = 200e18; mainnet TM = 200e18 |
| `minNetDebt` | `minNetDebt = 1800e18;` in `initialize` (BorrowerOperations.sol L144); governable, floor `MIN_NET_DEBT_MIN = 50e18`, change needs `proposeMinNetDebt` then `approveMinNetDebt` after 7 days | testnet = 1800e18; mainnet = 1800e18 |
| Liquidation collateral bonus | `PERCENT_DIVISOR = 200` "dividing by 200 yields 0.5%" (L30) | — |
| `MUSD.decimals()` | — | 18 on 31611, 31612, Ethereum, Base |
| Interest rate | `uint16 public interestRate` in InterestRateManager (governable; `MAX_INTEREST_RATE = 10_000`, `MIN_DELAY = 7 days`) | not read |
| Testnet state (context) | — | PriceFeed `fetchPrice()` = 73,879.74e18 (BTC/USD, 18 dp); TroveManager `getTroveOwnersCount()` = 361; StabilityPool `getTotalMUSDDeposits()` ≈ 86.2M MUSD; MUSD `totalSupply()` ≈ 524M |

Fees ([D-FEES], verbatim table): "Issuance fee 0.1% of borrowed MUSD — Opening or increasing a loan" · "Interest 1–5% APR (fixed at open) — Accrues on outstanding debt" · "Redemption fee 0.75% — Exchanging MUSD for BTC collateral" · "Refinance fee 0.02% of debt — Refinancing a loan to a new rate" · "Gas deposit 200 MUSD (flat) — Opening a loan (returned on close)". Gas deposit detail (verbatim): "The gas deposit is minted as extra debt in the loan and held in escrow until the loan is closed. This debt counts towards calculating the collateralization ratio." Fee routing (verbatim): "Fees are split between two destinations: (1) repaying the protocol bootstrap loan and (2) the MUSD Savings Vault. The initial split is 50/50 and is governable via the MUSD splitter."

## Entry-point signatures ([GH] `solidity/contracts`, `main`)

**BorrowerOperations**
```solidity
function openTrove(uint256 _debtAmount, address _upperHint, address _lowerHint) external payable; // BTC as msg.value
function addColl(address _upperHint, address _lowerHint) external payable;
function withdrawColl(uint256 _amount, address _upperHint, address _lowerHint) external;
function withdrawMUSD(uint256 _amount, address _upperHint, address _lowerHint) external;
function repayMUSD(uint256 _amount, address _upperHint, address _lowerHint) external;
function adjustTrove(uint256 _collWithdrawal, uint256 _debtChange, bool _isDebtIncrease, address _upperHint, address _lowerHint) external payable;
// "It therefore expects either a positive msg.value, or a positive _collWithdrawal argument. If both are positive, it will revert."
function closeTrove() external;
function refinance(address _upperHint, address _lowerHint) external;
function claimCollateral() external; // "Claim remaining collateral from a redemption or from a liquidation with ICR > MCR"
function getBorrowingFee(uint256 _debt) public view returns (uint);
function moveCollateralGainToTrove(address _borrower, address _upperHint, address _lowerHint) external payable; // Stability Pool only
```
**BorrowerOperationsSignatures** (EIP-712, act for a borrower via signature): `openTroveWithSignature`, `addCollWithSignature`, `withdrawCollWithSignature`, `withdrawMUSDWithSignature`, `repayMUSDWithSignature`, `adjustTroveWithSignature`, `closeTroveWithSignature`, `refinanceWithSignature`, `claimCollateralWithSignature`, `getNonce(address)`. (Full parameter lists: read the `.sol` file. Wave 1's Mezher used `withdrawMUSDWithSignature` to "borrow from the payer's trove straight to the merchant" [REV].)

**TroveManager**: `liquidate(address _borrower)` · `batchLiquidateTroves(address[] _troveArray)` · `redeemCollateral(uint256 _amount, address _firstRedemptionHint, address _upperPartialRedemptionHint, address _lowerPartialRedemptionHint, uint256 _partialRedemptionHintNICR, uint256 _maxIterations)` (parameter names per [D-RED]) · `getTCR(uint256 _price)` · `checkRecoveryMode(...)` · `getCurrentICR(address, uint256 price)` · `getEntireDebtAndColl(address)` · `getTroveMaxBorrowingCapacity(address)` · `MUSD_GAS_COMPENSATION()`.

**StabilityPool**: `provideToSP(uint256 _amount)` · `withdrawFromSP(uint256 _amount)` · `withdrawCollateralGainToTrove(...)` · `getDepositorCollateralGain(address)` · `getCompoundedMUSDDeposit(address)` · `getTotalMUSDDeposits()`.

**HintHelpers**: `getApproxHint(...)`, `getRedemptionHints(...)`, `computeNominalCR(...)`, `computeCR(...)`. **SortedTroves**: `findInsertPosition(nicr, prevId, nextId)`, `getLast()`. **PriceFeed**: `fetchPrice()` (view). **InterestRateManager**: `interestRate()`, `getAccruedInterest()`, `updateSystemInterest()`.

## Integration model and code (verbatim from [D-MUSD])

```typescript
// Compute expected total debt by adding gas compensation and fee
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
Liquidation: `troveManager.liquidate(borrower)` / `batchLiquidateTroves(addrs)`. Redemption without hints (verbatim, [D-RED] Option A): `_firstRedemptionHint 0x000…0`, upper/lower partial hints = your address, `_partialRedemptionHintNICR 1100000000000000000000`, `_maxIterations 0`. With hints: `HintHelpers.getRedemptionHints(amount, price, 50)` → `SortedTroves.findInsertPosition(NICR, you, you)` → `redeemCollateral(...)`.
Dev setup ([D-MUSD]): Node 18+, pnpm, Foundry; `git clone https://github.com/mezo-org/musd.git`. **Doc-rot gap:** [D-MUSD] links `musd/tree/main/examples` and `test/integration/Demo.test.ts`; neither path exists in the repo tree at fetch time (the `examples` path returns HTTP 404).

## Mechanics that bite (docs + source + judge reviews)

- **Contract structure.** A trove is one per address (Liquity). Any wrapper that pools or tranches troves (vaults, loan NFTs, sub-accounts) needs a contract or proxy per position, or a pooled trove. Wave 1 Deed and Annie's "Assumable" used per-position vault contracts controlled by NFTs.
- **Small loans are impossible natively:** net debt ≥ 1,800 MUSD plus the 200 MUSD gas deposit means total opening debt is at least 2,000 MUSD. Wave 1/2 entries worked around it by pooling (TinyVault "Borrow from 10 MUSD", Microtrove "Borrow 25 to 200 MUSD against $50 of bitcoin", Spend "small-borrower layer").
- **`maxBorrowingCapacity` per trove** is set at open from collateral/price and can only shrink on collateral withdrawal (BorrowerOperations L692–L897). The mbLP review: "handle MUSD's maxBorrowingCapacity (for example through refinance, or by resizing the trove) so the vault can grow past roughly 0.27 BTC without new deposits sitting idle". Mezher and RentOuts were also told to handle it.
- **Interest accounting:** "getEntireDebtAndColl already folds pendingInterest into interest, so adding it again misprices shares after a redistribution" (mbLP review). "fix close() so it accounts for pending redistribution debt" (Deed review).
- **Recovery Mode** (TCR < 150%): BorrowerOps restricts operations (`_requireNotInRecoveryMode`, "BorrowerOps: Operation not permitted during Recovery Mode"; adjustments must satisfy `_requireValidAdjustmentInRecoveryMode`). Liquidation is still only below 110% ("MUSD liquidates only below 110% in any mode", Lifeline review). Reviewers asked almost every borrow product to handle Recovery Mode in the UI and in its contracts.
- **Redemptions hit the lowest-ICR troves above 110% first** ([D-RED]). A redemption that would leave a trove below 1,800 MUSD net debt returns MUSD instead. A fully redeemed trove's leftover BTC needs `claimCollateral()`. Reviews asked for redemption-risk handling and a "come-back flow for redeemed trove borrowers".
- **`adjustTrove` cannot add and withdraw collateral in one call** (reverts if both are positive). Lifeline was told to "switch protect() to a single adjustTrove so mixed BTC+MUSD rescues below 110% don't revert".
- **Check max borrow at execution time:** price moves between quote and tx (participant note, [P4]; consistent with source).
- **MUSD price:** don't hard-code $1. Surety was told to "Add a MUSD/USD price feed or depeg check in place of the hard-coded $1". A Pyth MUSD/USD feed id is in `mezo-earn-pools-mezo.md`.
- **Verify your contracts** on the Mezo explorer (Blockscout; Sourcify-backed). Unverified sources were penalized repeatedly in reviews.

## Verification of third-party claims (from a competitor's comment, 2026-10-31)

| Claim | Verdict | Evidence |
|---|---|---|
| "minimum loan size is 1,800 MUSD, and with the 200 MUSD gas deposit total debt at opening is at least 2,000 MUSD" | **CONFIRMED** (current value; governable) | Source: `minNetDebt = 1800e18;` (BorrowerOperations.sol L144), `_requireAtLeastMinNetDebt(vars.netDebt)` on open, `MUSD_GAS_COMPENSATION = 200e18` (LiquityBase.sol L28). Chain: `minNetDebt()` = 1800e18 on 31611 and 31612; `MUSD_GAS_COMPENSATION()` = 200e18. Docs: [D-RED] "minimum debt requirement of 1,800 MUSD"; [D-FEES] "Gas deposit 200 MUSD (flat)". Nuance: net debt = requested debt + 0.1% issuance fee, and governance can lower `minNetDebt` (floor 50 MUSD) after a 7-day delay. |
| "MUSD uses 18 decimals on testnet" | **CONFIRMED** | `decimals()` on `0x1189…c503` (31611) = 18. Also 18 on mainnet, Ethereum and Base; x402 docs: "MUSD asset (18 decimals)". |
| "the Savings Vault address listed in the docs has no code on chain 31611" | **CONFIRMED** (it is a mainnet address) | The only Savings Vault address in the docs, `0xb4D498029af77680cD1eF828b967f010d06C51CC` (linked as mezo.org/earn/vaults/…), has **0 bytes on 31611** and **1159 bytes (proxy) on 31612**. The docs list **no testnet sMUSD address** (gap). Reviews imply one exists ("deposits into sMUSD on testnet", MUSD Compass) but don't give it. |
| "collateral is BTC only (via tBTC); MUSD is the debt asset, not a collateral asset" | **CONFIRMED** (for MUSD's CDP) | `openTrove(...) external payable` and the docs' call passes `{ value: assetAmount }`; "providing BTC" [D-MUSD]. BTC is Mezo's native gas asset, "BTC (via tBTC under the hood)" (dev FAQ). Third-party venues can still take MUSD as collateral (e.g. Morpho Blue markets), but MUSD's own troves cannot. |
| "Stability Pool withdrawals pause while any trove is under 110%" | **CONFIRMED** (nuance) | `withdrawFromSP(uint256 _amount)`: `if (_amount != 0) { _requireNoUnderCollateralizedTroves(); }`, which reads `sortedTroves.getLast()` (lowest ICR) and requires `ICR >= MCR`, else "StabilityPool: Cannot withdraw while there are troves with ICR < MCR" (StabilityPool.sol L172–L174, L565–L572). Lowest-ICR ≥ 110% is equivalent to "no trove under 110%". A zero-amount withdrawal (claiming collateral gains only) is not blocked. |
