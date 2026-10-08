# Test questions · dataset 04 (the knock at the door)

Ask these after uploading the four files. Each answer needs pieces from more than one document; the path is the string you should be able to follow in your graph.

| # | Question | Expected answer | Hops | Path through the graph | Documents needed |
|---|---|---|---|---|---|
| 1 | **Where did Tom hide the key?** | In Grandpa's secret drawer, under the window seat in Tom's room (the blue bedroom) | 3 | key → HIDDEN_IN → Grandpa's secret drawer → UNDER → window seat → IN → Tom's room | diary, floor plan |
| 2 | **Who knocked on Tom's door?** | Mr Bell, the new postman, bringing Tom's birthday parcel from Grandma Rose | 3 | man in a blue cap → WEARS → blue cap ← WEARS ← Mr Bell → BRINGS → birthday parcel | diary, letter |
| 3 | Why did the postman need Tom to open the door? | The parcel needed a signature: Mr Bell had to see him in person | 2 | Mr Bell → BRINGS → birthday parcel → DELIVERED_TO → No. 12 Lark Lane (signature needed) | letter, map |
| 4 | On which day does Mr Bell deliver to Lark Lane, and who was home? | Saturday; Tom and Biscuit (Mother was at the market) | 2 | Mr Bell → DELIVERS_ON → Saturday ← AT_MARKET_ON ← Margaret Hale | map, diary |
| 5 | Who sent the parcel, and where does she live? | Grandma Rose, Seaview Cottage, Brighton | 2 | birthday parcel ← SENT ← Grandma Rose → LIVES_AT → Seaview Cottage | letter |
| 6 | Which door does the key open? | The front door of No. 12 Lark Lane | 2 | key → OPENS → front door → PART_OF → No. 12 Lark Lane | diary, floor plan |

**Watch-out:** the map writes "No. 12 Lark Lane", the floor plan "12 Lark Ln". If your graph keeps two address nodes, the postman's round no longer reaches Tom's room. Count the links on No. 12 Lark Lane (reference: 8). Fixing it is entity resolution, episode 6.
