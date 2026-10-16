# Dataset 05 · four trips

The dataset shown in [05 · What Changes When You Switch From Plain RAG to a Graph?](../../episodes/05-switch-from-plain-rag-to-a-graph/). Emma's photos from four trips and the trip notes that go with them.

| Folder / file | What's inside |
|---|---|
| `01_trip_rome.md` … `04_trip_new_york.md` | One trip each: city, country, travellers, hotel, itinerary by date, bookings. They don't list the photos |
| `photos/` | 25 photo prints as PDFs. Page 1 is the picture (if there is one), the last page is the handwritten back: photo id, date and time, place, city and country, who was there, hotel, caption. 12 prints are back-only (no picture) |
| [`questions.md`](questions.md) | 4 test questions with expected answers: 2 answered in one place, 2 that need the links |

**Why it's built this way:** each photo is its own file, so each becomes its own chunk, and the backs and trip files use exactly the same names for cities, countries, dates, places, people and hotels. A graph turns those into shared nodes and collects a whole trip by following them; plain RAG only returns the top K chunks closest to the question.

All people, bookings and confirmation numbers are fictional.
