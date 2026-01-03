import React, { useState, useEffect } from 'react';
import { Database, Activity, TrendingUp, AlertCircle, PlayCircle, PauseCircle, RefreshCw } from 'lucide-react';

const DataEngineeringPortfolio = () => {
  const [activeTab, setActiveTab] = useState('overview');
  const [isSimulating, setIsSimulating] = useState(false);
  const [metrics, setMetrics] = useState({
    recordsProcessed: 0,
    throughput: 0,
    latency: 0,
    errorRate: 0
  });

  useEffect(() => {
    let interval;
    if (isSimulating) {
      interval = setInterval(() => {
        setMetrics(prev => ({
          recordsProcessed: prev.recordsProcessed + Math.floor(Math.random() * 100) + 50,
          throughput: Math.floor(Math.random() * 500) + 1000,
          latency: Math.floor(Math.random() * 50) + 20,
          errorRate: (Math.random() * 0.5).toFixed(2)
        }));
      }, 1000);
    }
    return () => clearInterval(interval);
  }, [isSimulating]);

  const architectureComponents = [
    { name: 'Data Sources', desc: 'Flight APIs, Weather APIs, Airport Data', color: 'bg-blue-500' },
    { name: 'Ingestion Layer', desc: 'Apache Kafka / AWS Kinesis', color: 'bg-green-500' },
    { name: 'Stream Processing', desc: 'Apache Spark Structured Streaming', color: 'bg-purple-500' },
    { name: 'Data Lake', desc: 'AWS S3 / Azure Data Lake (Parquet)', color: 'bg-yellow-500' },
    { name: 'Data Warehouse', desc: 'Snowflake / BigQuery', color: 'bg-red-500' },
    { name: 'Orchestration', desc: 'Apache Airflow', color: 'bg-indigo-500' },
    { name: 'Monitoring', desc: 'Prometheus + Grafana', color: 'bg-pink-500' }
  ];

  const keyFeatures = [
    'Real-time data ingestion from multiple APIs',
    'Stream processing with windowing and aggregations',
    'Delta Lake for ACID transactions',
    'Dimensional modeling (Star Schema)',
    'Incremental data loading strategies',
    'Data quality checks and validation',
    'Automated testing and CI/CD pipeline',
    'Cost optimization strategies'
  ];

  const technicalSkills = [
    { category: 'Languages', items: ['Python', 'SQL', 'Scala'] },
    { category: 'Big Data', items: ['Spark', 'Kafka', 'Hadoop'] },
    { category: 'Cloud', items: ['AWS', 'Azure', 'GCP'] },
    { category: 'Databases', items: ['PostgreSQL', 'MongoDB', 'Redis'] },
    { category: 'Warehouses', items: ['Snowflake', 'Redshift', 'BigQuery'] },
    { category: 'Orchestration', items: ['Airflow', 'Dagster', 'Prefect'] },
    { category: 'Tools', items: ['Docker', 'Kubernetes', 'Terraform'] },
    { category: 'Monitoring', items: ['Grafana', 'Datadog', 'ELK Stack'] }
  ];

  const codeExample = `# Apache Spark Streaming Pipeline Example
from pyspark.sql import SparkSession
from pyspark.sql.functions import window, col, avg, count

spark = SparkSession.builder \\
    .appName("FlightDataPipeline") \\
    .getOrCreate()

# Read from Kafka stream
flight_stream = spark.readStream \\
    .format("kafka") \\
    .option("kafka.bootstrap.servers", "localhost:9092") \\
    .option("subscribe", "flight-data") \\
    .load()

# Parse and transform data
parsed_flights = flight_stream.selectExpr(
    "CAST(value AS STRING)"
).select(from_json(col("value"), schema).alias("data")) \\
 .select("data.*")

# Windowed aggregations
aggregated = parsed_flights \\
    .withWatermark("timestamp", "10 minutes") \\
    .groupBy(
        window(col("timestamp"), "5 minutes"),
        col("airline"),
        col("origin_airport")
    ).agg(
        count("*").alias("flight_count"),
        avg("delay_minutes").alias("avg_delay")
    )

# Write to Delta Lake
query = aggregated.writeStream \\
    .format("delta") \\
    .outputMode("append") \\
    .option("checkpointLocation", "/checkpoints") \\
    .start("/data/flight-analytics")`;

  return (
    <div className="min-h-screen bg-gradient-to-br from-slate-900 via-slate-800 to-slate-900 text-white p-6">
      <div className="max-w-7xl mx-auto">
        <header className="mb-8">
          <div className="flex items-center gap-3 mb-2">
            <Database className="w-10 h-10 text-blue-400" />
            <h1 className="text-4xl font-bold">Real-Time Flight Data Pipeline</h1>
          </div>
          <p className="text-slate-300 text-lg">End-to-End Data Engineering Portfolio Project</p>
        </header>

        <div className="flex gap-2 mb-6 flex-wrap">
          {['overview', 'architecture', 'features', 'code', 'skills'].map(tab => (
            <button
              key={tab}
              onClick={() => setActiveTab(tab)}
              className={`px-6 py-2 rounded-lg font-medium transition-all ${
                activeTab === tab
                  ? 'bg-blue-500 text-white'
                  : 'bg-slate-700 text-slate-300 hover:bg-slate-600'
              }`}
            >
              {tab.charAt(0).toUpperCase() + tab.slice(1)}
            </button>
          ))}
        </div>

        {activeTab === 'overview' && (
          <div className="space-y-6">
            <div className="bg-slate-800 rounded-xl p-6 border border-slate-700">
              <h2 className="text-2xl font-bold mb-4 flex items-center gap-2">
                <Activity className="w-6 h-6 text-green-400" />
                Project Overview
              </h2>
              <p className="text-slate-300 mb-4">
                A production-grade data engineering project that demonstrates building a scalable,
                real-time data pipeline for processing flight information. This project showcases
                modern data engineering practices including stream processing, data warehousing,
                and pipeline orchestration.
              </p>
              <div className="grid grid-cols-2 gap-4 mt-6">
                <div className="bg-slate-900 p-4 rounded-lg">
                  <h3 className="font-semibold text-blue-400 mb-2">Business Problem</h3>
                  <p className="text-sm text-slate-300">
                    Airlines and travel platforms need real-time insights into flight delays,
                    cancellations, and patterns to optimize operations and improve customer experience.
                  </p>
                </div>
                <div className="bg-slate-900 p-4 rounded-lg">
                  <h3 className="font-semibold text-green-400 mb-2">Solution</h3>
                  <p className="text-sm text-slate-300">
                    Build a scalable pipeline that ingests flight data from multiple sources,
                    processes it in real-time, and delivers actionable analytics through a
                    dimensional data warehouse.
                  </p>
                </div>
              </div>
            </div>

            <div className="bg-slate-800 rounded-xl p-6 border border-slate-700">
              <div className="flex items-center justify-between mb-4">
                <h2 className="text-2xl font-bold flex items-center gap-2">
                  <TrendingUp className="w-6 h-6 text-yellow-400" />
                  Live Metrics Simulation
                </h2>
                <button
                  onClick={() => setIsSimulating(!isSimulating)}
                  className={`px-4 py-2 rounded-lg font-medium flex items-center gap-2 ${
                    isSimulating
                      ? 'bg-red-500 hover:bg-red-600'
                      : 'bg-green-500 hover:bg-green-600'
                  }`}
                >
                  {isSimulating ? (
                    <>
                      <PauseCircle className="w-4 h-4" />
                      Stop
                    </>
                  ) : (
                    <>
                      <PlayCircle className="w-4 h-4" />
                      Start
                    </>
                  )}
                </button>
              </div>
              <div className="grid grid-cols-4 gap-4">
                <div className="bg-slate-900 p-4 rounded-lg">
                  <p className="text-slate-400 text-sm mb-1">Records Processed</p>
                  <p className="text-2xl font-bold text-blue-400">
                    {metrics.recordsProcessed.toLocaleString()}
                  </p>
                </div>
                <div className="bg-slate-900 p-4 rounded-lg">
                  <p className="text-slate-400 text-sm mb-1">Throughput (rec/s)</p>
                  <p className="text-2xl font-bold text-green-400">{metrics.throughput}</p>
                </div>
                <div className="bg-slate-900 p-4 rounded-lg">
                  <p className="text-slate-400 text-sm mb-1">Latency (ms)</p>
                  <p className="text-2xl font-bold text-yellow-400">{metrics.latency}</p>
                </div>
                <div className="bg-slate-900 p-4 rounded-lg">
                  <p className="text-slate-400 text-sm mb-1">Error Rate (%)</p>
                  <p className="text-2xl font-bold text-red-400">{metrics.errorRate}</p>
                </div>
              </div>
            </div>
          </div>
        )}

        {activeTab === 'architecture' && (
          <div className="bg-slate-800 rounded-xl p-6 border border-slate-700">
            <h2 className="text-2xl font-bold mb-6">System Architecture</h2>
            <div className="space-y-4">
              {architectureComponents.map((component, idx) => (
                <div key={idx} className="flex items-start gap-4">
                  <div className={`w-3 h-3 rounded-full ${component.color} mt-2`}></div>
                  <div className="flex-1">
                    <h3 className="font-semibold text-lg">{component.name}</h3>
                    <p className="text-slate-400">{component.desc}</p>
                  </div>
                  {idx < architectureComponents.length - 1 && (
                    <div className="text-slate-600 text-2xl">↓</div>
                  )}
                </div>
              ))}
            </div>
            <div className="mt-8 p-4 bg-slate-900 rounded-lg border border-blue-500">
              <h3 className="font-semibold text-blue-400 mb-2 flex items-center gap-2">
                <AlertCircle className="w-5 h-5" />
                Architecture Highlights
              </h3>
              <ul className="text-sm text-slate-300 space-y-1">
                <li>• Lambda architecture supporting both batch and stream processing</li>
                <li>• Idempotent processing with exactly-once semantics</li>
                <li>• Horizontal scalability through partitioning strategies</li>
                <li>• Data lineage tracking and schema evolution support</li>
              </ul>
            </div>
          </div>
        )}

        {activeTab === 'features' && (
          <div className="bg-slate-800 rounded-xl p-6 border border-slate-700">
            <h2 className="text-2xl font-bold mb-6">Key Features & Implementation</h2>
            <div className="grid grid-cols-2 gap-4">
              {keyFeatures.map((feature, idx) => (
                <div key={idx} className="bg-slate-900 p-4 rounded-lg border border-slate-700">
                  <div className="flex items-start gap-3">
                    <div className="w-6 h-6 rounded-full bg-blue-500 flex items-center justify-center flex-shrink-0 mt-0.5">
                      <span className="text-xs font-bold">{idx + 1}</span>
                    </div>
                    <p className="text-slate-300">{feature}</p>
                  </div>
                </div>
              ))}
            </div>
            <div className="mt-6 p-4 bg-gradient-to-r from-purple-900 to-blue-900 rounded-lg">
              <h3 className="font-semibold mb-2">Data Model</h3>
              <p className="text-sm text-slate-300 mb-3">
                Implements a star schema with fact and dimension tables for optimal query performance.
              </p>
              <div className="grid grid-cols-3 gap-3 text-sm">
                <div className="bg-slate-800 p-3 rounded">
                  <p className="font-semibold text-yellow-400">Fact Tables</p>
                  <p className="text-slate-400">flight_events, delays</p>
                </div>
                <div className="bg-slate-800 p-3 rounded">
                  <p className="font-semibold text-green-400">Dimensions</p>
                  <p className="text-slate-400">airlines, airports, time</p>
                </div>
                <div className="bg-slate-800 p-3 rounded">
                  <p className="font-semibold text-blue-400">SCD Type 2</p>
                  <p className="text-slate-400">Historical tracking</p>
                </div>
              </div>
            </div>
          </div>
        )}

        {activeTab === 'code' && (
          <div className="bg-slate-800 rounded-xl p-6 border border-slate-700">
            <h2 className="text-2xl font-bold mb-4">Code Example</h2>
            <p className="text-slate-300 mb-4">
              Sample Spark Structured Streaming pipeline for processing flight data:
            </p>
            <pre className="bg-slate-900 p-4 rounded-lg overflow-x-auto text-sm border border-slate-700">
              <code className="text-green-400">{codeExample}</code>
            </pre>
            <div className="mt-4 p-4 bg-blue-900 rounded-lg">
              <h3 className="font-semibold mb-2">Additional Components</h3>
              <ul className="text-sm text-slate-300 space-y-1">
                <li>• Airflow DAGs for orchestrating batch jobs and data quality checks</li>
                <li>• DBT models for transformation logic and documentation</li>
                <li>• Great Expectations for data validation</li>
                <li>• Terraform configurations for infrastructure as code</li>
                <li>• GitHub Actions for CI/CD automation</li>
              </ul>
            </div>
          </div>
        )}

        {activeTab === 'skills' && (
          <div className="bg-slate-800 rounded-xl p-6 border border-slate-700">
            <h2 className="text-2xl font-bold mb-6">Technical Skills Demonstrated</h2>
            <div className="grid grid-cols-2 gap-4">
              {technicalSkills.map((skill, idx) => (
                <div key={idx} className="bg-slate-900 p-4 rounded-lg border border-slate-700">
                  <h3 className="font-semibold text-blue-400 mb-3">{skill.category}</h3>
                  <div className="flex flex-wrap gap-2">
                    {skill.items.map((item, i) => (
                      <span
                        key={i}
                        className="px-3 py-1 bg-slate-800 border border-slate-600 rounded-full text-sm"
                      >
                        {item}
                      </span>
                    ))}
                  </div>
                </div>
              ))}
            </div>
            <div className="mt-6 p-4 bg-gradient-to-r from-green-900 to-teal-900 rounded-lg">
              <h3 className="font-semibold mb-2 flex items-center gap-2">
                <RefreshCw className="w-5 h-5" />
                Portfolio Impact
              </h3>
              <p className="text-sm text-slate-300">
                This project demonstrates end-to-end data engineering capabilities including
                architecture design, implementation, testing, and deployment. The comprehensive
                documentation and clean code make it an excellent portfolio piece that shows
                both technical depth and production-readiness.
              </p>
            </div>
          </div>
        )}

        <footer className="mt-8 p-4 bg-slate-800 rounded-lg border border-slate-700 text-center text-slate-400 text-sm">
          <p>
            💡 Include a GitHub repository with complete code, documentation, architecture diagrams,
            and a demo video. Deploy a simplified version using free tiers of cloud services.
          </p>
        </footer>
      </div>
    </div>
  );
};
