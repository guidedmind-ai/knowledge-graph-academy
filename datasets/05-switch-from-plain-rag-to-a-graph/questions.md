# Test questions · dataset 05 (four trips)

Upload the four trip files (`01_trip_rome.md` … `04_trip_new_york.md`) and the 25 photo PDFs. Ask each question twice: once with plain RAG (graph extraction off) and once with the graph on. Mark each answer ✓ or ✗ against the expected answer.

| # | Question | Expected answer | Where the answer is | Type |
|---|---|---|---|---|
| Q1 | Where did we stay in Paris? | Hotel Lune, 14 Rue Cler | `02_trip_paris.md` | one place |
| Q2 | What did I eat at Da Nino? | Cacio e pepe | `photos/IMG_2231.pdf` | one place |
| Q3 | Show me every photo from the Rome trip. | 13 photos: IMG_2201, IMG_2203, IMG_2207, IMG_2209, IMG_2211, IMG_2214, IMG_2219, IMG_2224, IMG_2231, IMG_2236, IMG_2240, IMG_2244, IMG_2248 | 13 photo backs, each says "City: Rome. Country: Italy." and a date from 12–16 April 2025 | needs the links (more photos than top K) |
| Q4 | Who was with me at dinner on the day I saw the Colosseum? | Marco Bianchi and Giulia Rossi (Trattoria da Nino, 14 April 2025) | `IMG_2214` (Colosseum, 14 April 2025) → same date → `IMG_2231` (Da Nino, with Marco Bianchi and Giulia Rossi) | needs the links |

**How the links work:** each back is written in short sentences that name the photo, the date, the place, the city and country, the people and the hotel. Extraction turns these into nodes and edges: photo → city → country, photo → date, photo → place, photo → people, photo → hotel. The trip file names the same city, country, dates, people and hotel, so the graph ties the photos to their trip. The trip files never list their photos, so "every photo" has to be collected across 13 separate chunks.

**Why plain RAG struggles:** Q3 has 13 correct photos, more than plain RAG returns (top K), and Rome-sounding look-alikes from other trips ("like an old Roman temple", "like an old Roman triumphal arch") compete for those slots. Q4 is never answered in one chunk.
