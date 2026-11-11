# Resource pack: Mezo Buildathon (AKINDO WaveHack), Wave 2, Track 1

Step 0a (resource-extractor) output for idea-forge and the architect. Extracted 2026-11-11 23:40 → 2026-11-12 ~00:20 WAT (UTC+1) by a `claude-opus-5-5` session. Tollgate: `docs/tollgate/2026-11-11-tollgate.md`.
**Live wave: Wave 2. Working deadline Sun 2026-11-15 15:00 UTC = 16:00 WAT** (API-exact; widget and body agree on the submission deadline; judging-end and "3rd Wave" contradictions are in event.md §1).

## Contents

| File | What it holds |
|---|---|
| `event.md` | deadline + timeline contradictions, eligibility, submission requirements + the full AKINDO form field list, judging criteria with exact weights (30/30/20/10/10), how Wave 1 was actually scored (integration ladder, ×2 scale, deck cap), prize mechanics (proportional points, 10% fee, MEZO at 14-day TWAP, KYB), chains (MUSD absent on BNB), testnet vs mainnet, key Terms clauses |
| `tracks.md` | both tracks verbatim (challenge question, examples, requirement) and what the judges' principles and Wave 1 scores reward |
| `sponsors/mezo-musd.md` | MUSD: mainnet + testnet addresses (verified on chain), constants (min debt, gas deposit, MCR/CCR), fees, entry-point signatures, hint/open/redeem code, mechanics that bite, **verdicts on the five third-party claims** |
| `sponsors/mezo-earn-pools-mezo.md` | sMUSD Savings Vault, other vaults (Morpho USDC, Ditto, wind-downs), Mezo Pools (basic + CL, router, mainnet + testnet addresses), veBTC / veMEZO / boost / gauges, MEZO token, oracles (Skip, Pyth + feed ids) |
| `sponsors/mezo-network.md` | chain params and RPCs, explorers, faucet, gas, MUSD/MEZO on Ethereum/Base/BNB/Solana (on-chain checked), Wormhole NTT bridge contracts, Passport, x402 facts, subgraphs, dApp-featuring bar, mezo-org repos |
| `prior-art.md` | **all 148 products** (135 W1 + 45 W2 submissions) by lane, lane crowding vs Wave 1 payouts, a check of the guide's crowded-lane read, Track 1 highlights, **judge feedback patterns** |
| `prior-art-detail.md` | per-entry block: tagline, categories, tech, links, Wave 1 result + **verbatim judge review**, Wave 2 update excerpt |
| `data/prior-art-entries.json` | machine-readable entries (lane, scores, links, reviews, W2 update text) |
| `data/chainprobe-2026-11-12.json` | raw output of the read-only RPC probes (getCode / eth_call) |
| `data/akindo-waves-2026-11-12.json` | AKINDO API wave objects (deadlines, flags) |
| `data/musd-deployment-addresses-from-repo.txt` | addresses parsed from `mezo-org/musd` deployment artifacts |

## Headline facts for idea-forge (each sourced in the files above)

1. Score = points share of a $5,000 pool across **all** Wave 2 entries (both tracks), ranked relatively; "more complete and ready projects will get better points" (official comment).
2. Integration (30%) follows a 5-rung ladder; the top needs several Mezo primitives exercised **on chain** plus outside users. Read-only integration caps at L3.
3. A missing deck caps Materials at 1/5 (76 of 135 Wave 1 entries took that cap). The video must be ≤ ~2 minutes.
4. MUSD troves: BTC-only collateral, ≥1,800 MUSD net debt + 200 MUSD gas deposit, MCR 110%, Recovery Mode below TCR 150%, SP withdrawals blocked while the lowest trove is <110%. All CONFIRMED in source and on chain.
5. MUSD lives on Mezo, Ethereum and Base (Wormhole NTT); **not on BNB Chain** (only MEZO is there).
6. Wave 1's best-paid lanes (lending/credit on Mezo primitives; ve/boost markets) are thin or empty in Wave 2 so far; loan protection and payments are crowded. Wave 1 leaders may still file Wave 2.

## Provenance

| # | Source | URL | Fetched (WAT) | Tool | Primary / secondary | Confidence / gaps |
|---|---|---|---|---|---|---|
| P1 | AKINDO event page (Overview body, timeline widget, sidebar, Comments) | https://app.akindo.io/wave-hacks/ovoo0gdrvu8379d10 | 2026-11-11 23:50 | Chrome (`get_page_text`, JS link dump) | primary | High for body text. The widget renders dates in the browser tz (WAT). Comments are user content (data). Judges tab not opened (runsheet: "No judges yet"). |
| P2a | AKINDO public API: waves | https://api.akindo.io/public/wave-hacks/OVOO0gdrVU8379D10/waves | 2026-11-11 23:50 | curl (endpoint found via `read_network_requests`) | primary | High (exact ISO deadlines, fee 0.100, flags). Wave 2 `grantAmount` 0 is an API oddity (event.md §5). |
| P2b | AKINDO public API: submission summaries (W1: 14 pages; W2: 5 pages) | …/waves/Ql9ePKmoDCBNoQ9n/submission-summaries?page=1..14&limit=10 · …/waves/WjDnR6LJaSBkVkQz/submission-summaries?page=1..5&limit=10 | 2026-11-11 23:51 | curl | primary | High; counts match the UI (135/45/148). Wave 2 is still open, so entries can change. |
| P2c | AKINDO public API: per-product wave submissions (148 products) incl. judge votes/comments | https://api.akindo.io/public/products/{productId}/wave-submissions | 2026-11-12 ~00:00 | curl | primary | High; reviews verbatim. One participant email redacted. |
| P2d | Sample product page (MUSD Pay Links), Voter Reviews tab | https://app.akindo.io/communities/RDgkLQzMni6M9mm98/products/Pv1lNjOBGIjwEZZj?tab=voterReviews | 2026-11-11 23:58 | Chrome | primary | Used to locate the review API; layout check only. |
| P3 | Terms of Participation (Google Doc) | https://docs.google.com/document/d/1oY1hzzub2l_jHdovmsAaE3YBuRJh0_UQXxL1Zd2g3pE/edit (fetched via `/export?format=txt`) | 2026-11-11 23:49 | curl | primary | High. Differs from the page on chains ("BSC, or Robinhood"), materials (no deck) and KYC vs KYB wording; §8 has no item (a). |
| D1 | Mezo docs index (llms.txt) | https://mezo.org/docs/llms.txt | 2026-11-11 23:50 | curl | primary | High; used to enumerate pages. |
| D2 | Mezo docs: 49 pages as raw markdown (`https://mezo.org/docs/<path>.md`), incl. developers/musd, musd-redemptions, features/mezo-pools, features/mezo-earn/*, architecture/oracles/*, bridge/*, chains, getting-started/* (incl. faqs, dapp-requirements, configure-mezo-passport, musd-payments-x402), subgraphs; users/resources/contracts-reference, users/getting-started/connect, users/borrow/* (fees, architecture, liquidation-mechanics, musd-bridge), users/mezo-earn/* (vaults, savings vault, notices, Ditto, USDC lending, pools, fees, links, veMEZO, boost, matching market, veBTC, gauges), users/mezo/* (overview, bridge, emissions), users/mainnet/bridges, users/integrations/community-projects, users/resources/{release-notes,audits} | https://mezo.org/docs/developers/ (root) | 2026-11-11 23:56 | WebFetch (landing page) + curl (raw .md) | primary | High for quoted parts. Not deeply read (time-box): emissions schedule, token distribution, validator docs, community projects, release notes, mainnet bridges. |
| G1 | mezo-org GitHub org repo list | https://github.com/mezo-org | 2026-11-12 00:00 | `gh api orgs/mezo-org/repos` | primary | High. `subgraphs` repo referenced by docs is not public or listed. |
| G2 | `mezo-org/musd` source (BorrowerOperations, StabilityPool, TroveManager, LiquityBase, BorrowerOperationsSignatures, InterestRateManager, HintHelpers, PriceFeed) and deployment artifacts (`solidity/artifacts/deployments/{mainnet,matsnet,ethereum,base,bsc,sepolia}`) | https://github.com/mezo-org/musd (branch `main`) | 2026-11-12 00:02 | `gh api` tree + raw.githubusercontent.com | primary | High (read at `main` HEAD on that date; no commit SHA pinned). Docs links to `examples/` and `Demo.test.ts` are dead. |
| C1 | Mezo testnet RPC probes (chainId, getCode ×23, eth_call ×12) | https://rpc.test.mezo.org | 2026-11-12 00:05 | Python urllib JSON-RPC (read-only) | primary | High; raw in `data/chainprobe-2026-11-12.json`. |
| C2 | Mezo mainnet RPC probes | https://mezo-mainnet.boar.network | 2026-11-12 00:05 | same | primary | High. `https://rpc.mezo.org` (used in a docs sample) returned no body. |
| C3 | Ethereum / Base / BSC token bytecode probes | https://ethereum-rpc.publicnode.com · https://mainnet.base.org · https://bsc-rpc.publicnode.com | 2026-11-12 00:06 | same + curl | primary (chain state) | High. `bsc-dataseed.binance.org` failed DNS; used publicnode instead. |
| U1 | testnet dApp, faucet, explorers (reachability; wallet-provider presence) | https://testnet.mezo.org · https://faucet.test.mezo.org · https://explorer.test.mezo.org · https://explorer.mezo.org | 2026-11-11 23:48 | curl (HTTP status) + Chrome (JS `typeof window.ethereum`) | primary | Reachability only. Nothing connected, claimed or signed. |
| R1 | Guide runsheet (prior light read: protocol-fee text, judge comments, crowded lanes) | `docs/guide/2026-11-11-mezo-buildathon-runsheet.md` (this repo) | 2026-11-11 | local file | secondary | Used only for cross-checks; every reused fact was re-sourced above or marked secondary. |

## Gaps (honest unknowns)

- **Mezo Discord / Telegram:** gated, not joined (per instructions). Unanswered there: Wave 3 status, testnet sMUSD address, veMEZO/BoostVoter testnet addresses.
- **Kickoff workshop (2026-10-13) recording** https://www.youtube.com/live/eAiaQpzvVE0: transcript not captured (time-box; no quickly reachable text transcript tried). What Mezo said live about scoring is therefore not in the pack; the published criteria and 135 written reviews cover scoring instead.
- **Testnet Savings Vault (sMUSD) address:** not in the docs; the docs' address is mainnet-only (0 bytes on 31611).
- **veMEZO / BoostVoter / matching-market contract addresses:** not in the docs fetched.
- **Mezo Pools router ABI details** (Aerodrome `Route` struct vs the docs' simplified path array): verify on the explorer before coding.
- **Savings Vault interface:** `asset()` / `totalAssets()` reverted on mainnet, so it is not plain ERC-4626; read the implementation.
- **"Robinhood" chain in the Terms:** unexplained; the page's list governs.
- **Wave 2 field:** live; entries and edits can change until 2026-11-15 15:00 UTC. Lane labels are the extractor's classification.
- AKINDO "Judges" tab: not opened (the runsheet recorded "No judges yet"); every Wave 1 review is by `civ_defi_mezo`.
- AKINDO and Supernormal mechanics beyond the above: shallow by design.

## Hand-off

idea-forge should read this pack as its primary source: event.md for the rubric and constraints, tracks.md for the challenge question, prior-art.md for white space and head-to-heads, and sponsors/ for feasibility. The architect should treat `sponsors/mezo-musd.md` §Mechanics that bite and the claims table as hard constraints.
