# 03 · What Actually Happens to Your Documents Before an AI Can Use Them

▶️ **Watch:** {EP3_LINK}

Between "upload" and the first answer, every file goes through four steps. If you never open them, you're trusting whatever comes back.

## What you'll learn

- **Preprocessing is the unpacking.** The tool pulls the plain text out of each file and throws away the packaging: headers, footers, page numbers, boilerplate.
- **Chunking chops the text** into pieces small enough to search. Where you cut decides what a piece knows: split ticket #4812 in two, and the agent note (full refund, approved by Dana Ruiz) never mentions Acme.
- **Embedding labels each piece** with a list of numbers that captures its meaning, so similar pieces land close together.
- **The index is the shelf** where every vector waits, so a question can be compared with all of them at once.
- **The cost:** change the cleaning, the chunk size or the embedding model later, and every file is prepped again. Decide before you upload two hundred PDFs, not after.

## Reproduce it

Create a new knowledge base and upload the three **PDFs** from [`datasets/03-what-happens-to-your-documents/`](../../datasets/03-what-happens-to-your-documents/). This is dataset **v3**: the same content as v2, but delivered as PDFs with a running header and footer on every page (13 pages).

**1. Upload and process.** Upload `01_support_tickets.pdf`, `02_customer_contracts.pdf` and `03_refund_policy.pdf`. When processing is done, note the number of chunks and the processing time.

**2. Look for the packaging.** Open the tickets file. Compare the raw page with the cleaned text around ticket **#4815**: its customer message is on page 1 and its agent note on page 2. In the raw text, the page-1 footer and the page-2 header sit between them:

```
BL-SUP-2026-09 · Printed 28 Sep 2026        Page 1 of 8
Brightline Supply Co. · Support Desk Export · 14–25 Sep 2026        CONFIDENTIAL
```

After preprocessing they should be gone. Then open the file's chunks and check their sizes.

**3. Test it.** Search for *"What is the delivery time in Acme's contract?"* The top chunk should be contract C-12 (48 hours from dispatch confirmation), with a similarity score. Write that score down: it's your number to match.

Settings used in the video: [`config.md`](config.md).

## What you should see

| Step | If preprocessing worked | If it didn't |
|---|---|---|
| Ticket #4815 | Customer message, then agent note, nothing in between | "Page 1 of 8 · CONFIDENTIAL · Support Desk Export" inside the chunk |
| Chunks | Text only | The same header and footer in chunk after chunk, so they look more alike to the search |
| Test question | C-12, 48 hours, at the top | Usually still C-12, but with packaging in the chunk and a different score |

Your chunk count, time and score will differ with your settings. What matters: open one chunk and check that the packaging is gone.

Then run the preprocessing checks P1–P4 in [`questions.md`](../../datasets/03-what-happens-to-your-documents/questions.md).

## One thing to watch

Many PDF parsers drop repeated headers and footers on their own, and some don't. You only find out by opening a chunk. Where a chunk boundary falls depends on chunk size, overlap and method; the #4812 split in the video is an illustration. An embedding has a few hundred to a few thousand numbers depending on the model; the 2D picture in the video is a projection.

**Previous:** [02 · Knowledge Graph vs Regular RAG](../02-knowledge-graph-vs-regular-rag/)
**Next:** 04 · How Does a Document Become a Graph? (coming soon)
