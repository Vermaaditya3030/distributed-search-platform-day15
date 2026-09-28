# Architecture

1. Ingest Service receives write requests.
2. Search Service owns the document data and query API.
3. PostgreSQL stores documents.
4. Docker Compose provides repeatable local infrastructure.
5. A production version can add Kafka for asynchronous indexing and OpenSearch for inverted-index search.
