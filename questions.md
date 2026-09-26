# Test questions — Knowledge Graph Academy dataset

Use these to check what your graph (or plain RAG) can answer. "Hops" counts the links you need to walk.

| # | Question | Expected answer | Hops | Path |
|---|---|---|---|---|
| 1 | What is the delivery SLA in Acme's contract? | 48 hours from dispatch confirmation | 1 | Acme → C-12 |
| 2 | Which customers have open late-delivery tickets? | Acme (#4812), Veltra (#4823), Northpeak (#4834) | 1 | Ticket → Customer |
| 3 | Is Acme owed a refund for ticket #4812? | Yes. Order 7731 arrived 5 days after the 48-hour SLA, so Refund Policy §3 applies: full refund of the order value | 3 | #4812 → Acme → C-12 → Policy §3 |
| 4 | Is Veltra owed a refund for ticket #4823? | No. Veltra has no contract, so standard terms apply (Policy §5): no late-delivery refund | 2 | #4823 → Veltra → Policy §5 |
| 5 | Is Northpeak owed a refund for ticket #4834? | Yes. 5 days exceeds the 72-hour SLA in C-15, so Policy §3 applies | 3 | #4834 → Northpeak → C-15 → Policy §3 |
| 6 | If an Orbis Foods order arrives late, what does Orbis Foods get? | A 20% credit note, not a refund; C-19 replaces Policy §3 for Orbis Foods | 2 | Orbis Foods → C-19 (overrides Policy §3) |
| 7 | Which account manager handles the customer behind ticket #4812? | Dana Ruiz | 2 | #4812 → Acme → C-12 |
| 8 | Which customers does Dana Ruiz manage? | Acme and Orbis Foods | 1 | Dana Ruiz → C-12, C-19 |
| 9 | How many tickets has Acme opened? | Two: #4812 and #4819 | 1 | Acme → tickets |
| 10 | What does Northpeak get for the crushed pallet in order 7740? | A replacement or refund for the damaged items (Policy §4); Northpeak asked for a replacement | 2 | #4815 → Northpeak → C-15 → Policy §4 |
