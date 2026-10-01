# Test questions — Knowledge Graph Academy dataset

Use these to check what your graph, or plain RAG, can answer. "Hops" counts the links you need to walk. The reference graph in [`graph/relationships.csv`](graph/relationships.csv) contains every link used here.

## Core questions

| # | Question | Expected answer | Hops | Path |
|---|---|---|---|---|
| 1 | What is the delivery SLA in Acme's contract? | 48 hours from dispatch confirmation | 1 | Acme → C-12 |
| 2 | Which customers have open late-delivery tickets? | Acme (#4812) and Northpeak (#4834) | 1 | Ticket → Customer |
| 3 | Is Acme owed a refund for ticket #4812? | Yes. Order 7731 arrived 5 days after the 48-hour SLA, so Refund Policy §3 applies: full refund of $3,840, approved by Dana Ruiz | 3 | #4812 → Acme → C-12 → §3 |
| 4 | Is Veltra owed a refund for ticket #4823? | No. Veltra has no contract, so standard terms apply (§5): no late-delivery refund | 2 | #4823 → Veltra → §5 |
| 5 | Is Northpeak owed a refund for ticket #4834? | Yes. 124 hours exceeds the 72-hour SLA in C-15, so §3 applies: $7,960 | 3 | #4834 → Northpeak → C-15 → §3 |
| 6 | What did Orbis Foods get for its late order 7766? | Credit note CN-044 for $1,188 (20%), not a refund; C-19 replaces §3 | 3 | Order 7766 → #4837 → C-19 → CN-044 |
| 7 | Which account manager handles the customer behind ticket #4812? | Dana Ruiz | 2 | #4812 → Acme → Dana Ruiz |
| 8 | Which customers does Dana Ruiz manage? | Acme and Orbis Foods | 1 | Dana Ruiz → customers |
| 9 | How many tickets has Acme opened? | Five: #4812, #4819, #4840, #4847, #4852 | 1 | Acme → tickets |
| 10 | What did Northpeak get for the crushed pallet in order 7740? | A replacement: order 7749 with 40 cases of BX-100 (§4.1) | 2 | #4815 → §4.1 → Order 7749 |

## Deeper questions (multi-hop)

| # | Question | Expected answer | Hops | Path |
|---|---|---|---|---|
| 11 | Who must approve the refund for ticket #4834, and why? | Sam Okafor and Lena Brandt: $7,960 is over the $5,000 limit in §6.2 | 3 | #4834 → Order 7761 → §6.2 → Lena Brandt |
| 12 | Which customers have two claims against the same carrier? | Northpeak (NorthLine Logistics: CL-121, CL-124) and Halden Health (ColdLink: CL-126, CL-127) | 3 | Customer → Ticket → Claim → Carrier |
| 13 | Order 7766 got a credit note, so why was the leaking GP-5 claim on the same order declined? | GP-5 is cold-chain, so §4.2 needs a report within 48 hours; #4849 came 5 days after delivery | 3 | #4849 → Order 7766 → GP-5 → §4.2 |
| 14 | Can Veltra get money back for anything, even without a contract? | Late delivery: no (§5). Damaged goods: yes, §5 keeps §4 — #4841 refunded $96 for 4 water-damaged cases, approved by Lena Brandt because Veltra has no account manager | 3 | Veltra → §5 → §4.1 → #4841 |
| 15 | Northpeak asked for a refund for misprinted boxes. What did it get? | Replacement order 7779 only. BX-100-CP is custom-printed, so §4.3 rules out a refund | 3 | #4843 → Order 7763 → BX-100-CP → §4.3 |
| 16 | Which tickets does Tom Becker own, and how many led to money actually paid? | #4812, #4834, #4845, #4847. One paid (#4845, refund RF-3107); #4812 and #4834 await approval; #4847 was declined (§6.1) | 2 | Tom Becker → tickets → outcomes |
| 17 | Is Acme's leaking pallet jack covered, and by what? | Yes, by the 12-month warranty (§7): repair, no refund. Pallet jacks were added to C-12 by Amendment A1, and order 7718 was delivered on 9 July 2026 | 4 | #4840 → Order 7718 → A1 → C-12 → §7 |
| 18 | Which warehouse made a picking error, and who manages it? | The Newark warehouse (#4850, missing SR-4 bolt kits), managed by Mei Tan | 2 | #4850 → Newark warehouse → Mei Tan |
| 19 | Why do Acme's new LR-9 rolls jam? | Acme's LB-9 printers (order 7702) run firmware 2.0; LR-9 needs 2.1 or later | 3 | #4852 → LR-9 → LB-9 → Order 7702 |
| 20 | Whose customers opened the most tickets: Dana Ruiz's or Sam Okafor's? | Dana Ruiz: 8 (Acme 5, Orbis Foods 3). Sam Okafor: 6 (Northpeak 4, Halden Health 2) | 3 | Account manager → customers → tickets |
| 21 | Who signed the contract behind ticket #4845? | Paul Grant (Halden Health) and Marcus Hale (Brightline) | 2 | #4845 → C-21 → signatories |
| 22 | Which Acme refund request was declined, and under which rule? | #4847: late order 7690, but filed 45 days after delivery; §6.1 allows 30 | 2 | Acme → #4847 → §6.1 |
