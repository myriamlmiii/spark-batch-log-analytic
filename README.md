# Apache Spark Batch Processing for Log Analytics

A comprehensive batch processing implementation using Apache Spark with both PySpark and Scala, featuring RDD transformations, DataFrame operations, and HDFS integration for analyzing web server logs at scale.

## 🎯 Project Overview

This project demonstrates Apache Spark's capabilities for batch processing large-scale log data. Implemented classic data processing patterns including WordCount and web analytics on Nginx logs, showcasing Spark's versatility across both Python and Scala APIs. The system integrates with Hadoop's distributed file system for scalable data storage and processing.

## 🛠️ Technology Stack

- **Apache Spark 3.5.3** - Unified analytics engine for batch processing
- **PySpark** - Python API for Spark
- **Scala** - Primary language for Spark applications
- **Apache Hadoop/HDFS** - Distributed file system for data storage
- **Docker** - Containerized deployment environment
- **Jupyter Notebooks** - Interactive development with PySpark
- **Bitnami Images** - Pre-configured Spark containers

## 📋 Core Implementations

### Dual Deployment Strategies

**Native Installation:**
- Downloaded and configured Apache Spark from official source
- Environment variable setup (SPARK_HOME, PATH)
- Hadoop compatibility verification
- Manual configuration management

**Docker-Based Deployment:**
- Bitnami Spark container deployment
- Jupyter/PySpark notebook environment
- Isolated development environment
- Simplified dependency management

### RDD Operations & Transformations

**Basic Transformations:**
```scala
// Parallelization and mapping
val numbers = sc.parallelize(List(1, 2, 3, 4, 5))
val squares = numbers.map(x => x * x)

// Filtering and reduction
val filtered = numbers.filter(_ > 2)
val sum = numbers.reduce((a, b) => a + b)
```

**Key Operations Demonstrated:**
- `parallelize()` - Converting collections to distributed datasets
- `map()` - Element-wise transformations
- `filter()` - Conditional data selection
- `reduce()` - Aggregation operations
- `flatMap()` - One-to-many transformations
- `reduceByKey()` - Key-based aggregation

### DataFrame & Spark SQL

**Structured Data Processing:**
- JSON data source integration
- Schema inference and validation
- SQL-like querying on distributed data
- Temporary view creation for SQL operations
```scala
val df = spark.read.json("data.json")
df.createOrReplaceTempView("people")
spark.sql("SELECT * FROM people WHERE age > 18")
```

### WordCount Implementation

**Multi-Language Approach:**

**PySpark Version:**
- File reading and text processing
- Word tokenization with `flatMap()`
- Key-value pair creation
- Frequency counting with `reduceByKey()`

**Scala Version:**
- Native Spark RDD API usage
- Functional programming patterns
- Type-safe transformations
- Performance optimization

**Results:**
- Successfully counted word frequencies in text files
- Validated Spark's map-reduce capabilities
- Compared Python vs Scala performance characteristics

### Nginx Log Analytics

**Log Processing Pipeline:**
1. **Data Ingestion:** Read Nginx access logs into RDDs
2. **Parsing:** Extract page URLs using regex patterns
3. **Aggregation:** Count page visit frequencies
4. **Ranking:** Sort pages by visit count
5. **Output:** Display most visited pages

**Key Function:**
```scala
def extractPage(line: String): Option[String] = {
  val parts = line.split("\\s+")
  if (parts.length > 3) Some(parts(1)) else None
}
```

**Analysis Results:**
- Identified most visited pages from server logs
- Processed multiple log files concurrently
- Demonstrated real-world log analytics use case

### HDFS Integration

**Distributed Storage Implementation:**
- Connected Spark containers to Hadoop cluster
- Docker network configuration for inter-container communication
- Direct file reading from HDFS using `hdfs://` URIs
- NameNode IP address configuration

**Technical Challenge Solved:**
- Initial connectivity issues between Spark and Hadoop containers
- Successfully networked containers using Docker bridge networks
- Configured proper HDFS paths with NameNode addressing
- Validated distributed file access

**Integration Code:**
```scala
val hdfsUrl = "hdfs://172.20.0.2:8020"
val logData = sc.textFile(s"$hdfsUrl/nginx_logs/nginx_log1.log")
```

## 💡 Technical Insights

### Spark Architecture Understanding

**Execution Model:**
- Driver program coordination
- Executor task distribution
- In-memory computation advantages
- Lazy evaluation optimization

**RDD Characteristics:**
- Immutable distributed collections
- Fault tolerance through lineage
- Partitioning for parallelism
- Caching for iterative algorithms

### Performance Observations

**Resource Management:**
- Successfully ran on 8GB RAM configuration
- Memory allocation for executors and driver
- Partition tuning for optimal performance
- Garbage collection considerations

**Python vs Scala:**
- Scala provides type safety and performance
- PySpark offers ease of development
- Both APIs access same Spark core
- Language choice based on use case

### Docker Networking

**Container Orchestration:**
- Created shared Docker network for Hadoop-Spark communication
- Port mapping for web interfaces and data access
- Volume mounting for data persistence
- Network inspection and troubleshooting

## 📊 Results & Validation

**Successful Implementations:**
- WordCount execution in both PySpark and Scala
- Nginx log analysis with page visit ranking
- HDFS file reading from Spark
- DataFrame operations with JSON data
- SQL queries on distributed datasets

**Page Visit Analysis Output:**
```
/page0: 10129
/page4: 10055
/page5: 10051
/page1: 9992
/page2: 9940
/page3: 9982
...
```

## 🚀 Skills Demonstrated

- **Spark Programming:** RDD and DataFrame APIs in multiple languages
- **Functional Programming:** Map-reduce patterns and transformations
- **Distributed Computing:** Understanding of parallel processing concepts
- **Data Engineering:** ETL pipeline development for log analytics
- **System Integration:** Spark-Hadoop ecosystem connectivity
- **Containerization:** Docker-based deployment and networking
- **Problem Solving:** Debugging distributed system connectivity issues
- **Performance Tuning:** Resource allocation and optimization

## 🏗️ Data Processing Flow

**End-to-End Pipeline:**
1. Log data stored in HDFS across distributed nodes
2. Spark reads data into RDDs with partitioning
3. Transformations applied in parallel across executors
4. Results aggregated and sorted by driver
5. Output displayed or written back to storage

## 📄 Technical Documentation

For complete deployment steps, code implementations, comparative analysis, troubleshooting notes, and detailed technical specifications, see the [full project documentation](spark-batch-processing.pdf).

## 🎓 Background

Built this project to master Apache Spark's batch processing capabilities and understand how it compares to traditional MapReduce and Hive workflows. Explored both PySpark and Scala APIs to gain proficiency in Spark's ecosystem, learning patterns used by companies like Netflix, Uber, and Airbnb for large-scale data processing.

## 🔗 Connect

**Meriem Lmoubariki**
- GitHub: [@myriamlmiii](https://github.com/myriamlmiii)

---

*Demonstrating expertise in Apache Spark, distributed batch processing, and scalable data analytics.*
