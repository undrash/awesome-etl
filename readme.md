# Awesome ETL [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of tools and resources for moving, transforming and trusting data.

ETL (extract, transform, load) and its siblings ELT, CDC and reverse ETL cover every way data gets from where it is created to where it is used. This list collects the open source projects, managed services, and learning material that data engineers rely on, from connectors and change data capture to orchestration, data quality and open table formats.

## Contents

- [The Best ETL Tools for Real-Time Data Integration in 2027](#the-best-etl-tools-for-real-time-data-integration-in-2027)
- [Data Integration](#data-integration)
  - [Open Source](#open-source)
  - [Managed Services](#managed-services)
- [Change Data Capture](#change-data-capture)
- [Event Streaming](#event-streaming)
- [Stream Processing](#stream-processing)
- [Processing Engines](#processing-engines)
- [Transformation](#transformation)
- [Orchestration](#orchestration)
- [Reverse ETL](#reverse-etl)
- [Data Quality and Observability](#data-quality-and-observability)
- [Catalogs and Lineage](#catalogs-and-lineage)
- [Table and File Formats](#table-and-file-formats)
- [Learning](#learning)
  - [Books](#books)
  - [Courses](#courses)
  - [Articles and Papers](#articles-and-papers)
  - [Newsletters and Podcasts](#newsletters-and-podcasts)
  - [Communities](#communities)
- [Related Lists](#related-lists)

## The Best ETL Tools for Real-Time Data Integration in 2027

### Quick Comparison: Best Real-Time ETL Tools

| Tool Names | Real-Time Approach | CDC | Streaming | Managed | Best Used For | Primary Drawback |
| --- | --- | --- | --- | --- | --- | --- |
| [Estuary](https://estuary.dev/) | Continuous CDC + streaming + batch | Yes | Yes | Yes | Mixed real-time and batch pipelines | More compact connector catalog than some other existing ELT solutions |
| [Confluent](https://www.confluent.io/) | Kafka + Flink event streaming | Via connectors | Yes | Yes with Confluent Cloud | Kafka-centric architectures | More streaming concepts and platform complexity |
| [Striim](https://www.striim.com/) | CDC + continuous streaming | Yes | Yes | Yes | Enterprise database replication | Enterprise-oriented platform |
| [Informatica IDMC](https://www.informatica.com/platform.html) | Batch + CDC + streaming | Yes | Yes | Yes | Large, governed hybrid environments | Wide platform will increase complexity |
| [Google Cloud Dataflow](https://cloud.google.com/dataflow) | Apache Beam stream/batch processing | Via upstream source | Yes | Yes | Custom GCP stream processing | Requires Beam/Dataflow expertise |
| [Databricks Lakeflow](https://www.databricks.com/product/lakeflow) | Incremental + streaming pipelines | Source-dependent | Yes | Yes | Databricks lakehouse workloads | Strongest inside the Databricks ecosystem |
| [AWS Glue](https://aws.amazon.com/glue/) | Spark ETL + Structured Streaming | Usually via upstream CDC service | Yes | Yes | AWS-native ETL | Real-time architecture could include many AWS services. |
| [Fivetran](https://www.fivetran.com/) | Scheduled incremental replication + CDC | Yes | Limited as a general stream processor | Yes | Low-maintenance warehouse ingestion | Most traditional pipelines are synchronous |
| [Airbyte](https://github.com/airbytehq/airbyte) | Scheduled ELT + CDC for supported databases | Yes, source-dependent | Limited for replication | Cloud or self-hosted | Connector flexibility and open source | More operations for self-hosting |

## Data Integration

Tools that extract data from sources and load it into warehouses, lakes and databases.

### Open Source

- [Airbyte](https://github.com/airbytehq/airbyte) - Data integration platform with a large connector catalog and a low-code connector builder.
- [Apache Hop](https://hop.apache.org/) - Visual pipeline and workflow designer that grew out of Pentaho Data Integration.
- [Apache NiFi](https://nifi.apache.org/) - Flow-based system for routing, transforming and tracking data, with a browser-based editor.
- [Apache SeaTunnel](https://github.com/apache/seatunnel) - Distributed batch and streaming integration engine with a wide range of connectors.
- [CloudQuery](https://github.com/cloudquery/cloudquery) - ELT framework that syncs cloud infrastructure and SaaS APIs into databases.
- [dlt](https://github.com/dlt-hub/dlt) - Python library that loads data from APIs and files into destinations, inferring and evolving schemas.
- [Embulk](https://github.com/embulk/embulk) - Plugin-based bulk loader for moving data between databases, storage and services.
- [ingestr](https://github.com/bruin-data/ingestr) - CLI that copies a table between databases with a single command.
- [Meltano](https://github.com/meltano/meltano) - Declarative, CLI-first ELT built on the Singer specification.
- [Redpanda Connect](https://github.com/redpanda-data/connect) - Declarative stream processor, formerly Benthos, that connects inputs and outputs with YAML.
- [Singer](https://www.singer.io/) - Open specification for taps and targets that exchange data as JSON streams.
- [Sling](https://github.com/slingdata-io/sling-cli) - CLI for moving data between databases, files and object storage.
- [Vector](https://github.com/vectordotdev/vector) - High-performance pipeline for logs, metrics and events.

### Managed Services

- [AWS Glue](https://aws.amazon.com/glue/) - Serverless Spark-based ETL and data catalog on AWS.
- [Azure Data Factory](https://azure.microsoft.com/en-us/products/data-factory) - Managed data integration and orchestration on Azure.
- [Estuary](https://estuary.dev/) - Data movement platform with log-based CDC that runs streaming and batch pipelines from the same capture.
- [Fivetran](https://www.fivetran.com/) - Managed ELT with a large catalog of prebuilt connectors.
- [Hevo](https://hevodata.com/) - No-code pipelines from databases and SaaS applications into warehouses.
- [Informatica Intelligent Data Management Cloud](https://www.informatica.com/platform.html) - Enterprise integration, quality and governance suite, now part of Salesforce.
- [Integrate.io](https://www.integrate.io/) - Low-code ETL, ELT and CDC platform.
- [Matillion](https://www.matillion.com/) - Cloud data integration and transformation for warehouses and lakehouses.
- [Portable](https://portable.io/) - Managed connectors for long-tail SaaS sources.
- [Qlik Talend Cloud](https://www.qlik.com/us/di/products/qlik-talend-cloud) - Integration, transformation and data quality platform.
- [Stitch](https://www.stitchdata.com/) - Managed ELT service based on Singer taps.

## Change Data Capture

Tools that read a database's transaction log and turn every insert, update and delete into an event.

- [AWS Database Migration Service](https://aws.amazon.com/dms/) - Managed migration and ongoing replication between databases on AWS.
- [Canal](https://github.com/alibaba/canal) - MySQL binlog parser for incremental subscription and consumption.
- [Debezium](https://debezium.io/) - Log-based CDC connectors for Kafka Connect, with an embedded engine and a standalone server.
- [Estuary](https://estuary.dev/) - Managed log-based CDC from Postgres, MySQL, SQL Server, Oracle and MongoDB to many destinations.
- [Flink CDC](https://github.com/apache/flink-cdc) - Streaming integration framework for CDC sources built on Apache Flink.
- [Google Cloud Datastream](https://cloud.google.com/datastream) - Serverless CDC and replication into BigQuery and Cloud Storage.
- [Maxwell](https://github.com/zendesk/maxwell) - Reads MySQL binlogs and writes row updates as JSON to Kafka, Kinesis and other streams.
- [Oracle GoldenGate](https://www.oracle.com/integration/goldengate/) - Real-time replication for Oracle and heterogeneous databases.
- [PeerDB](https://github.com/PeerDB-io/peerdb) - Fast Postgres replication and CDC into warehouses, queues and storage.
- [pgstream](https://github.com/xataio/pgstream) - Postgres replication with schema change tracking.
- [Qlik Replicate](https://www.qlik.com/us/di/products/qlik-replicate) - Enterprise log-based replication across databases, mainframes and SAP.
- [Sequin](https://github.com/sequinstream/sequin) - Streams Postgres changes to Kafka, SQS, Redis and webhooks.
- [Striim](https://www.striim.com/) - Real-time integration platform with CDC and streaming SQL.
- [Supabase ETL](https://github.com/supabase/etl) - Rust framework for building Postgres logical replication pipelines.
- [wal2json](https://github.com/eulerto/wal2json) - Postgres logical decoding output plugin that emits changes as JSON.

## Event Streaming

Durable logs and brokers that pipelines publish to and consume from.

- [Amazon Kinesis Data Streams](https://aws.amazon.com/kinesis/data-streams/) - Managed real-time data streaming on AWS.
- [Apache Kafka](https://kafka.apache.org/) - Distributed event streaming platform and the de facto standard log for data pipelines.
- [Apache Pulsar](https://pulsar.apache.org/) - Multi-tenant messaging and streaming with tiered storage.
- [Apicurio Registry](https://github.com/Apicurio/apicurio-registry) - Schema and API registry compatible with Kafka serializers.
- [AutoMQ](https://github.com/AutoMQ/automq) - Kafka-compatible streaming that stores data on object storage.
- [Confluent](https://www.confluent.io/) - Managed Kafka, connectors, Schema Registry and Flink, now part of IBM.
- [Gazette](https://github.com/gazette/core) - Streaming infrastructure that stores journals as plain files in cloud storage.
- [Google Cloud Pub/Sub](https://cloud.google.com/pubsub) - Global, serverless messaging and ingestion service.
- [NATS](https://nats.io/) - Lightweight messaging system with JetStream persistence.
- [Redpanda](https://github.com/redpanda-data/redpanda) - Kafka API-compatible streaming platform written in C++.

## Stream Processing

Engines that compute over data while it is moving.

- [Apache Beam](https://beam.apache.org/) - Unified programming model for batch and streaming pipelines across runners.
- [Apache Flink](https://flink.apache.org/) - Stateful stream processing with event-time semantics and exactly-once guarantees.
- [Arroyo](https://github.com/ArroyoSystems/arroyo) - Distributed stream processing engine with a SQL interface, written in Rust.
- [Feldera](https://github.com/feldera/feldera) - Incremental computation engine that evaluates SQL over changing data.
- [Kafka Streams](https://kafka.apache.org/documentation/streams/) - Client library for building stream processing applications on Kafka.
- [Materialize](https://github.com/MaterializeInc/materialize) - Operational data store that keeps SQL views incrementally up to date.
- [Pathway](https://github.com/pathwaycom/pathway) - Python framework for stream processing and real-time pipelines.
- [Quix Streams](https://github.com/quixio/quix-streams) - Python library for stream processing on Kafka.
- [RisingWave](https://github.com/risingwavelabs/risingwave) - Postgres-compatible streaming database for continuous SQL.

## Processing Engines

General-purpose engines for batch transformation and querying.

- [Apache DataFusion](https://datafusion.apache.org/) - Extensible query engine in Rust built on Apache Arrow.
- [Apache Spark](https://spark.apache.org/) - Distributed engine for batch, streaming and machine learning workloads.
- [Daft](https://github.com/Eventual-Inc/Daft) - Distributed dataframe engine for multimodal data.
- [DuckDB](https://duckdb.org/) - In-process analytical database that reads Parquet, CSV and JSON directly.
- [Ibis](https://ibis-project.org/) - Portable Python dataframe API that compiles to many backends.
- [Polars](https://pola.rs/) - Fast dataframe library with a lazy query engine, written in Rust.
- [Trino](https://trino.io/) - Distributed SQL engine for federated queries across data sources.

## Transformation

Tools for modeling and testing data once it has landed.

- [Bruin](https://github.com/bruin-data/bruin) - CLI that combines ingestion, SQL and Python transformation, and quality checks.
- [Coalesce](https://coalesce.io/) - Visual, column-aware transformation platform for cloud warehouses.
- [Dataform](https://cloud.google.com/dataform) - SQL workflow development for BigQuery.
- [dbt](https://github.com/dbt-labs/dbt) - SQL-first transformation framework with testing, documentation and lineage.
- [SQLFluff](https://github.com/sqlfluff/sqlfluff) - Dialect-aware SQL linter and formatter.
- [SQLGlot](https://github.com/tobymao/sqlglot) - SQL parser, transpiler and optimizer for dozens of dialects.
- [SQLMesh](https://github.com/SQLMesh/sqlmesh) - Transformation framework with virtual environments and column-level lineage.

## Orchestration

Schedulers and workflow engines that run pipelines in order and recover from failure.

- [Apache Airflow](https://airflow.apache.org/) - Platform to author, schedule and monitor workflows as Python DAGs.
- [Argo Workflows](https://argoproj.github.io/workflows/) - Container-native workflow engine for Kubernetes.
- [Dagster](https://github.com/dagster-io/dagster) - Asset-oriented orchestrator with built-in lineage and observability.
- [Flyte](https://flyte.org/) - Kubernetes-native orchestrator for data and machine learning pipelines.
- [Kestra](https://github.com/kestra-io/kestra) - Declarative, event-driven orchestration defined in YAML.
- [Mage](https://github.com/mage-ai/mage-ai) - Notebook-style tool for building and running data pipelines.
- [Prefect](https://github.com/PrefectHQ/prefect) - Python workflow orchestration with dynamic flows and retries.

## Reverse ETL

Tools that sync modeled data from the warehouse back into operational systems.

- [Hightouch](https://hightouch.com/) - Reverse ETL and composable customer data platform.
- [RudderStack](https://github.com/rudderlabs/rudder-server) - Customer data pipelines covering event streaming and reverse ETL.

## Data Quality and Observability

Tools that check data is correct, complete and on time.

- [Deequ](https://github.com/awslabs/deequ) - Library for unit-testing data at scale on Apache Spark.
- [Elementary](https://github.com/elementary-data/elementary) - dbt-native data observability with anomaly detection and reports.
- [Great Expectations](https://github.com/fivetran/great_expectations) - Data validation framework built on declarative expectations.
- [Monte Carlo](https://montecarlo.ai/) - Data observability platform that detects and triages pipeline incidents.
- [Pandera](https://github.com/unionai-oss/pandera) - Statistical schema validation for dataframes.
- [Soda Core](https://github.com/sodadata/soda-core) - Data quality checks written in a YAML-based language.

## Catalogs and Lineage

Tools that record what data exists, where it came from and who depends on it.

- [Apache Atlas](https://atlas.apache.org/) - Metadata management and governance for the Hadoop ecosystem and beyond.
- [Apache Polaris](https://github.com/apache/polaris) - Open catalog implementing the Apache Iceberg REST specification.
- [DataHub](https://github.com/datahub-project/datahub) - Metadata platform for discovery, lineage and governance.
- [Marquez](https://github.com/MarquezProject/marquez) - Reference implementation of OpenLineage for collecting and visualizing lineage.
- [OpenLineage](https://openlineage.io/) - Open standard for collecting lineage metadata from pipelines.
- [OpenMetadata](https://github.com/open-metadata/OpenMetadata) - Unified metadata platform with discovery, quality and lineage.
- [Unity Catalog](https://github.com/unitycatalog/unitycatalog) - Open catalog for tables, files and AI assets.

## Table and File Formats

Formats that pipelines write and query engines read.

- [Apache Arrow](https://arrow.apache.org/) - Columnar in-memory format and libraries for fast data interchange.
- [Apache Avro](https://avro.apache.org/) - Row-based serialization format with schema evolution, common in streaming.
- [Apache Hudi](https://hudi.apache.org/) - Open table format with record-level upserts and incremental processing.
- [Apache Iceberg](https://iceberg.apache.org/) - Open table format for large analytic tables with schema and partition evolution.
- [Apache Paimon](https://paimon.apache.org/) - Lake format built for streaming updates.
- [Apache Parquet](https://parquet.apache.org/) - Columnar file format for efficient analytical storage.
- [Delta Lake](https://delta.io/) - Open table format with ACID transactions on object storage.
- [DuckLake](https://ducklake.select/) - Lakehouse format that keeps table metadata in a SQL database.

## Learning

### Books

- [Data Pipelines Pocket Reference](https://www.oreilly.com/library/view/data-pipelines-pocket/9781492087823/) - Concise guide to moving and processing data for analytics, by James Densmore.
- [Designing Data-Intensive Applications](https://dataintensive.net/) - Foundations of storage, replication, logs and stream processing, by Martin Kleppmann.
- [Fundamentals of Data Engineering](https://www.oreilly.com/library/view/fundamentals-of-data/9781098108298/) - The data engineering lifecycle end to end, by Joe Reis and Matt Housley.
- [Kafka: The Definitive Guide](https://www.oreilly.com/library/view/kafka-the-definitive/9781492043072/) - How Kafka works and how to run it in production.
- [Streaming Systems](https://www.oreilly.com/library/view/streaming-systems/9781491983867/) - Watermarks, windows and exactly-once processing, by Tyler Akidau, Slava Chernyak and Reuven Lax.
- [The Data Warehouse Toolkit](https://www.kimballgroup.com/data-warehouse-business-intelligence-resources/books/data-warehouse-dw-toolkit/) - The reference on dimensional modeling, by Ralph Kimball and Margy Ross.

### Courses

- [Data Engineering Professional Certificate](https://www.coursera.org/professional-certificates/data-engineering) - DeepLearning.AI and AWS program taught by Joe Reis.
- [Data Engineering Zoomcamp](https://github.com/DataTalksClub/data-engineering-zoomcamp) - Free course covering ingestion, warehousing, transformation and streaming.
- [dbt Learn](https://learn.getdbt.com/) - Free courses on analytics engineering with dbt.

### Articles and Papers

- [Functional Data Engineering](https://maximebeauchemin.medium.com/functional-data-engineering-a-modern-paradigm-for-batch-data-processing-2327ec32c42a) - Idempotent, partition-based batch pipelines, by Maxime Beauchemin.
- [Streaming 101](https://www.oreilly.com/radar/the-world-beyond-batch-streaming-101/) - Introduction to unbounded data and event time, by Tyler Akidau.
- [The Dataflow Model](https://www.vldb.org/pvldb/vol8/p1792-Akidau.pdf) - Paper on balancing correctness, latency and cost in unbounded data processing.
- [The Log](https://engineering.linkedin.com/distributed-systems/log-what-every-software-engineer-should-know-about-real-time-datas-unifying) - Why the append-only log unifies databases and data integration, by Jay Kreps.
- [Turning the Database Inside Out](https://martin.kleppmann.com/2015/03/04/turning-the-database-inside-out.html) - Treating the change log as the source of truth, by Martin Kleppmann.

### Newsletters and Podcasts

- [Data Engineering Podcast](https://www.dataengineeringpodcast.com/) - Weekly interviews with the people building data tools and platforms.
- [Data Engineering Weekly](https://www.dataengineeringweekly.com/) - Weekly roundup of data engineering articles and news.
- [SeattleDataGuy's Newsletter](https://seattledataguy.substack.com/) - Practical writing on data engineering careers and architecture.
- [Start Data Engineering](https://www.startdataengineering.com/) - Hands-on tutorials on pipeline design and best practices.

### Communities

- [DataTalks.Club](https://datatalks.club/) - Global community of data practitioners with free courses and events.
- [dbt Community](https://www.getdbt.com/community/join-the-community) - Slack and events for analytics engineers.
- [Locally Optimistic](https://locallyoptimistic.com/community/) - Community and blog for analytics leaders.
- [r/dataengineering](https://www.reddit.com/r/dataengineering/) - Active forum for questions, tool comparisons and career advice.

## Related Lists

- [awesome-data-engineering](https://github.com/igorbarinov/awesome-data-engineering) - Broad list of data engineering tools.
- [awesome-dbt](https://github.com/Hiflylabs/awesome-dbt) - Resources for dbt.
- [awesome-pipeline](https://github.com/pditommaso/awesome-pipeline) - Pipeline toolkits and workflow managers.
- [awesome-streaming](https://github.com/manuzhang/awesome-streaming) - Streaming frameworks, applications and resources.

## Contributing

Contributions are welcome. Read the [contribution guidelines](contributing.md) first.
