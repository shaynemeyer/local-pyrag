# SQL Queries

```sql
-- find how many chunks we have
select count(*) from chunks;
```

```sql
--look at an embedding
select embedding from chunks limit 1;
```

```sql
-- Cosine similarity higher = more similar (1 = identical direction)
WITH q AS
  (SELECT embedding
   FROM chunks
   WHERE chunk_index = 0
   LIMIT 1)
SELECT c.chunk_index,
        LEFT(c.content, 80),
        c.embedding <=> q.embedding AS dist
FROM chunks c, q
ORDER BY c.embedding <=> q.embedding
LIMIT 5;
```

`<=>` is the cosine distance operator provided by the pgvector extension. It returns a value between 0 and 2, where 0 means identical vectors and 2 means opposite. Used in ORDER BY to find the nearest embeddings:

```sql
SELECT content FROM chunks
ORDER BY embedding <=> '[0.1, 0.2, ...]'::vector
LIMIT 5;
```

The other pgvector distance operators are `<->` (L2/Euclidean) and `<#>` (negative inner product).
