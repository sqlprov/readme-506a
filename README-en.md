SQL Query API (506a)

**What it is:** A fucking SQL gateway that accepts any SQL query and returns results in JSON. The database is SQLite-compatible, running on goddamn powerful servers. You pay once for lifetime access, not for hardware.
Endpoint
`POST https://506a.sqlprov.workers.dev`
**Headers:**  
- `x-key: private_key` (required, nothing will come without it).
**Request body:**  
Raw SQL query (string). Example: `"SELECT * FROM users WHERE id = 1"`
**Response:**  
- On success: JSON array of objects (query result).  
- On error (invalid SQL, connection issues, etc.): `[]` (empty array) or just empty body. Fuck it, you'll figure it out.
Two curl examples
```bash
curl -X POST https://506a.sqlprov.workers.dev -H "x-key:w_8p9ZhxSbT_b5F_2-JF61dYQp9BL1Rz" -d "SELECT name FROM users LIMIT 5"
```
```bash
curl -X POST https://506a.sqlprov.workers.dev/w_8p9ZhxSbT_b5F_2-JF61dYQp9BL1Rz -d "SELECT name FROM users LIMIT 5"
```
What is supported
- **SELECT**, **INSERT**, **UPDATE**, **DELETE**, **CREATE TABLE**, **ALTER TABLE**, **DROP TABLE**.
- Transactions (`BEGIN`, `COMMIT`, `ROLLBACK`).
- Standard aggregate functions (`COUNT`, `SUM`, `AVG`, etc.).
- JOIN, subqueries, UNION.
- Triggers not tested, may not work.
Not working
- `VACUUM`, `ATTACH DATABASE`, `REINDEX`.
- Full‑text search FTS5 - no.
- Foreign keys - may not be enforced, but usually work.
Limits and quotas
- **Max request size:** 5 MB.
- **Max execution time:** 10 seconds (if the query lags - no response).
- **Requests per day:** 100,000.
- **Database size:** 5 GB (enough for any of your crap).
How to get the key
Write to me (`@TheUser2026`) in private, we discuss the price. The key is issued for life, you can do anything with it. The database is yours alone.
Important shit (must read)
1. Do not hammer heavy queries with large tables - the server isn't rubber.
2. If you want to store binary data, use `BLOB` and base64 on the client.
3. The database is not automatically backed up. If you accidentally lose your data - I'm not your nanny.
4. The access key is your password. Don't show it to anyone, otherwise your database will be trashed.
**Other questions ---> Telegram `@TheUser2026`.**
