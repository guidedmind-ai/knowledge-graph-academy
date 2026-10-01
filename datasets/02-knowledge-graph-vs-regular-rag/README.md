# Dataset v2 · used from episode 02

The dataset shown in [02 · Knowledge Graph vs Regular RAG](../../episodes/02-knowledge-graph-vs-regular-rag/). Same company and story as [v1](../01-what-is-a-knowledge-graph/), with more tickets, people and links, so multi-hop questions have something to walk.

A fictional supplier, **Brightline Supply Co.**, and five customers: Acme, Northpeak, Orbis Foods, Halden Health and Veltra.

| File | What's inside |
|---|---|
| [`01_support_tickets.md`](01_support_tickets.md) | 16 support tickets, each linked to who reported it, who owns it, the order, products, warehouse, carrier, contract and the policy sections applied |
| [`02_customer_contracts.md`](02_customer_contracts.md) | 4 customer contracts and 1 amendment with signatories, account managers, SLAs, covered products and carriers, plus the product catalog |
| [`03_refund_policy.md`](03_refund_policy.md) | The refund policy: late delivery, damage (general, cold-chain, custom-printed), standard terms, deadlines and approvals, warranty, carrier claims |
| [`graph/`](graph/) | The reference graph: 110 entities and 364 relationships a good extraction should find, plus a picture of it |
| [`questions.md`](questions.md) | 22 test questions with expected answers, hop counts and paths |

![Reference graph](graph/graph_preview.png)

## What changed from v1

- Tickets: 6 → 16. Every ticket now names the reporter, the owner, the order, products, warehouse and carrier.
- New customer: Halden Health (contract C-21). New contract amendment: C-12 A1.
- People: account managers (Dana Ruiz, Sam Okafor), support agents, billing, warehouse managers, customer contacts.
- Refund policy: sections 4.1–4.3, 6.1–6.2, 7 (equipment warranty) and 8 (carrier claims).
- The episode 01 example works the same way in v2 (ticket #4812 → Acme → contract C-12 → policy section 3). Some ticket statuses and details differ, so use v1's questions with v1 and v2's with v2.
