# Runsheet — Mezo Buildathon (AKINDO WaveHack), Track 1: DeFi

_Guide seat: claude-sonnet-5-5 · tier standard · effort high (model id stated by the session at boot; effort set by the user per the kickoff, user-attested). Created 2026-11-11 23:36 WAT. All times WAT = UTC+1 (the user's local tz)._

## Event
- **Name / URL:** Mezo Buildathon — "Build with MUSD and MEZO: $7,000 USD in MEZO Grants" — https://app.akindo.io/wave-hacks/ovoo0gdrvu8379d10 (tabs: Overview · Judges ("No judges yet") · Submissions (148) · Comments (33)). Organizer: Mezo (Thesis) × Supernormal Foundation; run on AKINDO. Discord https://discord.mezo.org (required for support).
- **WAVE CORRECTION (guide finding, 2026-11-11 23:35):** the kickoff said "Wave 1". **Wave 1 is closed** (build Oct 16–26, judging to Nov 1, results posted Oct 31). **The live wave is Wave 2** (Nov 2 – Nov 15, $5,000 pool). Anyone can still join and submit in Wave 2 ("registration stays open throughout"; "new teams are welcome"). This campaign targets **Wave 2**. User to correct if they meant something else.
- **Deadline:** **Sun 2026-11-15 16:00 WAT (= 15:00 UTC).** Derived from the page's live countdown (3d 16:25 left at 23:35 WAT Nov 11) and matches the timeline widget ("11/15 16:00 Deadline") and the body ("Wave 2: November 2 – November 15"). Judging per body Nov 16–22 (the widget shows 11/19 06:30 — inconsistent, non-blocking); online winner announcement + demo session Nov 23. The widget also lists a "3rd Wave" (deadline 11/30, to 12/6) and two Wave-2 entries mention Wave 3, while the body says two Waves — unconfirmed, ask in Discord; not a planning input.
- **Prizes:** program $7,000 in MEZO ($2,000 W1 / $5,000 W2). **Not a top-3:** each eligible project's share of the wave pool = its share of total points the Mezo core team allocates. Paid in MEZO at the 14-day TWAP on the day KYB completes; **KYB required** before payout (W9/W8-BEN, ID, proof of address, wallet). The Submissions tab shows "Protocol fee is 10.0% of distribution." **Payouts look heavily skewed:** the seven Wave-1 projects visible on page 1 show "Previous Wave Amount" of 12–18 USDT; a commenter reports a Wave-1 reward of about 3,861 MEZO. "Winning" = landing at the top of the points distribution.
- **Judging (weights as published):** Mezo Integration **30%** (depth beats surface use) · Product & Business Viability **30%** (extends MUSD/MEZO utility per the track's challenge question; problem-solution fit; business viability; fit with the Mezo audience) · Technical Implementation **20%** (code quality, architecture, security, composable and deployable, not just a demo) · User Experience **10%** · Submission Materials Quality **10%** (demo clarity, pitch). Two stages: AKINDO DevRel screening (MUSD/MEZO integration present, working deployment on a supported chain, all materials) → Mezo core-team scoring. Extra principles: integration mandatory · "extend, don't detour" · composability wins (lending markets, DEXs, vote-escrow) · long-term commitment counts.
- **Judge signals seen in comments (official Mezo-side account, treat as informative):** Oct 19 — judges prioritize "it works as expected; users can fully test all features; no clear security flaws"; Nov 6 — Wave 2 projects are **ranked against each other**, "more complete and ready projects will get better points".
- **Tracks:** Track 1 DeFi (Borrowing, Lending, Looping, Yield) — "How might we expand MUSD and MEZO utility as collateral and productive capital across DeFi?"; examples: lending protocols taking MUSD/MEZO as collateral (single or cross-chain), looping strategies, yield vaults / auto-compounders, MUSD/MEZO pools and DEX integrations on other chains, staking derivatives. Track 2 Access & Distribution (bots, discovery, marketplaces/aggregators, wallets/interfaces). The form's track field is multiple choice (can tick both).
- **Chains:** Mezo (testnet chain 31611 accepted), Ethereum, Base, BNB Chain. Testnet: dApp https://testnet.mezo.org · explorer https://explorer.test.mezo.org · RPC https://rpc.test.mezo.org · faucet https://faucet.test.mezo.org (test BTC + MEZO; MUSD by borrowing against test BTC or swapping in the dApp). Docs https://mezo.org/docs/developers/ · GitHub https://github.com/mezo-org/.
- **Hard requirements:** MUSD and/or MEZO integration · working deployment (Mezo testnet OK) · developed during the event or a new extension of an existing product · extends MUSD/MEZO utility.
- **What to submit (AKINDO form):** live testnet/mainnet link · **public GitHub repo** · **project/product deck** · **2-minute pitch video** · project name · category (3–5 words) · TL;DR (one sentence) · how it works (problem, function, how MUSD/MEZO is used and positioned) · target group · tech stack · track(s) · chain · status (new vs existing + site) · readiness (mainnet / testnet / demo only) · **future milestones (next three, with timelines)** · team info (members, roles, X/LinkedIn). Submissions cannot be cancelled but **can be updated until the deadline** → file an early submission once a live testnet build exists, then update.
- **Eligibility / registration (human gates):** AKINDO account · join the Mezo Discord and ask for the Developer role · registration questions (name, email, Telegram, Discord, GitHub, experience, focus, product status, location, plans after) · agree to the Terms of Participation · 18+ · one team per Wave · not resident of a prohibited jurisdiction (DPRK, DRC, Cuba, Donetsk/Luhansk/Crimea, Iran, Iraq, PRC, Syria, plus sanctions-driven exclusions) — **user to check own residence**. User's Chrome showed a logged-in AKINDO session; registration for this event NOT verified.
- **Competition read (guide, light, 1 of 5 pages of Wave-2 entries; 45 entries in W2, 135 in W1):** established iterating teams in Track 1: Morbit (borrow MUSD + earn, one-click loops 1.5×/2×/2.5×, auto-compound, MEZO rewards, Telegram liquidation alerts, 43 tests) · Bulwark (loan rescue before liquidation, Stability-Pool-earning reserve, keeper, 22 fork tests, first outside user) · Liqvera (arm/protect keeper + paid risk reports) · CreditGraph (credit/lending vault) · MUSD Reach (cross-chain savings, empty update) · skim (MUSD ⇄ USDC bridge, Mezo + Base mainnet). Track 2: PayLink, MUSD Pay Links, mPocket, MUSD Pocket, MezoGig. **Crowded lanes:** loan-protection/keeper/alerts, borrow+earn dashboards, savings goals, payment links. **What the W1→W2 update texts show judges asked for:** real (not cosmetic) integration, productive reserves, explorer-verified contracts, outside users with checkable txs, a revenue model, a deck, fork/security tests. _Source of truth is the Step 0a pack's prior-art.md; this is strategy-only._
- **Third-party claims to VERIFY (from a competitor's comment, unverified — extractor must confirm against docs/chain):** minimum loan 1,800 MUSD + 200 MUSD gas deposit (≈2,000 MUSD opening debt) · MUSD uses 18 decimals on testnet · the docs' Savings Vault address has no code on chain 31611 · collateral is BTC only (MUSD is debt, not collateral) · Stability Pool withdrawals pause while any trove is under 110%.

## Project repo
- **`Dotman-Bei/mezo-buildathon-2026`** — **private**, pipeline-created by the guide 2026-11-11 23:36 WAT per `references/repo-bootstrap.md`. Local clone: `C:\Users\bamig\Documents\VIBE CODE\Hackathons\mezo-buildathon-2026` (sibling of the kit, not inside it). Commits so far: `a592e01` README stub + .gitignore · `c17e23f` docs/design/frontend.md (verified: local HEAD = `origin/main` = `c17e23f`). idea-forge / architect may rename it to the project slug; record every rename here and in every kickoff's `REPO:`.
- Kit checkout: `C:\Users\bamig\Documents\VIBE CODE\Hackathons\build-system` (origin `bitnormie01/build-system`), at origin/main `230bbc8`, 0 behind, verified 2026-11-11 23:3x WAT. (Prompts say `~/hackathons/build-system`; the real path is the Hackathons workspace folder.)
- Git note: the default credential helper can stall; use `git -c credential.helper= -c "credential.helper=!gh auth git-credential" <cmd>`. The workspace path has a space ("VIBE CODE"): quote every path; if a Node tool shells out unquoted, build from a no-space clone (as in the last campaign).

## Tollgate
- Report: **not yet created** — Step 0a's Stage 0 creates `docs/tollgate/<date>-tollgate.md` (0a is in the plan, so the guide does not run the campaign tollgate itself).
- Guide pre-checks 2026-11-11 23:3x WAT (informational, not a report): row 1 git 2.54.0 + identity PASS · row 2 `gh` logged in as Dotman-Bei PASS (scopes repo, workflow, read:org, gist) · row 3 kit at origin/main PASS · row 4 repo created PASS · row 5 claude-in-chrome responded **in this session** (session-scoped; 0a re-probes) · row 9 Node v22.23.4 / npm 10.9.9 PASS. Rows 6–8, 10–13, 15–18 not probed (0a Stage 0 owns them).
- **Verdicts:** pending Stage 0. No step BLOCKED on the pre-checks.

## Goal / skills
- **Goal (user):** win the sponsor's track — Track 1 DeFi. **Guide reframing:** there is no per-track winner; scoring is a points share across all eligible Wave-2 entries (both tracks), so "win" operationalizes as *score at the top of the Wave-2 distribution with a Track-1 product*.
- **Skills (user-confirmed 2026-11-11 ~23:50 WAT):** Solidity/EVM/DeFi, TypeScript/React/Node, Python/ML.

## Strategy decisions
| Decision | Choice | Reason |
|---|---|---|
| Mode | guided | user approves each baton; ~88 h clock; real wallets/funds even on testnet |
| 0a extractor | **RUN, time-boxed ≤60 min**, deep on Mezo | the build lives on Mezo's contract surface and the docs carry live gotchas; the Submissions tab (148 entries + judge-response texts) is the best intel on what is saturated and what judges ask for |
| 0 idea-forge | **RUN**, Track 1 only, `safe-feasible` (user decides) | no idea yet. Rubric is 80% integration depth + viability + engineering, judges rank on completeness/readiness, ~88 h runway, Liquity-style trove semantics are unfamiliar. The kit's safe-feasible vs novel-wow knob only moves ±5 pts and never lifts novelty above buildability, so this is low-regret; the white-space check against the pack's prior-art still applies |
| 1 architect | RUN, budget ≤2.5 h, **a deck task and a pitch-script task are required in the plans** | the public repo, deck and 2-min video are hard submission items; the pipeline's demo-studio makes the video, not the deck |
| 2 orchestrator | RUN; review mode decided at Step 2 boot — lean `autonomous` (testnet only, time-boxed, user sleeping), Solidity/security tasks pinned `top` | |
| 2.5 demo-studio | RUN if ≥8 h remain after green, else the user records | the 2-minute pitch video is mandatory; "Submission Materials Quality" is 10% |
| 3 gate-concierge | **both passes** | preflight right after Step 1 (test wallet, faucet BTC/MEZO, MUSD via borrow or swap, AKINDO/Discord/terms registration, Vercel/host); closing (public-repo flip, deploy, **early submission then update**, final submission). Registration, Discord, Terms acceptance, repo-public flip and Submit are consent-gated |
| Track shortlist | (1) **Track 1 DeFi — primary**; (2) Track 2 — tick as a second track only if the finished product honestly answers the Access & Distribution question too (a real interface/bot surface) | only two tracks exist; viability (30%) is judged against the chosen track's challenge question, so a forced double-tick dilutes it |
| Sponsor depth (0a) | **deep:** Mezo — MUSD (BorrowerOperations/troves, min debt, interest, redemption, Stability Pool, PriceFeed/oracles, HintHelpers), Savings Vault (sMUSD) / Mezo Earn, Mezo Pools (router, pools), MEZO + vote-escrow/boost, tBTC, example contracts and the `mezo-org` repos, testnet + mainnet addresses, MUSD/MEZO on Ethereum/Base/BNB (bridge/token addresses), AKINDO Submissions tab (all W1+W2 entries) · **shallow:** AKINDO mechanics, Supernormal, Discord/Telegram (gated → gap, do not join) | Mezo is the whole event |
| Calendar fit | **fits only as a vertical slice** — final call after the brief exists | see Calendar |

## Calendar (WAT) — internal, not the event's
- Now Nov 11 23:36 → deadline Nov 15 16:00 = **~88 h**; internal submit-by **Nov 15 10:00** = ~82 h.
- **Tonight (Nov 11–12):** 0a ≤60 min → guide review → idea-forge (≤60 min) → guide calendar-fit call. Then rest; the architect is a long one-question-at-a-time dialogue and needs fresh attention.
- **Nov 12 ~09:00–11:30:** architect (≤2.5 h) → guide review → **~11:45 Step 3 preflight** → orchestrator starts ~12:00.
- **Tripwire — Nov 12 end of day:** our own contract/flow completes a real transaction on Mezo testnet (tx hash). If not, stop and escalate.
- **Nov 13:** build; first public testnet deploy; **early AKINDO submission (user consent), then update**.
- **Nov 14:** feature freeze ~12:00; green by ~18:00; demo-studio + deck 18:00–23:00; README.
- **Nov 15:** final submission **by 10:00**; 10:00–16:00 buffer only.

## Frontend constraint (carry into the architect kickoff)
- `docs/design/frontend.md` (the design-taste-frontend skill's SKILL.md, committed `c17e23f`). Architect kickoff **DOCS** must list it; **CONSTRAINTS** must include verbatim: *"All UI follows docs/design/frontend.md. Every frontend task's code applies its tokens, type, layout and components, and its task block cites the file."*
- Caveats: the skill is a marketing-site skill; for a DeFi dApp the architect applies tokens/type/layout to the app and keeps scene/shader moments to a landing page, if any. Its SKILL.md points at sibling files (`layout-v4.md`, `sections.md`, `assets/`) that are NOT in the repo; the kit folder is 38 MB with no licence file → keep it outside the repo, referenced in place (`claude --add-dir`), copy only what is used and list third-party assets in `docs/gates/submission-draft.md` before the public flip.

## Step status
| Step | Status | Artifact / verification | Seat settings it ran at |
|---|---|---|---|
| 0a | **pending — kickoff handed over 2026-11-11** | `docs/resources/<date>-mezo-buildathon/` + `docs/tollgate/<date>-tollgate.md` | opus · high (user to attest) |
| 0 | pending | `docs/idea-forge/*-brief.md` | top · max |
| 1 | pending | spec + plans + `manifest.json` + `docs/gates/submission-draft.md` | top · xhigh |
| 3 preflight | pending (after Step 1) | `docs/gates/*-gate-ledger.md` | standard · high |
| 2 | pending | built, gated, committed tasks | top · high |
| 2.5 | pending | `docs/demo/*-demo-script.md` + video | standard · high |
| 3 closing | pending | submission confirmed on AKINDO | top · high |

## Next action
- **User pastes the Step 0a (resource-extractor) kickoff** in a fresh session set to `opus` + effort `high`; when it finishes, come back here and the guide verifies the pack and the tollgate report before green-lighting Step 0.

## Open blockers / decisions
- **B1 — RESOLVED (user, 2026-11-11 ~23:50 WAT):** target is **Wave 2**.
- **B2 — RESOLVED, user-attested:** "I am registered" for this buildathon (AKINDO account, Discord, registration questions, Terms). The guide did not independently verify it; Step 3 preflight re-checks the Discord Developer role and the Submit button state.
- **B3 — RESOLVED, user-attested:** "I'm eligible" (jurisdiction check). **KYB readiness not separately confirmed:** payout after Nov 23 needs W9/W8-BEN, ID, proof of address and a wallet — user to prepare early (not a build blocker).
- **B4:** widget-vs-body judging-date mismatch and the unconfirmed Wave 3 — ask in Discord; not a planning input.
- **B5:** tollgate rows 6–8, 10–13, 15–18 unknown until Stage 0.
