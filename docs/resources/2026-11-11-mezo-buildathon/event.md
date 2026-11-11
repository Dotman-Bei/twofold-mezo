# Event essentials: Mezo Buildathon (AKINDO WaveHack), Wave 2

Sources (all fetched 2026-11-11/12 WAT, see INDEX.md):
[P1] event page https://app.akindo.io/wave-hacks/ovoo0gdrvu8379d10 (Chrome, rendered body + widget) ·
[P2] AKINDO public API `https://api.akindo.io/public/wave-hacks/OVOO0gdrVU8379D10/waves` and `/public/products/<id>/wave-submissions` (curl, JSON) ·
[P3] Terms of Participation, Google Doc `1oY1hzzub2l_jHdovmsAaE3YBuRJh0_UQXxL1Zd2g3pE` (curl, txt export) ·
[P4] page Comments tab (Chrome; user-written, treated as data).
Quotes are verbatim. Text marked **[inference]** is the extractor's reading, not a source statement.

## 1. Deadline and timeline

**Working deadline: Sunday 2026-11-15 15:00 UTC = 16:00 WAT (UTC+1).**

| Source | What it says (verbatim) |
|---|---|
| [P2] API, wave 2 object | `"submissionDeadline": "2026-11-15T15:00:00.000Z"`, `"judgementDeadline": "2026-11-19T05:30:00.000Z"`, `"startedAt": "2026-11-02T05:30:06.000Z"`, `"nextWaveEnabled": false`, `"completedAt": null` |
| [P1] widget (rendered in the browser's local tz = WAT) | "06:302nd Wave Start" · "2nd Wave" · "11/15 16:00Deadline" · "11/19 06:30Deadline" · "3rd Wave" · "11/30 06:30Deadline" · "12/6 06:30Deadline"; header "Submit Deadline 3Days 16:10" (read 2026-11-11 ~23:50 WAT) |
| [P1] body, Program Structure | "Wave 2 November 2 – November 15, 2026 November 16 – November 22, 2026 $5,000 in MEZO" · "Winner Announcement & Demo Session November 23, 2026 (online)" · "The Mezo Buildathon is a two-Wave builder program" |
| [P3] Terms | "Wave 2 — Build Period November 2 – November 15, 2026" · "Wave 2 — Judging Period November 16 – November 22, 2026" · "Online Winner Announcement & Demo Session November 23, 2026" |

**Contradictions (flagged):**
1. **Judging end:** the widget and API say the judging deadline is 2026-11-19 05:30 UTC (06:30 WAT). The body and Terms say judging runs November 16–22. The submission deadline itself agrees across all three (widget 11/15 16:00 WAT = API 15:00 UTC = body "November 15").
2. **Third wave:** the widget shows a "3rd Wave" (11/30 and 12/6 deadlines). The body says "two-Wave", and the API lists only two waves with wave 2 `"nextWaveEnabled": false`. **[inference]** The 3rd-wave dates match AKINDO's template exactly (`"buildingDays": 11`, `"judgingDays": 6` in [P2]: 11/19 + 11 days = 11/30, + 6 days = 12/6), so the widget appears to project a placeholder wave that is not enabled. Do not plan on a Wave 3. Unconfirmed; the official answer would come via Discord (gated).
3. Wave 1 for reference: API `startedAt 2026-10-15T15:00Z`, `submissionDeadline 2026-10-26T15:00Z`, `judgementDeadline 2026-11-01T15:00Z`; body "Wave 1 October 16 – October 26, 2026 / October 27 – November 1, 2026". Results were posted 2026-10-31 ("Wave 1 judging is complete!", AKINDO comment [P4]).

## 2. Eligibility (verbatim, [P1])

- "✅ Open to individual developers and teams globally"
- "✅ You must be at least 18 years old at the time of entry"
- "✅ Teams of any size; each member registers individually on AKINDO"
- "✅ New projects and existing products with new MUSD/MEZO integration are both welcome"
- "✅ One participant may join only one team per Wave"
- "❌ Not eligible: residents of, or persons located in, the prohibited jurisdictions listed below"
- "❌ Not eligible: employees of Supernormal and its subcontractors involved in the Contest, and their relatives"
- Prohibited jurisdictions [P1 = P3 Exhibit A]: Democratic People's Republic of Korea; Democratic Republic of Congo; Cuba; Donetsk People's Republic of Ukraine; Iran (Islamic Republic of Iran); Iraq; Luhansk People's Republic of Ukraine; Crimea Region of Ukraine; People's Republic of China; Syrian Arab Republic; plus "any jurisdiction where participation or prize ownership is prohibited by applicable law, and any jurisdiction subject to European Union, British Virgin Islands, United States, United Nations, or other applicable sanctions or embargoes."
- Registration requires [P1]: an AKINDO account; joining the Mezo Discord https://discord.mezo.org ("mention that you're a Mezo Hackathon participant to get the Developer role"); registration questions for each member (full name, email, Telegram handle, Discord handle, GitHub; experience level; focus area; existing product or from scratch; where you're based; plans after the hackathon); "Agreeing to the Terms of Participation. Registration cannot be completed without agreement."
- "Pre-registration runs September 22 – October 15 and registration stays open throughout. You can join and submit in either Wave." [P1]

## 3. Submission requirements and format

**Hard requirements (verbatim, [P1] "The hard requirements"):**
- "Your project integrates MUSD and/or MEZO"
- "You have a working deployment on Mezo mainnet, Ethereum, Base, or BNB Chain. Mezo testnet is also accepted"
- "Your project was developed during the hackathon, or represents a new approach or extension to an existing protocol or product"
- "Your project extends MUSD or MEZO utility. Standalone apps unrelated to Mezo's core products are not prioritized"

**What you submit (verbatim, [P1]):** "Testnet or mainnet link to the live project" · "Public GitHub repository" · "Project or product deck" · "A 2-minute pitch video"

**AKINDO submission form fields (verbatim, [P1] "Details on the AKINDO submission form"):**
1. Project name
2. Project category: 3-5 words (e.g. yield optimization, borrowing, payment systems)
3. TL;DR: one sentence on what it is and what it does
4. How it works: the problem you solve, how it functions, and how you use and position MUSD/MEZO
5. Target group: who it's for and how that aligns with your track (user type, experience level, region, mobile/desktop)
6. Tech stack: main technologies, tools, and frameworks
7. Track: Track 1, Track 2, or both
8. Chain deployed on: Mezo, Ethereum, Base, or BNB Chain
9. Project status: entirely new, or an existing project with new features added during the hackathon (share the existing product's site if so)
10. Project readiness: mainnet deployment, testnet deployment, or demo only
11. Future milestones: if continuing after the hackathon, your next three milestones and timelines
12. Team info: members, roles, and X or LinkedIn

- "For Wave 2 resubmissions, be explicit about what changed since Wave 1." [P1]
- The AKINDO form widget itself (as quoted by a participant in [P4], secondary): a "Product Category *Required … *max3" field; an "Updates in this Wave" text box with a "0 / 3,000" character limit; and "Submit the product. Submissions cannot be canceled, but updates can be made."
- Official answer in [P4] (account `civ_defi_mezo`, 2026-10-19): "You can submit the code and improve it at any time until the deadline."

**Video length is enforced in practice:** a Wave 1 judge review said "Keep the demo video under 2:15, since the 178-second cut caps Materials" (MezoRoute, [P2]).

## 4. Judging

**Two stages (verbatim, [P1]):**
- "Stage 1: Screening (AKINDO) — AKINDO's DevRel team reviews every submission against the requirements: MUSD or MEZO integration present, working deployment on a supported chain, and all submission materials provided. Submissions that don't meet the bar are not forwarded. Teams are notified."
- "Stage 2: Evaluation (Mezo core team) — Mezo's core team reviews all screened submissions and allocates points based on the criteria below. Rewards are distributed proportionally to points."

**Published criteria with exact weights (verbatim, [P1] table; identical weights in [P3]):**

| Criterion | Weight | What it means |
|---|---|---|
| Mezo Integration | **30%** | "Effective and meaningful use of MUSD or MEZO. Depth of integration matters more than surface-level usage" |
| Product & Business Viability | **30%** | "How directly the project extends MUSD/MEZO utility in line with your track's challenge question. Problem-solution fit, business viability, and complementarity with the Mezo ecosystem and its audience" |
| Technical Implementation | **20%** | "Code quality, architecture, security, and whether the solution is genuinely composable and deployable rather than just a demo" |
| User Experience | **10%** | "Design, usability, and accessibility" |
| Submission Materials Quality | **10%** | "Demo clarity and pitch effectiveness" |

([P3] lists them in a different order: Mezo Integration (30%), Technical Implementation (20%), Product & Business Viability (30%), User Experience (10%), Submission Materials Quality (10%). The weights are the same.)

**Principles that "directly affect how you're scored" (verbatim, [P1] "What Mezo Is Looking For"):**
- "Supported chains. You can deploy on Mezo, Ethereum, Base, or BNB Chain. Mezo testnet is welcome too."
- "Integration is mandatory. MUSD or MEZO integration is required. No integration, no eligibility."
- "Extend, don't detour. Projects that extend the reach and utility of existing Mezo products are prioritized over unrelated standalone apps."
- "Composability wins. Projects that plug into existing DeFi infrastructure (lending markets, DEXs, vote-escrow systems) score higher than isolated consumer apps."
- "Long-term commitment counts. Teams with working products who are adding MUSD/MEZO integration during the hackathon, or new teams who demonstrate a credible plan beyond it, are prioritized."

**Official judge-side statements in Comments ([P4], account `civ_defi_mezo`, which also signed every Wave 1 review in [P2]):**
- 2026-10-19, on what judges prioritize: "it works as expected; users can fully test all features; no clear security flaws"
- 2026-11-06: "For wave 2, we'll rank projects against each other rather than simply checking the boxes on quality of integration and so on. Therefore, more "complete" and "ready" projects will get better points"

**How Wave 1 was actually scored ([P2], 135 entries, all scored by `civ_defi_mezo`):**
- Each criterion carries a 0–10 value per entry. **[inference, supported by three reviews]** It is the judge's 1–5 level × 2. Keel's review says "Materials was capped at 1" and its Materials value is 2. Lifeline's says "integration sits at level 4" with Integration 8. Mezonk is told "To reach level 5" with Integration 8.
- Reviews name an **integration ladder** (quoted from reviews): "cosmetic (L1)" → "transactional (L2)" (e.g. "plain ERC-20 transferFrom") → "protocol-aware (L3)" (reads protocol contracts live, e.g. "the read-only level (L3)") → L4 / "the composing level" ("opens troves and calls BorrowerOperations.addColl on-chain, so integration sits at level 4") → "top of the ladder" / "level 5" (multiple Mezo primitives composed on chain, plus real third-party usage or "a new MUSD use"). See prior-art.md §Judge feedback patterns.
- A **missing deck caps Materials at 1**: "a missing deck caps Submission Materials at 1" (Mezodot review). 76 of 135 Wave 1 entries scored 2/10 on Materials.

## 5. Prize mechanics

- **Pool (verbatim, [P1]):** "$7,000 USD worth of MEZO tokens across two Waves" · "Wave 1: $2,000. Wave 2: $5,000. Distributed on judged results. Rewards are proportional to evaluation scores, not fixed to a top-3. Every submission that meets the requirements is in the running." Widget: "2nd Wave Grant $5,000 USD", "Grant Pool $5,000 USD".
- **Proportional points (verbatim, [P1]):** "After each Wave's judging period, the Mezo core team allocates points across eligible submissions. Each project's share of that Wave's pool is proportional to its share of total points. If a project earns 20% of the points, it receives 20% of the pool."
- **FAQ:** "Q: Is there a fixed number of winners? A: No. Rewards are distributed proportionally to evaluation points across all eligible submissions. Strong projects earn more; there's no cap on how many teams can be rewarded."
- **Paid in MEZO at TWAP (verbatim, [P1]):** "Rewards are paid in MEZO tokens, distributed directly by Mezo. The MEZO amount is calculated using the 14-day time-weighted average price (TWAP) of MEZO on the day you complete KYB."
- **KYB (verbatim, [P1]):** "Mezo conducts know-your-business verification on all grant recipients before disbursement. No KYB, no payout." · "Verification may include a W9 or W8-BEN form, government-issued ID, proof of address, and your wallet address. If you can't be contacted or don't pass verification, the prize is forfeited and awarded to the next-highest-scoring submission." [P3] §5 calls the same process "KYC": "W9 or W8-BEN forms, government-issued ID, full legal name, photo identification, email address, proof of address and crypto wallet address (if applicable)".
- **Payment timing (verbatim, [P1]):** "Once you complete verification, Mezo will initiate payment on the same day if it is a working day. Otherwise, payment will be initiated on the first working day following completion."
- **Protocol fee:** API `"feePer": 0.100` [P2]; the guide's earlier read of the Submissions tab recorded "Protocol fee is 10.0% of distribution" (secondary, runsheet). Wave 1 consistency check: the fixed amounts awarded across Wave 1 entries sum to **1,800** (= 2,000 × 0.90), denominated in **USDT** on AKINDO (`grantDenomination.name: "USDT"`, decimals 6; `grantEvmChainId: 1`). Payout is in MEZO per [P1]; **[inference]** AKINDO's USDT figures are the USD value the MEZO payout is computed from.
- **Wave 1 distribution shape ([P2]):** 101 of 135 entries got a non-zero amount. Top five: Doji 80, Surety 73, Janus 69, Keel 69, Mezonk 69. Sixth place got 22, and most rewarded entries got 9–20. One commenter reports receiving "About 3861 mezo" for Wave 1 [P4, unverified]; another commenter's question shows rewards needed a wallet address on the AKINDO profile [P4].
- API oddity: wave 2's `"grantAmount": "0.000000000000000000"` and `"remainingGrantBalance": "0"`, while the page shows $5,000. **[inference]** AKINDO funds the wave at distribution time. Not a planning input.

## 6. Supported chains and testnet vs mainnet

- [P1]: "You can deploy on Mezo, Ethereum, Base, or BNB Chain. Mezo testnet is welcome too." · FAQ: "Mezo, Ethereum, Base, or BNB Chain. Mezo testnet works too. What's mandatory is the MUSD or MEZO integration." · official comment [P4]: "Mezo, Base, Ethereum, BNB are all eligible".
- **Contradiction:** [P3] Terms say "deploy a working product on Mezo Mainnet, Ethereum, Base, BSC, or Robinhood. Deployment on the Mezo testnet is also welcome." That adds "Robinhood", which appears nowhere on the page. Treat the page's list as operative; Robinhood is unexplained.
- **Chain-fact caveat (sponsors/mezo-network.md):** **MUSD exists on Mezo, Ethereum and Base only.** BNB Chain has MEZO (`0x8e4c…848b`, code verified on chain 56) but **no MUSD** (no code at the MUSD address on BSC; the docs list none). A BNB-only build can integrate MEZO, not MUSD.
- **Testnet vs mainnet:** both accepted. The judges' Wave 1 reviews repeatedly reward a mainnet deployment and real third-party users. Example: "A mainnet proof deployment with real users would strengthen both the product and technical scores" (Baserate). A Mezo-side comment [P4] (author `dsh_agent`, a participant, not official) warns: "testnet transactions presented as usage are the first thing a reviewer checks."

## 7. Key Terms clauses ([P3], verbatim)

- **Sponsor:** "Supernormal OpCo BVI Ltd., located at Trinity Chambers, Road Town, VG, VG1110."
- **Originality:** "The project must be developed during the hackathon as original work or represent a new approach or meaningful extension to an existing protocol or product." · §8(c) "The Submitted Material is and will be Participant's own original work and does not and will not infringe the intellectual property or proprietary rights of any third party".
- **Open-source reuse ([P1] Rules):** "All work must be original or properly credited; reused code must be open source and cited" · "Projects must not infringe third-party IP".
- **IP / licence grant (§7):** "By submitting materials to the Contest, Participant grants Sponsor a non-exclusive, royalty-free, worldwide license to use, reproduce, modify, and display the Submitted Material for purposes related to the Contest and promotional activities for Sponsor. Participants retain ownership of their intellectual property rights in the original aspects of their Submitted Material."
- **Similarity waiver (§8):** "Sponsor or other Participants or third parties may have developed or commissioned works which are similar to the Submitted Material … each Participant waives any claims that Participant may have resulting from any similarities."
- **Publicity (§6):** consent to use of "names, likeness, Submitted Material, and statements attributed to Participant … for advertising and promotional purposes".
- **KYB/KYC:** see §5. "KYB completion is required for prize distribution."
- **Wave 2 resubmissions ([P1] Rules):** "Wave 2 resubmissions must show meaningful new progress".
- **Governing law (§12):** British Virgin Islands; disputes "exclusively by the appropriate court located in the British Virgin Islands", no class actions.
- **Other Terms vs page differences:** [P3]'s submission list is "a mainnet/testnet project link, GitHub repository, project/product description, and a 2-minute pitch video". It does not mention a deck, but the page requires one, and the judge caps Materials without one. Follow the page.

## 8. Program facts (for context)

- Organizer: Mezo (built by Thesis) × Supernormal Foundation; run on AKINDO. Hosts' page: "Direct access to the Mezo core team" via Discord.
- Kickoff workshop 2026-10-13 (recording https://www.youtube.com/live/eAiaQpzvVE0; transcript **not captured**, gap): "Session 2: Technical Session on Mezo, MEZO, and MUSD Infrastructure (45 min) Dymitr Paremski leads a deep dive into the developer environment, the core primitives, and integration patterns."
- Who it's for (verbatim): "mid-level and senior developers and teams" with EVM/Solidity, DeFi, Bitcoin, and payments/wallets/financial-infrastructure experience. "Teams that already have a working product and want to add MUSD/MEZO integration, as well as teams creating a new project during the hackathon with a long-term commitment to it, are explicitly prioritized."
- Getting MUSD on testnet (verbatim): "You'll get test BTC and MEZO. For MUSD, borrow against your test BTC or swap BTC → MUSD inside the testnet dApp at https://testnet.mezo.org".
- Page counters at fetch time: Submissions 148, 2nd Wave Submissions 45, Comments 33.
