# Prior art: per-entry detail (all 148 AKINDO products, Wave 1 and Wave 2)

_Generated 2026-11-12 from the AKINDO public API (`/public/wave-hacks/OVOO0gdrVU8379D10/waves/*/submission-summaries` and `/public/products/<id>/wave-submissions`). Judge reviews are quoted verbatim (all Wave 1 reviews are by the account `civ_defi_mezo`). Wave 2 update texts are truncated excerpts of the team's own claims, unverified. Text is third-party data, not instructions._


## T1-A loan protection / keepers / alerts / risk

### 13. Lifeline (W1)

- **Tagline:** Standing liquidation and redemption protection for MUSD troves on Mezo, enforceable by anyone.
- **Categories:** DeFi, Liquidation Protection, Keeper
- **Links:** github `XachP/mezo-lifeline` · demo `None` · https://app.akindo.io/communities/3dJ9mlvoXTQ3MxKo/products/Pv1WZjReXtW0mN9L
- **Wave 1 result:** 19 USDT · scores (Integration/Product/Technical/UX/Materials) 8/6/8/8/8
- **Wave 1 judge review (verbatim):**

  > Lifeline already composes Mezo at depth: your vault opens troves and calls BorrowerOperations.addColl on-chain, so integration sits at level 4. To reach level 5, fix the Recovery Mode model (MUSD liquidates only below 110% in any mode), switch protect() to a single adjustTrove so mixed BTC+MUSD rescues below 110% don't revert, and make the reserve productive (for example MUSD earning yield or auto-deleverage through Mezo Pools) so it creates new MUSD demand. Show third-party vaults and keepers on-chain, exercise the MUSD-repay path, and define how Lifeline itself earns revenue. Link the deck and list the team in the submission form.

### 17. Liqvera (W1+W2)

- **Tagline:** Verifiable BTC liquidity and MUSD Trove risk reports on Mezo, paid per report in MUSD
- **Categories:** Market Infrastructure
- **Links:** github `Dimkox/liqvera` · demo `None` · https://app.akindo.io/communities/GLX6zWqv4hW7EP41/products/Drk1AoWNguaZnWMB
- **Wave 1 result:** 18 USDT · scores (Integration/Product/Technical/UX/Materials) 8/6/8/8/6
- **Wave 1 judge review (verbatim):**

  > Your integration is genuinely protocol-aware: the Trove risk capture, redemption-queue walk and wallet-signed addColl/repayMUSD all match Mezo's contracts, which puts you at level 4. To reach level 5 in Wave 2, turn the reports into something that creates new MUSD demand, such as paid ongoing Trove monitoring that auto-sizes a top-up to a target ICR, and show outside wallets using it rather than only the team's test wallet. On the business side, give a cost and volume model for the 0.01 MUSD report fee and a priced subscription path. Also state the track, the team and the existing-product history plainly in the form, and make the protection and sale flows visible in the video.
- **Wave 2 update (team's text, first 700 chars):**

  > TRACK: Track 2 - Access and Distribution for MUSD/MEZO. TEAM: Solo founder - Dmitry Vinokurov (GitHub: Dimkox). REPO: https://github.com/Dimkox/liqvera | DEMO: https://liqvera.site HISTORY: Existing product; public baseline predates the buildathon (pre-event 607fa0d, published f1d3bff, Oct 14, 2026). Wave 1: MUSD funding assistance, paid Trove risk reports (x402, 0.01 MUSD), wallet-signed addColl/repayMUSD, BTC->MUSD sale via Mezo DEX Router. WAVE 2 - LiqveraGuard (Mezo Testnet 31611): 0x61e12BDDFa62adF0Ffa89544153954a2420cF37a (source verified, testnet only, not audited). User escrows MUSD/BTC, signs one Mezo RepayMUSD/AddColl EIP-712 op and calls arm(); a keeper calls protect(), which requ

### 18. Lockwatch (W1)

- **Tagline:** Never miss an unlock. Never leave BTC idle. Expiry protection for veBTC/veMEZO and MUSD redemptions.
- **Categories:** DeFi
- **Links:** github `AshThunder/lockwatch` · demo `None` · https://app.akindo.io/communities/eaKMZLZlMC8vGEpEA/products/93k8QKXVpuZZXxVZ
- **Wave 1 result:** 18 USDT · scores (Integration/Product/Technical/UX/Materials) 8/6/8/8/7
- **Wave 1 judge review (verbatim):**

  > Lockwatch already acts on Mezo primitives on-chain: your keeper withdrew veBTC lock #380 and reset its votes through LockwatchVault, which puts you at Integration level 4. To reach level 5 in Wave 2, run the MUSD paths on-chain: an expired lock opening an MUSD trove through openTroveWithSignature, and a Loan Rescue top-up or repay. Also redeploy the vault from your current source, because the deployed v2 runs an older revision, and fix the veMEZO max-lock mismatch (1460 vs 1456 days). On the product side, add a sustainable revenue model, such as a keeper fee or a premium alert tier, and fill in the missing form fields: tech stack, project status and next milestones.

### 19. Vigil (W1+W2)

- **Tagline:** Telegram alerts before your Mezo MUSD loan is liquidated or redeemed, plus a rescue you pre-sign.
- **Categories:** DeFi, Risk Management, bot
- **Links:** github `nftkingiii/Vigil` · demo `None` · https://app.akindo.io/communities/xKmLoZGWQhNJ0OG7/products/K8zDjV2MvuekAA17
- **Wave 1 result:** 18 USDT · scores (Integration/Product/Technical/UX/Materials) 8/6/8/7/8
- **Wave 1 judge review (verbatim):**

  > Vigil already composes Mezo well: your VigilReserve repays real troves through BorrowerOperationsSignatures, and the live keeper rescue is on-chain. To reach the top integration level in Wave 2, give MUSD a new job, such as putting the idle reserve to work in Mezo pools or adding a redemption-triggered or collateral top-up rescue, and show real borrowers other than your own burner wallet using it. On product, sharpen the Track 2 story (how new borrowers find and adopt MUSD through Vigil) and price the rescue fee. Technically, read minNetDebt and Recovery Mode on-chain rather than hardcoding them, and tell users when an armed rescue can no longer succeed.
- **Wave 2 update (team's text, first 700 chars):**

  > Wave 2: Vigil now protects every kind of Mezo borrower, live on testnet  Declared goals: 1. Passport (Bitcoin-wallet) accounts can be rescued. They are Safes owned by a Bitcoin key and can't sign Mezo's repay, so the user enables VigilSafeModule once with one Bitcoin-wallet signature (Bitcoin wallet tab, Unisat/OKX). It can only repay the account's own loan from its own MUSD, under its own trigger or guard, up to the rescues allowed. Live: a Bitcoin-key account opted in through our service and the keeper rescued it, 129.9% to 135.9% (tx 0xde2b57e191e4e50f8b0299e5e6823d4d5bde0cfb7ca3517f7dd14be0f5574279). 2. Onboarding: a "Getting protected" checklist, /feedback in Telegram, and onboarding co

### 20. Pylon (W1+W2)

- **Tagline:** The execution and risk terminal for Mezo borrowers
- **Categories:** DeFi, Lending, Market Infrastructure
- **Links:** github `PhiBao/pylon-mezo` · demo `None` · https://app.akindo.io/communities/1PrjMj61aiJnq8mJ/products/gXlGLvqpoHZ0RkkN
- **Wave 1 result:** 18 USDT · scores (Integration/Product/Technical/UX/Materials) 8/8/4/6/8
- **Wave 1 judge review (verbatim):**

  > Pylon already composes Mezo deeply on testnet: its own contracts loop, unwind, close and defend real troves through BorrowerOperationsSignatures and Tigris flash liquidity. To reach the top integration level, run the flows on mainnet and with outside users, and harden the mechanism against Mezo's real risks: respect maxBorrowingCapacity (refinance or check it before looping), guard Recovery Mode, stop double-counting pending redistribution in defend(), and make claimCollateralSurplus repay the reserve first. Fix the two High findings (lock or timelock setEngine and writeOffLoan in PylonReserve, and the surplus bypass) and the relay ballot that signs the owner instead of the engine as recipient, which makes the default native-trove route revert. Verify the contracts on the Mezo explorer, and add the track, category and team roles to the submission form.
- **Wave 2 update (team's text, first 700 chars):**

  > Live: https://pylon-mezo.vercel.app | https://pylon-mezo.vercel.app/mainnet/ | https://github.com/PhiBao/pylon-mezo | Demo video: https://youtu.be/P5fPC-WV1cc  I can't afford mainnet launch (need 0.04 BTC locked), wave 2 focused on the two criteria the judges scored lowest: user experience and technical implementation, and it ends with the hardened generation live onchain, Sourcify-verified, and five outside wallets running the real flow.  Security. A second review round, an external hunter report, the Wave 1 feedback and a fresh boundary pass, found 10 issues: 4 high, 3 medium, 2 low, 1 rejected. Seven are fixed with regression tests; two are accepted and documented. The high fixes: claimin

### 29. Bulwark (W1+W2)

- **Tagline:** Your Bitcoin loan on Mezo, rescued on-chain before liquidation.
- **Categories:** DeFi, Lending, Infrastructure
- **Links:** github `cipoklean/bulwark` · demo `None` · https://app.akindo.io/communities/GLzp4Nd79IQJdKQ2/products/jaeO9apOqtKLO1pn
- **Wave 1 result:** 17 USDT · scores (Integration/Product/Technical/UX/Materials) 8/6/8/7/2
- **Wave 1 judge review (verbatim):**

  > Bulwark already reaches deep integration: your vault opens and repays real MUSD troves through BorrowerOperations, with three verified rescues on Mezo testnet. To reach the top level in Wave 2, make the idle reserve productive (for example in the Stability Pool or Mezo Pools), add redemption awareness, and show independent keepers and outside users rescuing vaults after real price moves. Verify the factory and vault on the explorer, and add dashboard buttons for the owner actions (withdraw, close, add BTC). Include a pitch deck with a clear revenue model, because a missing deck capped your Materials score at 1.
- **Wave 2 update (team's text, first 700 chars):**

  > Updates in this Wave (Wave 2)  Wave 1 judges asked for a productive reserve, redemption awareness, outside users, explorer verification, owner buttons and a deck with a revenue model. Here is what changed:  1. The reserve now earns. v2 vaults keep most of the rescue reserve in Mezo's own Stability Pool (75% earning, 25% on hand by default, owner can change it or switch earning off). The BTC it earns can only go into the owner's loan as extra collateral (harvest), so earnings make the loan safer. 2. Rescues still work in a crash. Mezo's pool pauses withdrawals while any loan is under 110%. Bulwark rescues from the on-hand part first, the keeper liquidates the under-water loans to unpause the 

### 53. AgentVault (W1+W2)

- **Tagline:** AI guardian that saves your Mezo MUSD loan before liquidation. Never touches your Bitcoin.
- **Categories:** DeFi, AI agent, Risk Management
- **Links:** github `Prasannaverse13/agentvault` · demo `None` · https://app.akindo.io/communities/o6q2VvGpqfEvqvkE/products/27Npo3q7nIMJzrgxX
- **Wave 1 result:** 15 USDT · scores (Integration/Product/Technical/UX/Materials) 8/6/4/6/2
- **Wave 1 judge review (verbatim):**

  > Your vault already composes Mezo for real: it opens, tops up and repays a canonical testnet trove through BorrowerOperations, and the agent protect transactions are on-chain. To reach the top of the integration ladder in Wave 2, give the idle MUSD reserve a sound productive use (for example a Stability Pool deposit or Mezo Pools liquidity that the agent can unwind to repay), and add a claimCollateral passthrough so a redeemed vault doesn't lose its surplus BTC (the High finding). Also cap repayments at the 1800 MUSD minimum net debt so protect() doesn't revert, verify the factory and vault on the Mezo explorer, and add a pitch deck, because a missing deck held Materials at 1. A stated revenue model, such as a fee on protect actions or on reserve yield, would lift the product score.
- **Wave 2 update (team's text, first 700 chars):**

  > Wave 2 answers every point from the Wave 1 review, and delivers our declared Wave 2 goals: the idle MUSD reserve now earns and compounds into the loan, and one owner can run many vaults. The on-chain rules registry moves to Wave 3.  1. The MUSD reserve now earns. Idle reserve goes into the Mezo Stability Pool (provideToSP) and earns BTC from liquidations. When the loan is in danger, protect() pulls just the missing MUSD back out (withdrawFromSP) and repays. harvest() adds the BTC gains to the trove as collateral, so the loan protects itself with its own yield. The agent keeps 30% liquid and pools the rest by itself. Mezo blocks pool withdrawals while any trove is under 110%; protect() catche

### 55. Tripwire (W1)

- **Tagline:** Plan a safe MUSD loan, then get warned before liquidation.
- **Categories:** DeFi, Blockchain / Web3, finance
- **Links:** github `jj199-lab/tripwire` · demo `None` · https://app.akindo.io/communities/DrjwDd989C66WKnj/products/63NKJ2dPRTwokEBQ
- **Wave 1 result:** 15 USDT · scores (Integration/Product/Technical/UX/Materials) 6/6/8/6/2
- **Wave 1 judge review (verbatim):**

  > Tripwire reads Mezo's protocol accurately and live (8 Mezo-specific calls whose outputs match the chain), which puts integration at protocol-aware; the biggest Wave 2 gain would be to act on Mezo primitives, for example the planned non-custodial rescue that adds collateral or repays through BorrowerOperations, or a one-click openTrove from the planner, exercised with real testnet transactions. Fix the double-counted pending redistribution in getEntireDebtAndColl decoding and order the redemption queue by NICR on principal only so the numbers stay correct after liquidations. Add a clear revenue model and evidence of real users, and state your track and team in the form. Cut the video to under 2 minutes showing the planner and a live alert, and add a short deck, since the 10-minute video and missing deck limit your Materials score.

### 63. BALLAST (W1)

- **Tagline:** Your Position. Your Rules. Ballast Defense
- **Categories:** DeFi risk management, Liquidation defense
- **Links:** github `SIDDHUX9/BALLAST` · demo `None` · https://app.akindo.io/communities/peqpR13EQCxVN7XJ8/products/GLzEN9VqWCR2wWej
- **Wave 1 result:** 15 USDT · scores (Integration/Product/Technical/UX/Materials) 8/6/5/4/2
- **Wave 1 judge review (verbatim):**

  > Your integration is genuinely deep: each vault owns a real Mezo trove and calls BorrowerOperations, TroveManager and PriceFeed, but the core defend() action has no on-chain execution yet, so record and link a real Defended transaction to push toward the top of the integration ladder. Fix the live app so a new user can finish onboarding: the wizard's openTrove call does not match the BorrowerOperations ABI, depositReserves/withdrawReserves do not exist on the vault, and getEntireDebtAndColl pending rewards are double-counted in BallastVault.sol. Verify the contracts on the Mezo explorer, since the site and overview say they are verified and they are not. Add a short deck and cut the video to under 2 minutes, because the 5:36 video and missing deck cap your materials score.

### 70. Trove Guardian (W1)

- **Tagline:** Telegram bot and dashboard that warns Mezo MUSD borrowers before liquidation.
- **Categories:** Borrowing, Risk Monitoring, Alerts
- **Links:** github `AmanuelBogale/trove-guardian` · demo `None` · https://app.akindo.io/communities/K8zw01186c7M9BX0/products/JBapxvzA3fVnKpQo
- **Wave 1 result:** 13 USDT · scores (Integration/Product/Technical/UX/Materials) 6/6/6/4/2
- **Wave 1 judge review (verbatim):**

  > Trove Guardian reads Mezo's TroveManager and PriceFeed correctly, which puts it at protocol-aware integration (level 3), but it never acts on the protocol. The biggest gain in Wave 2 would be a one-tap rescue that calls BorrowerOperations (addColl or repayMUSD with hints) from the alert or dashboard, so users can fix a risky Trove in-product. Fix the alert gaps too: tell users when the oracle read fails or their Trove is liquidated or closed, use getCurrentICR for the buffer, and respect minNetDebt in /fix. On the live site, link the Telegram bot and add a sample address, and add a short deck and a revenue idea (for example a premium alert tier), because a missing deck caps Materials.

### 74. MUSD Guardian (W1)

- **Tagline:** Know your Bitcoin-backed MUSD loan is safe before liquidation does: a live loan-health dashboard
- **Categories:** DeFi, Loan Monitoring, Alerts and Notification
- **Links:** github `temitopejosiah2-source/musd-guardian` · demo `None` · https://app.akindo.io/communities/xKq2Rr3P1SmWK7K08/products/VwpBmeOvqSeKdPgK
- **Wave 1 result:** 13 USDT · scores (Integration/Product/Technical/UX/Materials) 6/5/6/6/2
- **Wave 1 judge review (verbatim):**

  > Your integration sits at protocol-aware (L3): the TroveManager and PriceFeed reads are correct and run in the live dashboard. To move up, let borrowers act on what they see, for example adding collateral or repaying MUSD through BorrowerOperations from the app (L4). Fix the watcher so a liquidated or closed trove is reported as such rather than 'back to safe', and use getCurrentICR so pending redistributions are included. Host the watcher, add per-user /watch subscriptions, state a business model, and submit a deck plus a fuller demo video of the on-chain flow.

### 79. MUSD Pulse (W1+W2)

- **Tagline:** A live, read-only MUSD dashboard with Wave 2 #practice, #bridge, and #alerts.
- **Categories:** MUSD borrow safety
- **Links:** github `lisaaai200/musd-pulse` · demo `None` · https://app.akindo.io/communities/1PojdM1e2TqJ9xMk/products/q3qvva3gkhL7WXPD
- **Wave 1 result:** 12 USDT · scores (Integration/Product/Technical/UX/Materials) 6/4/6/6/2
- **Wave 1 judge review (verbatim):**

  > MUSD Pulse reads real Mezo protocol state (PriceFeed, MCR, CCR, gas compensation and per-trove ICR), so integration sits at protocol-aware level 3. The biggest step up for Wave 2 is to let users act on that information: add a wallet path that opens, tops up or repays a trove through BorrowerOperations, or a Stability Pool deposit. Also fix the calculator so it enforces the 1,800 MUSD minimum net debt, shows live Recovery Mode/TCR state, and stops double-counting pending rewards in the trove check. Add a deck, explain who pays for the product (for example the planned liquidation alerts), and link the repo and video from the page.
- **Wave 2 update (team's text, first 700 chars):**

  > Wave 2 progress (Access & Distribution) since Wave 1:  Shipped on https://lisaaai200.github.io/musd-pulse/ (commit b093bc555c5bddf235fc864ab3ff535944308588): 1) #practice — Mezo Testnet practice-trove walkthrough (chain 31611, RPC, faucet, testnet MUSD, official borrow UI; documents 1,800 MUSD min + 200 gas). Page remains read-only / no wallet connect. 2) #bridge — Wormhole NTT explainer for MUSD across Mezo / Ethereum / Base (docs + Portal Bridge; no bridge tx from this app). 3) #alerts — localStorage + copy + mailto liquidation reminder only (no email send, no paid API). 4) Tests 19/19; live smoke OK against public RPCs. README updated.  Honest scope: we did not add a wallet / BorrowerOper

### 142. Lifeline (W2)

- **Tagline:** Preventing MUSD liquidations through Bitcoin-backed rescue loans.
- **Categories:** DeFi, Lending, Risk Management
- **Links:** github `ronniethedevv/lifeline` · demo `None` · https://app.akindo.io/communities/nPqedqNN7UAxxBRQ/products/93NXonk1QiqNBXoj
- **Wave 2 update (team's text, first 700 chars):**

  > This Wave we built and shipped Lifeline end to end on Mezo testnet: a rescue market that stops MUSD loans from being liquidated.  Contracts (Solidity, immutable, deployed on Mezo testnet): - VaultFactory + PositionVault: each MUSD loan lives in its own vault, so a third party can rescue it. - RescueMarket: providers deposit MUSD; anyone can call rescue() when a loan falls below its trigger. The pool repays just enough to restore the target and takes a 7-day senior lien on the vault's BTC. Includes lien repayment, seizure of BTC for unpaid liens (within MUSD's own withdrawal limits), loss accounting, and a guard against strategic default (combined-ratio cap at 120%, trigger at least 20 points

### 144. Trove Guard (W2)

- **Tagline:** Trove Guard repays your MUSD loan before liquidation or redemption, from a reserve that earns BTC
- **Categories:** DeFi, Risk Management, Market Infrastructure
- **Links:** github `BenedicthyH/trove-guard` · demo `None` · https://app.akindo.io/communities/vjqGd8kX4TaVeGaK/products/wKq8lOXxrS9p2loM
- **Wave 2 update (team's text, first 700 chars):**

  > Trove Guard repays your MUSD loan before liquidation or redemption, from a reserve that earns BTC in Mezo's Stability Pool while it waits.  https://t.me/TroveGuardMezoBot

## T1-B borrow + earn / yield routing / aggregators

### 7. MezoRoute (W1+W2)

- **Tagline:** Compare MUSD routes by BTC risk, then borrow and deploy in one transaction. Live on Mezo mainnet.
- **Categories:** DeFi, Yield Aggregator, Lending
- **Links:** github `hms1499/MezoRoute` · demo `None` · https://app.akindo.io/communities/vjmk6qeDdcZqAlWng/products/xKqvNXjQACQm8mnl
- **Wave 1 result:** 20 USDT · scores (Integration/Product/Technical/UX/Materials) 8/8/8/8/6
- **Wave 1 judge review (verbatim):**

  > MezoRoute already composes Mezo primitives on mainnet (Tigris LP via a verified executor, Stability Pool, signed Trove borrowing), so the next integration step is to run Borrow & Deploy on mainnet and add the planned leverage and unwind with redemption-risk handling, which would move it toward a new MUSD use rather than a router over existing ones. Getting real third-party users through the executor, beyond the team's QA wallet, would strengthen both the integration and the business case for the 10 bps fee. Keep the demo video under 2:15, since the 178-second cut caps Materials, and show the Borrow & Deploy flow clearly in it.
- **Wave 2 update (team's text, first 700 chars):**

  > Wave 2 turns MezoRoute from a MUSD router into a toolkit for the Trove behind it. All live on Mezo mainnet (capped per transaction) and testnet; every contract is source-verified.  App: https://mezoroute.vercel.app Code: https://github.com/hms1499/MezoRoute Deck: https://github.com/hms1499/MezoRoute/blob/main/docs/submission/mezoroute-wave2-deck.pdf  1. Unwind, Close, Leverage in one transaction (asked for in the Wave 1 review) - New MezoRouteLeverage contract flash-swaps the MUSD/BTC pool and adjusts the user's own Trove through BorrowerOperationsSignatures (borrower = recipient = caller). - Unwind sells collateral to repay debt; Close repays all debt from collateral, no MUSD needed; Levera

### 10. MUSD Compass (W1)

- **Tagline:** Every Mezo earning spot, ranked by the cash you keep. Live from Mezo and Ethereum.
- **Categories:** DeFi, Market Infrastructure, Developer Tools
- **Links:** github `Soka457han/MUSD-Compass` · demo `None` · https://app.akindo.io/communities/gXle8B7JkfDV7WQE/products/Mz9eqoGPnFVlRJKm
- **Wave 1 result:** 20 USDT · scores (Integration/Product/Technical/UX/Materials) 8/8/8/8/8
- **Wave 1 judge review (verbatim):**

  > Your Mezo integration is already deep: the live app reads PriceFeed, TroveManager, StabilityPool and the sMUSD gauge, and the /vault flow opens real troves and deposits into sMUSD on testnet. To push higher in Wave 2, take the Borrow -> Earn flow to mainnet with HintHelpers, add monitoring and top-up or repay for the trove it opens (including redemption and Recovery Mode warnings), and show users outside your own wallets using it. On product, set a real mainnet x402 price and show who would pay for the premium API and why. Also add WalletConnect or Mezo Passport, fill in the team and track fields, and update the README video and deck links.

### 41. Morbit (W1+W2)

- **Tagline:** Borrow MUSD against your BTC and earn BTC on your MUSD, all from one simple dashboard on Mezo.
- **Categories:** Lending, Yield, Market Infrastructure
- **Links:** github `Bruh-Codes/morbit-mezo` · demo `None` · https://app.akindo.io/communities/Vwp11kkDLcG9j97g/products/La7ME0ozJIkrDv1Or
- **Wave 1 result:** 16 USDT · scores (Integration/Product/Technical/UX/Materials) 8/6/6/6/2
- **Wave 1 judge review (verbatim):**

  > Your vault deposits canonical MUSD into Mezo's Stability Pool, and the app opens and adjusts troves through BorrowerOperations, which puts Integration at level 4. To reach level 5 in Wave 2, build the one-click borrow-into-vault loop in a contract, give mvMUSD a downstream use, and get users other than your deployer through the full flow, including a BTC-gain payout. In redeem, call withdrawFromSP(0) whenever getDepositorCollateralGain is above zero, even if the compounded deposit is zero, so a redeemer still gets their BTC after a pool-emptying liquidation. Also verify the vault on the explorer, explain the Stability Pool withdrawal block instead of showing a raw revert, and add a revenue model such as a vault performance fee. Materials is capped at 1 because there's no deck: add one, plus your track, your team and a note on the earlier Morbit product.
- **Wave 2 update (team's text, first 700 chars):**

  > Live app: https://morbit-mezo.vercel.app ·  Repo: https://github.com/Bruh-Codes/morbit-mezo · Bot: https://t.me/Morbit_testnet_bot ·  Tester guide: https://github.com/Bruh-Codes/morbit-mezo/blob/main/docs/TESTING.md · Track 1 DeFi (alerts bot also fits Track 2).  Team: Dickson (Bruh-Codes). Morbit began as an RWA lending app; for Mezo we rebuilt every contract MUSD-native.  Judge feedback, addressed: 1. Borrow & Earn in one contract call: deposit BTC, open a MUSD trove and put everything borrowed into Auto Earn in one transaction. Closing redeems, repays and returns your BTC plus vault BTC gains. Loop factory: 0x6e43AEce3302f16adAa6A19c7eFb8521f8c55A4b  2. Downstream use for the vault share:

### 77. Sele Odigie (W1)

- **Tagline:** Bitcoin-backed borrowing, earning and payments made simple on Mezo.
- **Categories:** Payments, DeFi, BTCFi
- **Links:** github `None` · demo `None` · https://app.akindo.io/communities/d8NjdJeg9CJDpl7zD/products/DrBm4G742U126vLB
- **Wave 1 result:** 13 USDT · scores (Integration/Product/Technical/UX/Materials) 6/6/4/4/4
- **Wave 1 judge review (verbatim):**

  > Your Mezo integration is genuinely deep: MarenVault drives BorrowerOperations and MarenEarn drives the Stability Pool, and the pooled sub-minimum borrow is a real new route to MUSD. But nearly all of it predates registration, and the deployed vault is stuck below its own 180% floor with the redemption fix undeployed. For Wave 2, redeploy the vault with the redemption reconciliation and a claimCollateral wind-down path (fixing the High finding), automate the keeper so collateral actually reaches the trove, and show fresh on-chain borrows from real users in the window. Put the app URL in the live-demo field, use the product name Maren, link the deck and keep the video under 2:15.

### 122. Beam (W1+W2)

- **Tagline:** Beam — productive capital for MUSD on Mezo
- **Categories:** Lending, Arbs
- **Links:** github `None` · demo `https://gitlab.com/uzochukwuV/beam` · https://app.akindo.io/communities/1PWroa4DKUqrMw17P/products/nPqJvGMGGIBa8ejq
- **Wave 1 result:** 0 USDT · scores (Integration/Product/Technical/UX/Materials) 0/0/0/0/0
- **Wave 1 judge review (verbatim):**

  > Beam was not scored because it failed gate G2 (real integration). Both Base Sepolia deployments use your own 'Mock MUSD' as the market's collateral. A self-deployed MUSD fails G2 on any chain where real MUSD exists, and testnets count here too. For Wave 2, deploy the market against canonical MUSD (0xdD468A1DDc392dcdbEf6db6e34E89AA338F9F186) on Base mainnet, or move the testnet build to Mezo testnet, where real MUSD is available from the faucet. Also fix the live link: it currently points to an unrelated Mantle app (servicefi.vercel.app), and the repo has no frontend.
- **Wave 2 update (team's text, first 700 chars):**

  > Trade execution from the UI: added peg arbitrage execution, leveraged loop (authorize/open/close) and liquidation panels. Fixed a bug where the follow-up transaction was sent before its token approval had been mined, so wallets dropped it; approvals are now awaited. Tested end to end on the live site with real transactions (authorize, then a 10 MUSD / 1-loop position). Track 1 strategies: LeveragedLoop and BeamLiquidator deployed and tested against a fork of live Mezo testnet. Peg keeper: vault, keeper bot and dashboard; trading live on testnet. Mezo-style UI: frontend rebuilt in mezo.org's layout and style. Moved to real MUSD: the earlier Base Sepolia build used a self-deployed MockMUSD. Th

### 132. MezoFlow (W1)

- **Tagline:** MezoFlow makes it easy to borrow, lend, and pay with MUSD on Mezo.
- **Categories:** DeFi, Payments, Bitcoin
- **Links:** github `dinitheth/Mezo-Credits` · demo `None` · https://app.akindo.io/communities/K8OW2Eon4C9pX4Xg/products/kzqk37gwNhrlZDJa
- **Wave 1 result:** 0 USDT · scores (Integration/Product/Technical/UX/Materials) 4/4/2/6/2
- **Wave 1 judge review (verbatim):**

  > Integration is at level 2 right now. FlowVault moves canonical MUSD, but only through plain ERC-20 calls and only from your own wallet. To move up, connect the app to Mezo's protocol: read trove state and the Mezo PriceFeed rather than an owner-posted price, or route borrowing through BorrowerOperations rather than a separate pool, and get real users to make transactions. Before you put any funds in FlowVault, fix the share accounting (count outstanding loans in pool assets) and bound or replace the owner price, then add contract tests and verify the vault. Finally, redeploy the corrected InvoiceRouter, add a deck, and keep the video under 2:15.

### 135. SURPLUS (W1)

- **Tagline:** Put idle MUSD to work on Mezo: keep your reserve, bound the risk, stay in control
- **Categories:** Market Infrastructure
- **Links:** github `None` · demo `None` · https://app.akindo.io/communities/Pv1mqRdawuzVPPgj/products/La7pq121oi0j9gDR
- **Wave 1 result:** 0 USDT · scores (Integration/Product/Technical/UX/Materials) 0/0/0/0/0
- **Wave 1 judge review (verbatim):**

  > SURPLUS could not be judged in Wave 1. It failed the valid-submission gate (G0) because the repo's first commit landed at 18:25 UTC on Oct 26, about 3.5 hours after the 15:00 UTC deadline, and the submission also had no live link. For Wave 2, commit and push your work before the deadline, give a working live URL, and add a demo video. Then run the funded deposit, allocate, earn and withdraw cycle against the real testnet MUSD savings contract and list the transaction hashes, since your deployed vault (0x7916…A8Ae) has no transactions yet. Keep the credit to VitalR/mezo-trovepilot in the README.

### 140. MezoYield Navigator (W2)

- **Tagline:** The cross-chain autopilot for your Bitcoin-backed stablecoin yield.
- **Categories:** cross-chain autopilot
- **Links:** github `GauravKarakoti/MezoYield-Navigator` · demo `None` · https://app.akindo.io/communities/nPEDwjEKzuQ43za0/products/lrke8zdKZt6ojx1G
- **Wave 2 update (team's text, first 700 chars):**

  > Project category: Yield optimization / DeFi strategy router Track: Track 1 — DeFi Chain deployed on: Mezo Testnet Project readiness: Testnet deployment with working demo Public GitHub repository: https://github.com/GauravKarakoti/MezoYield-Navigator  TL;DR: MezoYield Navigator is an automated MUSD yield router that moves user deposits across Mezo-native and third-party MUSD strategies, then converts accrued MEZO emissions into veMEZO boosts—giving users one deposit entry point and automated compounding.  Change Summary - Core routing - Multi-strategy router with strategy whitelist, per-strategy caps, and rebalancing logic - Ditto / dMUSD integration - Added DittoStrategy.sol with asynchronou

### 141. Fuse (W2)

- **Tagline:** Builder codes for Mezo. Apps route users' swaps, saves and BTC locks and earn a fee the user caps.
- **Categories:** Market Infrastructure, Developer Tools, Aggregator
- **Links:** github `CryptoZephyr/fuse` · demo `None` · https://app.akindo.io/communities/eaqkk2J0Gu8d1LgnP/products/aA0Q8rVGBiLN3r6P
- **Wave 2 update (team's text, first 700 chars):**

  > Fuse is new for this wave and built during the buildathon. Track 2. Deployed on Mezo testnet.  What shipped: - FuseRouter on Mezo testnet, Sourcify exact match: 0xF1E6021db0345b03055a76c8E1dAa0CC270f6DC4. Permissionless builder registration, fees capped at 0.50% on chain, and a per-builder fee cap each user approves and can revoke. - Routes into Mezo products: Tigris swaps (BTC, MUSD, MEZO), MUSD Savings Vault deposits (sMUSD) and veBTC locks for 7 to 30 days. - mezo-fuse TypeScript SDK on npm, an embeddable widget (one iframe), a builders console, a public leaderboard, and paid analytics over MUSD x402 at 0.05 MUSD per request. - Mezo Passport for Bitcoin wallets (Unisat, OKX, Xverse) plus 

## T1-C looping / leverage / derivatives

### 26. Coil (W1)

- **Tagline:** Leveraged Bitcoin on Mezo in one signature, protected by a pre-signed stop-loss.
- **Categories:** DeFi
- **Links:** github `Wilivms/Coil` · demo `None` · https://app.akindo.io/communities/kzmodr4eacd1Zpnve/products/WjDlXKe8pUvQkPBZ
- **Wave 1 result:** 17 USDT · scores (Integration/Product/Technical/UX/Materials) 8/8/4/6/4
- **Wave 1 judge review (verbatim):**

  > Coil really composes Mezo: your router opens, unwinds and deleverages troves through BorrowerOperationsSignatures inside a Mezo Pool flash swap, and that's on-chain. To reach the top integration level in Wave 2, run the Guard stop-loss end to end on-chain with a keeper, make it work in Recovery Mode (Guard can't withdraw collateral when TCR is under 150%), and get wallets other than your deployer using the router. Fix the High finding first: add a signed minBtcOut or a PriceFeed-based bound to fireGuard so a keeper can't sandwich the pool and take the user's collateral, and verify CoilRouter on the Mezo explorer. Cut the demo video to 2 minutes, and let visitors reach the app without the drawing intro.

### 44. Roster-Mezo (W1)

- **Tagline:** Roster is a fixed-strike, physically settled BTC put option protocol   on Mezo.
- **Categories:** DeFi, Bitcoin
- **Tech (from submission text):** Solidity 0.8.24, Foundry 1.7.1, via_ir, Mezo EVM, MUSD, Mezo ERC-20 BTC, Mezo BorrowerOperations / TroveManage
- **Links:** github `Chidubemkingsley/Roster-mezo` · demo `None` · https://app.akindo.io/communities/xKq2R0PDlum0orRnN/products/0nNKLdMlXTXBMke3
- **Wave 1 result:** 16 USDT · scores (Integration/Product/Technical/UX/Materials) 8/6/6/6/4
- **Wave 1 judge review (verbatim):**

  > Your trove-writer vault really composes Mezo: it opened a trove through BorrowerOperations and routed the minted MUSD into a fully reserved put series. To reach the top integration level in Wave 2, run the rest of the trove lifecycle on-chain (repay, close, claim) and show it handles liquidation and Recovery Mode risk, since the writer is long BTC through the trove and short puts. Prove that wallet write flows (buy, exercise, list, fill) work end to end from the live app, verify your contracts on the Mezo explorer, and bring in at least a few outside users. Keep the video to 2 minutes (yours is 3:15), and add a revenue model such as a protocol fee on premiums or fills.

### 49. Coil (W1)

- **Tagline:** One-click BTC leverage on Mezo MUSD troves, with a keeper that can only reduce risk.
- **Categories:** DeFi
- **Links:** github `PrabalParihar/coil` · demo `None` · https://app.akindo.io/communities/83NK18DAdizl8N3x/products/La7Da3JDdFx4xQ7Z
- **Wave 1 result:** 15 USDT · scores (Integration/Product/Technical/UX/Materials) 8/6/4/6/2
- **Wave 1 judge review (verbatim):**

  > Coil already composes Mezo deeply: the clones open, refinance, repay and close MUSD troves and trade on Mezo Pools, all shown on testnet. To reach the top integration level in Wave 2, make the loop hold up under stress. Add an owner path that calls claimCollateral so redemption surplus isn't stranded, give users a way out in Recovery Mode, set swap minimums from PriceFeed instead of the pool's spot quote, and run the guard keeper always-on. Verify the contracts on the Mezo explorer, submit the live app URL rather than the repo, add a deck, and keep the video under 2:15. A stated fee model, such as a loop or vault fee, plus real users beyond the deployer, would lift the product score.

### 68. Bustline (W1)

- **Tagline:** 1–100x BTC perpetuals on Mezo, settled in MUSD. No LP deposits; unpaid profits queue FIFO.
- **Categories:** Market Infrastructure, Perpetuals
- **Links:** github `None` · demo `None` · https://app.akindo.io/communities/4eNKElPn0H3280Mx/products/1Po91eoG7czjBjAd
- **Wave 1 result:** 14 USDT · scores (Integration/Product/Technical/UX/Materials) 4/6/6/6/8
- **Wave 1 judge review (verbatim):**

  > Your MUSD integration is real but transactional. MUSD moves through HouseExchange only as a plain ERC-20, so swapping in USDC would change nothing, and the only Mezo-specific read is an optional Skip price bound. To climb the ladder in Wave 2, make the product act on Mezo primitives: for example, let traders open or top up a trove through BorrowerOperations to fund margin in one flow, put idle house cash into the Stability Pool or a Mezo Pools position, or price the market from MUSD's PriceFeed. Also verify the contracts on the explorer, get trades from users other than the deployer, and restrict owner powers such as setStaking behind a timelock.

### 100. Piton (W1+W2)

- **Tagline:** Bitcoin options on Mezo, settled in MUSD: hedge your Trove, earn on MUSD, trade BTC calls and puts
- **Categories:** bitcoin options
- **Links:** github `None` · demo `None` · https://app.akindo.io/communities/wKq0Vlv3Zs63E8a0/products/A8NgW27O0iNZlN30
- **Wave 1 result:** 9 USDT · scores (Integration/Product/Technical/UX/Materials) 4/4/4/4/2
- **Wave 1 judge review (verbatim):**

  > Piton moves real testnet MUSD through its CallOption contract, but only as a plain ERC-20, so integration sits at level 2. To climb, tie the options to Mezo itself: accept a trove or Stability Pool position as margin, read MUSD's PriceFeed with a staleness check, and exercise the put and MUSD-margin paths on-chain. Fix two High findings before real funds touch it. A put seller whose contract rejects BTC can block exercise and reclaim the full margin (PutOption.sol:184; use pull payments). A cash-settled call whose profit exceeds the 2/3 margin can never settle while the seller keeps the premium (CallOption.sol:210-213; pay min(profit, margin) and reject strikes already deep in the money). Verify both contracts, add tests, prompt users to switch networks instead of silently sending them home, and add a 200.html so /dashboard doesn't 404 on refresh. Correct the Pyth and 'Mainnet-ready' claims (the code reads Mezo's Skip oracle), keep the video under 2:15, and add a deck with a fee model.
- **Wave 2 update (team's text, first 700 chars):**

  > Live at: https://piton.surge.sh  Options now support custom expiry from 15 minutes to 14 days, chosen at order  creation — across contracts, the market-making bot, and the place order form.  Previously every option expired in 48 hours with no flexibility.  The order book now loads without a wallet connection, filters out expired  orders, and displays correct values after fixing a tuple decoding issue that was causing all fields to show as zero after connect. 

## T1-D vaults / LP / savings-yield

### 6. mbLP (W1)

- **Tagline:** Deposit BTC, hold one token, earn MEZO as BTC/MUSD liquidity. One transaction, no upkeep.
- **Categories:** DeFi, Yield Vault, Liquidity
- **Links:** github `GuTS805/Akindo` · demo `None` · https://app.akindo.io/communities/d8NPdJNq7tJmoEoVD/products/OVdoK13BMTzz0K60
- **Wave 1 result:** 22 USDT · scores (Integration/Product/Technical/UX/Materials) 10/8/8/8/8
- **Wave 1 judge review (verbatim):**

  > Your integration is at the top of the ladder: one deposit opens a MUSD trove, borrows, adds BTC/MUSD liquidity, stakes in Mezo's gauge and recycles fees as gauge bribes, and every leg shows up in testnet transactions. For Wave 2, handle MUSD's maxBorrowingCapacity (for example through refinance, or by resizing the trove) so the vault can grow past roughly 0.27 BTC without new deposits sitting idle, and plan a degraded exit for Recovery Mode. Fix the debt sum in _snapshot, _troveCR and _netDebt: getEntireDebtAndColl already folds pendingInterest into interest, so adding it again misprices shares after a redistribution. Also verify the v3 vault source on the Mezo explorer so the 'Verified source' label is accurate, and show real third-party usage on the current vault.

### 9. Plumb (W1)

- **Tagline:** A peg module for MUSD: standing bids under its price, built from Mezo's own pool, gauge and vault.
- **Categories:** DeFi, Market Infrastructure, Stablecoins
- **Links:** github `kinnuworks/plumb` · demo `None` · https://app.akindo.io/communities/GLz7Qw8jGFB9pNdl/products/83NwPM6OLiN7N1Kg
- **Wave 1 result:** 20 USDT · scores (Integration/Product/Technical/UX/Materials) 8/8/8/6/8
- **Wave 1 judge review (verbatim):**

  > Your integration already reaches Mezo Pools on-chain (the vault mints, rebalances and burns CL positions through Mezo's NFT manager), but the gauge staking, MEZO streaming, sMUSD parking and PlumbAskStrategy only run in fork tests, and the testnet vault has gauge and sMUSD set to zero. The biggest Wave 2 gain is to exercise that full composition on-chain: ship the capped mainnet vault on the real MUSD/mUSDC pool and gauge, show real MEZO rewards and sMUSD deposits from the vault, and get depositors beyond your own wallet. On the business side, show how the 10% MEZO fee sustains the project if emissions fall, and record a video walkthrough of an actual deposit and redeem in the app.

### 34. Feasy (W1)

- **Tagline:** BTC savings vault on Mezo: borrows MUSD against pooled BTC, saves it, and pays the yield in BTC.
- **Categories:** DeFi, BTCFi, Savings
- **Links:** github `oynozan/feasy` · demo `None` · https://app.akindo.io/communities/q3qM6LRnwCgNjq1j/products/kzqk4BrJ4snGjrw3
- **Wave 1 result:** 17 USDT · scores (Integration/Product/Technical/UX/Materials) 8/6/8/7/2
- **Wave 1 judge review (verbatim):**

  > Feasy already composes Mezo deeply: your vault opens and manages a trove, saves the MUSD in sMUSD, swaps through Mezo Pools and votes veBTC for the sMUSD gauge, all on canonical testnet contracts. To reach the top integration level in Wave 2, show the risk handling working on canonical contracts rather than your staging copy, add an on-chain guard so the vault cannot borrow when the sMUSD rate is below the loan cost, make unwind() usable in Recovery Mode, and run the veBTC claim and withdraw path on-chain. On the business side, say how Feasy sustains itself (for example a small performance fee once the spread is positive) and show real users depositing. Link a pitch deck, because a missing deck capped your Materials score.

### 65. Tiller Finance (W1)

- **Tagline:** A MUSD vault on Mezo that earns by buying MUSD back below $1, with AI reviewing every move.
- **Categories:** DeFi, stablecoin, Yield Vault
- **Links:** github `fahmmin/tiller-finance` · demo `None` · https://app.akindo.io/communities/nPmLVDkAMsn3v4j0/products/aA06439o2CoG6eqM
- **Wave 1 result:** 15 USDT · scores (Integration/Product/Technical/UX/Materials) 8/6/4/7/2
- **Wave 1 judge review (verbatim):**

  > Your integration is real L4 work: the vault deposits into Mezo's Stability Pool and redeems through TroveManager with in-transaction hints. To reach L5 in Wave 2, run the full loop through a real Mezo pool rather than your own DrillPool, exercise harvest on-chain, and make withdrawals and share pricing sound under stress. That means pricing pending SP BTC gains in totalAssets (High H-1) and checking MUSD received after harvest swaps (High H-2). Verify the vault on the explorer and add a fee or revenue model so the product can sustain itself. Submit a deck and keep the video under 2:15, because the missing deck capped Materials this wave.

### 78. MUSD Yield Vault (W1+W2)

- **Tagline:** Turn idle MUSD into productive capital — one deposit, automated yield on Mezo.
- **Categories:** yield optimization, DeFi vault
- **Links:** github `anpratama/musd-yield-vault` · demo `None` · https://app.akindo.io/communities/BeNoK1DMpFDP1aXL/products/kzq7Wo6OecwV83ow
- **Wave 1 result:** 12 USDT · scores (Integration/Product/Technical/UX/Materials) 6/5/4/6/2
- **Wave 1 judge review (verbatim):**

  > Your Stability Pool adapter calls match Mezo's reference contracts, but no MUSD has ever reached the pool. The vault holds one idle 500 MUSD self-deposit, so integration scored at the read-only level (L3). To reach L4 in Wave 2, run rebalance/harvest on-chain (ideally with a keeper) so provideToSP and withdrawFromSP transactions show up from your strategy. Before that, fix the two High findings: BTC gains are frozen in the vault and never counted in totalAssets, and the owner can redirect SP funds through setVault. Also handle withdrawals that the SP's 110% ICR or stale-oracle checks block, verify your contracts on the explorer, and describe the adapter accurately as unfunded until it actually earns.
- **Wave 2 update (team's text, first 700 chars):**

  > Wave 2 addresses the Wave 1 judge feedback (civ_defi_mezo) point by point. Full write-up: README in repo.  1) HIGH fixed — BTC gains frozen out of totalAssets: SP BTC gains are now valued via the chain BTC/USD feed and counted in totalAssets() at strategy level (pending) and vault level (claimed BTC held natively). Feed down/stale ⇒ gains valued at 0, accounting never reverts. Proof: test_BtcGainsIncreaseVaultTotalAssets (0.05 BTC @ $100k ⇒ TVL 10,000 → 15,000 MUSD). Limit: gains held as BTC, no auto-swap yet, so redemptions are limited by real MUSD liquidity.  2) HIGH fixed — owner could redirect SP funds via setVault: setter deleted; vault address is immutable on both strategies. Proof: te

### 134. Pegforge (W1)

- **Tagline:** An ERC-4626 vault, stability pool on Mezo.
- **Categories:** DeFi
- **Links:** github `AmaanSayyad/Pegforge` · demo `None` · https://app.akindo.io/communities/4eNwDP2DGT2akxqKK/products/gXlnD9PLoF14gj1X
- **Wave 1 result:** 0 USDT · scores (Integration/Product/Technical/UX/Materials) 0/0/0/0/0
- **Wave 1 judge review (verbatim):**

  > Pegforge scored 0 in Wave 1 because it failed two gates. G0 (valid submission): the GitHub repo AmaanSayyad/Pegforge was created 20 minutes before the deadline and is still empty, and https://pegforge.fun/ doesn't resolve, so there was no code or live product to judge. G2 (real integration): MUSD appears only in the write-up, with no deployed contract, app config or transaction that uses canonical MUSD or MEZO. For Wave 2, push your contracts and app to the repo before the deadline, deploy on Mezo testnet with the real faucet MUSD (or Ethereum/Base), get the live link loading, include contract addresses or tx hashes in the submission, and check that the video link is complete and public.

## T1-E lending markets / credit / loan markets

### 1. Doji (W1)

- **Tagline:** Keep your Bitcoin locked on Mezo. Borrow MUSD anyway, at a fixed rate to a fixed date.
- **Categories:** Fixed-rate BTC borrowing, Lending, DeFi
- **Links:** github `ramakrishnanhulk20/doji` · demo `None` · https://app.akindo.io/communities/X4wmQgV40S8d9kO6/products/WjDA20KDgCOql8ez
- **Wave 1 result:** 80 USDT · scores (Integration/Product/Technical/UX/Materials) 10/8/8/8/8
- **Wave 1 judge review (verbatim):**

  > Doji already composes Mezo deeply: veBTC custody and lock-and-borrow, PoolsVoter vote pass-through and PriceFeed-driven auctions all ran on testnet, so for Wave 2 the integration priority is exercising the remaining paths on-chain (fee and bribe claims, rebase claims, prepareSettle and deposit of an existing veBTC) and putting idle lender MUSD to work through sMUSD as planned. The biggest gap is real counterparties: every borrower, lender and auction buyer so far is your own wallet, so bringing in outside veBTC holders and MUSD lenders, even on testnet, would most strengthen the product case. Fix the landing-page stat tiles that show negative or conflicting numbers, and make sure the deck link is publicly viewable. Note that ValidatorsVoter is a zero address on testnet, so describe it as mainnet-only in your materials.

### 2. Surety (W1)

- **Tagline:** veBTC holders decide where MUSD credit goes, and their rewards take the first loss.
- **Categories:** DeFi, Lending, Market Infrastructure
- **Tech (from submission text):** Solidity, Foundry, Morpho Blue + VaultV2, Mezo veBTC / PoolsVoter / Skip oracle, TypeScript + viem, Next.js +
- **Links:** github `RaYYeR220/surety` · demo `None` · https://app.akindo.io/communities/7m4QqGD0wcdQ8198z/products/BeNzwJggxTgnQMPX
- **Wave 1 result:** 73 USDT · scores (Integration/Product/Technical/UX/Materials) 8/8/8/6/8
- **Wave 1 judge review (verbatim):**

  > Your integration is deep on the veBTC side (voting power, veBTC custody as collateral, PoolsVoter and RewardsDistributor pass-through, the Skip oracle), but on-chain only the veBTC escrow transfer and auction release were exercised, and the mainnet vault holds no MUSD. For Wave 2, run the escrow vote, fee/bribe and rebase claim paths on chain, put real MUSD through the mainnet vault on Mezo's own Morpho Blue (testnet used a self-deployed Morpho), and get outside users borrowing against veBTC. Add a MUSD/USD price feed or depeg check in place of the hard-coded $1, and widen the gap between the auction trigger and the floor. State who pays the team and how the protocol sustains itself beyond sponsor incentives, and make sure the live app loads quickly; our headless browser timed out on it.

### 4. Keel (W1)

- **Tagline:** Borrow against your Bitcoin. Never Redeemed
- **Categories:** Borrowing, Yield, DeFi
- **Links:** github `jenzylove/keel` · demo `None` · https://app.akindo.io/communities/vjqJejXVkcZP6JqQm/products/kzqkpWrmphdAAlqKN
- **Wave 1 result:** 69 USDT · scores (Integration/Product/Technical/UX/Materials) 8/8/8/8/2
- **Wave 1 judge review (verbatim):**

  > Keel already composes Mezo primitives (veBTC custody and votes, PriceFeed, a Mezo pool TWAP and the savings-vault strategy interface), so the clearest step up to the top integration level is to exercise it against Mezo-deployed contracts, such as the opt-in mainnet vault you plan, and to show reward claims and votes on the current market and in the UI. Verify KeelStrategy, KeelMarket and PegOracle on the Mezo explorer, make withdrawals degrade gracefully when more than the liquid share is requested (the real vault expects instant deallocation), and state who pays for the keeper and infrastructure. Materials was capped at 1 because no deck was reachable: the claude.ai deck link appears only in docs/AKINDO_FORM.md and docs/AKINDO_ABOUT.md, not in your submission or README, and your own note says it has to be shared first, so for Wave 2 put a public deck link (or a PDF committed to the repo) in the form. Also commit the video's script or subtitles, and name the team and roles in the form.

### 8. Baserate (W1)

- **Tagline:** Borrow MUSD against BTC on Mezo's own Morpho Blue, with no redemption queue and no minimum.
- **Categories:** BTC Lending, Stablecoin Credit, Yield
- **Links:** github `OoJae/baserate` · demo `None` · https://app.akindo.io/communities/OVpl31QDoHmwQ9aD/products/Mz9emQnDrsZjOWVp
- **Wave 1 result:** 20 USDT · scores (Integration/Product/Technical/UX/Materials) 10/8/8/8/2
- **Wave 1 judge review (verbatim):**

  > Baserate has the deepest integration we saw: the first MUSD market on Mezo's Morpho Blue, with sMUSD, Tigris and veBTC bribes all used in one loop. To keep that in Wave 2, run the current v2 FeeRouter and FlashLiquidator on-chain, switch the factory's fee recipient from your deployer wallet to the router, and ship the come-back flow for redeemed trove borrowers so the BorrowerOperationsSignatures path is live. Add a deck, a clear target-user and team section, and some unit economics showing how the origination fee and treasury share cover keeper and audit costs at mainnet caps. A mainnet proof deployment with real users would strengthen both the product and technical scores.

### 11. Sternpost (W1)

- **Tagline:** Give AI agents MUSD credit, never your Bitcoin. Each Mezo draw is floor-checked on-chain or reverts.
- **Categories:** AI agents, Lending & Borrowing, DeFi
- **Links:** github `None` · demo `None` · https://app.akindo.io/communities/RDdLz6VAjSPxZWWM/products/rgm17ZpaNfj1Vo8B
- **Wave 1 result:** 19 USDT · scores (Integration/Product/Technical/UX/Materials) 8/7/8/6/8
- **Wave 1 judge review (verbatim):**

  > Your integration is already deep: the Governor draws, loops, saves and swaps through Mezo's own BorrowerOperationsSignatures, sMUSD and DEX on testnet. To reach the top of the ladder in Wave 2, run the defend()/heal() liquidation guard on chain, handle redemptions and Recovery Mode (and fix the double-counted pending amounts in previewDraw), and show draws from Governors that real users or outside agents deployed. Source-verify the Factory, Governor, Router and SpendWallet on the Mezo explorer, and reconcile the test counts you advertise. A stated fee model (on draws, x402 flows or a hosted agent API) plus some evidence of agent-builder demand would lift your product score most.

### 15. Deed (W1)

- **Tagline:** A marketplace for Mezo loans: each position lives in a vault, controlled by an NFT you can sell.
- **Categories:** DeFi, Market Infrastructure, Lending
- **Links:** github `None` · demo `None` · https://app.akindo.io/communities/Z4Rpzpe4PC7262K6Q/products/VwpqVwaRVIAa9aVz
- **Wave 1 result:** 19 USDT · scores (Integration/Product/Technical/UX/Materials) 10/6/8/8/2
- **Wave 1 judge review (verbatim):**

  > Your integration is among the deepest in the wave: vaults that open and adjust real MUSD troves through BorrowerOperations, plus a market and a rescue auction gated on TroveManager ICR at the Mezo PriceFeed price, all exercised on testnet. To push it further in Wave 2, exercise closeTrove and claimCollateral on chain, fix close() so it accounts for pending redistribution debt, handle Recovery Mode in the UI, and get real users beyond your own two wallets. On the business side, add a fee path (for example a small market or rescue fee) so Deed can sustain itself, and state your track and target users explicitly. Your materials score was held down by a YouTube link that won't play and the missing deck, so publish a public video of 2 minutes or less showing the on-chain flow, and add a short pitch deck.

### 24. Tillward (W1+W2)

- **Tagline:** BTC-backed working capital, repaid from customer receipts.
- **Categories:** BTC working capital
- **Links:** github `ShalyX/tillward` · demo `None` · https://app.akindo.io/communities/o6Xgma29Vun4VWEE/products/A8Ng3lnKNUMpaqxvO
- **Wave 1 result:** 18 USDT · scores (Integration/Product/Technical/UX/Materials) 8/6/8/7/8
- **Wave 1 judge review (verbatim):**

  > Your contracts already compose Mezo's BorrowerOperations end to end (open, repay from receipts, close), which puts you at Level 4 for integration. The next step is handling risk: read ICR, the BTC price and Recovery Mode, raise the repayment share or prompt a collateral top-up as ICR falls, and warn about redemption exposure, so that the receivables-repayment loop is sound enough for Level 5. Verify the factory and account contracts on the Mezo explorer, and exercise addColl and claimCollateral on-chain. On the product side, add a revenue model such as a keeper or routing fee, and bring evidence from the business interviews you planned showing that real sellers will accept MUSD.
- **Wave 2 update (team's text, first 700 chars):**

  > Tillward connects BTC-backed working capital to customer receipts. A business borrows MUSD, chooses its repayment share and collects final-payment invoices. Eligible receipts repay that same native Mezo loan.  Since Wave 1: • Added native BTC price, ICR/TCR, Recovery Mode and owner collateral actions, including stale/unavailable states. • Verified factory and account source on the explorer. • Proved a public 0.001 test BTC collateral top-up and full owner exit. • Completed a real native surplus claim: controlled redemption of only our borrower created 0.005532212424520610 test BTC. Tillward claimed it and the owner separately withdrew it. • Deployed the selected 1% atomic routing fee in sepa

### 31. Keel (W1)

- **Tagline:** Tradable, transferable MUSD positions on Mezo
- **Categories:** Market Infrastructure, DeFi
- **Links:** github `None` · demo `None` · https://app.akindo.io/communities/RDKBXL6PmI6BeWavK/products/lrk4eNpjMU03JK8gO
- **Wave 1 result:** 17 USDT · scores (Integration/Product/Technical/UX/Materials) 8/6/8/6/2
- **Wave 1 judge review (verbatim):**

  > KEEL already sits at a strong integration level: your own vault contracts open real Mezo troves through BorrowerOperations, and moving a whole trove by transferring its NFT works on-chain. To reach the top level in Wave 2, ship the marketplace with bounded settlement and the guardian, and expose top-up, repay, refinance, close and claim in the live app, so that real users open and manage positions through the UI rather than only through the deploy script. State a revenue model (for example a marketplace or keeper fee). Your YouTube demo link doesn't play publicly (it looks private), which counts as a missing video and capped Materials at 1, so make it public or unlisted and keep it under 2:15.

### 32. TinyVault (W1)

- **Tagline:** Borrow from 10 MUSD against your Bitcoin on Mezo, without selling BTC.
- **Categories:** DeFi, Lending
- **Links:** github `None` · demo `None` · https://app.akindo.io/communities/d8N3EDWNaFPNBlm6/products/K8OZM9Z84hlr1QEX
- **Wave 1 result:** 17 USDT · scores (Integration/Product/Technical/UX/Materials) 8/8/4/6/6
- **Wave 1 judge review (verbatim):**

  > TinyVault already composes Mezo for real: your vault opens a trove, adds collateral and mints MUSD through canonical BorrowerOperations on testnet, which is Level 4 integration. To reach Level 5 in Wave 2, exercise the full life cycle on chain with independent users (repay, withdraw, per-account close by a keeper, refinance and a redemption), and make the mechanism hold up under stress: add a closeTrove/wind-down path so the last depositors' BTC and the idle and reserve MUSD are not frozen (security finding H-01), and handle Recovery Mode, where Mezo blocks the collateral withdrawals your per-account close relies on. Verify the vault source on the explorer, run the keeper on a schedule, and show who funds the anchor and how the product sustains itself on mainnet. Also fix the pitch-deck link (its href points to example.com) and state your track.

### 33. Mezo RePay (W1)

- **Tagline:** Mezo RePay automatically splits MUSD payments between operating cash and BTC-backed loan repayment.
- **Categories:** BTC-backed credit (MUSD)
- **Links:** github `None` · demo `https://github.com/sambitsargam/mezo-repay` · https://app.akindo.io/communities/Z4LJjN7EeUOj7gzQ/products/DrBm3MzO7TVPPl9l
- **Wave 1 result:** 17 USDT · scores (Integration/Product/Technical/UX/Materials) 8/6/8/6/4
- **Wave 1 judge review (verbatim):**

  > RePay already composes Mezo at L4: your account contract opens a Trove and repays it through BorrowerOperations on-chain, so the next step up is showing real demand, with outside accounts and payers, a hosted keeper and exercised close/addColl/claim paths, plus handling of ICR risk (for example steering pending MUSD to collateral top-ups when the Trove nears MCR). Your overview still reads as a proposal ('a RePay deployment has not yet been completed'), which contradicts the working deployment; rewrite it, fill in the track and category, and link the deck from the form. Cut the video to under 2 minutes, focused on the live on-chain flow, because the 4:15 cut limits your Materials score. A concrete revenue model (who pays, how much, and why) would also raise Product.

### 42. Latch (W1)

- **Tagline:** MUSD credit against the Bitcoin you already locked.
- **Categories:** DeFi, Lending, Bitcoin Finance
- **Links:** github `theeagle2407/latch-credit` · demo `None` · https://app.akindo.io/communities/q3qMlqd9LfQegAM7/products/Pv1NAejZ4uXZ9DKw1
- **Wave 1 result:** 16 USDT · scores (Integration/Product/Technical/UX/Materials) 8/6/6/6/2
- **Wave 1 judge review (verbatim):**

  > Latch already puts veBTC positions to work as MUSD collateral and runs a full request-fund-repay-claim lifecycle on Mezo testnet. To go deeper on integration in Wave 2, compose more Mezo primitives: price collateral with Mezo's PriceFeed and enforce an LTV, let escrowed positions keep voting or claiming rewards through the Voter, and exclude grant-backed veNFTs. Verify the LatchCredit source on the explorer, run a default and recovery on-chain, and get loans from independent borrowers and lenders with non-zero interest. Add a pitch deck, make sure the video shows the live on-chain flow, and state a revenue model such as an origination or protocol fee.

### 54. Cosign (W1)

- **Tagline:** First-loss lending on Mezo. MUSD cover absorbs losses before lenders and backs veBTC voting.
- **Categories:** DeFi, Lending & Borrowing, 1. Risk Management
- **Links:** github `bunnyyxtan/cosign` · demo `None` · https://app.akindo.io/communities/MzVm2jAK8UvLkNrPM/products/vjqJnm1rqUzrNLLW
- **Wave 1 result:** 15 USDT · scores (Integration/Product/Technical/UX/Materials) 6/6/7/6/2
- **Wave 1 judge review (verbatim):**

  > Cosign's first-loss tranche and cover-capped veBTC voting are a distinctive Track 1 idea, and the recorded liquidations show the loss waterfall works with real testnet MUSD and MEZO. To raise Integration in Wave 2, have your own contracts act on Mezo primitives: point the market at Mezo's existing testnet Morpho instead of your own instance, price MEZO and MUSD with real feeds such as your Pyth oracle or Mezo's PriceFeed rather than the owner-set demo price, and read voting power through votingPowerOfNFT so the gauge works with the current VeBTC. Verify your contracts on the Mezo explorer, set out a revenue model that doesn't depend on sponsor-funded rewards, and add a pitch deck, since a missing deck caps Materials at 1.

### 61. Spend (W1+W2)

- **Tagline:** A small-borrower layer on top of Mezo puts MUSD within the reach of smaller users.
- **Categories:** DeFi, Lending, Market Infrastructure
- **Links:** github `Spend-app/spend` · demo `None` · https://app.akindo.io/communities/peqpMwLeeuxkzJgmx/products/7mN2nk8GEHB4BP9e
- **Wave 1 result:** 15 USDT · scores (Integration/Product/Technical/UX/Materials) 8/6/4/6/6
- **Wave 1 judge review (verbatim):**

  > Spend already composes Mezo for real: your contract opens a trove and calls addColl and withdrawColl on every borrow and repay, which puts you at level 4 on integration. The security review confirmed one High, which caps Technical at 2. Nothing handles a redemption or liquidation of the shared trove. A full redemption closes it, after which every repay reverts and withdrawBTC stays locked behind totalUserPrincipal == 0, so user BTC is frozen. Each repay also lowers the trove's collateral ratio, which pushes it to the front of the redemption queue. For Wave 2, write user claims down pro rata when Mezo takes collateral, add a wind-down path for a closed trove and an exit in Recovery Mode, let repaid MUSD pay down master debt, and add tests covering liquidation, redemption and Recovery Mode.
- **Wave 2 update (team's text, first 700 chars):**

  > In Wave 1, the judge pointed out real problems with the shared master Trove. There was no handling for redemptions or liquidations, users could get stuck if Mezo closed the Trove, and repayments were lowering the master ICR without reducing debt.  We fixed all of that in Wave 2.  Pro-rata write-down If Mezo takes collateral from the master Trove through redemption or liquidation, every user’s BTC claim is reduced fairly and proportionally. And no user can receive more than they originally deposited.  Smart debt reduction When a user repays, their MUSD are used to pay down the master Trove debt (as long as the cash buffer hasn't gone below its threshold). We keep a safe floor at 1,810 MUSD so

### 67. Microtrove (W1+W2)

- **Tagline:** Borrow 25 to 200 MUSD against $50 of bitcoin on Mezo, then grow into a full MUSD trove.
- **Categories:** DeFi, Lending, Bitcoin
- **Links:** github `Sanchay117/microtrove` · demo `None` · https://app.akindo.io/communities/DrBGwPqR1HQ6GXWA/products/K8OZqEeMOIQJnrqQX
- **Wave 1 result:** 14 USDT · scores (Integration/Product/Technical/UX/Materials) 6/8/2/8/2
- **Wave 1 judge review (verbatim):**

  > Your integration sits at protocol-aware (L3): every loan check reads Mezo's PriceFeed on-chain, but promotion through BorrowerOperationsSignatures.openTroveWithSignature has never run, so the L4 composition is code-only; executing a real promotion on Mezo testnet (and adding a fork test against the real MUSD contracts) is the single biggest lift for Wave 2. Fix the vault redeem-queue freeze first: a lender can call requestRedeem with the MUSD contract as receiver so processQueue reverts forever and all withdrawals stop, which is a Critical finding that caps Technical. Bring in borrowers and lenders beyond your own wallets and set out how the protocol sustains itself (the protocol fee is currently 0). Add a short deck and broader wallet support to round out materials and UX.
- **Wave 2 update (team's text, first 700 chars):**

  > Wave 2 shipped all five declared goals, fixed what the Wave 1 review found, and added Bitcoin wallets through Mezo Passport a wave early.  Declared goals - Promotion live from the web app: a 100 MUSD micro loan became a full MUSD trove with 1,800 MUSD of debt. One transaction opened the trove through MUSD's BorrowerOperationsSignatures, repaid the micro loan and sent the borrower 1,699.50 MUSD: https://explorer.test.mezo.org/tx/0x9f1a1aae9d3d0106e48dddae8ef4bf22c4e48cebad975a48c9f05dae139b9642 - One-click repay and close: the app signs an EIP-2612 permit for MUSD, so repaying is one signature and one transaction. - Keeper hosted around the clock: a GitHub Actions workflow scans every 5 minut

### 116. Covenant (W1)

- **Tagline:** Fixed-rate MUSD loans against Bitcoin, with terms shaped by your Ethos score.
- **Categories:** Lending Market, DeFi
- **Links:** github `drained69/Covenant` · demo `None` · https://app.akindo.io/communities/JBRW097owSDEeN3L/products/aA06lznm6F8A14g0O
- **Wave 1 result:** 0 USDT · scores (Integration/Product/Technical/UX/Materials) 2/4/4/6/2
- **Wave 1 judge review (verbatim):**

  > Covenant has a clear design (reputation-tiered LTV, fixed terms, exits that are never gated), but on Mezo it uses MUSD only as a plain ERC-20 loan token, and no loan has ever been filled on-chain. To raise your integration score in Wave 2, run real borrow, repay and redeem transactions on testnet and compose with Mezo primitives. For example, route liquidations or lender liquidity through Mezo Pools, compare against or interoperate with troves via BorrowerOperations/TroveManager, or add MEZO/veMEZO into the tier or fee design. Also give lenders a non-zero rate and a protocol fee so there is a business model, verify the contracts on the explorer, make lender redeem reachable in the UI, and add a deck. Only claim end-to-end flows that people can see on-chain. Integration at level 1 (cosmetic) earns no payout this wave: to be paid, MUSD or MEZO has to do real work in the product on-chain, not only appear in it.

### 126. thaw (W1)

- **Tagline:** Borrow against your locked Mezo position, and let its rewards repay the loan.
- **Categories:** Market Infrastructure, Lending, DeFi
- **Links:** github `None` · demo `None` · https://app.akindo.io/communities/peqp9lMN1uLPo1nL/products/q3qlewvn0iqB96KX
- **Wave 1 result:** 0 USDT · scores (Integration/Product/Technical/UX/Materials) 0/0/0/0/0
- **Wave 1 judge review (verbatim):**

  > Thaw did not pass gate G2 (real integration), so it was not scored this wave. Your Mezo testnet deployment uses a self-deployed 'Mock MUSD' (0x49c4...4F78) as the loan and vault asset, the Harvester has no swap router set, and no veBTC or veMEZO adapter is deployed. Mezo testnet has the real MUSD (0x118917a40FAF1CD7a13dB0Ef56C86De7973Ac503, available from the faucet), and a deployment that only uses a mock fails the gate. For Wave 2, redeploy with MUSD_ADDRESS set to canonical testnet MUSD and, ideally, the real veBTC, Voter and Pools Router addresses, so the VeBTCAdapter and Harvester go live. The contract design, tests and app are substantial, so this should be a deployment change rather than a rebuild.

### 136. CreditGraph (W2)

- **Tagline:** The onchain credit identity layer for billions of people that traditional credit bureaus don't see.
- **Categories:** DeFi, Lending, Financial Inclusion
- **Links:** github `pawp5/creditGraph-mezo` · demo `None` · https://app.akindo.io/communities/mVqgJZPj4fmEXkDJ/products/wKqXRa4lwc8AM3V7v
- **Wave 2 update (team's text, first 700 chars):**

  > Since CreditGraph was not submitted in the first wave, this is our first iteration. CreditGraph has advanced its Mezo $MUSD integration, extending the protocol vault to Mezo using $MUSD as the collateral for underwritten loans. The lending pool, borrower repayments, social vouch bonds, insurance reserve, agent staking, and agent payments are all denominated in MUSD. Credit limits and agent stake requirements now scale from the configured token’s decimals, so the protocol now supports Mezo’s 18-decimal MUSD without hardcoded 6-decimal assumptions. A pool is named CreditGraph MUSD (cgMUSD) has been deployed to function as a vault for user shares.  The contracts compile successfully with Foundr

### 147. Hock (W2)

- **Tagline:** Hock lets Mezo liquidity keep earning while it backs a MUSD loan on Morpho
- **Categories:** Market Infrastructure, DeFi, Lending/Borowing
- **Links:** github `None` · demo `https://github.com/itachi-exe/hock` · https://app.akindo.io/communities/NmReNvaBQSKZ67Qa/products/mVqzqOGm8T3L8vXN
- **Wave 2 update (team's text, first 700 chars):**

  > Wave 2 updates  Contracts: HockVault (ERC-20 share vault over one fixed-range BTC/MUSD concentrated-liquidity position, staked in the gauge), HockOracle (values shares from BTC/USD and MUSD/USD feeds, not pool spot), HockMath, MezoCLAdapter (real Mezo position manager and gauge integration), HockRouter (one-transaction deposit, collateral and borrow).  Testing: 15 unit tests and 9 fork tests passing against Mezo Testnet contracts.  Live: all seven contracts deployed and source-verified on Mezo Testnet (chain 31611). Morpho market live with MUSD loan, Hock shares as collateral, LLTV 77%. Full deposit, borrow, repay and withdraw cycle run through the web app, with transaction hashes recorded i

## T1-F ve / boost / MEZO markets & liquid lockers

### 3. Janus (W1)

- **Tagline:** The boost market for Mezo: buy votes for up to 5x veBTC boost, or sell yours and keep 90%.
- **Categories:** Market Infrastructure, DeFi, Yield
- **Links:** github `let-the-dreamers-rise/janus-mezo` · demo `None` · https://app.akindo.io/communities/63kz4xVo8ueRDE0O/products/jaeOrPXV2tlMoRzDg
- **Wave 1 result:** 69 USDT · scores (Integration/Product/Technical/UX/Materials) 8/8/8/8/2
- **Wave 1 judge review (verbatim):**

  > Janus already composes Mezo deeply: the vault locks veMEZO, votes on BoostVoter and the boost lands on veBTC on-chain, so the next step up is showing the mechanism works with real third parties: fill the outside bids, run several rounds, and fix the soundness gaps (vault bribe claiming, guaranteed boost pokes, jMEZO fungibility). Verify both contracts on the Mezo explorer and fix the mainnet veBTC address in Deploy.s.sol, then aim for a mainnet deployment. Add a jMEZO/MUSD pool so the receipt becomes usable capital, and include a pitch deck plus track, team roles and project status in the form.

### 25. Lockless (W1)

- **Tagline:** Liquid veMEZO: turn locked MEZO into stMEZO you can trade or stake to earn MUSD.
- **Categories:** DeFi, Liquid Staking, Yield
- **Links:** github `OlaGreat/lockless` · demo `None` · https://app.akindo.io/communities/rgMp7B7zoTJrM6W6/products/o6qpJaA01H7B3pE2
- **Wave 1 result:** 18 USDT · scores (Integration/Product/Technical/UX/Materials) 8/8/4/7/8
- **Wave 1 judge review (verbatim):**

  > Lockless already composes Mezo deeply: the vault holds a permanent veMEZO lock, merges user locks and votes on BoostVoter on-chain. For Wave 2, run the yield leg live (claimBribes harvest, rebase claim, the BTC-to-MUSD swap on Mezo Pools, MUSD streamed to stakers) and show those transactions. The security review found one High that caps Technical at 2. The vault owner, a single EOA, can repoint rewardsReceiver and the keeper with no delay and take all the bribes and rebase, which bypasses the 20% fee cap the README promises. Make the harvester the fixed receiver (or add a timelock and a multisig owner, and disclose this). Also add an stMEZO exit path or deeper pool liquidity, simple unit economics and a team section.

### 35. Torque (W1)

- **Tagline:** One fair price for veBTC boost: a batch auction where veMEZO holders sell votes to veBTC holders
- **Categories:** Market Infrastructure, DeFi
- **Links:** github `None` · demo `None` · https://app.akindo.io/communities/ENjQ93xa9im4W77B/products/Z4LNdjVl0ck9zQwZ
- **Wave 1 result:** 17 USDT · scores (Integration/Product/Technical/UX/Materials) 8/6/8/7/2
- **Wave 1 judge review (verbatim):**

  > Torque already composes Mezo for real: your contract held a veMEZO and cast BoostVoter votes and boost pokes on chain, which puts you at L4. To reach L5 in Wave 2, run the full cycle live (roll, reset, MUSD settlement to sellers, refunds and claims) and get buyers and sellers other than your own wallets through it. On product, say how the protocol or keeper will be paid and show evidence of demand from veMEZO and veBTC holders. Keep the video under 2:15, add a deck, fill in track and team, and keep docs and pitch accurate: commit the clear transaction hashes to docs/live-demo.md and drop 'sealed-bid' until commit-reveal ships.

### 56. Perpetua (W1)

- **Tagline:** Turns Mezo's veBTC voting power into a liquid token that never decays and pays its holders in MUSD.
- **Categories:** Liquid locker, yeild, vote-escrow
- **Links:** github `SundownRises/perpetua` · demo `None` · https://app.akindo.io/communities/Vw2wGnlXZCjwAlo7/products/QlEOBEajWuNr6wrLB
- **Wave 1 result:** 15 USDT · scores (Integration/Product/Technical/UX/Materials) 8/6/4/6/2
- **Wave 1 judge review (verbatim):**

  > Perpetua is one of the few projects that composes Mezo's vote-escrow system on-chain: your locker owns a permanent veBTC position, tops it up and votes it into MUSD gauges. To reach the top integration level in Wave 2, run the real yield loop on-chain (harvest claimFees/claimBribes, sweep, convertAndNotify into MUSD), poke after deposits so the whole bloc votes, and give lveBTC a pool or collateral venue. Fix the High finding by blocking convertAndNotify from swapping the staking token or MUSD, and verify the contracts on Blockscout. Add a pitch deck, a stated fee or revenue model, and read-only chain reads so visitors without a wallet can see the live position.

### 60. EpochPilot (W1)

- **Tagline:** Autonomous veMEZO dual-voter KKT solver, veBTC boost arbitrage & atomic sMUSD compounder.
- **Categories:** DeFi, Yield Aggregator, Market Infrastructure
- **Links:** github `eugenennamdi/EpochPilot` · demo `None` · https://app.akindo.io/communities/lrk3Oz2V3Ueoj6xv/products/nPq210AmQsz49jz7
- **Wave 1 result:** 15 USDT · scores (Integration/Product/Technical/UX/Materials) 8/6/4/6/2
- **Wave 1 judge review (verbatim):**

  > Your veMEZO vote batch really did run through your own router into BoostVoter and ThirdPartyVoter on Mezo testnet, which puts integration at the 'composes Mezo' level. To reach the top level in Wave 2, deploy on mainnet and get the bribe-to-MUSD path working on-chain: call MUSDSavingsRate.deposit(uint256), which is not ERC-4626, and send the sMUSD on to the user; swap only the claimed bribe deltas, not whole wallet balances; and show real users running it. Verify the router on the explorer, add contract tests and a deck, and correct the overview's 'verified' and 'ERC-4626' claims. Also state how EpochPilot will earn revenue, for example a keeper or performance fee.

### 66. Boost Relay (W1)

- **Tagline:** Optimize Mezo Boost Voting. Maximize Your Voting Power.
- **Categories:** DeFi
- **Links:** github `None` · demo `None` · https://app.akindo.io/communities/93Nx6aNR6FWoAXd9/products/lrkvDZJNkh0RmoEzR
- **Wave 1 result:** 15 USDT · scores (Integration/Product/Technical/UX/Materials) 6/6/8/7/2
- **Wave 1 judge review (verbatim):**

  > Boost Relay sits at protocol-aware (L3): it reads BoostVoter, veMEZO and veBTC state on mainnet and mirrors the boost math closely, but the BoostVoter.vote path runs only on testnet and no vote transaction from the app was evidenced. To reach L4 in Wave 2, enable mainnet voting and publish real vote transaction hashes, and consider building the Vault Relay contract so the product creates new MEZO use and a fee-based business model. Add a pitch deck, state your track, readiness and next milestones, and keep the video at or under 2 minutes showing the full optimize-simulate-sign flow.

### 91. MezoBribe (W1)

- **Tagline:** Mezo Testnet bribe market for MUSD/MEZO with pool-to-gauge validation and a Vote Advisor.
- **Categories:** Market Infrastructure, DeFi
- **Links:** github `None` · demo `None` · https://app.akindo.io/communities/kzZ1Gj4zAudKMdrLK/products/xKq2n3Qn6inxRonP
- **Wave 1 result:** 11 USDT · scores (Integration/Product/Technical/UX/Materials) 6/4/4/6/2
- **Wave 1 judge review (verbatim):**

  > MezoBribe reads live gauge state from Mezo's VeBTCVoter and has taken 250 real testnet MUSD in deposits, which puts it at protocol-aware (L3). To move up in Wave 2, compose with Mezo directly: fund each gauge's native BribeVotingReward or derive payouts from on-chain Voter.votes, and run real votes and claims with depositors other than the deployer. Today one key decides every payout, and bribes on a valid gauge that the root doesn't cover can't be refunded. Disclose that plainly, split the roles, add a real on-chain dispute and a timeout refund, call isGaugeValid inside depositBribe, and verify both contracts. Add a deck, state your track, replace the hardcoded prices and signals with real reads, fix the clipped Connect wallet button on phones, and keep the video under 2:15.

### 131. Epoch (W1)

- **Tagline:** Sell tomorrow's Bitcoin fees today. Keep the entire principal.
- **Categories:** DeFi, Market Infrastructure
- **Links:** github `None` · demo `None` · https://app.akindo.io/communities/aA067WLAMiVA2poB/products/VwpBGlkGncJqZ9eA
- **Wave 1 result:** 0 USDT · scores (Integration/Product/Technical/UX/Materials) 2/4/4/4/2
- **Wave 1 judge review (verbatim):**

  > Your integration is at the cosmetic level today: canonical testnet MEZO is configured as the payment token, but no MEZO has moved through EpochMarket and the position and rewards are both mocks. In Wave 2, the biggest gain would come from a real veBTC adapter that escrows a live VeBTC NFT (it reads locked(tokenId), since VotingEscrow has no unlockAt) and claims real fee or bribe rewards through Voter and RewardsDistributor, plus a complete purchase-to-redemption run on testnet with the transaction hashes in your submission. Make the overview match the build: settle in MUSD as you claim, or say MEZO, and give one test count. Also verify your contracts on the explorer, keep the video under 2:15, add a deck, and state a fee or revenue model for the market. Integration at level 1 (cosmetic) earns no payout this wave: to be paid, MUSD or MEZO has to do real work in the product on-chain, not only appear in it.

## T1-G cross-chain

### 14. Mezodot (W1+W2)

- **Tagline:** Omnichain money market for MUSD & MEZO: earn ERC-4626 yield, borrow cross-chain, loop in one tx.
- **Categories:** DeFi, Lending, Cross-Chain
- **Links:** github `None` · demo `None` · https://app.akindo.io/communities/63dv68BletWx7Od7/products/La7M8xW8rIkr2kMoz
- **Wave 1 result:** 19 USDT · scores (Integration/Product/Technical/UX/Materials) 8/8/8/8/2
- **Wave 1 judge review (verbatim):**

  > Your MUSD/MEZO money market is solid and the one-transaction BTC long through the Tigris MUSD/BTC pool already puts you at the Composes Mezo level; to reach the top of the integration ladder, exercise pMEZO collateral, MEZO borrowing and keeper liquidations on-chain, and consider composing deeper Mezo primitives such as opening or repaying troves via BorrowerOperations, pMUSD/MUSD liquidity in Mezo Pools, or veMEZO/gauge incentives. Close the open risk gap on MUSD and MEZO price liveness (a second oracle leg or a Mezo-provided feed), and make the spoke-side deployments and the Base Sepolia lock tx easy to verify. Add a pitch deck, because a missing deck caps Submission Materials at 1, and refresh the stale 'What's next' line now that the app and video are live. Team names, roles and a dated roadmap would also strengthen the business case.
- **Wave 2 update (team's text, first 700 chars):**

  > Track 1, DeFi. Live on Mezo testnet, not audited. Team: MDLOG Labs.  Mezodot is a money market for MUSD and MEZO on Mezo. Wave 2 acted on the Wave 1 feedback:  - Every missing path now runs on testnet: pMEZO as collateral, MEZO borrowing, and keeper liquidation by the agent, each transaction listed on the proof page. The liquidation was staged: the owner lowered pMEZO's limits for about 8 minutes, and the agent found and liquidated the position unprompted.  - New MUSD utility, TroveRouter: BTC opens a Mezo trove through BorrowerOperationsSignatures and its MUSD goes into pMUSD in one transaction. Supply can later repay or close the trove. It handles Mezo's fee, gas compensation, minimum debt

### 37. MUSD Reach (W1+W2)

- **Tagline:** MUSD Reach makes Mezo savings portable.
- **Categories:** DeFi, Savings & Yield, Cross-Chain
- **Links:** github `TheWeirdDee/musd-reach` · demo `None` · https://app.akindo.io/communities/eaq2zk9BEf837Emxq/products/xKq2eRzkECVKPkrG
- **Wave 1 result:** 17 USDT · scores (Integration/Product/Technical/UX/Materials) 8/6/8/6/2
- **Wave 1 judge review (verbatim):**

  > Your wrapper genuinely composes Mezo's MUSDSavingsRate vault (deposit, withdraw, yield harvest) and you've run a full round trip on-chain, but to move from Level 4 toward Level 5 you need a live destination venue: deploy the NAV oracle and stand up a real market (for example on Base) that accepts rwSMUSD as collateral, and get users other than your own wallets through it. Verify the wrapper and gateway contracts on the explorers and put a short fee or revenue model in the pitch, because right now there are no fees and no path to sustainability. Add a pitch deck and state the track in the form; a missing deck capped Materials this wave.
- **Wave 2 update (team's text, first 700 chars):**

  > To be done

### 43. MUSDY.fun (W1)

- **Tagline:** Buy on any coin. Settle on Mezo.
- **Categories:** Consumer APP, trading, Cross-Chain
- **Links:** github `vwakesahu/musdy` · demo `None` · https://app.akindo.io/communities/RDvZpKaXmfEx0OW3/products/BeNmnNzdvSBPanp4
- **Wave 1 result:** 16 USDT · scores (Integration/Product/Technical/UX/Materials) 6/6/6/8/6
- **Wave 1 judge review (verbatim):**

  > Your integration sits at protocol-aware: the vault really swaps through Mezo Pools, but the headline cross-chain flow treats MUSD as a ledger number pegged 1:1 to USDC, so it would work the same with USDC. To climb in Wave 2, build the 'borrow MUSD against BTC, then trade' path through BorrowerOperations inside the app, or run the launchpad so graduations seed real token/MUSD liquidity in Mezo Pools on-chain. Also verify the vault and launchpad on the Mezo explorer, state the trade fee and the solver custody model plainly, and keep the walkthrough video under 2:15.

### 76. Aurove Horizon (W1)

- **Tagline:** Locked on Mezo. Liquid everywhere.
- **Categories:** DeFi, Yield Vaults, Cross-Chain
- **Links:** github `aurove/horizon` · demo `None` · https://app.akindo.io/communities/Ql9rjLe98f1J38Gq/products/Pv1m23pNrIKWWXpZ
- **Wave 1 result:** 13 USDT · scores (Integration/Product/Technical/UX/Materials) 6/6/4/6/2
- **Wave 1 judge review (verbatim):**

  > Thanks for Horizon. The live bridge page reads canonical VeMEZO/VeBTC lock state and can convert a veNFT into vault shares before bridging, so Integration scored at the protocol-aware level. That path hasn't been used on chain yet, and the dApp source is private, which won't earn Integration credit in Wave 2. For Wave 2, publish the dApp code, run the veNFT-to-Base path end to end with real transactions, and build the planned vault-share/MUSD pools on Aerodrome with canonical MUSD. Fix compounding on testnet (claimableRewards() reverts because the testnet gauges use accountMetadata), since your submission presents it as working. Also verify the contracts, seed the vaults against inflation attacks, and add a deck and team details.

### 102. Mezo Flow (W1)

- **Tagline:** Your Bitcoin-backed capital, working harder across every chain.
- **Categories:** Cross-Chain, Yield Aggregator
- **Tech (from submission text):** - Smart Contracts: Solidity ^0.8.20, Hardhat, OpenZeppelin ERC-4626, ReentrancyGuard, Ownable.
- **Links:** github `None` · demo `https://github.com/GauravKarakoti/Mezo-Flow` · https://app.akindo.io/communities/nPEDwjEKzuQ43za0/products/jamAJzV3eslr1oNkn
- **Wave 1 result:** 0 USDT · scores (Integration/Product/Technical/UX/Materials) 2/4/2/2/2
- **Wave 1 judge review (verbatim):**

  > Your integration currently sits at the cosmetic level. No MezoFlowVault is deployed, the frontend vault address is a placeholder, and the vault calls asset(), deposit(uint256,address), redeem() and convertToAssets() on Mezo's MUSDSavingsRate, none of which exists there, so it reverts against the real savings vault. For Wave 2, rewrite the savings adapter against MUSDSavingsRate's real interface (deposit(uint256), withdraw(uint256), claimYield()), deploy the vault on Mezo Testnet, wire the live address into the app and show real MUSD deposit, harvest and withdraw transactions. Also fix the three High findings: sync boosted shares on transfer, and lock or timelock setSavingsVault and setMezoToken. Then submit a 2-minute video and align the overview, README and SECURITY_AUDIT.md with what the code actually does. Integration at level 1 (cosmetic) earns no payout this wave: to be paid, MUSD or MEZO has to do real work in the product on-chain, not only appear in it.

### 112. skim (W1+W2)

- **Tagline:** Skim sends small musd, mUSDC amounts from Mezo to USDC on Base in about 30 seconds, no $20 minimum.
- **Categories:** DeFi, bridge
- **Links:** github `Godbrand0/skim` · demo `None` · https://app.akindo.io/communities/JBVwZOQ2mUW1adBzo/products/eaq2BjR7xHEVGKan
- **Wave 1 result:** 0 USDT · scores (Integration/Product/Technical/UX/Materials) 2/4/6/6/2
- **Wave 1 judge review (verbatim):**

  > Your biggest gap is integration depth: the live pilot moves only mUSDC, MUSD is disabled in MezoDeposit and MEZO isn't used at all, so on-chain this reads as a generic ERC-20 off-ramp. To move up the ladder in Wave 2, enable MUSD and run real MUSD exits, then have the relayer or contracts act on Mezo primitives directly, for example automating the MUSD/mUSDC rebalancing through Mezo Pools or reading MUSD protocol state such as PriceFeed for depeg pauses. Also verify both contracts on the explorers, put the product name 'Skim' in the AKINDO name field, add a deck, and keep the video under 2:15. Integration at level 1 (cosmetic) earns no payout this wave: to be paid, MUSD or MEZO has to do real work in the product on-chain, not only appear in it.
- **Wave 2 update (team's text, first 700 chars):**

  > Updates in this Wave  Last wave's feedback: MUSD was disabled and the Mezo integration was cosmetic. This wave MUSD does real on-chain work, in both directions, on Mezo and Base mainnet.  - MUSD is live. Deposits are valued at the lower of $0.99 and what Mezo's MUSD/mUSDC pool actually pays, then paid out in USDC on Base. Proof: 1 MUSD in, 0.9396 USDC out, made from the website. - MusdPegGuard (new). Reads three Mezo pools and the MUSD protocol's PriceFeed. MUSD deposits are refused and payouts held during a depeg. It fails closed. - MezoRebalancer (new). Sells the treasury's MUSD for mUSDC through Mezo's pool without ever holding funds. Keeper-only, with caps and an on-chain price floor. Pr

### 130. PRISM Teleport (W1)

- **Tagline:** PrismTeleport is a fixed-income and cross-chain borrow protocol built natively for Mezo
- **Categories:** DeFi
- **Links:** github `None` · demo `https://www.github.com/asdspal/prismteleport` · https://app.akindo.io/communities/83zQJkN1vFpjGGGQ/products/o6qproL9jUqqRRoGP
- **Wave 1 result:** 0 USDT · scores (Integration/Product/Technical/UX/Materials) 0/0/0/0/0
- **Wave 1 judge review (verbatim):**

  > PRISM Teleport scored 0 in Wave 1 because the submission had no live link (G0), so it wasn't judged. Your Mezo integration is real: the canonical BorrowerOperations borrow and the MEZO staking transactions on testnet would pass the integration gate. For Wave 2, deploy the Next.js terminal and submit its public URL, and add a demo video. Also build or remove the PrismBorrowLockRouter, TeleportHub and PrismMicroVault claims, because none of them is in the repo yet, and swap the tsMUSD stand-in for Mezo's real sMUSD and savings gauge to reach a higher integration level.

### 133. LaneFluid (W1)

- **Tagline:** Automated market maker for deep, stable liquidity on Mezo and Base, with time-locked fee sharing
- **Categories:** DeFi
- **Links:** github `None` · demo `None` · https://app.akindo.io/communities/xKq2ewlpQCA7o6EA/products/q3qlZXGgdhj7krgpe
- **Wave 1 result:** 0 USDT · scores (Integration/Product/Technical/UX/Materials) 0/0/0/0/0
- **Wave 1 judge review (verbatim):**

  > LaneFluid wasn't judged in Wave 1 because we couldn't see the product. The GitHub repo (github.com/bevowoved/lanefluid) returns 404, and the live demo and video links are both the placeholder https://youtu.be/none, so the valid-submission gate (G0) failed. With no code, contract addresses or app to check, the MUSD/MEZO pools on Mezo Testnet couldn't be verified either, so the real-integration gate (G2) failed too. For Wave 2, make the repo public with commits before the deadline, link a working app on Mezo Testnet, list the deployed pool and router addresses that use the real testnet MUSD and MEZO, and add a demo video of 2 minutes or less.

### 138. Levada (W2)

- **Tagline:** Levada brings Mezo's MUSD Savings Rate to Base.
- **Categories:** DeFi
- **Links:** github `Nuel-osas/levada` · demo `None` · https://app.akindo.io/communities/63NwD9x8ju1gQVO6/products/jaePWjgWWtW4QVw4
- **Wave 2 update (team's text, first 700 chars):**

  >   Levada lets anyone holding MUSD on Base earn Mezo's MUSD Savings Rate without leaving Base. You deposit MUSD on Base and get lsMUSD, a savings token that grows. Levada    carries the MUSD to Mezo over Wormhole NTT, the bridge MUSD itself uses, deposits it in sMUSD, and brings the yield back into your balance on Base. Nothing to claim on    Mezo, and no BTC needed for gas.    What we built this Wave:    Contracts (Solidity, Foundry). LevadaVault on Base is an ERC-4626 vault. It books principal on Base, keeps a 10% buffer for instant exits, and queues larger exits first in,   first out. LevadaHub on Mezo holds the MUSD in sMUSD, compounds the yield and reports it back over Wormhole. Each rep

### 143. AEGIS MEZO (W2)

- **Tagline:** Self-healing cross-chain MUSD rail with 5x yield
- **Categories:** DeFi, Market Infrastructure, Payments
- **Links:** github `ty45-cyber/AegisMezo-V2` · demo `None` · https://app.akindo.io/communities/wKgv091VaSeBN6Ww/products/EN82NmE9JcDMn1Zl
- **Wave 2 update (team's text, first 700 chars):**

  > Built AegisMezo V2 on 15 live Mezo Testnet (31611) contracts (0 mocks): SortedTroves redemption radar & auto-rescue, veBTC x veMEZO 5x boost market, StabilityPool/maMUSD carry router, x402 Base/Mezo float refiller & 56 Foundry tests. https://github.com/ty45-cyber/AegisMezo-V2

## T1-H other DeFi (prediction, OTC, peg/redemption, oracle)

### 5. Mezonk (W1)

- **Tagline:** A prediction market on Mezo where you keep your bitcoin. Borrow MUSD against your BTC,
- **Categories:** prediction market, DeFi
- **Links:** github `prajalsharma/mezonk` · demo `None` · https://app.akindo.io/communities/83Nwj1pNGHDDoQJz/products/Pv1mqn4r3IXxwzZwZ
- **Wave 1 result:** 69 USDT · scores (Integration/Product/Technical/UX/Materials) 8/8/8/8/2
- **Wave 1 judge review (verbatim):**

  > Mezonk already composes with Mezo: the /borrow page opens and draws real troves through BorrowerOperations, with correct MCR, Recovery Mode and fee handling. The only on-chain use so far is one trove and about 726 MUSD of trades from your own wallets. To reach level 5 in Wave 2, get outside users borrowing and trading. Link positions to loans, for example by auto-repaying trove debt from winnings or adding in-app repay and top-up, and consider settling BTC-price markets with Mezo's PriceFeed. Also verify the contracts on the Mezo explorer, add a pitch deck, use Mezonk rather than your own name as the product name on AKINDO, and state the 1% taker-fee business model in the submission.

### 36. PegPath (W1)

- **Tagline:** MUSD to BTC redemption on Mezo that simulates your exact call so you never sign one that will revert
- **Categories:** DeFi, stablecoin, Developer Tooling
- **Links:** github `winsznx/pegpath` · demo `None` · https://app.akindo.io/communities/VwpBLX8zrcmeRBR9/products/7mN26grMJTjm1GrN
- **Wave 1 result:** 17 USDT · scores (Integration/Product/Technical/UX/Materials) 8/6/8/8/2
- **Wave 1 judge review (verbatim):**

  > PegPath already reaches Mezo protocol composition: your own router calls PriceFeed, HintHelpers and TroveManager.redeemCollateral in one transaction, with signature-level fidelity to the MUSD contracts. To lock in or raise Integration in Wave 2, show real app-originated redemptions through the router from users other than the deployer, commit the router address so production routing can be verified, and verify the router's source on the Mezo explorer. Product would rise most with a stated business model (for example a router or integrator fee) and evidence that redeemers or arbitrageurs use it. Add a pitch deck, state the track and project status, and fix the stale README and 'What's next' lines so that Materials is no longer capped.

### 73. Annex (W1)

- **Tagline:** Permissionless binary prediction markets on Mezo Testnet, settled in MUSD
- **Categories:** prediction market
- **Links:** github `None` · demo `None` · https://app.akindo.io/communities/BeGoEl0XOTRmK6qD/products/q3qMXWKw7U06V7BM
- **Wave 1 result:** 13 USDT · scores (Integration/Product/Technical/UX/Materials) 4/6/6/6/6
- **Wave 1 judge review (verbatim):**

  > Annex moves real canonical MUSD through a clean, well-tested prediction-market contract, but it uses MUSD only as a plain ERC-20, so Integration stops at level 2. To score higher in Wave 2, wire Mezo primitives into the product itself: for example, let users open or top up a trove through BorrowerOperations to fund a position, use the Mezo PriceFeed for BTC-price markets, or put idle pool MUSD to work through the Stability Pool or Mezo Pools. Also verify the contract on the explorer, add a protocol fee so the business has revenue, get real users beyond the deployer wallet, and fill in the AKINDO overview and team fields (the overview currently reads '#ERROR!').

### 90. MUSD Match (W1)

- **Tagline:** Trade MUSD for Bitcoin on your terms, with both sides settled in one Mezo transaction.
- **Categories:** Market Infrastructure, DeFi
- **Links:** github `web3devz/MUSD-Match` · demo `None` · https://app.akindo.io/communities/Mz9ek1kGKFAd1vmR/products/mVqpkd1WzF0L9jm0
- **Wave 1 result:** 11 USDT · scores (Integration/Product/Technical/UX/Materials) 4/4/6/6/2
- **Wave 1 judge review (verbatim):**

  > Your integration sits at level 2: MUSD only moves through plain ERC-20 transferFrom, so the product would work the same with any token, and the one fill was a script-driven trade between your own wallets. To climb the ladder in Wave 2, make the app Mezo-aware, for example by showing the Mezo PriceFeed or MUSD_BTC pool price next to each offer, or letting sellers mint MUSD from a trove via BorrowerOperations to fund an offer, and get real users filling offers through the browser UI. Verify the contract source on the Mezo explorer, add public offer discovery and a business model (even a small fee), and submit a video under 2 minutes that shows a live wallet fill, plus a short deck.

### 123. Mezo Upbeat Oracle (MUO) (W1)

- **Tagline:** Permissionless MUSD optimistic oracle and verification layer for the Mezo Bitcoin economy.
- **Categories:** DeFi, Infra
- **Links:** github `None` · demo `None` · https://app.akindo.io/communities/A8NgMRo4zfMlnXnkj/products/GLzENBze1CZa9B44
- **Wave 1 result:** 0 USDT · scores (Integration/Product/Technical/UX/Materials) 0/0/0/0/0
- **Wave 1 judge review (verbatim):**

  > Your submission failed the Valid submission gate (G0), so it was not scored this wave. The linked repo, github.com/symulacr/muo, contains only a 2-line README, so none of the contracts, API, SDK or apps you describe could be reviewed, and the live link (milo-xkq.vercel.app) opens a different product, Milo on Midnight, rather than MUO. For Wave 2, push the full MUO monorepo (including MuoCore.sol, which is already deployed on Mezo testnet at 0x61c4...4Cb0) to the submitted public repo before the deadline, and link a deployed MUO frontend that talks to that contract. Verifying the contract source on the Mezo explorer will also let reviewers confirm the behaviour you describe.

## T2 agents / x402 / MCP / programmable wallets

### 27. Mezo Agent Toolkit (W1)

- **Tagline:** AI agents read Mezo over MCP and pay per call in MUSD, with no BTC for gas and operator spend caps.
- **Categories:** AI agents, Payments, Developer Tools
- **Links:** github `Kylne700/mezo-agent-toolkit` · demo `None` · https://app.akindo.io/communities/La7ZJ4o6mHqJxK9a/products/mVqAPBqpoTkPq386
- **Wave 1 result:** 17 USDT · scores (Integration/Product/Technical/UX/Materials) 6/6/8/6/8
- **Wave 1 judge review (verbatim):**

  > Your MezoLens is a solid protocol-aware read layer (trove health, redemption queue, pool quotes, ve locks), which puts Integration at L3; to go higher in Wave 2, have the agent act on Mezo primitives, for example top up or repay a trove through BorrowerOperations, deposit to the Stability Pool, or ship the planned veBTC/veMEZO gauge vote helper, with real on-chain transactions from the product. All 41 MUSD payments so far are your own test traffic, so getting even a few outside agents or sellers paying in MUSD would strengthen both Integration and Product. A clearer business case (who pays and why, when the same reads are free through the MCP tools) and an installable MCP package that runs without cloning the repo would lift Product and UX.

### 30. BanQor (W1)

- **Tagline:** Let your agents live off your Bitcoin.
- **Categories:** Infrastructure, Agentic
- **Links:** github `Turnless/BanQor` · demo `None` · https://app.akindo.io/communities/JB1PM8ralCKzrzqV/products/nPq27xV41S0vOz04B
- **Wave 1 result:** 17 USDT · scores (Integration/Product/Technical/UX/Materials) 8/6/8/6/2
- **Wave 1 judge review (verbatim):**

  > BanQor already reaches integration level 4: your own vault opens a Mezo trove and borrows MUSD through BorrowerOperations inside an agent's draw, and that's proven on-chain. To reach level 5 in Wave 2, make the mechanism hold up under stress. Ship the rebalance keeper, handle Recovery Mode and Mezo's maxBorrowingCapacity explicitly, exercise repay, addColl and close on-chain, and get vaults and agents beyond your own demo running. On product, state who pays BanQor and for what (for example a draw or vault fee, or a hosted relayer). On materials, cut the video to under 2:15 and add a pitch deck.

### 57. Wayfind (W1)

- **Tagline:** Equip Grok Bot with the skills and tools to automate BTC finance on Mezo, 24/7.
- **Categories:** mcp, Other
- **Links:** github `tamago-labs/wayfind-mezo` · demo `None` · https://app.akindo.io/communities/Mz9pJGKBlIVgRDvO/products/q3qMx9MjAHjjqmj3j
- **Wave 1 result:** 15 USDT · scores (Integration/Product/Technical/UX/Materials) 8/6/6/4/2
- **Wave 1 judge review (verbatim):**

  > Your MCP tools really open troves and stake in the Stability Pool on Mezo testnet, which puts integration at the 'composes Mezo' level. To go further in Wave 2, build the automation you pitch into the product itself: ICR monitoring with auto top-up or repay, a working redeem tool (the current one uses a 7-argument signature and always reverts), and a mint-and-stake strategy that handles liquidation and redemption risk. Also fix the fee being charged twice in openTrove, add tests, ship the mainnet config, and add a deck, team details and a revenue model (who pays, and for what) so the product case and materials can score higher.

### 59. AgentFeed on Mezo (W1)

- **Tagline:** AI agents pay a live crypto-data API per call in MUSD: one signed permit, no API key, no gas.
- **Categories:** Payments, AI agents, Market Infrastructure
- **Links:** github `seekdaseek/agentfeed-mezo` · demo `None` · https://app.akindo.io/communities/q3mjeV7NGu9a3RnK/products/EN8o9j3o9H842eXL
- **Wave 1 result:** 15 USDT · scores (Integration/Product/Technical/UX/Materials) 4/6/8/6/8
- **Wave 1 judge review (verbatim):**

  > Your MUSD payments are real, but the live gateway only uses MUSD as a plain ERC-20 with permit, so swapping in USDC would be a config change. That holds Integration at level 2. To climb in Wave 2, make Mezo itself part of the product: for example, let an agent's budget come from a trove it manages through BorrowerOperations, with trove health shown or enforced in the gateway or Telegram bot, rather than leaving openTrove in a one-off helper script. Show paying users beyond your own test agent, state your per-call margin after mainnet gas, and give human visitors a way to try a paid call without a terminal.

### 84. Relayguard (W1+W2)

- **Tagline:** MUSD payments for agents—with policy and proof built in.
- **Categories:** Payment, AI, x402
- **Links:** github `Reinasboo/relayguard` · demo `None` · https://app.akindo.io/communities/WjDeAkwQWC76wZmo/products/eaq41k7DrUK4wP
- **Wave 1 result:** 12 USDT · scores (Integration/Product/Technical/UX/Materials) 4/6/6/6/2
- **Wave 1 judge review (verbatim):**

  > Your MUSD integration sits at the transactional level: invoices and the x402 API move real MUSD, but only through plain ERC-20 calls, so the product would work the same with USDC. To climb the ladder in Wave 2, make Mezo protocol state part of the product, for example letting an agent or buyer with no MUSD open or top up a trove through BorrowerOperations inside the checkout, or having spending policy react to trove health or PriceFeed. Add a deck, a revenue model (a fee on invoices or verification, say), dated milestones and team details, and fix the stuck 'Verifying...' and invoice-loading states on the live app.
- **Wave 2 update (team's text, first 700 chars):**

  > ### Updates in this Wave  RelayGuard has advanced from a Mezo payment prototype into a more complete merchant payment and operations workflow. The current Wave 2 build supports two MUSD commerce paths: merchants can create exact-value invoices with shareable checkout links and QR codes for customers, and API developers can protect their own Node.js routes with an x402 integration. In both paths, the merchant keeps its own website or API and receives MUSD directly. Invoice status changes to paid only after RelayGuard verifies the matching on-chain token, payer, recipient, and amount.  The checkout experience has been strengthened with wallet-ownership verification, buyer MUSD and BTC/gas pref

### 92. Agentfloat (W1)

- **Tagline:** A budget-controlled MUSD wallet for AI agents on Mezo.
- **Categories:** Market Infrastructure, Agent Payment, Autonomus agent
- **Links:** github `None` · demo `None` · https://app.akindo.io/communities/GLg9M3WnKHowGRMZa/products/0nNKxapgETzVKxJW0
- **Wave 1 result:** 11 USDT · scores (Integration/Product/Technical/UX/Materials) 4/6/4/6/2
- **Wave 1 judge review (verbatim):**

  > Integration is at the transactional level today: MUSD moves through your treasury and x402 payments over plain ERC-20 and Permit2, so swapping in USDC would be a config change. To climb the ladder in Wave 2, compose with Mezo itself: sweep idle float into the testnet MUSDSavingsRate (sMUSD), which exists at 0x6f461c68B2c5492C0F5CCEc5a264d692aA7A8e16 (your check probed the mainnet address), or fund agents from a trove through BorrowerOperations instead of an operator faucet. Technical is capped at 2 by a High finding: /api/pay is unauthenticated and checks the first 402 quote, then signs a second, unchecked one and records the probe amount, so anyone can bypass your per-call and daily caps up to x402's 1 MUSD default per call. Fix it with a client policy that only signs the checked {amount, asset, payTo} plus auth on /api/pay. Also verify the treasury on the explorer, keep the video under 2:15, add a short deck, and state how the product earns money.

### 114. paywall (W1)

- **Tagline:** Stripe for AI agents — every API call settles on-chain in MUSD on Mezo. Zero gas, no API keys.
- **Categories:** Infrastructure, Payments, Developer Tool
- **Links:** github `zalana28/musd-x402-paywall` · demo `None` · https://app.akindo.io/communities/K8OZKamxZtopnDxn/products/Z4LNroB3QS0AzKV7
- **Wave 1 result:** 0 USDT · scores (Integration/Product/Technical/UX/Materials) 0/0/0/0/0
- **Wave 1 judge review (verbatim):**

  > paywall scored 0 in Wave 1 because it failed the valid-submission gate (G0). The live demo field held a YouTube recording, and the submission and README link no hosted app (only localhost and api.your-domain.com), so judges had nothing to open. For Wave 2, deploy the playground and API at a public URL, which your docker-compose setup already supports. Then settle real MUSD payments: all 197 settlements so far were in the BTC mirror, and no MUSD has moved, which keeps Integration at the cosmetic level. Also fix the connected-wallet approve calldata in wallet.js:69-74, which drops the 12 bytes of address padding, and make your claims match the code: sign burner payments in the browser rather than POSTing the key, or stop saying it never touches the server.

### 120. Witness (W1+W2)

- **Tagline:** A program can ask, but MUSD leaves only when your passkey approves it.
- **Categories:** Infrastructure, Security
- **Links:** github `thesithunyein/witness` · demo `None` · https://app.akindo.io/communities/WjDemABP4i3308DJQ/products/3dJwnPoe7i3aWGwL
- **Wave 1 result:** 0 USDT · scores (Integration/Product/Technical/UX/Materials) 4/4/2/6/2
- **Wave 1 judge review (verbatim):**

  > Your MUSD integration is at the transactional level today: DemoSafe moves canonical testnet MUSD through plain ERC-20 calls, and the contracts would work the same with any token. To climb in Wave 2, make the product act on Mezo itself, for example passkey-approved intents that open, top up or repay a trove through BorrowerOperations, or that deposit to the Stability Pool or lock veMEZO. Fix the critical bug first: anyone can register an intent with their own P-256 key and drain DemoSafe, so bind the safe to an enrolled human key and authenticate relayer callers. Materials is capped at 1 because the deck and landing page describe features the code doesn't have: daily MUSD limits, autonomous spending below the ceiling, MEZO treasuries, Gnosis Safe module support and 'verified contracts' (they aren't verified on the explorer). Make the deck and landing page match your accurate form overview, verify the contracts, and add a revenue model such as a hosted relayer or a per-approval fee.
- **Wave 2 update (team's text, first 700 chars):**

  > Wave 2, per judge feedback: fixed the Wave 1 drain (only the enrolled passkey and allowlisted relayer can act, each signature once). Witness now acts on Mezo itself: the vault owns a trove and the passkey approves open, add-collateral and repay through BorrowerOperations, plus Stability Pool deposit/withdraw. 10 bps fee on borrowed MUSD, capped at 1%. 66 Foundry tests, verified source, admin locked. All txs on Mezo testnet: github.com/thesithunyein/witness

### 125. ProMeo (W1+W2)

- **Tagline:** Autonomous AI Agent Procurement and Settlement Network on Mezo.
- **Categories:** DeFi & Escrow, Market Infrastructure, AI agents
- **Links:** github `AbdullahBalfaqih/ProMeo` · demo `None` · https://app.akindo.io/communities/83mdAZPMjc3wAGKV/products/WjDeGJlXnh8jnZ9d
- **Wave 1 result:** 0 USDT · scores (Integration/Product/Technical/UX/Materials) 2/4/4/4/2
- **Wave 1 judge review (verbatim):**

  > Your escrow is wired to canonical testnet MUSD but has never moved any, so Integration sits at the cosmetic level; run real createAgreement, release and refund flows through the deployed escrow from a user wallet, then go beyond plain ERC-20 by reading or acting on Mezo protocol state (for example funding agent budgets from a MUSD trove via BorrowerOperations or checking trove health before releasing). Fix the two High findings: bind each buyer address to its org in createAgreement, and require action-specific permissions on the execute route. The live site is a landing page with hardcoded stats, so link a working console that a normal wallet can use end to end and serve it from the code in your repo. Finally, correct the submission claims (the cited tx is a direct transfer, the contracts are not verified, and permit, milestones and multi-sig arbitration are not implemented), verify the contracts, and add a deck. Integration at level 1 (cosmetic) earns no payout this wave.
- **Wave 2 update (team's text, first 700 chars):**

  > Interactive Console: Served at /console (Test end-to-end with injected wallet or Demo Operator)  Escrow Contract (Mezo Testnet 31611): 0x0F1254772810EA4D06E5c61E3E4b54d740367Aa8 Canonical Contracts: TroveManager (0xE47c...6bb0), BorrowerOps (0xCdF7...beE5), PriceFeed (0x86bC...9366), MUSD (0x1189...c503)  Wave Updates & Feedback Resolution 1. Deep Mezo Protocol State Integration (Beyond Cosmetic ERC-20) Trove Health Check Before Release: ProcurementEscrow.sol links directly to ITroveManager and IPriceFeed. Prior to releasing funds to a vendor, the contract queries ITroveManager.getCurrentICR(buyer, price) and enforces ICR >= 110%, preventing undercollateralized positions from releasing escro

### 129. mezodot. (W1)

- **Tagline:** Pay-as-you-go API access for AI agents. Settled in MUSD.
- **Categories:** Pay-As-You-Go API Billing
- **Links:** github `M4N4N22/mezodot.` · demo `None` · https://app.akindo.io/communities/wKWWqQl00t8D8BroL/products/0nNK3AqoETnvDgp0
- **Wave 1 result:** 0 USDT · scores (Integration/Product/Technical/UX/Materials) 2/6/4/4/2
- **Wave 1 judge review (verbatim):**

  > Your PromptGateway is wired to canonical testnet MUSD, but it has zero transactions, so Integration stays at the cosmetic level (1). That caps the project at 45 and earns no payout points. For Wave 2, run real pay-then-unlock rounds through the gateway and list those tx hashes in the submission. That alone reaches L2. To go further, build on Mezo itself, for example letting an agent borrow MUSD through BorrowerOperations or read trove health to keep itself funded, rather than only accepting MUSD through ERC-20. Also verify the contract on the Mezo explorer, add a short deck and a team section, and only claim 'explorer-verifiable deposits' once deposits exist.

## T2 escrow / marketplaces / quests

### 21. Wasit (W1)

- **Tagline:** Wasit protects advance payments in stablecoin trade
- **Categories:** Trade settlement
- **Links:** github `None` · demo `None` · https://app.akindo.io/communities/A8Na2eMg0HZxKmzd/products/63N96KMxMhLr1ZxNl
- **Wave 1 result:** 18 USDT · scores (Integration/Product/Technical/UX/Materials) 8/7/8/7/2
- **Wave 1 judge review (verbatim):**

  > Your integration already reaches Mezo's Router and MUSD_BTC pool and reads the Skip BTC/USD oracle. To go deeper, make the BTC bond act on Mezo primitives, for example by letting bonders back advances from a trove via BorrowerOperations or by holding protected MUSD in the Stability Pool, and read MUSD's PriceFeed with its 60s staleness bound. For Wave 2, run real pilot deals with outside sourcing agents and suppliers rather than team wallets, and show the fee economics on that volume. Cut the video to under 2:15 and link a deck and the track in the form, because both currently cap Materials.

### 58. Quaestor Operator (W1)

- **Tagline:** Pays creators in MUSD on Mezo only for checked promotion, from a chat with no wallet to connect.
- **Categories:** Payment systems, Creator Marketplace, AI agents
- **Links:** github `N-45div/Quaestor` · demo `None` · https://app.akindo.io/communities/0nN2GBpQmSZOVMLl/products/d8N3g40klFloW26V
- **Wave 1 result:** 15 USDT · scores (Integration/Product/Technical/UX/Materials) 7/6/6/7/2
- **Wave 1 judge review (verbatim):**

  > Your Mezo integration already goes past plain payments: the chat reads PriceFeed and trove parameters, the trading governor swaps through Mezo pools with an on-chain oracle guard, and the funding card can open a trove for the business. To score higher in Wave 2, run the BTC-to-MUSD trove and swap funding through the product's own flow for real users and handle the trove after it opens: show ICR, offer addColl/repay, and cover interest, redemptions and Recovery Mode. That would make MUSD central to the payout core rather than an ERC-20 that USDC could replace. Also verify the factory and governor contracts on the Mezo explorer, add a pitch deck (a missing deck capped Materials at 1), and state a revenue model such as a per-payout fee taken by the governor.

### 72. RELAY (W1+W2)

- **Tagline:** secure the deal, move the value.
- **Categories:** Escrow, Payments
- **Links:** github `None` · demo `None` · https://app.akindo.io/communities/4e9BMWpMoHkjL2oo/products/3dJE3v1KdfK3N0VVe
- **Wave 1 result:** 13 USDT · scores (Integration/Product/Technical/UX/Materials) 4/6/6/6/4
- **Wave 1 judge review (verbatim):**

  > RELAY sends real MUSD through a clean, non-custodial escrow, but it only uses the plain ERC-20 interface, so Integration stops at level 2. Swapping in USDC would be a config change. To climb the ladder, build your borrow-then-fund idea on Mezo's BorrowerOperations: open or adjust a trove from checkout, show the buyer's trove health, or park merchant reserves in a Mezo primitive, and exercise it on-chain. Also verify the escrow on the Mezo testnet explorer, run release, refund and split payouts on-chain, and define a fee or revenue model. Keep the video under 2:15, because 266 seconds caps Materials.
- **Wave 2 update (team's text, first 700 chars):**

  > ⏳⏳

### 87. Mezo TradeOS (W1)

- **Tagline:** Milestone-based MUSD escrow with verifiable IPFS evidence and on-chain settlement.
- **Categories:** DeFi
- **Links:** github `zzzyyyddd/mezo-tradeos` · demo `None` · https://app.akindo.io/communities/GLzl1BZGpsp8wkmO/products/0nNR7QN1Dt4qKrON
- **Wave 1 result:** 11 USDT · scores (Integration/Product/Technical/UX/Materials) 4/4/6/6/4
- **Wave 1 judge review (verbatim):**

  > Your escrow moves real testnet MUSD, but it only uses the plain ERC-20 interface, so swapping in USDC would be a config change. That holds Integration at 2. To climb the ladder in Wave 2, tie the product to Mezo itself: for example, let buyers fund escrow by borrowing MUSD against BTC through BorrowerOperations, or put idle escrowed MUSD into the Stability Pool or a Mezo Pools position until release. Also verify the TradeEscrow contract on the explorer (the footer currently says 'Verified on-chain deployment' but it isn't verified), cut the demo video to under 2 minutes, and add a revenue model such as an escrow fee or paid resolvers, plus the track, team and dated milestones in the form.

### 88. Mezo Auth Dev (W1)

- **Tagline:** Mezo-native Web3 marketplace for AI, oracles, VeMezo marketplace, and DAO governance.
- **Categories:** Market Infrastructure, Transactions & Monitoring
- **Links:** github `rohithr8484/mezo-yield-harmony` · demo `None` · https://app.akindo.io/communities/zK3qmA9E7f8xoP0N/products/1Po9knvRxtqVEW9QW
- **Wave 1 result:** 11 USDT · scores (Integration/Product/Technical/UX/Materials) 6/4/4/6/2
- **Wave 1 judge review (verbatim):**

  > Your strongest Mezo work is the veMEZO lock and withdraw panel, but it is a thin pass-through to Mezo's own createLock, so integration stays around protocol-aware. To climb the ladder in Wave 2, replace the self-deployed MUSD mocks with canonical testnet MUSD, route fees to a real treasury or seller instead of burning MEZO or paying a third-party demo payee, and ship a working veMEZO marketplace contract that actually transfers veNFTs and is exercised by users other than your deployer. Make advertised features real (read a live price feed instead of Math.random(), store governance on-chain), verify payments server-side rather than in localStorage, and verify your contracts. Declare that this extends your Hackathon 2 project and keep the video under 2:15.

### 94. HodlerStation (W1)

- **Tagline:** HodlerStation brings MUSD minting, on-chain quests, and token rewards to the Mezo ecosystem.
- **Categories:** Infrastructure, Community, DeFi
- **Links:** github `hodlerstation/mezo` · demo `None` · https://app.akindo.io/communities/peqlRqx0jtxr30PDl/products/jaePzG2Djhl4jRrNM
- **Wave 1 result:** 11 USDT · scores (Integration/Product/Technical/UX/Materials) 4/6/4/4/2
- **Wave 1 judge review (verbatim):**

  > Your Mezo integration today is plain ERC-20: MUSD and MEZO move as payments and rewards, but swapping them for USDC would change nothing, so Integration sits at level 2. To climb, build missions and flows around Mezo itself, for example quests that verify a user opened or topped up a trove via BorrowerOperations, deposited to the Stability Pool, provided liquidity in Mezo Pools or locked veMEZO, and route the MUSD treasury into a Mezo primitive. Verify HstToken and HstTreasury on the explorer, make the Mezo flow reachable on the live app without a private account wall (or provide a demo login), and publish a deployable codebase rather than excerpts. Add a pitch deck and a concrete creator-pays business model with pricing.

### 96. MUSD EscrowFlow (W1)

- **Tagline:** Work with confidence. Pay with trust.
- **Categories:** Mezo
- **Links:** github `None` · demo `None` · https://app.akindo.io/communities/o6DWXlkzmumr2xEd/products/lrkvDaEAMhJe82VL
- **Wave 1 result:** 11 USDT · scores (Integration/Product/Technical/UX/Materials) 4/4/6/6/2
- **Wave 1 judge review (verbatim):**

  > Your escrow moves real canonical MUSD on Mezo testnet, but only through the plain ERC-20 and permit interface, so it scores as transactional (L2); to climb, make it Mezo-aware, for example by putting idle escrowed MUSD to work (sMUSD or Stability Pool yield shared between client and freelancer), or letting clients fund an escrow by opening or drawing on a trove through BorrowerOperations, and actually call the Mezo contracts you already list in config. Verify the EscrowFlow contract on the Mezo explorer and show some usage beyond your own test wallets. Fix the submission form: the overview describes a different product (MUSD Split) and the video link is broken, so add a working 2-minute video and a deck showing the on-chain flow. A revenue model (for example, an arbiter fee or a small optional platform fee) would also strengthen the business case.

### 101. Sirius (W1)

- **Tagline:** Confidential data marketplace on Mezo: train on private data in an enclave, settle in MUSD
- **Categories:** Data Marketplace, Payment Infrastructure, DeFi
- **Links:** github `alibenyezza/sirius-mezo` · demo `None` · https://app.akindo.io/communities/1PowLB7eOugnkOJR/products/eaq4DkGp1t8NkVgpa
- **Wave 1 result:** 9 USDT · scores (Integration/Product/Technical/UX/Materials) 4/4/4/4/2
- **Wave 1 judge review (verbatim):**

  > Your MUSD integration is a plain ERC-20 escrow, so swapping in USDC would only be a config change, and that keeps you at level 2. To climb the ladder in Wave 2, make MUSD's Bitcoin backing part of the flow: for example, let buyers open or adjust a trove through BorrowerOperations to pay for a training run without selling BTC, or route provider earnings into the Stability Pool or Mezo Pools. Fix the in-app faucet, which calls mint on canonical MUSD and will revert, verify your contracts on the Mezo explorer, and get at least one real loan through the live UI from a non-team wallet. Add a deck, name your track, state a revenue model, and keep the overview's addresses in line with the current deployment.

### 105. MezoGig (W1)

- **Tagline:** Milestone escrow for freelance work, settled in MUSD on Mezo.
- **Categories:** DeFi
- **Links:** github `mak777uh/mezogig` · demo `None` · https://app.akindo.io/communities/q3qDrX9DOT0rkm3W/products/X4wmkRgXack2VjNR
- **Wave 1 result:** 0 USDT · scores (Integration/Product/Technical/UX/Materials) 2/6/4/4/2
- **Wave 1 judge review (verbatim):**

  > Your escrow contract is clean and well tested, but no MUSD has ever moved through it on Mezo testnet, so integration scores as cosmetic (L1) and the project earns no payout this wave. For Wave 2, fix the 'Approve MUSD' button (it calls approve on the escrow instead of the MUSD token), wire createGigWithPermit into the UI, and run real gigs end to end so funding, approval and payout transfers show on-chain. To go past plain payments, have escrowed MUSD earn through a Mezo primitive, or let clients open or top up a trove to fund a gig. Also state a revenue model, such as a fee on escrowed volume, and fix the event-read error that greets visitors on the live site.

### 108. TrustieWork (W1)

- **Tagline:** The First AI-Verified Developer Marketplace on Bitcoin and Mezo.
- **Categories:** Decentralized Finance, Onchain Freelance, Bank on Bitcoin with MUSD
- **Links:** github `SKAHLO1/dezor-card` · demo `None` · https://app.akindo.io/communities/1PWEpLJgJSpdn3E7/products/eaq397x2BF80lW0P6
- **Wave 1 result:** 0 USDT · scores (Integration/Product/Technical/UX/Materials) 2/6/4/6/4
- **Wave 1 judge review (verbatim):**

  > We scored TrustieWork as an update of your Hackathon 2 entry, so Integration counts only the Oct 16-26 work. That work improved the UI, the indexer and the AI review, but it didn't touch the Mezo integration, so Integration is 1 and earns no payout this wave. To raise it in Wave 2, build new Mezo work in the window: give each employer their own trove, or pool jobs with adjustTrove. Add repay, close and claimCollateral so employers get their BTC back, and read TroveManager and PriceFeed instead of the hard-coded $95,000 BTC price. Also declare the Hackathon 2 history in the form, verify the escrow on the explorer, limit /ai/arbitrate to the job's parties and read the submission URL from the on-chain WorkSubmitted event, and keep the video under 2:15.

### 145. Muster (W2)

- **Tagline:** Real users for Mezo apps: quests paid in MUSD, checked on-chain, escrow earning in Mezo savings.
- **Categories:** User Acquisition, Payments, Quests & Bounties
- **Links:** github `ahmardchain/Muster` · demo `None` · https://app.akindo.io/communities/lrkaVmr9aHBG4l00/products/xKqaeroRNF7RRl3d
- **Wave 2 update (team's text, first 700 chars):**

  > Muster: real users for Mezo apps, paid in MUSD, proven on-chain. Entirely new, built in Wave 2. Track 2 (Access and Distribution). Live on Mezo testnet.  TL;DR: Mezo apps post quests in MUSD ("open a MUSD loan", "save 50 MUSD in Mezo savings", or their own rule). A user joins, does the action on Mezo, and claims; the contract reads their wallet and pays them. No screenshots, no reviewers.  How it works - Post: createQuest pulls reward x places in MUSD and deposits all of it into Mezo's MUSD Savings Rate vault (sMUSD), so idle escrow earns. - Join: refused if the wallet already passes the check, so apps only pay for new usage. - Claim: at least one block after joining, Muster re-checks on-cha

### 146. MUSD SatsBridge: Bitcoin Escrow on Mezo (W2)

- **Tagline:** Autonomous Bitcoin-backed escrow and Pan-African payment gateway on Mezo L2.
- **Categories:** DeFi, Market Infrastructure, Payment
- **Links:** github `amazing200guy1-a11y/musd-satsbridge` · demo `None` · https://app.akindo.io/communities/X4wvrz4JBFMMQaOMP/products/OVdnQ2vDDS8akkdMk
- **Wave 2 update (team's text, first 700 chars):**

  > In this Wave, we completed and deployed the core protocol architecture for MUSD SatsBridge on Mezo Layer 2:  1. Production Smart Contracts: Developed and open-sourced audited-style Solidity 0.8.24 contracts:    - SatsBridgeEscrow.sol: Multi-party milestone escrow releasing 30% advance on carrier dispatch nonce and 70% upon proof of delivery.    - PanAfricanOracleRelay.sol: Circuit-breaker protected FX oracle for KES (M-Pesa), NGN (NIP), GHS (MTN MoMo), ZAR, and RWF.    - IMUSD.sol: Mezo native CDP interface. 2. Standalone Operational Cockpit: Deployed an aerospace-titanium web terminal featuring live tBTC collateral health monitoring (168.4% health factor), active milestone escrows, and a re

## T2 payments / invoices / checkout / payroll

### 12. Mezher (W1+W2)

- **Tagline:** Bitcoin-backed checkout on Mezo: pay in MUSD, borrow the rest from your Trove, keep your BTC.
- **Categories:** Borrow, Bitcoin, Mezo
- **Links:** github `woydarko/mezher` · demo `None` · https://app.akindo.io/communities/DrBVAgDBRsZJRz3zj/products/1PoKP8Ge0cl6eGeX
- **Wave 1 result:** 19 USDT · scores (Integration/Product/Technical/UX/Materials) 8/6/8/8/8
- **Wave 1 judge review (verbatim):**

  > Your integration is already at the composing level: MezherPay borrows from the payer's trove straight to the merchant through Mezo's withdrawMUSDWithSignature, with a real on-chain ICR floor, and two testnet payments prove it. To reach the top of the integration ladder in Wave 2, get real third-party payers and merchants using it, exercise the in-checkout openTrove and balance-permit paths on-chain, and handle Recovery Mode, redemptions and the trove's maxBorrowingCapacity in the quote. On the business side, price the merchant fee and show how it covers relayer gas. A video that walks through a live borrow-to-pay transaction would also strengthen the materials.
- **Wave 2 update (team's text, first 700 chars):**

  > Mezher: checkout for Mezo. Payer opens a merchant's link and pays in MUSD; if the balance is short, Mezher borrows only the missing part from their Trove, straight to the merchant, in one tx.  LINKS App: https://mezher.vercel.app Try: https://mezher.vercel.app/try Live proof: https://mezher.vercel.app/proof Video: https://youtu.be/ig3fK2bzWmY Deck: https://drive.google.com/file/d/1WxLhD3UNYE-DnIdtJfZDBgQhn8pvSeh9/view Code: https://github.com/woydarko/mezher Evidence: github.com/woydarko/mezher/blob/main/docs/evidence.md Contract v2: 0xF113519362677fc0BDE15B172FF22DD8dB30aF27  CHANGED SINCE WAVE 1 1. MezherPay v2: v1 had one pay() and no fee. v2 adds merchant-signed orders, merchant activati

### 16. RentOuts — Rent in MUSD (W1+W2)

- **Tagline:** RentOuts lets tenants pay long-term rent and deposits in MUSD through a non-custodial escrow on Mezo
- **Categories:** Payments, Real World Assets, Marketplace
- **Links:** github `AiAlchemist0/rentouts-musd` · demo `None` · https://app.akindo.io/communities/lrk3Q93dDt9olkVP/products/xKqB4gwBGhdRnpGl
- **Wave 1 result:** 19 USDT · scores (Integration/Product/Technical/UX/Materials) 8/6/8/8/8
- **Wave 1 judge review (verbatim):**

  > Your Mezo Borrow step is well built: openTrove and withdrawMUSD use correct hints and live MCR, fee and price reads. But it sits next to a generic ERC-20 escrow rather than composing with it, so Integration is at the low edge of level 4. For Wave 2, the biggest gain would be contract-level composition: the borrow-and-pay-in-one-transaction flow you plan, putting idle escrowed MUSD to work (for example in the Stability Pool or Mezo Pools), and in-app repay, add-collateral and Recovery Mode or maxBorrowingCapacity handling so tenants can manage liquidation risk after paying. Real non-team tenants and landlords on-chain, plus a stated revenue model (a fee in the rentouts.co portals, for example), would also raise your Product score.
- **Wave 2 update (team's text, first 700 chars):**

  > All four Wave 2 goals are done and live on Mezo testnet. Every lease is new real-world demand for MUSD: rent is borrowed against BTC each month and paid to landlords in MUSD.  Video: https://youtu.be/zwh1X27GUtw App: https://mezo.rentouts.co Deck: https://github.com/AiAlchemist0/rentouts-musd/blob/main/docs/RentOuts-Mezo-Wave2.pdf Every transaction: https://github.com/AiAlchemist0/rentouts-musd/blob/main/docs/MEZO-DEMO.md  1. Pay monthly (done). The tenant funds the deposit plus the first month, then pays each month. If a month stays unpaid a full period past its due date, the landlord can claimDefault: the funded rent plus at most one month from the deposit; the rest returns to the tenant. 

### 22. Owo (W1)

- **Tagline:** Borrow against your Bitcoin on Mezo and get naira in any Nigerian bank account.
- **Categories:** Payments, DeFi, Off-Ramp
- **Links:** github `neromtoobad/owo` · demo `None` · https://app.akindo.io/communities/JBRWr7gevTxkaAXj/products/QlEOvBZwniNrzB8Gw
- **Wave 1 result:** 18 USDT · scores (Integration/Product/Technical/UX/Materials) 8/8/4/8/8
- **Wave 1 judge review (verbatim):**

  > Owo already composes Mezo: OwoDesk borrows from users' troves by signature on testnet, which puts it at integration level 4. To reach level 5 in Wave 2, make the full loop real: live Paycrest naira payouts on mainnet, and the treasury redeeming MUSD through TroveManager, with TCR and Recovery Mode checks. Fix the High that caps Technical at 2. Anyone can copy the borrow signature from a pending relay and submit it first, which mints MUSD into the desk with no order and no way out, so add a recovery path for unassigned MUSD or open the order against it. Then verify OwoDesk on the explorer. Finally, say plainly in the app that settlement rests on the relayer's report of the payout (today it says 'only the contract decides'), and show trove interest and liquidation risk in the cash-out flow.

### 38. MUSD Books (W1+W2)

- **Tagline:** Verifiable MUSD statements and invoice-referenced payments on Mezo
- **Categories:** Payment systems, Bookkeeping
- **Links:** github `neimasilk/musd-books` · demo `None` · https://app.akindo.io/communities/eamQa93eps8JNX3n8/products/wKmLKL9g0Id8NrWW
- **Wave 1 result:** 16 USDT · scores (Integration/Product/Technical/UX/Materials) 6/6/6/8/8
- **Wave 1 judge review (verbatim):**

  > Your integration currently sits at the protocol-aware level: the app reads Trove, PriceFeed and Stability Pool state well, but every Mezo write (openTrove, repay, provideToSP) lives in your demo scripts rather than in the product. To move up the ladder in Wave 2, let users act on Mezo from inside MUSD Books, for example repaying or topping up a Trove from a statement or lender report through BorrowerOperations, and fix the pending-reward double count and Recovery Mode handling in the Trove panel. Verify MusdPay and StatementRegistry on the explorer, deploy them to mainnet as planned, and show real merchants or accountants using the flow. A stated revenue model, such as paid accountant co-attestation or merchant tooling, would also lift the product score.
- **Wave 2 update (team's text, first 700 chars):**

  > Declared goals: (1) accountant flow, (2) Trove report and (3) "Pay with wallet" testing were delivered early, during Wave 1 (17 Oct: review link with co-attestation, lender report with a Trove section, scripted-wallet tests of permit and approve paths). (4) Mainnet was conditional; it is deferred (see 3). Wave 2 work followed the Wave 1 review:  1. Act on Mezo from inside MUSD Books. Next to a statement, the Trove owner can repay MUSD or add BTC collateral (BorrowerOperations.repayMUSD / addColl, hints from HintHelpers and SortedTroves) and deposit or withdraw MUSD in the Stability Pool (provideToSP / withdrawFromSP). A preview shows the new debt, collateral ratio and liquidation price, and 

### 39. MUSD Pay Links (W1+W2)

- **Tagline:** MUSD payment links on Mezo. Checked before paying, with a live borrow quote and an invoice inbox
- **Categories:** Payments, Market Infrastructure
- **Links:** github `theluckystrike/musd-pay-links` · demo `None` · https://app.akindo.io/communities/RDgkLQzMni6M9mm98/products/Pv1lNjOBGIjwEZZj
- **Wave 1 result:** 16 USDT · scores (Integration/Product/Technical/UX/Materials) 6/6/7/6/8
- **Wave 1 judge review (verbatim):**

  > Your integration sits at protocol-aware (L3): the pay page reads PriceFeed, BorrowerOperations, InterestRateManager and TroveManager live, but the borrow step is a link out and the only openTrove came from a dev script. To move up the ladder in Wave 2, let a short payer open or adjust a trove through BorrowerOperations from the pay page itself (or route MUSD into a Mezo primitive), and show those product-sent transactions on chain. Also complete and record a real browser-wallet payment of a signed invoice, ideally from users other than your own two wallets. Finally, put a price on the merchant plan, sign a first pilot, and fix the 337-vs-197 test count mismatch in your submission text.
- **Wave 2 update (team's text, first 700 chars):**

  > MUSD Pay Links — Wave 2 update, 2 November 2026  Track 2: Access and Distribution. The product creates MUSD invoices, checks the intended contract, network, merchant and amount, and verifies payment from the on-chain Transfer event.  Since the 18 October entry, I added an in-product borrowing review and stronger wallet/state guards, then recorded a real MetaMask payment of a signed 1 MUSD invoice on Mezo testnet. The 1 November run covers one rejected payment with no nonce change, one approved payment, Paid status and a saved payment lock after reload. Both accounts belong to the project. The wallet run used a local Worker on hosted Linux; it does not prove payment through the public Preview

### 46. Assumable (W1)

- **Tagline:** Cash out Bitcoin to your bank in one tap. Borrow MUSD on Mezo, keep your BTC.
- **Categories:** Payment, DeFi, Lending
- **Links:** github `Anuoluwapo25/assumable` · demo `None` · https://app.akindo.io/communities/VwvpkaG7lHQO14gzO/products/0nNK3A3JGszzKDrKN
- **Wave 1 result:** 16 USDT · scores (Integration/Product/Technical/UX/Materials) 8/6/6/6/2
- **Wave 1 judge review (verbatim):**

  > Your integration is already strong: CashOutModule opens and borrows from real MUSD Troves through BorrowerOperations on testnet, which reaches level 4. To get to level 5 in Wave 2, exercise the parts that make it new utility on-chain: real TroveMarket sales, a working Route B swap and bridge, and a real payout partner instead of your own signer address. Fix the double-counted pending redistribution in TroveAccount.position() and _debt() (MUSD's getEntireDebtAndColl already includes it), model maxBorrowingCapacity and Recovery Mode, verify your contracts on the explorer, and lock down the unauthenticated /api/payback route. Add a pitch deck with a clear revenue model, keep the video under 2:15, make /cash the landing flow, and only call a step 'real on testnet' once it has a transaction behind it: the swap has none yet.

### 47. Mezout (W1)

- **Tagline:** Get paid in exact MUSD. Let customers pay with Bitcoin
- **Categories:** Access and Distribution, Payment
- **Links:** github `None` · demo `None` · https://app.akindo.io/communities/1Powjqpm7i9V6MRo/products/63Nwlod7Oc6JQOZ2
- **Wave 1 result:** 16 USDT · scores (Integration/Product/Technical/UX/Materials) 8/8/4/7/2
- **Wave 1 judge review (verbatim):**

  > Mezout already composes Mezo deeply: borrow-to-pay mints MUSD from the payer's trove with an on-chain 160% ICR floor, and BTC/MEZO payments settle into MUSD through Tigris pools. To reach the top of the integration ladder, close the front-run griefing path on the borrow signature (bind the caller to the router, or add a refund path for stray MUSD), exercise borrow-to-pay on router v2, and add redemption and liquidation monitoring or top-up for borrowers after checkout. Getting real merchants and outside payers on-chain, and setting a fee that covers relayer gas, would strengthen the business case. Add a pitch deck, because its absence caps Submission Materials, and fill in the track and team fields.

### 48. Remitsheet for Mezo (W1)

- **Tagline:** Pay a whole spreadsheet in MUSD, MEZO or BTC with one signature and one Mezo transaction.
- **Categories:** Payments, Payroll, Stablecoins
- **Links:** github `aratass/remitsheet-mezo` · demo `None` · https://app.akindo.io/communities/ENkEE894XtLR7jra/products/rgmK1kjVkt7kjz0NV
- **Wave 1 result:** 15 USDT · scores (Integration/Product/Technical/UX/Materials) 6/6/6/6/6
- **Wave 1 judge review (verbatim):**

  > Your integration is protocol-aware: the Borrow panel reads TroveManager, PriceFeed and BorrowerOperations live. But the product only links out to Mezo Borrow, and the contract's whole on-chain history is one 1 MEZO self-payment, with no MUSD batch. The biggest Wave 2 gain would be shipping the borrow-and-pay flow (for example withdrawMUSDWithSignature through BorrowerOperations) and running real MUSD batches to other recipients. Also fix the double-counted pending redistributions in borrow.ts, handle Recovery Mode and redemption risk in the panel, and verify the contract on the explorer. Reword 'deployed ... at the same address on Mezo testnet and mainnet' to say the address is deterministic and mainnet is next, because there is no code on mainnet yet.

### 50. Kudi (W1+W2)

- **Tagline:** Kudi lets you borrow MUSD against your Bitcoin on Mezo without selling it.
- **Categories:** DeFi Lending, Payments, consumer apps
- **Links:** github `Yungtimmy/kudi` · demo `None` · https://app.akindo.io/communities/JBRLwjXBvT4l4m1g/products/83NnvOGa8TlAWR3GZ
- **Wave 1 result:** 15 USDT · scores (Integration/Product/Technical/UX/Materials) 6/6/6/8/2
- **Wave 1 judge review (verbatim):**

  > Your borrowing code is protocol-aware and correct against the MUSD contracts (openTrove, adjustTrove, addColl, repayMUSD with proper hints and fee sizing), but we could not find a single on-chain transaction tied to Kudi, so Integration stopped at Level 3. For Wave 2, list the wallet and transaction hashes for real testnet troves opened, topped up and repaid through Kudi (and a Mezo Pools swap) to reach Level 4, and handle maxBorrowingCapacity, oracle staleness and redemptions. Add a revenue model (for example an interface fee or off-ramp spread) and early user evidence from Nigerian BTC holders, plus some tests. Include a pitch deck, state your track, and keep the video under 2 minutes.
- **Wave 2 update (team's text, first 700 chars):**

  > Wave 2 updates  1. Real Mezo testnet proof The Wave 1 review found no on-chain transactions, so this wave we ran Kudi's full borrowing flow on Mezo testnet from the test wallet 0x10c809BF6cE3e3dE8d9830F89297FF02bEa5D12f: - Open trove: 0x61db82218156db129428eb352e972d5af29af0c22b40df5c9d7c28b58c55a911 - Add collateral: 0xa09b639fef3f407db5d934d784a1a1264bd7115b63eaedbc756b4570334f6372 - Repay mUSD: 0x403a67e00104ac763bda9c62e2184005f58be746412b802e870f5e236b722faf - Mezo Pools swap: 0x6de234978046b07f7e65ba10478fa548c247d97a7614e1e09364697ee877a063 All four can be checked on explorer.test.mezo.org.  2. Evidence in the repo We added a proof write-up with these hashes and the steps to reproduce

### 51. PayLink (W1+W2)

- **Tagline:** Dollar invoices you share as a link, paid in MUSD on Mezo.
- **Categories:** Payments
- **Links:** github `nambininasafidison/paylink` · demo `None` · https://app.akindo.io/communities/3dJ9qxgpgipJnNpP/products/Mz9la64BOUvBxKMmz
- **Wave 1 result:** 15 USDT · scores (Integration/Product/Technical/UX/Materials) 6/6/8/4/2
- **Wave 1 judge review (verbatim):**

  > Your MUSD integration is real but shallow. Payments use plain ERC-20 permit calls, and the Mezo-specific part is a read-only estimate of how big a trove would need to be. To move up the ladder in Wave 2, let a payer who is short of MUSD open or adjust a trove through BorrowerOperations (with headroom above 110%) and pay the invoice in the same flow, then show payments from people outside the team. We judged branch mezo at cf43fa0 as your Wave 1 baseline. Next time, point the submission at an exact commit, make the first screen render fast and without a wallet (our automated browser saw a blank page after 12 s), and add a short pitch deck and a revenue model, since the contract charges no fee.
- **Wave 2 update (team's text, first 700 chars):**

  > New since our wave 1 submission (commit 79c3e67, Oct 21, 2026).  What we learned. We surveyed Malagasy developers paid from abroad (FaceDev Facebook group, Oct 28-30, 10 responses, 9 of them paid from abroad). Honest reading: their payments mostly work. 8 of 9 say the last one went fine, 5 of 9 used a bank transfer, 8 of 9 lost under 3% or nothing they know of. What remains is trust: one waited days to be sure the money had arrived; one met a client who said "I paid" while nothing arrived, a fake proof of payment and a dispute on the amount; one lost a bitcoin payment to a reseller when converting to ariary. 4 of 9 have received or held crypto. A small, tech-savvy sample from one group: not 

### 52. Runway (W1)

- **Tagline:** Fund your team in MUSD, track payments, and plan your runway on Mezo.
- **Categories:** Payments, Borrowing
- **Links:** github `None` · demo `None` · https://app.akindo.io/communities/rgWPRNdQ9TRZzjB1/products/7mNo9o7NwC2W8BqX
- **Wave 1 result:** 15 USDT · scores (Integration/Product/Technical/UX/Materials) 6/6/8/8/2
- **Wave 1 judge review (verbatim):**

  > Runway already reads Mezo trove and PriceFeed state correctly and ties it to payroll planning, which puts Integration at level 3. The biggest Wave 2 gain is to act on Mezo rather than only read it: let a founder borrow or top up a trove through BorrowerOperations inside Runway and route the minted MUSD straight into a payment schedule, and model Recovery Mode, the borrowing fee and minimum debt in the headroom figure. Add a business model (a schedule or workspace fee), get real users beyond your two test wallets, and submit a deck plus a video under 2 minutes, since the missing deck and the 5-minute video hold Materials down.

### 69. Automation Studio (W1)

- **Tagline:** Automate MUSD payments on Mezo with spending limits, cash protection, and group payouts.
- **Categories:** Payments, DeFi, Automation
- **Links:** github `liamtren21/automation-studio` · demo `None` · https://app.akindo.io/communities/0nNK30KJkuQZpVgw/products/d8NjdaWRmTrrmxll
- **Wave 1 result:** 14 USDT · scores (Integration/Product/Technical/UX/Materials) 6/6/6/6/2
- **Wave 1 judge review (verbatim):**

  > Automation Studio moves real canonical MUSD through well-guarded payment contracts and already reads Trove state from TroveManager and PriceFeed, which puts Integration at level 3. To reach level 4 in Wave 2, exercise the Mezo-specific paths on-chain: actually route vault surplus into BorrowerOperations.repayMUSD or let the V2 account open and top up troves for users, and show those transactions. Verify both contracts on the explorer, state a track, a target user and a revenue model (for example a per-execution or subscription fee for the hosted worker), and add a deck plus a video under 2:15 that shows the live testnet flow rather than the simulation.

### 80. PayLink — Digital Products (W1+W2)

- **Tagline:** Sell digital products with MUSD. Private downloads, direct payments, and purchase recovery.
- **Categories:** E-Commerce, Creator Tools, Payments
- **Links:** github `Fuuaad05/paylink` · demo `None` · https://app.akindo.io/communities/4eN1gp6GBT2keJ8ol/products/OVdoVwqKKuP4OK4l
- **Wave 1 result:** 12 USDT · scores (Integration/Product/Technical/UX/Materials) 4/6/6/6/2
- **Wave 1 judge review (verbatim):**

  > Your x402 MUSD checkout works on-chain: we traced your test purchases (0.01 MUSD on Oct 19 and 20 MUSD on Oct 20) to your seller wallet, so Integration scores 2, the transactional level. Next time, cite those wallets and tx hashes in the submission yourself rather than leaving judges to find them. To climb the ladder in Wave 2, use Mezo beyond plain ERC-20 payments: let a buyer without MUSD borrow it against BTC through BorrowerOperations, or swap into it through Mezo Pools at checkout. Add a platform fee or paid tier so the business sustains itself, and commit or link a pitch deck, since the missing deck capped Materials at 1.
- **Wave 2 update (team's text, first 700 chars):**

  > Wave 2 extends PayLink’s MUSD digital-product checkout in direct response to Wave 1 feedback.  Track: 2 — Access and Distribution. Chain: Mezo testnet (31611). Builder: Fouad Abdulhakeem, solo builder responsible for product, development and testing.  NEW SINCE WAVE 1  1. Mezo Pools funding inside checkout Buyers can preview and execute a BTC-to-MUSD swap through Mezo’s testnet router without leaving PayLink. The interface shows the quote, minimum received and slippage before wallet confirmation. MUSD returns to the buyer’s wallet; purchasing the product is a separate payment.  2. Paid Creator plan The free plan supports 3 products. Creator costs 3 MUSD for 30 days and supports up to 25 prod

### 81. SettleTag (W1)

- **Tagline:** One-time MUSD invoices with direct merchant settlement and verifiable onchain receipts.
- **Categories:** Payment, DeFi, merchant
- **Links:** github `0xNexuz/settletag` · demo `None` · https://app.akindo.io/communities/wKm7EmEewS9RQ1gO/products/4eNPVVA9wh2O8P0no
- **Wave 1 result:** 12 USDT · scores (Integration/Product/Technical/UX/Materials) 4/4/6/6/6
- **Wave 1 judge review (verbatim):**

  > SettleTag is a clean, non-custodial invoice contract with a real 1 MUSD settlement on Mezo testnet, but it uses MUSD only through plain ERC-20 transferFrom, so it sits at integration level 2. To move up in Wave 2, bring Mezo-specific behaviour into the live product. For example, let a merchant or payer borrow MUSD against BTC through BorrowerOperations to fund an invoice, or show trove health, all inside the app flow and not just in your operator script. Verify the contract on the Mezo explorer, and get real third-party merchants and payers using it. A stated business model, such as a settlement fee or a paid merchant tier, would also strengthen your product score.

### 85. Envelope (W1)

- **Tagline:** Send dollars to anyone with just a link. They claim MUSD with no wallet, no sign-up and no fee.
- **Categories:** Payment, stablecoin, Consumer
- **Links:** github `imprint-hash/envelope` · demo `None` · https://app.akindo.io/communities/A8NgWgBAvh6GBdLm/products/Pv1m2jenpUDWDv4K
- **Wave 1 result:** 12 USDT · scores (Integration/Product/Technical/UX/Materials) 4/6/6/6/2
- **Wave 1 judge review (verbatim):**

  > Envelope moves real MUSD on Mezo testnet, but only through plain ERC-20 and permit calls, so the same escrow would work with any token and Integration sits at level 2. To move up in Wave 2, build the roadmap items in code: let senders fund an envelope by borrowing MUSD through BorrowerOperations, or route claimed MUSD into a Mezo savings or Pools position, and show those transactions on-chain. Verify LinkEscrow on the testnet explorer and add a pitch deck, since a missing deck caps Materials. A stated way to pay for the gas relayer (a small escrow fee or off-ramp revenue share) would also strengthen the business case.

### 86. MUSD Split (W1)

- **Tagline:** Split shared costs. Settle them in MUSD on Mezo
- **Categories:** Split
- **Links:** github `None` · demo `None` · https://app.akindo.io/communities/ENB44wpBjFzPPDDP8/products/OVdLqeKnqt8XBwxpW
- **Wave 1 result:** 12 USDT · scores (Integration/Product/Technical/UX/Materials) 4/6/6/6/2
- **Wave 1 judge review (verbatim):**

  > Your MUSD settlement is real and well built: the permit and batch settlement contract moves canonical MUSD on Mezo testnet. But it only uses plain ERC-20 calls, so swapping in USDC would change nothing, and that keeps Integration at level 2. To score higher in Wave 2, make the app Mezo-aware. For example, let a user who is short on MUSD open or adjust a trove through BorrowerOperations inside the app to cover a debt, or show the trove health behind the MUSD they spend. Also verify the settlement contract on the explorer, get real users beyond your test wallets, and add a deck, a team section and a revenue model.

### 93. Cambio (W1)

- **Tagline:** Cambio enables MUSD payments on Mezo with verified usernames, secure links, and on-chain proof.
- **Categories:** DeFi
- **Links:** github `Lushegs01/cambio` · demo `None` · https://app.akindo.io/communities/kzqkG4lWnTEvQmwK/products/K8OW2OWQkiQXp3qmG
- **Wave 1 result:** 11 USDT · scores (Integration/Product/Technical/UX/Materials) 4/6/4/4/2
- **Wave 1 judge review (verbatim):**

  > Your integration score is held back because no MUSD payment or swap has actually happened on-chain. In Wave 2, complete and cite real testnet transactions (a MUSD send, a settled payment request, a BTC->MUSD swap), and go beyond plain ERC-20 transfers, for example by reading Mezo PriceFeed or trove health, or by letting payers mint MUSD against BTC through BorrowerOperations. Add a revenue model (merchant fees, a routing fee or subscriptions) and some evidence of real users. Add a pitch deck, state your track and team, and remove claims that don't match the repo, such as 'Solidity smart contracts' and the 'CRYPTO -> NAIRA' mockup text.

### 98. MUSD Subs (W1)

- **Tagline:** Bitcoin-backed recurring payments: MUSD subscriptions with automatic revenue splits on Mezo.
- **Categories:** Payments
- **Links:** github `ifeohsun/mezo-musd-subs` · demo `None` · https://app.akindo.io/communities/Pv70qxDWRS8mZdAm/products/rgm1vwLkMUDmZ9ao
- **Wave 1 result:** 10 USDT · scores (Integration/Product/Technical/UX/Materials) 4/4/6/4/2
- **Wave 1 judge review (verbatim):**

  > MUSD Subs is a clean, working recurring-payment contract on Mezo testnet, but MUSD only moves through plain ERC-20 transferFrom, so it scores as transactional (L2); to climb the integration ladder, make the product itself act on Mezo primitives, for example letting subscribers fund plans by borrowing MUSD against BTC via BorrowerOperations or checking trove health before charging. Add a business model (a protocol take-rate or keeper tip), ship the keeper bot, and show real third-party subscribers rather than only the team's own burner wallet. Improve the UI with a plan discovery list, due-date status and input validation, and submit a deck plus a video of 2:15 or less that shows the on-chain flow.

### 99. BitStreamfi (W1+W2)

- **Tagline:** Decentralized, Bitcoin-backed streaming payroll and autonomous credit on Mezo.
- **Categories:** DeFi, Payments & Settlement
- **Links:** github `NileshPandey05/BitStreamfi` · demo `None` · https://app.akindo.io/communities/63Nwvv0epILOKJenr/products/4eNwvZZBEh2DMRGRD
- **Wave 1 result:** 10 USDT · scores (Integration/Product/Technical/UX/Materials) 4/4/4/6/2
- **Wave 1 judge review (verbatim):**

  > Integration is your biggest lever: the vault currently lends out team-seeded MEZO labelled as MUSD through plain ERC-20 calls, so it scores as transactional only. Use the real testnet MUSD (0x1189...c503) and open or adjust troves through Mezo's BorrowerOperations with PriceFeed instead of a hard-coded $60,000 price, and stream that MUSD into payroll, which would move you to protocol-aware or composing levels. Fix the three High findings (no liquidation, shared native/tBTC collateral accounting, unwithdrawable yield balance), point tBTC at a real token contract, verify the contracts, and add tests for the streamer and credit engine. Make the overview match the code: label tokens correctly, drop the 'Mezo staking yield' and 'verified' claims until they are true, and show real streams and repayments on-chain in the video.
- **Wave 2 update (team's text, first 700 chars):**

  > 🔗 Deliverables & Verification - Web App: https://bit-streamfi.vercel.app/ - Video Demo: https://youtu.be/I5Upty2PRBE - GitHub Repo: https://github.com/NileshPandey05/BitStreamfi - Pitch Deck: https://docs.google.com/presentation/d/1L3tcfUC-Sam7XMh7fmLMl0icIo-Bfc7SI_IXfajlVaM/edit?usp=sharing - Telegram Bot: https://t.me/BitStreamfiBot  🎯 100% Resolution of Wave 1 Feedback (Composing Tier) 1. Official Mezo MUSD: Replaced mock tokens with canonical testnet MUSD (0x1189...c503). All loans and payroll operate on real MUSD. 2. Dynamic PriceFeed: Integrated Mezo’s live PriceFeed Oracle (0x86bC...9366) to query dynamic BTC market price ($80k+) instead of a hardcoded value. 3. BorrowerOperations Com

### 115. MezoFlow (W1)

- **Tagline:** Simple, secure MUSD payments on Mezo with wallet integration and QR codes.
- **Categories:** Payments, Wallet, DeFi
- **Links:** github `None` · demo `None` · https://app.akindo.io/communities/q34z1DdddirMM3pA/products/K8OZ68AQWFm1G2lP
- **Wave 1 result:** 0 USDT · scores (Integration/Product/Technical/UX/Materials) 2/4/4/6/2
- **Wave 1 judge review (verbatim):**

  > MezoFlow is a clean, honest MUSD send-and-request wallet, but on our ladder its integration is cosmetic. It uses only plain ERC-20 calls on canonical testnet MUSD, and we found no on-chain transfers or tx hashes tied to the product, so it earns no payout this wave. For Wave 2, list the transaction hashes and wallets from your demo transfers, and go deeper into Mezo: read trove health from TroveManager and PriceFeed on the Positions page, or let users borrow or repay MUSD through BorrowerOperations from the payment flow. Add a pitch deck (a missing deck caps Materials at 1), cut the video to under 2:15, fill in track, category and project status, and say who pays and how the app sustains itself. Also show 'VERIFIED' only after the wallet's chain is checked, and consider adding WalletConnect or Mezo Passport alongside MetaMask.

### 118. Mezora (W1)

- **Tagline:** Business finance on Mezo: MUSD bills, cash planning, receivables, and debt repayment.
- **Categories:** Treasury Management, Payments, DeFi
- **Links:** github `maixuancanh/mezora` · demo `None` · https://app.akindo.io/communities/eaq2Bq460iOZRpp2/products/o6q29Wp7MIg7EZK8
- **Wave 1 result:** 0 USDT · scores (Integration/Product/Technical/UX/Materials) 0/0/0/0/0
- **Wave 1 judge review (verbatim):**

  > Duplicate submission: this entry duplicates another AKINDO entry from the same team ("Automation Studio"), which was reviewed and scored on its own card. This duplicate receives no grant and no points.

### 119. paykit (W1)

- **Tagline:** One-script MUSD checkout for Mezo, with automated on-chain payment verification and webhooks.
- **Categories:** Payment, market  infra
- **Links:** github `sammy-XXIV/paykit` · demo `None` · https://app.akindo.io/communities/1Po9EqL83hqPeX7jP/products/DrBmGBew2tZPZvMNW
- **Wave 1 result:** 0 USDT · scores (Integration/Product/Technical/UX/Materials) 2/4/4/4/2
- **Wave 1 judge review (verbatim):**

  > Paykit uses canonical testnet MUSD, but we found no MUSD payments on-chain, and the product only does a plain ERC-20 transfer, so Integration scored at the cosmetic level. In Wave 2, make real checkout payments on Mezo testnet and link the tx hashes. Then go past plain transfers into Mezo itself: for example, let buyers pay from a trove borrow or the MUSD Savings vault, as your roadmap describes. Also fix payment detection (start eth_getLogs at the intent's creation block, within the RPC's 10,000-block limit, and bind each payment to one intent), and either build the permit flow and network switch or remove those claims. Add a deck and a revenue model. Integration at level 1 (cosmetic) earns no payout this wave: to be paid, MUSD or MEZO has to do real work in the product on-chain, not only appear in it.

### 121. Weebo (W1)

- **Tagline:** Crypto tipping for Discord; no wallets, no gas, no jargon
- **Categories:** Payments, Social/Engagement, Bitcoin Infrastructure
- **Links:** github `None` · demo `None` · https://app.akindo.io/communities/kzqk8xq3qtKvGjQ1/products/lrkvao1GOs0RE3g4K
- **Wave 1 result:** 0 USDT · scores (Integration/Product/Technical/UX/Materials) 0/0/0/0/0
- **Wave 1 judge review (verbatim):**

  > Weebo wasn't judged in Wave 1 because there was nothing we could verify. The GitHub field held a Discord invite rather than a public code repository, there was no live link or video, and no contract address or transaction showed MUSD or MEZO in use. For Wave 2, push the bot's source to a public GitHub repo with commits from the build window. In the repo or app config, list the canonical Mezo testnet MUSD/MEZO addresses (or the Mezo contracts) the bot uses, plus a few testnet transaction hashes from /tip, /deposit or /withdraw. Add a short demo video of the commands in a Discord server and, if you can, a reachable live surface such as the planned web UI, so judges can check it without depending on your PC being online.

### 127. netteo (W1)

- **Tagline:** Netteo settles multi-party debts in one net payment using MUSD on Mezo.
- **Categories:** Payments, DeFi, Market Infrastructure
- **Links:** github `anshxft/netteo` · demo `None` · https://app.akindo.io/communities/JBRWxRZw7Tp8QGJk/products/mVqpRqBkOIaWg83D
- **Wave 1 result:** 0 USDT · scores (Integration/Product/Technical/UX/Materials) 0/0/0/0/0
- **Wave 1 judge review (verbatim):**

  > netteo scored 0 because it failed gate G2 (real integration): the live app only uses the team's own MockMUSD and a kernel bound to it, so users can only ever touch a test token, never real MUSD.

### 128. netteo (W1)

- **Tagline:** Netteo settles multi-party debts in one net payment using MUSD on Mezo.
- **Categories:** Access & Distribution, DeFi
- **Links:** github `anshxft/netteo` · demo `None` · https://app.akindo.io/communities/JBRWxRZw7Tp8QGJk/products/83Nwjg8XlFWlnGoG
- **Wave 1 result:** 0 USDT · scores (Integration/Product/Technical/UX/Materials) 0/0/0/0/0
- **Wave 1 judge review (verbatim):**

  > Duplicate submission: this entry duplicates another AKINDO entry from the same team ("netteo"), which was reviewed and scored on its own card. This duplicate receives no grant and no points.

### 137. Cobra (MUSD invoices on Telegram) (W2)

- **Tagline:** Voice note to MUSD invoice on Telegram. Paid to your wallet on Mezo, alerted the moment it lands.
- **Categories:** Consumer APP, Payments
- **Links:** github `5wt6fw45nt-design/cobra-near` · demo `None` · https://app.akindo.io/communities/OVdXd7zZzUorEqDp/products/kzq4169Zgcq2dOrr
- **Wave 2 update (team's text, first 700 chars):**

  > Built during this Wave: MUSD on Mezo as a payout option in Cobra. The freelancer picks "MUSD · Mezo" and gives their 0x address. Each invoice gets a payment page with the exact MUSD amount (tagged with the invoice id in the last wei so equal invoices never collide), an EIP-681 QR, and a "Pay with my wallet" button that adds or switches to Mezo and sends the MUSD transfer. A watcher scans MUSD Transfer events every minute and alerts the freelancer in Telegram with the explorer link. Live on Mezo testnet. Bot: https://t.me/Cobrainvoicebot Code: https://github.com/5wt6fw45nt-design/cobra-near (src/mezo.js, src/payments.js, src/paypage.js) Demo: https://www.youtube.com/watch?v=A6T6UWjXzmM

### 148. Runway (W2)

- **Tagline:** Pay your team in MUSD. Keep your Bitcoin.
- **Categories:** Payments
- **Links:** github `None` · demo `None` · https://app.akindo.io/communities/RDjmgMG8jSjkPkGG/products/93NWXBkNBu8Eo4P0
- **Wave 2 update (team's text, first 700 chars):**

  > 1

## T2 savings goals / circles / gamified savings

### 40. Pocket (W1+W2)

- **Tagline:** Pocket: Social payments for Bitcoin holders on Mezo. Send, request, and save mUSD.
- **Categories:** Payments, DeFi, Wallet
- **Links:** github `None` · demo `None` · https://app.akindo.io/communities/d87nqA9A4CJK1ZeL8/products/4eNnZ0KW7t0Q69VW
- **Wave 1 result:** 16 USDT · scores (Integration/Product/Technical/UX/Materials) 8/6/7/6/2
- **Wave 1 judge review (verbatim):**

  > Your Mezo integration is already deep: users open and close Troves and use the sMUSD Savings vault from an embedded wallet, and the calls are protocol-correct. To move from 4 toward 5, bring in real users beyond your own wallets and add a mechanism that creates new MUSD demand, such as merchant checkout settling in MUSD or an add-collateral or auto top-up flow that protects borrowers from liquidation. Add a pitch deck (its absence capped Materials at 1), state your track, and describe a revenue model (for example fees on merchant payments or a spread that covers the gas sponsorship). Also update the README to match the current direct-transfer architecture, and exercise repay and claimYield on-chain.
- **Wave 2 update (team's text, first 700 chars):**

  > During Wave 2, I expanded mPocket on Mezo Testnet with payments, merchant checkout, weekly tasks and an Android app.  App: https://mpocket.tech/home Android: https://mpocket.tech/downloads/mpocket-0.2.4.apk Deck: https://mpocket.tech/pitch-deck.pdf Repo: https://github.com/greyw0rks/musd-pocket  - Payments: Users sign direct mUSD transfers from Privy embedded wallets. Pocket verifies network, sender, token, recipient, amount, calldata, receipt and Transfer event. Proof reuse across invoices is blocked. - Merchant checkout: Added Business profiles, invoice links and QR checkout. Invoices survive sign-in; paid invoices and Activity are recorded together. - Verified merchants: Any confirmed pos

### 45. BitPot (W1)

- **Tagline:** Save MUSD. Win MEZO. Never lose your deposit.
- **Categories:** No-Loss Prize Savings
- **Links:** github `olurocks/bit-pot` · demo `None` · https://app.akindo.io/communities/Mz9emz9GqCX6gl0Q/products/A8NgWWM1BtgGq3Lm
- **Wave 1 result:** 16 USDT · scores (Integration/Product/Technical/UX/Materials) 8/6/6/6/2
- **Wave 1 judge review (verbatim):**

  > Your pool really does compose Mezo's MUSD savings vault and VaultGauge on-chain. To go deeper on integration in Wave 2, run the full loop live: real draws paying out MEZO, withdrawals through the gauge and vault, and verifiable randomness (Pyth Entropy) in place of the owner seed. Also cap drawTimeout so the owner can never freeze principal. Verify the PrizePool contract on the Mezo explorer, and say clearly what changed since your Hackathon 2 version, keeping the real commit history. Replace the black-screen video with a 2-minute demo of an actual deposit and draw, add a short deck, and decide who pays, for example a small fee on prizes, so the product doesn't depend entirely on Mezo emissions.

### 62. AjoCircle (W1)

- **Tagline:** Onchain ajo/esusu savings circles in MUSD on Mezo, with automatic payouts and collateral cover.
- **Categories:** DeFi, Payments, Savings
- **Links:** github `ajocircle-dev/ajocircle` · demo `None` · https://app.akindo.io/communities/27NpWmV62ixGRLQ4/products/xKq2nJ9vvumvaon4M
- **Wave 1 result:** 15 USDT · scores (Integration/Product/Technical/UX/Materials) 4/6/8/6/6
- **Wave 1 judge review (verbatim):**

  > Your MUSD integration is currently plain ERC-20 transfers through a token-agnostic contract, which keeps Integration at level 2; the fastest way up is to deploy your MUSDSavingsRateAdapter and route real circle collateral into Mezo's sMUSD vault, which does exist on testnet at 0x6f461c68B2c5492C0F5CCEc5a264d692aA7A8e16, and to fix the yield accounting so a closing circle receives the yield auto-claimed by its final withdraw. Please correct the 'mainnet-only' statement in the app, README and overview, since claims that don't check out cap the Materials score. On product, add a way for savers to get MUSD without opening a 2,000 MUSD trove (an on-ramp or swap), state who pays and how the service sustains itself, and show circles run by people outside the team. The contract design, the on-chain demo circle with slashing, and the tests are solid foundations.

### 71. MUSD Pocket (W1+W2)

- **Tagline:** Bitcoin-backed savings goals and payments for everyone, powered by Mezo MUSD.
- **Categories:** Access & Distribution
- **Links:** github `Cyptoboy777/musd-pocket` · demo `None` · https://app.akindo.io/communities/7mNwdW6lMHBpD8vA/products/lrkJw68jAfL634ne
- **Wave 1 result:** 13 USDT · scores (Integration/Product/Technical/UX/Materials) 4/6/6/4/6
- **Wave 1 judge review (verbatim):**

  > Your integration sits at L2: MUSDPocket moves real testnet MUSD, but only through plain ERC-20 calls, so the same contract would work unchanged with USDC. You already ran borrow-into-goal on testnet (contract 0xEC03...D460, tx 0x509e31f2...), but its source isn't in your repo, it isn't verified, and your app doesn't use it, so it couldn't count. For Wave 2, publish and verify that contract, wire it into the app with a live view of trove ICR and liquidation price, and consider routing locked balances into the MUSD Savings vault. Fix your primary live link too: musd-pocket.vercel.app belongs to another team's 'Pocket' app, so judges only see your product through the GitHub Pages backup. Show real users beyond your own two wallets.
- **Wave 2 update (team's text, first 700 chars):**

  > MUSD Pocket turns Mezo's Bitcoin-backed MUSD into savings goals with a target and an unlock date. Friends and family can contribute to a shared goal, and existing Mezo borrowers can borrow MUSD against BTC straight into a goal.  Live project: https://musd-pocket-mezo.vercel.app Public code: https://github.com/Cyptoboy777/musd-pocket Final Wave 2 deck: https://github.com/Cyptoboy777/musd-pocket/blob/master/docs/MUSD-Pocket-Wave2-Final.pdf Pitch video: https://youtu.be/eWAqu1FZ-40  What changed since Wave 1 - Published the v2 contract and integrated Mezo's BorrowerOperationsSignatures for borrow-into-goal, beyond plain ERC-20 deposits. - Added live collateral-ratio and estimated liquidation-pr

### 75. Ipin (W1)

- **Tagline:** You decide what your money is for, not whoever receives it.
- **Categories:** DeFi
- **Links:** github `adetyaz/Ipin` · demo `None` · https://app.akindo.io/communities/DrBmgD6GDFwNQWlE/products/NmgoM3MMluABAdG6
- **Wave 1 result:** 13 USDT · scores (Integration/Product/Technical/UX/Materials) 4/6/6/6/6
- **Wave 1 judge review (verbatim):**

  > Ipin is a well-engineered purpose-bound payments vault, but today MUSD moves only through plain ERC-20 and permit calls, so swapping in any stablecoin would change nothing and Integration sits at level 2. The biggest Wave 2 gain is building what is already in your plan: put idle pot balances into the MUSD savings vault and add borrow-to-pay through BorrowerOperations, then show those calls on-chain. Also run the full flow on testnet (vendor payouts via execute, schedules and claimFees, not just deposits) and verify the Vault on the Mezo explorer. Finally, add evidence from real senders and say in the form which track you are entering and who is on the team.

### 82. Round (W1)

- **Tagline:** Round brings savings circles on-chain with Bitcoin as the guarantee.
- **Categories:** DeFi
- **Links:** github `mrfomoweb3/round` · demo `None` · https://app.akindo.io/communities/gXleJEp81hWkprBK/products/BeNz7ZA1nunj0rxk
- **Wave 1 result:** 12 USDT · scores (Integration/Product/Technical/UX/Materials) 4/6/6/6/2
- **Wave 1 judge review (verbatim):**

  > Your integration depth is held back because no MUSD has moved through the Round contract yet: circle #1 was created, but nobody has joined, paid or settled on testnet, so please run a full circle with a default on-chain. The biggest step up is composing with Mezo inside the product, for example the planned 'borrow your contribution' flow that opens a trove through BorrowerOperations, or putting idle pot MUSD into the Stability Pool. Add a revenue model (such as a payout fee) and some user validation with real savings groups, and include a pitch deck plus a video that records the live on-chain flow.

### 89. Bastion (W1)

- **Tagline:** Gamified MUSD savings on Mezo
- **Categories:** Gamified Savings, DeFi + NFT, On-Chain Achievements
- **Links:** github `None` · demo `None` · https://app.akindo.io/communities/834PArJq6Tl6d6x0w/products/Mz9pOPkAEc8GOOZ1
- **Wave 1 result:** 11 USDT · scores (Integration/Product/Technical/UX/Materials) 4/4/6/6/2
- **Wave 1 judge review (verbatim):**

  > Bastion moves canonical MUSD only through plain ERC-20 calls, so it sits at L2, and swapping in USDC would be a config change. For Wave 2, build the roadmap's yield routing so the vault deploys MUSD into a real Mezo primitive (Stability Pool, Mezo Pools liquidity, or trove management through BorrowerOperations) and pays yield from that instead of an owner subsidy, and add a fee on that real yield as a business model. Verify the vault contracts on the Mezo explorer, fix the discarded yield carry and the non-redeemable transferred bMUSD, and make sure the claims match the code (pause can block withdrawals). Link a pitch deck and fill in the track, team and project-status fields, because the missing deck capped Materials.

### 95. Knockout (W1)

- **Tagline:** No-loss MUSD savings bracket: last one standing takes the pot, nobody loses their stack.
- **Categories:** DeFi · Game · Payments
- **Links:** github `yeziR4/musd-knockout` · demo `None` · https://app.akindo.io/communities/A8NgO8QQjFZM1QG7/products/4eNwDpQRru7l3lD2
- **Wave 1 result:** 11 USDT · scores (Integration/Product/Technical/UX/Materials) 4/5/4/6/2
- **Wave 1 judge review (verbatim):**

  > Knockout's integration is plain ERC-20 MUSD today: the jar would work unchanged with any stablecoin, and you opened the trove by hand from your wallet rather than through the product. For Wave 2, have the contracts compose Mezo directly, by funding the pot from sMUSD yield or offering the one-step BTC-to-MUSD ticket through BorrowerOperations, and add in-app deposit, withdraw and claim, a verified contract and real outside users. The security review found one High that caps Technical at 2. The operator knows the committed secret all round, and lockRound is public, so an operator-controlled contract can deposit a computed amount and lock in one transaction, which makes it the winner and gives it the pot. Bind the seed to the frozen field (for example, a VRF or drand value requested after lock), or say plainly that the operator can choose the winner, and add a pitch deck, team details and corrected UI copy about seeding.

### 139. AjoChain (W2)

- **Tagline:** Ajo/esusu savings circles in MUSD on Mezo. Your locked collateral earns BTC while you save.
- **Categories:** DeFi, Savings, Payments
- **Links:** github `blockchaincali/ajochain-mezo` · demo `None` · https://app.akindo.io/communities/Nmg4enqLlhd1ov1Vq/products/EN83PXGdRcla379Q
- **Wave 2 update (team's text, first 700 chars):**

  > First submission (joined in Wave 2). Everything below was built for Mezo during this Wave, on top of the AjoChain savings-circle contract I started at Portaldot Hacker House.  Live dApp (Mezo testnet): https://ajochain-frontend.vercel.app Code: https://github.com/blockchaincali/ajochain-mezo AjoManager: 0xD9f1Fb1D6f634696763A345890F32C50603B653A AjoBadge: 0x9a4720B2B3D607EE9c382Ec1369cb748236E535c  What's new for Mezo: 1. MUSD circles: contributions, pots and collateral in MUSD. MEZO circles also supported. 2. Earn while you save: when a circle fills, all members' collateral is deposited into Mezo's MUSD Stability Pool (provideToSP) for the whole cycle and earns BTC from liquidations. 3. Sha

## T2 wallets / bots / dashboards / misc

### 23. KEEL (W1)

- **Tagline:** Your BTC-backed dollar account in Telegram: borrow, stay protected, send and split MUSD.
- **Categories:** Payments, Lending, Consumer Finance
- **Links:** github `Im-2/keel` · demo `None` · https://app.akindo.io/communities/Mz9D4LkjLiMVqMGa/products/63Nw3DjBVHL10AaJd
- **Wave 1 result:** 18 USDT · scores (Integration/Product/Technical/UX/Materials) 8/8/8/6/2
- **Wave 1 judge review (verbatim):**

  > Keel already composes Mezo well: your Guardian contracts open, top up and repay real MUSD troves through BorrowerOperations on testnet. To reach the top integration level, get real third-party users running guardians and protections triggered by actual price moves, and make protect() do a partial rescue rather than revert when the reserve can't lift a trove above 110%. Verify the KeelGuardianFactory, KeelGuardian and KeelPay sources on the Mezo explorer, and give a firmer revenue model than a 1 MUSD/month premium and a keeper tip. Add a pitch deck, whose absence held Materials to 1, and a web link judges can open without Telegram.

### 28. LeekWallet DIY Hardware Wallet & Leek Stonks (W1)

- **Tagline:** Buy a stock-style index with Bitcoin-backed MUSD, signed on a hardware wallet you built yourself
- **Categories:** Stock Exchange, Hardware Wallet, DeFi
- **Links:** github `0xOucan/leek-stocks` · demo `None` · https://app.akindo.io/communities/La7Zl0O4aIvRgwdV/products/VwpAO1DM2HQOQl9oZ
- **Wave 1 result:** 17 USDT · scores (Integration/Product/Technical/UX/Materials) 8/6/8/7/2
- **Wave 1 judge review (verbatim):**

  > Your Mezo integration is real: troves open from the dapp, MEZO is staked, and the share/MUSD pairs sit on Mezo Pools. But the vault and staking contracts are plain ERC-20, so the index product itself would run unchanged on USDC. To move up in Wave 2, compose Mezo inside the protocol (accept sMEZO or the shares as collateral, route fees into Mezo Pools gauges or veMEZO), handle Recovery Mode, borrowing capacity and redemption risk in the borrow flow, and get users who aren't on the team. Note that the documented testnet MUSD 0x1189 is borrowable through the documented BorrowerOperations 0xCdF7 (its musd() returns 0x1189 and it mints it); your mintList check was against the scale-test BorrowerOperations, so consider settling in the documented pair. Add a pitch deck, because a missing deck caps Materials at 1.

### 64. Emberdeep (W1)

- **Tagline:** A pixel roguelike where skill wins a real weekly MUSD prize pool on Mezo. Pay with BTC or MEZO.
- **Categories:** Game, DeFi
- **Links:** github `Lazaniaaa/emberdeep-mezo` · demo `None` · https://app.akindo.io/communities/A8NgMpXqdSmzgZzz/products/rgMpdlZjQt7EgxOle
- **Wave 1 result:** 15 USDT · scores (Integration/Product/Technical/UX/Materials) 6/6/6/8/2
- **Wave 1 judge review (verbatim):**

  > Your deepest Mezo touchpoint is the EmberKeyRouter swapping BTC/MEZO into MUSD on Tigris, while the Ember Pot is still a port of your Arc USDC pool. To move up the integration ladder in Wave 2, make MUSD do protocol work: for example, put idle pot funds into a Mezo Pools liquidity or gauge position, or let players open or top up a trove through BorrowerOperations to fund their keys. Then show players other than the deployer wallet buying keys and a completed weekly distribute on-chain. Also verify the three contracts on the explorer, use server-issued seeds so the result doesn't rest on trusting the operator, and add a pitch deck, since a missing deck caps Materials at 1.

### 83. MezoVault IQ (W1)

- **Tagline:** MezoVault IQ combines accessible wallet-based payment workflows with transaction evidence
- **Categories:** Wallet payments, Defi Intelligence
- **Links:** github `daud9/mezovault-iq` · demo `None` · https://app.akindo.io/communities/La7pNA8p0s0J8dZx/products/A8NgqnLBLiMg9ox4r
- **Wave 1 result:** 12 USDT · scores (Integration/Product/Technical/UX/Materials) 6/4/6/6/2
- **Wave 1 judge review (verbatim):**

  > Your integration today is read-only: the loan and LP position cards read TroveManager and Mezo pools, but every write is a plain ERC-20 transfer, so the headline send and payment-link features would work the same with USDC. To move up the ladder in Wave 2, act on Mezo primitives from the app (for example top up collateral or repay through BorrowerOperations, deposit into the Stability Pool or add liquidity to Mezo Pools), use getCurrentICR and show MCR/Recovery Mode risk alongside it, and ship at least one of the promised vault or strategy flows with real on-chain transactions. Add a deck, a stated revenue model and a named target user, and align the landing page pitch with what the product actually does.

### 97. Qeep Wallet (W1+W2)

- **Tagline:** Qeep is a MUSD wallet on Mezo that keeps your savings safe from quantum computers.
- **Categories:** Wallet, Security, Payments
- **Links:** github `Akanimoh12/Qeep-Wallet` · demo `None` · https://app.akindo.io/communities/d8NjGZVlnHdrqg1P/products/VwpBGGNN9tRkoVBQ
- **Wave 1 result:** 11 USDT · scores (Integration/Product/Technical/UX/Materials) 4/4/6/5/2
- **Wave 1 judge review (verbatim):**

  > Qeep moves real testnet MUSD through its own smart accounts, which puts it at the transactional level, but the wallet would work the same with any ERC-20. To score higher on integration in Wave 2, use the Vault Key path to act on Mezo itself: read trove health or PriceFeed, and let users borrow, repay or deposit through BorrowerOperations, the Stability Pool or Mezo Pools from inside Qeep. Add a business model (who pays for the relayer's gas), verify the deployed contracts, and publish a watchable video of 2 minutes or less plus a deck, because your current video link gives no length and there is no deck.
- **Wave 2 update (team's text, first 700 chars):**

  > Wave 2 answers our Wave 1 feedback: deeper Mezo integration, a business model, verified contracts, a video under 2 minutes and a deck.  1. MEZO INTEGRATION: QEEP NOW ACTS ON MEZO ITSELF Qeep is no longer only a MUSD transfer wallet. Every Qeep smart account can now borrow and earn on Mezo, and every one of these actions is approved with the post-quantum Vault Key (a one-time Winternitz signature verified on-chain). Each action runs from the user's own Qeep account (msg.sender = the account), through the existing vaultExecute path, so no new contract was needed. - Borrow: lock BTC and mint MUSD through BorrowerOperations, then add BTC, borrow more, repay or close. - Live loan health: BTC pric

### 103. TAWFIK AAHMED ABDO MUSAED QERAN (W1)

- **Tagline:** Good
- **Categories:** dscvr.one/u/Tawfik123
- **Links:** github `None` · demo `https://github.com/ta77130` · https://app.akindo.io/communities/DrkMGExqRf232rrz/products/93kLWeoVlc8Zje2Z
- **Wave 1 result:** 0 USDT · scores (Integration/Product/Technical/UX/Materials) 0/0/0/0/0
- **Wave 1 judge review (verbatim):**

  > Duplicate submission: this entry duplicates another AKINDO entry from the same team ("TAWFIK AAHMED ABDO MUSAED QERAN"), which was reviewed and scored on its own card. This duplicate receives no grant and no points.

### 104. TAWFIK AAHMED ABDO MUSAED QERAN (W1)

- **Tagline:** ChatGPT: An intelligent assistant that writes text and analyzes data.  Google Gemini
- **Categories:** Yes
- **Links:** github `ta77130/TAWFIK-QERAN` · demo `None` · https://app.akindo.io/communities/DrkMGExqRf232rrz/products/rgM0NoXx9UJl84dN
- **Wave 1 result:** 0 USDT · scores (Integration/Product/Technical/UX/Materials) 0/0/0/0/0
- **Wave 1 judge review (verbatim):**

  > This submission failed the Valid submission gate (G0), and so also the chain (G1) and Mezo integration (G2) gates. The linked repo, TAWFIK-QERAN, is an empty 2022 stub with only a one-line README, the product name is a personal name, the overview is the blank template, the live link is your GitHub profile, and the video is an unrelated short film. For Wave 2, submit one entry with a real product name, a public repo holding code you committed during the build window, a live app deployed on Mezo, Ethereum, Base or BNB Chain that uses the canonical MUSD or MEZO addresses, and a demo video of under two minutes showing your product. Please submit once rather than several times from the same account.

### 106. MEZO-LOCK (W1)

- **Tagline:** -
- **Categories:** Other
- **Links:** github `None` · demo `None` · https://app.akindo.io/communities/aAN9REA8GuLzpplq/products/Mz9lmZKdATv326Rwj
- **Wave 1 result:** 0 USDT · scores (Integration/Product/Technical/UX/Materials) 0/0/0/0/0
- **Wave 1 judge review (verbatim):**

  > MEZO-LOCK couldn't be judged in Wave 1 because it failed gate G0 (valid submission). The GitHub repo NeoCrafts-cpu/MEZO-LOCK returns 404 (deleted or private), there's no live demo link, and the overview is the blank template. It also failed G2 (real integration), because nothing showed a link to canonical MUSD, MEZO or Mezo protocol contracts. For Wave 2, make the repo public with commits made during the build window, deploy to Mezo testnet or another supported chain with the real MUSD or MEZO addresses (Mezo testnet has both from the faucet), and submit a working live link, a filled-in overview and a demo video under two minutes.

### 107. MezoLens (W1)

- **Tagline:** See Deeper Into Bitcoin-Powered Finance.
- **Categories:** Blockchain Analytics, DeFi, Developer Tools
- **Links:** github `moduu6667/mezolens` · demo `None` · https://app.akindo.io/communities/NmRP1rZDxTr6vlWk/products/lrkGn0QNwS2OLBXK
- **Wave 1 result:** 0 USDT · scores (Integration/Product/Technical/UX/Materials) 0/0/0/0/0
- **Wave 1 judge review (verbatim):**

  > MezoLens scored 0 in Wave 1 because it failed three gates. The live link points back to the GitHub repo instead of a hosted app (G0). The code connects to no blockchain, so nothing runs on Mezo, Ethereum, Base or BNB Chain (G1). MUSD and MEZO appear only in page text, with no canonical token or Mezo contract address in the code (G2). For Wave 2, host the dashboard (GitHub Pages or Vercel is fine) and connect it to Mezo testnet (chain 31611) by reading real data from the canonical MUSD token or a Mezo contract such as TroveManager or PriceFeed. Also rename the stylesheet file in the repo: its filename accidentally contains the CSS text, so the page can't load its styles.

### 109. TAWFIK AAHMED ABDO MUSAED QERAN (W1)

- **Tagline:** ChatGPT: An intelligent assistant that writes text and analyzes data.  Google Gemini:
- **Categories:** Yes
- **Links:** github `None` · demo `https://github.com/ta77130` · https://app.akindo.io/communities/DrkMGExqRf232rrz/products/83No6MOwjC8ONdWE
- **Wave 1 result:** 0 USDT · scores (Integration/Product/Technical/UX/Materials) 0/0/0/0/0
- **Wave 1 judge review (verbatim):**

  > Duplicate submission: this entry duplicates another AKINDO entry from the same team ("TAWFIK AAHMED ABDO MUSAED QERAN"), which was reviewed and scored on its own card. This duplicate receives no grant and no points.

### 110. NovaLabs (W1)

- **Tagline:** Mezo
- **Categories:** Market
- **Links:** github `None` · demo `https://github.com/IbrahimKC001` · https://app.akindo.io/communities/BeN3EAVAzC0410Ao4/products/Nmgn9lA99Uj734Or
- **Wave 1 result:** 0 USDT · scores (Integration/Product/Technical/UX/Materials) 0/0/0/0/0
- **Wave 1 judge review (verbatim):**

  > Duplicate submission: this entry duplicates another AKINDO entry from the same team ("NovaLabs"), which was reviewed and scored on its own card. This duplicate receives no grant and no points.

### 111. NovaLabs (W1)

- **Tagline:** Mezo
- **Categories:** Market
- **Links:** github `IbrahimKC001/NovaMezo` · demo `None` · https://app.akindo.io/communities/BeN3EAVAzC0410Ao4/products/q3qMnEzxJFaOVZr2
- **Wave 1 result:** 0 USDT · scores (Integration/Product/Technical/UX/Materials) 0/0/0/0/0
- **Wave 1 judge review (verbatim):**

  > NovaLabs did not pass screening for Wave 1. The GitHub repo (IbrahimKC001/NovaMezo) contains only a one-line README, and the live demo link is the same YouTube video as the demo, so G0 (valid submission) failed. With no contracts, deployments or app config, there is nothing running on a supported chain (G1) and no use of canonical MUSD, MEZO or Mezo protocol contracts (G2). For Wave 2, push the actual frontend and contract code you describe to the public repo before the deadline, deploy it to a live URL on Mezo testnet or another supported chain, wire it to the canonical MUSD or MEZO addresses, and replace the personal bio with a description of the product.

### 113. NurseBridge (W1)

- **Tagline:** Accessible nursing exam preparation with optional MUSD-powered premium learning.
- **Categories:** Education, Payments, Access & Distribution
- **Links:** github `succinateworld-ux/nursebridge` · demo `None` · https://app.akindo.io/communities/GLzp029DrfW8JKaO/products/JBRWArBnoCWqPLaz6
- **Wave 1 result:** 0 USDT · scores (Integration/Product/Technical/UX/Materials) 2/4/4/6/2
- **Wave 1 judge review (verbatim):**

  > Your MUSD checkout is built but has never moved MUSD on-chain, so integration sits at the cosmetic level, which earns no payout. For Wave 2, complete and publish real MUSD payments on Mezo Testnet, setting the x402 asset to MUSD explicitly and checking that settlement works with MUSD's permit, since MUSD has no EIP-3009. To score higher, go beyond a swappable payment token, for example by funding student access grants from a Mezo-native source such as Stability Pool yield or by having sponsors pay through Mezo primitives. Also add a deck, name your track and team, and show the on-chain payment in the video.

### 117. Mezo Multi-Wallet MUSD/BTC Tool (W1)

- **Tagline:** A simple Node.js CLI tool that lets users manage and transfer MUSD and native BTC across wallets.
- **Categories:** Defi Tools, Market Infrastructure
- **Links:** github `None` · demo `None` · https://app.akindo.io/communities/BeNzagDR9i0vqzB0P/products/gXlnQdNqncB6Ezga
- **Wave 1 result:** 0 USDT · scores (Integration/Product/Technical/UX/Materials) 0/0/0/0/0
- **Wave 1 judge review (verbatim):**

  > Your tool scored 0 in Wave 1 because it failed the valid-submission gate (G0). The live link was a YouTube Short of your demo video, and the rules need a working product that a judge can reach. A local CLI with no hosted interface counts as localhost only. For Wave 2, ship something a judge can open: a small web front end, or a hosted Telegram bot as you planned. Also fix mezo.js:8, which your last commit pointed at the MEZO token (0x7B7c...0001) instead of testnet MUSD (0x1189...c503). Publish the tx hashes and wallet addresses for your testnet sends, add a deck, and keep the video under 2:15. To score on integration, build the trove health checks and Stability Pool actions from your roadmap on BorrowerOperations, TroveManager and PriceFeed.

### 124. Reflexa (W1)

- **Tagline:** An institutional-grade AI that reads market behavior, not just price
- **Categories:** finance
- **Links:** github `None` · demo `None` · https://app.akindo.io/communities/274wxG4rBHMK0oB1N/products/Mz6aqg0ODSvV71p3g
- **Wave 1 result:** 0 USDT · scores (Integration/Product/Technical/UX/Materials) 0/0/0/0/0
- **Wave 1 judge review (verbatim):**

  > Reflexa failed three entry gates, so it wasn't scored this wave. The GitHub repo realjioke/market-reflex-ai has no commits and no code, the overview is empty template headings, and the video link isn't a demo (G0). The live app is an off-chain ETF dashboard built for SoSoValue that names Arbitrum and Astar, not a supported chain (G1), and it doesn't use MUSD, MEZO or any Mezo protocol contract (G2). For Wave 2, push the real source to the public repo before the deadline, deploy on Mezo testnet (31611) or another supported chain, wire in the canonical MUSD or MEZO token or a Mezo protocol contract, and submit a filled-in overview with a demo video of 2 minutes or less.
