# Mezo, part 3 of 3: network, RPCs, cross-chain MUSD/MEZO, bridges, wallet connection, x402, repos

Sources (fetched 2026-11-11/12; see INDEX.md): [D-GS] https://mezo.org/docs/developers/getting-started · [D-CONN] https://mezo.org/docs/users/getting-started/connect · [D-CR] https://mezo.org/docs/users/resources/contracts-reference · [D-MB] https://mezo.org/docs/users/borrow/musd-bridge · [D-MZB] https://mezo.org/docs/users/mezo/mezo-bridge · [D-FAQ] https://mezo.org/docs/developers/getting-started/faqs · [D-PASS] …/configure-mezo-passport · [D-X402] …/getting-started/musd-payments-x402 · [D-REQ] …/getting-started/dapp-requirements · [D-SUB] https://mezo.org/docs/developers/subgraphs · [GH-ORG] `gh api orgs/mezo-org/repos` · [CHAIN] extractor probes 2026-11-12.

## Network parameters

| | Testnet | Mainnet |
|---|---|---|
| Chain ID | `31611` ([D-GS], [D-CONN]; probe → `0x7b7b`) ✓ | `31612` ([D-GS], [D-CONN]; probe via Boar) ✓ |
| RPC (HTTPS) | `https://rpc.test.mezo.org` ✓ | Boar `https://mezo-mainnet.boar.network` ✓ · Imperator `https://rpc_evm-mezo.imperator.co` · Validation Cloud `https://mainnet.mezo.public.validationcloud.io` · dRPC `https://mezo.drpc.org` ([D-GS]) |
| RPC (WSS) | `wss://rpc-ws.test.mezo.org` | `wss://mezo-mainnet.boar.network` etc. |
| Explorer | https://explorer.test.mezo.org (HTTP 200 ✓) | https://explorer.mezo.org (HTTP 200 ✓) |
| Faucet | https://faucet.test.mezo.org/ (HTTP 200 ✓): "test BTC and MEZO" | — |
| dApp | https://testnet.mezo.org (HTTP 200 ✓; injects nothing itself; the user's wallet provides `window.ethereum`) | https://mezo.org |
| Gas token | "BTC (via tBTC under the hood)" [D-FAQ]. BTC is the native coin at `0x7b7C000000000000000000000000000000000000` (ERC-20 view, `decimals()` 18 ✓) | same |
| Chainlist | https://chainlist.org/chain/31611 | https://chainlist.org/chain/31612 |

- **Gotcha:** the Earn dev guide's sample uses `https://rpc.mezo.org`. The extractor's `eth_chainId` POST to it returned no body (2026-11-11), so use the providers in [D-CONN].
- Hardhat config sample in [D-GS] uses `url: "https://rpc.test.mezo.org", chainId: 31611`. Mezo is "fully EVM-compatible … Hardhat and Foundry" [D-FAQ]. viem chain config: `mezo-org/chains` ("Mezo chain configuration for Viem").
- Gas for users without BTC: "Get Gas feature to swap a small amount of MUSD or MEZO for BTC gas when your balance is low" (…/getting-started/get-gas). The x402 path is "gas sponsored" (below).

## MUSD and MEZO on other chains (addresses + live bytecode check)

| Token | Mezo | Ethereum (1) | Base (8453) | BNB Chain (56) | Solana |
|---|---|---|---|---|---|
| **MUSD** | `0xdD468A1DDc392dcdbEf6db6e34E89AA338F9F186` ✓ | `0xdD468A1DDc392dcdbEf6db6e34E89AA338F9F186` ✓ 6436 B, `decimals` 18 | `0xdD468A1DDc392dcdbEf6db6e34E89AA338F9F186` ✓ 6436 B, `decimals` 18 | **none**: 0 bytes at that address (probe via `bsc-rpc.publicnode.com`); not listed in [D-CR] | — |
| **MEZO** | `0x7B7c000000000000000000000000000000000001` ✓ | `0x8e4cbBcc33dB6c0a18561fDE1F6bA35906d4848b` ✓ 5070 B | `0x8e4c…848b` ✓ 5070 B | `0x8e4c…848b` ✓ 5070 B | `8niMFW4yuv3vLoqTtBaC6rchyasmUhgvpgSyPEeeCrw6` |

- `mezo-org/musd` deployment artifacts include `ethereum/MUSD.json` (same address) plus `TokenDeployer` on ethereum, base and **bsc** (`0x255e7CE3aBc1280891Cd74fdFb560a7C1708495E`), but **no `bsc/MUSD.json`**. **[inference]** A BSC deployment was prepared but MUSD is not live there.
- Event page vs facts: the event says "Extend MUSD and MEZO on Mezo, Ethereum, Base, and BNB Chain". On BNB Chain only **MEZO** exists.

## Bridge mechanism: Wormhole Native Token Transfer (NTT)

- MUSD [D-MB] verbatim: "The MUSD bridge enables transfers between Mezo, Ethereum, and Base networks using Wormhole's Native Token Transfer (NTT) protocol." · "From Mezo to Ethereum/Base: MUSD tokens are locked on Mezo and the equivalent tokens are minted on the destination chain" · "From Ethereum/Base to Mezo: MUSD tokens are burned on the source chain and equivalent tokens are unlocked on Mezo". UIs: the Mezo dApp (Mezo↔Ethereum) and the Portal UI https://portalbridge.com/ (Mezo↔Ethereum↔Base).
- MEZO [D-MZB] verbatim: "The MEZO bridge enables transfers between Mezo and multiple networks including Ethereum, Base, BSC, and Solana using Wormhole's Native Token Transfer (NTT) protocol."
- NTT contracts [D-CR]: **MUSD**: Mezo NTT Manager `0x7efb386675d75280D39Aae42964A6776DE0ee0bD`, Transceiver `0x56E27f1A8425515FFD4BD76A254Ac1a5c0B66D71` · Ethereum Manager `0x5293158bf7a81ED05418DA497a80F7e6Dbf4477E`, Transceiver `0x76ddB3f1dDe02391Ef0A28664499B74C29d18d3E` · Base Manager `0x3EB418BdBE95b4b9cf465ecfBD8424685ACD1Bc1`, Transceiver `0x15C465E7dF34f8cA06FDCae0569206cEDf3f4467`. **MEZO**: Mezo Manager `0x5E668D912F69db0762CD0fE00647dA9fa6b29591`, Transceiver `0x528edf2dBbC6Ae6978c88E54B260AB86B682D18c` · Ethereum `0x13916D0daB357DCBAa1600b594d62C641840686A` / `0x920871aF2D4106E76d204fEA7122fA129C9283b1` · Base `0x0c46f496C410465975a427e34a976fc15a2edE4f` / `0x27321f84704a599aB740281E285cc4463d89A3D5` · BSC `0x09959798B95d00a3183d20FaC298E4594E599eab` / `0xa10aD2570ea7b93d19fDae6Bd7189fF4929Bc747` · Solana `Ntt4AnEASZ9oLw25PTmXFrwSFD473ufd3rCLWoX5Gg7` / `6aVRLvdjgrovCiZa5q5kifUtvD6p2ogaQ2J248MpfCa3`.
- Repos: `ntt-bridge-musd-mainnet`, `ntt-bridge-musd-testnet` ("NTT bridge contracts and toolings for MUSD on testnets"), `ntt-bridge-mezo-mainnet`, `ntt-bridge-mezo-testnet`, `demo-ntt-ts-sdk` [GH-ORG]. **Testnet bridge routes (which testnets, addresses): GAP**, not extracted.
- Native BTC in: tBTC Portal / BitcoinDepositor contracts on Ethereum and Sepolia are listed in [D-CR] (Portal Proxy mainnet `0xAB13B8eecf5AA2460841d75da5d5D861fD5B8A39`, Sepolia `0x6978E3e11b8Bc34ea836C1706fC742aC4Cb6b0Db`). Bridged assets on Mezo (mUSDC `0x04671C72…c197`, mUSDT `0xeB5a5d39…bB8E`, mcbBTC, mSolvBTC, mDAI, mUSDe, mT and others) are in [D-CR].

## Wallet connection: Mezo Passport

- [D-PASS] verbatim: "Mezo Passport is a package built on top of RainbowKit and provides additional wallet connection options specifically tailored for Bitcoin wallets and Mezo." npm `@mezo-org/passport`.
- Reviews asked for it: "add WalletConnect or Mezo Passport" (MUSD Compass) [REV]. A Bitcoin-wallet connection path is a plausible UX/integration plus.

## MUSD payments via x402 (relevant mainly to Track 2)

- [D-X402] verbatim table: "Mezo Testnet `eip155:31611` `0x118917a40FAF1CD7a13dB0Ef56C86De7973Ac503`" · "Mezo Mainnet `eip155:31612` `0xdD468A1DDc392dcdbEf6db6e34E89AA338F9F186`" · "Facilitator `https://facilitator.vativ.io` (serves both networks)" · "Settlement proxy `0x402085c248EeA27D92E8b30b2C58ed07f9E20001`" · "EIP-712 domain name `Mezo USD`, version `1` — distinct from the `MUSD` symbol" · "Transfer method `permit2` + EIP-2612". **Gotcha:** the EIP-712 domain name is `Mezo USD`, not `MUSD`, so permit signatures break if you use the symbol.

## Indexing and data

- Subgraphs via Goldsky [D-SUB]; repo `mezo-org/subgraphs` is referenced by the docs (schema, mappings) but **does not appear in the public org listing** [GH-ORG] (gap; may be private or renamed).
- Network stats and dashboards: …/users/resources/network-stats (not extracted). Community monitor named in [D-CR]: "mezotools.cc" ("Check real-time Trove health … View recent system-wide redemptions and liquidations").

## Ecosystem bar for being featured (context for "long-term commitment")

- [D-REQ] verbatim: "dApps on Mezo must meet the following requirements to be featured in the Mezo Market and receive promotional support: MUSD Integration … Audit Report: The dApp must have completed a third-party security audit. The report must be submitted to the Supernormal Foundation. … Mainnet Functionality: The dApp must be fully deployed and functional on Mezo Mainnet."
- Audits: repo `mezo-org/audits` ("The collection of security audits performed for Mezo") and …/users/resources/audits.

## mezo-org GitHub repos (public, sorted by last push; [GH-ORG] 2026-11-12)

| Repo | Description (verbatim) | Last push |
|---|---|---|
| documentation | — | 2026-11-09 |
| mezod | Reference client implementation for Mezo chain. | 2026-11-05 |
| musd | Smart contracts and the dapp for MUSD | 2026-10-26 |
| chains | Mezo chain configuration for Viem | 2026-10-26 |
| validator-kit | The Validator Kit is a collection of tools and documentation helping to run a validator no[de] | 2026-10-22 |
| ntt-bridge-mezo-mainnet | (Wormhole NTT fork) | 2026-10-20 |
| audits | The collection of security audits performed for Mezo | 2026-04-28 |
| ntt-bridge-musd-testnet / -mainnet | NTT bridge contracts and toolings for MUSD on testnets / mainnets | 2026-03 |
| tigris (archived) | Smart contracts powering the Mezo gauge system and DEX, inspired by Solidly. | 2025-11-18 |
| demo-ntt-ts-sdk | — | 2025-09-08 |
| thUSD | Threshold USD monorepo containing the contracts, SDK and Dev UI frontend. | 2025-01-22 |
| (others) | balance-exporter, go-ethereum, keep-common, homebrew-tap, safe-deployments, sourcify, evm-chain-list, cosmos-sdk, pre-commit-hooks, AllocationsRaw | — |

**No official "example contracts" repo was found.** The docs' `musd/tree/main/examples` link is 404 and `Demo.test.ts` is not in the tree (see `mezo-musd.md`). The page's "example contracts" pointer goes to https://mezo.org/docs/ in general.

## Gated or unextracted (gaps)

- Mezo Discord (https://discord.mezo.org) and Telegram (https://t.me/mezonetwork) are gated; not joined. That is where testnet sMUSD and veMEZO/BoostVoter addresses and the Wave-3 question would be answered.
- Kickoff workshop recording (https://www.youtube.com/live/eAiaQpzvVE0): transcript not captured.
