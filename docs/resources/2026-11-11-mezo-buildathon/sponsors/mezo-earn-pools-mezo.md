# Mezo, part 2 of 3: Mezo Earn (Savings Vault / sMUSD, vaults), Mezo Pools, veBTC / veMEZO / gauges, MEZO, oracles

Sources (fetched 2026-11-11/12; see INDEX.md): [D-SV] https://mezo.org/docs/users/mezo-earn/vaults/musd-savings-vault · [D-VN] …/vaults/vault-notices · [D-USDC] …/vaults/usdc-lending-vault · [D-DITTO] …/vaults/ditto-musd-savings-vault · [D-POOLS] https://mezo.org/docs/developers/features/mezo-pools · [D-EARN] https://mezo.org/docs/developers/features/mezo-earn/mezo-earn · [D-INC] …/mezo-earn/deploying-incentives · [D-VEMEZO] https://mezo.org/docs/users/mezo-earn/lock/vemezo (+ boost-mechanism) · [D-VEBTC] …/lock/vebtc · [D-GAUGES] …/vote/mezo-gauges · [D-MEZO] https://mezo.org/docs/users/mezo · [D-ORA] https://mezo.org/docs/developers/architecture/oracles/read-oracle · [D-PF] …/pools/pools-fees · [D-PL] …/pools/pools-links-and-resources · [CHAIN] extractor probes 2026-11-12 · [REV] Wave 1 judge reviews. All docs were fetched as raw `.md` from `https://mezo.org/docs/<path>.md`.

## 1. MUSD Savings Vault (sMUSD)

- Verbatim [D-SV]: "Deposit MUSD and receive sMUSD — a receipt token representing your share of the vault" · "Yield accumulates in the sMUSD exchange rate: over time, 1 sMUSD becomes redeemable for more than 1 MUSD." · "Yield comes from two sources within the MUSD system: MUSD protocol fees (lending interest, origination fees, refinancing fees) and BTC fees from MUSD loan operations, which are converted to MUSD and distributed weekly".
- Vault details table (verbatim): Deposit token MUSD · Receipt token sMUSD · Strategist Mezo · Withdrawal fee None · Withdrawal time-lock 0h · Current APR Variable.
- **Gauge trade-off (verbatim):** "Staked sMUSD: Your portion of interest and fee revenue is redirected to veBTC voters on the gauge. In exchange, you earn emissions based on how many votes the gauge receives". "The MUSD Savings Rate gauge competes for votes alongside LP pool gauges".
- Fee split: "MUSD protocol fees are split 50/50 between … MUSD Savings Vault … [and] Protocol bootstrap loan repayment … with a minimum of 50% going toward loan repayment until the bootstrap loan is fully repaid. After repayment, all fees flow to the Savings Vault."
- **Address:** mainnet `0xb4D498029af77680cD1eF828b967f010d06C51CC` (the only address in the docs, from the link "mezo.org/earn/vaults/0xb4D4…"). [CHAIN]: 1159 bytes (proxy) on 31612; `decimals()` = 18; `asset()` and `totalAssets()` **reverted**, so do not assume an ERC-4626 interface. Read the implementation on the explorer. **0 bytes on testnet 31611.** **Testnet sMUSD address: GAP** (not in docs; ask in Discord or find via the testnet explorer).
- Judges treated sMUSD routing as a real integration step: "putting idle lender MUSD to work through sMUSD" (Doji), "Baserate … with sMUSD, Tigris and veBTC bribes all used in one loop" [REV]. Plumb's review notes its "testnet vault has gauge and sMUSD set to zero" (so the testnet wiring was missing).

## 2. Other vaults (context; state as of the docs)

- [D-VN] (verbatim table): "BTC Vault — Winding down. Deposits are closed. — Withdraw by October 28, 2026" · "cbBTC Vault — Deposits are closed. Migration to the BTC Vault has ended." · "Stablecoin Vault — Deposits are paused and the vault is winding down". **Don't build on these.**
- **USDC Lending Vault** [D-USDC]: "Supply mUSDC to the BTC-backed Morpho lending market on Mezo and earn borrower interest or MEZO emissions". Addresses (mainnet): Morpho Vault V2 (`morphoBTC-mUSDC`) `0x06291b67e3d7660240ab44Afc9a708d82b976a8B` · Lending Vault adapter `0xd3f6F147662Bf2943ca09ee16beDaEa28AE28788` · Vault gauge `0x11E98DEc5B1965E4eB872552E64Ef8580bBBbae7` · mUSDC `0x04671C72Aab5AC02A03c1098314b1BB6B560c197`. So **Morpho Blue is deployed on Mezo mainnet** (Baserate built "the first MUSD market on Mezo's Morpho Blue" [REV]; Surety's testnet used "a self-deployed Morpho" [REV], meaning there is no known Mezo-official Morpho on testnet).
- **Ditto MUSD Savings Vault** [D-DITTO]: "Deposit MUSD on Mezo and receive dMUSD for an automated cross-chain vault with an initial allocation to Spark Savings"; vault page `0x9171Cb787C3fEEbBC808D07CaB62B1d789CE14F8`; "Approx. 3.60% as of September 29, 2026, in line with Spark Savings — variable".
- **aMUSD** (contracts reference): "the receipt token users get for depositing in the Morpho Alpha MUSD Core Vault. It is currently only available on Ethereum." Ethereum `0x52317a47585A6ACDfbD7a29B494c3E2baAE96aBc`.

## 3. Mezo Pools (DEX)

- [D-POOLS] verbatim: "Basic pools use an Aerodrome-style AMM with either constant-product (volatile) or stable-curve (stable) pricing." · "Swap Fees: 0.30% for volatile pools, 0.02% for stable pools" · "Position Type: Fungible LP tokens (ERC-20)". CL pools: "Mezo's CL implementation is based on Velodrome's Slipstream" · "Position Type: Non-fungible (ERC-721 NFTs via NonfungiblePositionManager)" · "Built-in TWAP Oracle: Each CL pool maintains a time-weighted average price oracle". CL tick spacing → default fee: 1→0.01%, 10→0.05%, 50→0.05%, 100→0.05%, 200→0.30%, 2,000→1.00%. "An `unstakedFeeModule` controls the portion of swap fees redirected from unstaked to staked positions (default: 10%)."
- Swap (basic) verbatim: "Call router's `swapExactTokensForTokens(...)` with path array". [D-EARN] code: `routerContract.swapExactTokensForTokens(amountIn, minAmountOut, [tokenIn, tokenOut], to, deadline)` and `addLiquidity(tokenA, tokenB, amountA, amountB, minA, minB, …)`. **[inference]** The Aerodrome router's real `Route` struct takes a `stable` flag. Check the deployed ABI on the explorer before coding against the docs' simplified call. CL: `exactInputSingle(...)` / `exactInput(...)`; NFPM `mint`, `increaseLiquidity`, `decreaseLiquidity`, `collect`.
- **Repo:** `mezo-org/tigris` — "Smart contracts powering the Mezo gauge system and DEX, inspired by Solidly." (archived 2025-11-18). Reviews call the pools "Tigris".

| Contract | Mainnet (31612) | Testnet (31611) |
|---|---|---|
| Router | `0x16A76d3cd3C1e3CE843C6680d6B37E9116b5C706` ✓ 18209 B | `0x9a1ff7FE3a0F69959A3fBa1F1e5ee18e1A9CD7E9` ✓ 18209 B |
| PoolFactory | `0x83FE469C636C4081b87bA5b3Ae9991c6Ed104248` | `0x4947243CC818b627A5D06d14C4eCe7398A23Ce1A` ✓ |
| MUSD/BTC pool (volatile) | `0x52e604c44417233b6CcEDDDc0d640A405Caacefb` | `0xd16A5Df82120ED8D626a1a15232bFcE2366d6AA9` ✓ (45 B, minimal proxy) |
| MUSD/mUSDC pool (stable) | `0xEd812AEc0Fecc8fD882Ac3eccC43f3aA80A6c356` | `0x525F049A4494dA0a6c87E3C4df55f9929765Dc3e` |
| MUSD/mUSDT pool (stable) | `0x10906a9E9215939561597b4C8e4b98F93c02031A` | `0x27414B76CF00E24ed087adb56E26bAeEEe93494e` |
| CLFactory | `0xBB24AF5c6fB88F1d191FA76055e30BF881BeEb79` | `0x7B61BC8Aa460476d142F1CD107A47297002f69ff` |
| CLSwapRouter | `0x37cDd11919ec3860eaD9efB8673d7476E5326225` | `0x3112908bB72ce9c26a321Eeb22EC8e051F3b6E6a` ✓ |
| NonfungiblePositionManager | `0x509Bc221df2B83927c695FA0bb0f5B21053C874c` | `0x9B753e11bFEd0D88F6e1D2777E3c7dac42F96062` ✓ |
| CLGaugeFactory | `0xfc41E1AAe0e58E8bDC32e85d8C995A902FEdEb13` | `0x5b0dbAfdcE363d6662F36163D91862B0a3808373` |
| CLPool impl / CLGauge impl | `0x819C…3E5F` / `0x8f11…9c33` | `0xfB28…19CD` / `0x1aE1…a3EE` |

Other mainnet pools [D-PL]: mcbBTC×BTC `0x72E6b3F126cF4F6C90C08114aC29038A0E269210` · msolvBTC×MUSD `0x5Cd2A025C001E07Ae354A4C22C3009908De1aC59` · msolvBTC×BTC `0xf6f950485b0A65828F07581Ca979ef1271778d6A` · mUSDC/MUSD stable CL pool `0xCC372B7E15535aB225fe17c1075831D38ef7aC1a` ([D-VN]). Off-Mezo MUSD pools [D-PL]: Uniswap (Ethereum) tBTC×MUSD, USDC×MUSD, ETH×MUSD (v4 pool ids in the doc); Curve (Ethereum) USDC×USDT×MUSD `0xB5571E76693ba60110B5811DD650FFefce1C955f`, sUSDe×MUSD `0x765Cbd88947fcBc5df1F763d02E384B0a2DD285E`; Aerodrome (Base) USDC/MUSD and MEZO/MUSD ([D-GAUGES]).

## 4. veBTC, veMEZO, gauges, boost (vote-escrow)

- **veBTC** [D-VEBTC]: lock BTC; "Minimum lock 1 day" · "Maximum lock 28 days" · "Lock decay Linear". Earns "Voting power to direct emissions", "Protocol fees from chain activity and bridging", and as voter: "Swap fees from pools you vote for", "MUSD interest/fee revenue if you vote for the MUSD Savings Rate gauge", "Incentives that protocols or users post to attract votes". "Each lock can vote once per epoch".
- **veMEZO** [D-VEMEZO]: "veMEZO is the tokenized (NFT) representation of MEZO locked on Mezo Network. Locking MEZO lets you boost your veBTC voting power by up to 5x … and earn anti-dilution rebases via MEZO emissions." "Minimum lock 1 week" · "Maximum lock 4 years (1,456 days)". [D-MEZO]: "veMEZO positions are ERC-721 NFTs that can be transferred or merged" · "veMEZO cannot vote on staking gauges without veBTC."
- **Boost** (verbatim): "Maximum multiplier: 5x" · "Relative, not absolute — Your boost depends on your share of total veBTC and total veMEZO, not raw amounts" · "If you hold 1% of all veBTC, you need at least 1% of all veMEZO to reach the maximum 5x multiplier." A **matching market** pairs veBTC and veMEZO holders (…/vemezo/matching-market).
- **MEZO Gauges** [D-GAUGES]: veMEZO votes direct emissions **off Mezo** as incentives to Uniswap USDC/MUSD (Ethereum, Merkl), Curve USDT/USDC/MUSD (Ethereum, Merkl), Aerodrome USDC/MUSD and MEZO/MUSD (Base). "MEZO Gauges are funded from the non-staking gauge branch of emissions, currently 8% of weekly emission rewards."
- **Creating gauges** [D-INC] (verbatim): "All Mezo assets (BTC, MEZO, and mainnet contract tokens) have been whitelisted in the PoolsVoter contract. Anyone can now create voting gauges for…". PoolsVoter (mainnet) `0x48233cCC97B87Ba93bCA212cbEe48e3210211f03` → `createPoolGauge`.
- **Governance contracts** [D-POOLS]: mainnet VeBTC `0x7D807e9CE1ef73048FEe9A4214e75e894ea25914` ✓ · VeBTCVoter `0x3A4a6919F70e5b0aA32401747C471eCfe2322C1b` · VeBTCRewardsDistributor `0x535E01F948458E0b64F9dB2A01Da6F32E240140f` · VeBTCEpochGovernor `0x1494102fa1b240c3844f02e0810002125fb5F054` · ChainFeeSplitter `0xcb79aE130b0777993263D0cdb7890e6D9baBE117`. Testnet VeBTC `0xB63fcCd03521Cf21907627bd7fA465C129479231` ✓ · VeBTCVoter `0x72F8dd7F44fFa19E45955aa20A5486E8EB255738` ✓ · VeBTCRewardsDistributor `0x10B0E7b3411F4A38ca2F6BB697aA28D607924729` · VeBTCEpochGovernor `0x12fda93041aD8aB6d133aE4d038b5159033d937a` · ChainFeeSplitter `0x63aD4D014246eaD52408dF3BC8F046107cbf6065`. **veMEZO / BoostVoter addresses: GAP** (not in the docs fetched; Wave 1 entries Janus and Boost Relay used "BoostVoter"/"BoostVote" on testnet [REV]).
- **Gotcha [REV]:** "ValidatorsVoter is a zero address on testnet, so describe it as mainnet-only in your materials" (Doji review).

## 5. MEZO token

- [D-MEZO]: "The native token for boosting voting power and value capture"; MEZO is liquid; veMEZO is the locked NFT.
- Addresses (contracts reference + [CHAIN]): Mezo `0x7B7c000000000000000000000000000000000001` ✓ (3021 B on testnet; `decimals()` 18) · Ethereum/Base/BSC `0x8e4cbBcc33dB6c0a18561fDE1F6bA35906d4848b` ✓ (5070 B on each; `decimals()` 18 on Ethereum) · Solana `8niMFW4yuv3vLoqTtBaC6rchyasmUhgvpgSyPEeeCrw6`. Bridge: Wormhole NTT (see `mezo-network.md`).
- Emissions/distribution: …/users/mezo/emissions ("Bitcoin-inspired halving") and …/token-distribution. Not extracted in detail (time-box).
- Faucet gives test MEZO ([P1]: "You'll get test BTC and MEZO").

## 6. Oracles

- **Skip BTC/USD (Chainlink-compatible)** [D-ORA] verbatim: "The Skip oracle implements a Chainlink-compatible interface. Call `latestRoundData()` to retrieve the latest price". Address `0x7b7c000000000000000000000000000000000015` on mainnet and testnet ✓ (585 B on testnet).
- **Pyth** [D-ORA]: "Use `getPriceNoOlderThan(pair_id, maxAgeSeconds)`". Mezo mainnet and testnet `0x2880aB155794e7179c9eE2e38200202908C17B43` ✓ · Ethereum `0x4305FB66699C3B2702D4d05CF36551390A4c69C6` · Sepolia `0xDd24F84d36BF92C65F92307595335bdFab5Bbd21`. Feed ids (verbatim): MUSD/USD `0x0617a9b725011a126a2b9fd53563f4236501f32cf76d877644b943394606c6de` · MEZO/USD `0x80beaaedbdd228e77c5d62dfcd74b0305674b7e27a5cc6a46e71bd3a696826df` · BTC/USD `0xe62df6c8b4a85fe1a67db44dc12de5db330f7ac66b72dc658afedf0f4a415b43` · USDC/USD `0xeaa020c61cc479712813461ce153894a96a6c00b21ed0cfc2798d1f9a9e9c94a` · USDT/USD `0x2b89b9dc8fdf9f34709a5b106b472f0f39bb6ca9ce04b0fd7f2e971688e2e53b` (more in the doc: SolvBTC, cbBTC, T, equities).
- MUSD's own `PriceFeed.fetchPrice()` returns the BTC/USD price MUSD uses for ICR (18 dp on testnet, read 73,879.74e18 on 2026-11-12).
- Judges flagged price liveness: "Close the open risk gap on MUSD and MEZO price liveness (a second oracle leg or a Mezo-provided feed)" (Mezodot review).
