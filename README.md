# IceCache: Distributed Smart Caching Layer for Apache Iceberg
IceCache is an open-source, distributed caching layer designed for Apache Iceberg data lakes. It integrates tightly with Apache Spark and is aware of Iceberg's snapshot-based architecture to enable high-performance and intelligent cache invalidation.

📦 Core Modules

1. Snapshot Tracker

* Monitors Iceberg table metadata.
* Detects snapshot changes using snapshot ID, manifest list and metadata files.
* Emits change events for downstream modules.

2. Smart Invalidator

* Uses snapshot diffs to determine which partitions or data files have changed.
* Invalidates only the affected cache entries.
* Supports file-level and partition-level granularity.

3. Spark Integration Layer

Offers a user-friendly API for PySpark and Scala:
```python
from icecache import IceCache
df = spark.read.format("iceberg").load("my_table")
IceCache.cache(df, "my_table")
```

Internally hooks into Spark’s logical plan and leverages caching APIs with smart layer.

4. Cache Backend Abstraction

* Pluggable backend architecture.
* Initial support: Redis.
* Future support: RocksDB, Apache Ignite, in-memory tiered caching.

5. Metrics & Monitoring

* Collects cache metrics (hit/miss rate, eviction stats, etc.).
* Exposes Prometheus-compatible endpoint.
* Optional integration with Grafana dashboards.

🚀 MVP Scope

* Redis backend with basic file-level caching.
* Iceberg snapshot monitoring (polling-based).
* PySpark integration with smart cache API.
* Invalidation mechanism for appended or deleted data files.
* Basic CLI tool to inspect cache entries.

🛠️ Future Enhancements

* Listener-based snapshot tracking via Iceberg APIs.
* Adaptive TTL based on access frequency.
* Cost-based cache eviction strategy.
* Query plan caching for sub-second response times.
* Time-travel aware multi-version caching.
* Integration with Flink and Trino.

-------------------------------------------------------------------------------------------

Let's build IceCache to make Iceberg blazing fast and smart! 🚀
