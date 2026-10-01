# Knowledge Graph Academy

Short video tutorials on knowledge graphs for AI agents, with everything you need to reproduce each episode yourself.

Every episode has **its own dataset folder**, so you always download exactly the files shown in the video. All datasets tell the same story (a fictional supplier, Brightline Supply Co., and its customers) and are small enough to fit a free tier.

▶️ **Playlist:** {PLAYLIST_LINK}

---

## How to use this repo

1. Download or clone the repo.
2. Open the episode you're watching in [`episodes/`](episodes/): what it covers, the steps to reproduce it, and what you should see.
3. Upload the files from the matching folder in [`datasets/`](datasets/) to the tool you're following along with. In the videos we use [GuidedMind.ai](https://guidedmind.ai).
4. Test your graph with that dataset's `questions.md`. Each question has an expected answer and the number of hops it needs.

## Episodes

| # | Episode | Type | Episode folder | Dataset |
|---|---|---|---|---|
| 1 | What Is a Knowledge Graph? | Concept | [`01-what-is-a-knowledge-graph`](episodes/01-what-is-a-knowledge-graph/) | [v1](datasets/01-what-is-a-knowledge-graph/) |
| 2 | Knowledge Graph vs Regular RAG | Concept | [`02-knowledge-graph-vs-regular-rag`](episodes/02-knowledge-graph-vs-regular-rag/) | [v2](datasets/02-knowledge-graph-vs-regular-rag/) |
| 3 | What Actually Happens to Your Documents Before an AI Can Use Them | Practical | coming soon | |
| 4 | How Does a Document Become a Graph? | Concept | coming soon | |
| 5 | What Changes When You Switch From Plain RAG to a Graph? | Practical | coming soon | |
| 6 | What Is Entity Resolution and Why Does It Break Your Graph? | Concept | coming soon | |
| 7 | How Do You Know if Your Retrieval Is Any Good? | Practical | coming soon | |
| 8 | What Are Graph Communities? | Concept | coming soon | |
| 9 | How Does Graph Search Work? | Concept | coming soon | |
| 10 | Why Did Your Agent Answer That? Tracing What It Retrieved | Practical | coming soon | |

## The datasets

| Version | Used in | Size | What's new |
|---|---|---|---|
| [v1](datasets/01-what-is-a-knowledge-graph/) | Episode 1 | 6 tickets, 3 contracts, refund policy §1–6 | The starting point: one customer (Acme), one contract, one policy chain |
| [v2](datasets/02-knowledge-graph-vs-regular-rag/) | Episode 2 onward | 16 tickets, 4 contracts + 1 amendment, refund policy §1–8, reference graph (110 entities, 364 relationships) | People, orders, products, carriers and approvals on every ticket, so multi-hop questions have something to walk |

The files are connected on purpose. Most answers need more than one hop: to decide whether Acme is owed a refund for ticket #4812 you go ticket → Acme → contract C-12 → refund policy section 3. That's the kind of question a knowledge graph is built for.

![Reference graph, dataset v2](datasets/02-knowledge-graph-vs-regular-rag/graph/graph_preview.png)

## Repo layout

```
knowledge-graph-academy/
├── episodes/
│   └── NN-episode-name/
│       ├── README.md      # what the episode covers, steps, expected result
│       └── config.md      # the settings used on screen
└── datasets/
    └── NN-episode-name/   # exactly the files used in episode NN
        ├── README.md      # version, contents, what changed
        ├── 01_support_tickets.md
        ├── 02_customer_contracts.md
        ├── 03_refund_policy.md
        ├── questions.md   # test questions for this dataset
        └── graph/         # reference graph (from v2)
```

Each episode gets its own dataset folder, even when the data hasn't changed from the episode before, so you never have to work out which version a video used.

## License

Dataset and tutorials: [CC BY 4.0](LICENSE). Reuse them freely, with attribution.
