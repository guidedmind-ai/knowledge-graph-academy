# Knowledge Graph Academy

Short video tutorials on knowledge graphs for AI agents, with everything you need to reproduce each episode yourself.

Every episode uses **the same small dataset**, so you can follow along from episode 1 onward, build the same graph, and compare your results with ours. The dataset is small enough to fit a free tier.

▶️ **Playlist:** {PLAYLIST_LINK}

---

## How to use this repo

1. Download or clone the repo.
2. Upload the three files in [`dataset/`](dataset/) to the tool you're following along with. In the videos we use [GuidedMind.ai](https://guidedmind.ai).
3. Open the folder for the episode you're watching in [`episodes/`](episodes/). Each folder has what the episode covers, the steps to reproduce it, and what you should see.
4. Use [`questions.md`](questions.md) to test your graph. Each question has an expected answer and the number of hops it needs.

## Episodes

| # | Episode | Type | Folder |
|---|---|---|---|
| 1 | What Is a Knowledge Graph? | Concept | [`01-what-is-a-knowledge-graph`](episodes/01-what-is-a-knowledge-graph/) |
| 2 | Knowledge Graph vs Regular RAG | Concept | coming soon |
| 3 | What Actually Happens to Your Documents Before an AI Can Use Them | Practical | coming soon |
| 4 | How Does a Document Become a Graph? | Concept | coming soon |
| 5 | What Changes When You Switch From Plain RAG to a Graph? | Practical | coming soon |
| 6 | What Is Entity Resolution and Why Does It Break Your Graph? | Concept | coming soon |
| 7 | How Do You Know if Your Retrieval Is Any Good? | Practical | coming soon |
| 8 | What Are Graph Communities? | Concept | coming soon |
| 9 | How Does Graph Search Work? | Concept | coming soon |
| 10 | Why Did Your Agent Answer That? Tracing What It Retrieved | Practical | coming soon |

## The dataset

A fictional supplier, **Brightline Supply Co.**, and four customers: Acme, Northpeak, Orbis Foods and Veltra.

| File | What's inside |
|---|---|
| [`01_support_tickets.md`](dataset/01_support_tickets.md) | 6 support tickets: late deliveries, damaged goods, billing, account changes |
| [`02_customer_contracts.md`](dataset/02_customer_contracts.md) | 3 customer contracts with delivery SLAs and remedies, plus one customer with no contract |
| [`03_refund_policy.md`](dataset/03_refund_policy.md) | The refund policy the contracts point to (sections 1–6) |

The three files are connected on purpose. Some answers need more than one hop: for example, to decide whether Acme is owed a refund for ticket #4812 you have to go ticket → Acme → contract C-12 → refund policy section 3. That's the kind of question a knowledge graph is built for.

Some episodes add extra files, for example duplicate company spellings for the entity resolution episode. Those files live in the episode's own folder, so the core dataset never changes.

## Repo layout

```
knowledge-graph-academy/
├── dataset/          # the 3 core documents, shared by every episode
├── questions.md      # the shared test set
└── episodes/
    └── NN-episode-name/
        ├── README.md # what the episode covers, steps, expected result
        └── config.md # the settings used on screen
```

## License

Dataset and tutorials: [CC BY 4.0](LICENSE). Reuse them freely, with attribution.
