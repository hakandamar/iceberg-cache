# IceCache

**IceCache** is an open-source, distributed smart caching layer for Apache Iceberg, built to accelerate data retrieval in large-scale data lake environments.

---

## 🚀 Overview
Apache Iceberg is designed for reliable and large-scale data lake storage. However, its snapshot-based architecture and metadata layout can lead to performance bottlenecks, especially with high-frequency data updates and large numbers of small files.

IceCache solves this by integrating deeply with Apache Spark to provide:
- Snapshot-aware smart caching
- Intelligent cache invalidation
- Distributed caching backend support
- Significant reduction in metadata and query planning latency

---

## 🎯 Key Features
- ✅ **Snapshot-Aware Caching:** Automatically tracks Iceberg table snapshots and invalidates outdated cache entries.
- ⚡ **Accelerated Metadata Access:** Caches frequently accessed metadata and manifest information.
- 🧠 **Smart Invalidation:** Only invalidates changed partitions/files using Iceberg snapshot diff.
- 🔁 **Spark Integrated API:** Drop-in replacement for `.cache()` with Iceberg-specific optimizations.
- 🧱 **Pluggable Cache Backends:** Redis support out-of-the-box. RocksDB and others coming soon.
- 📊 **Observability:** Built-in metrics exporter for Prometheus/Grafana.

---

## 💡 Why IceCache?

Apache Iceberg performance can degrade due to:
- Large number of manifest files
- Small file explosion
- Frequent updates generating many snapshots

IceCache introduces an intelligent layer that reduces metadata access time and accelerates query execution by minimizing redundant file scans and planning overhead.

---

## 📦 Architecture Modules
- `snapshot-tracker` – Monitors Iceberg metadata and triggers cache events
- `smart-invalidator` – Performs selective invalidation
- `spark-integration` – Provides PySpark/Scala API
- `cache-backend` – Manages cache logic (initially Redis-based)
- `metrics-server` – Exposes cache stats for observability

---

## 🛠️ MVP Scope
- Redis backend with file-level caching
- Snapshot polling tracker
- PySpark-friendly API
- Smart invalidation logic
- CLI to inspect cache state

---

## 🧪 Planned Enhancements
- Listener-based live snapshot tracking
- Time-travel aware versioned caching
- Adaptive TTL and cost-based eviction
- Integration with Trino and Flink

---

## 📥 Installation & Usage
_**(Coming soon)**_

```bash
pip install icecache
```

```python
from icecache import IceCache

# Read data
df = spark.read.format("iceberg").load("catalog.db.table")

# Cache using IceCache
IceCache.cache(df, "catalog.db.table")
```

---

## 📜 License
Apache License 2.0

---

## 🤝 Contributing
We welcome contributions from the community! Feel free to open issues, suggest features, or submit PRs.

- Join discussions in GitHub Projects & Discussions tab
- Help us test across compute engines
- Share feedback and optimization ideas

---

Let’s make Apache Iceberg faster and smarter together. 🔥

