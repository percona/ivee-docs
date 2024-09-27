# Ivee for PostgreSQL and AI

## pgvector

In the rapidly evolving world of AI, the ability to efficiently store, manage, and query vector embeddings has become paramount. 
[pgvector](https://github.com/pgvector/pgvector) extension steps in to address this need, seamlessly extending the capabilities of PostgreSQL 
to handle these high-dimensional mathematical representations that underpin many modern AI applications. 

From powering semantic search engines that understand the meaning behind queries to enabling recommendation systems that anticipate user preferences, 
`pgvector`'s applications span a wide spectrum. 

With Ivee for PostgreSQL you can easily enable `pgvector` extension and unlock a new level of AI-driven functionality within your database.

* Connect to your database:

   ```bash
   psql -U your_username -h ivee_pg_host -p ivee_pg_port
   ```

You define the username at the cluster creation time. The host and the port can be obtained from *Connectivity* tab in [Ivee portal](https://app.ivee.cloud).

* Enable pgvector extension:

```
CREATE EXTENSION vector;
```

Your database is ready for vector data.

## Verify and test

You can quickly validate if pgvector works as expected by running the following commands:

* Create a simple table

```
CREATE TABLE items (
    id BIGSERIAL PRIMARY KEY,
    embedding vector(3) 
);
```

* Insert some sample embeddings:

```
INSERT INTO items (embedding) VALUES 
    ('[1.2, 3.4, 5.6]'),
    ('[0.1, 0.9, 2.3]'),
    ('[4.5, 6.7, 8.9]');
```

* Find the nearest neighbor to a query embedding:
```
SELECT * FROM items 
ORDER BY embedding <-> '[1.0, 3.0, 6.0]' 
LIMIT 1;
```

This query uses the `<->` operator to calculate the Euclidean distance between vectors.
