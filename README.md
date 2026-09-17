# PySpark Troubleshooting Lab

<p align="center">
  <img src="https://img.shields.io/badge/PySpark-E25A1C?style=for-the-badge&logo=apachespark&logoColor=white" alt="PySpark" />
  <img src="https://img.shields.io/badge/Apache_Spark-E25A1C?style=for-the-badge&logo=apachespark&logoColor=white" alt="Apache Spark" />
  <img src="https://img.shields.io/badge/Databricks-FF3621?style=for-the-badge&logo=databricks&logoColor=white" alt="Databricks" />
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python" />
</p>

> 🚧 **Planned**...Content will land as the project takes shape.

A collection of reproducible Spark failures, each one isolated, explained, and fixed. The point isn't the fix. The point is understanding *why* the failure happens, so you can recognise it in production before it takes down a pipeline.

## What this is

Real Spark pain points, reproduced in a controlled environment:

- **Data skew** - what happens when one partition gets 90% of the rows, and why salting works
- **OOM executors** - driver vs. executor memory, when it's a memory problem and when it's actually a partition problem
- **Partition tuning** - how many partitions is too many, too few, and why `spark.sql.shuffle.partitions` is almost never the right answer
- **Schema drift** - what breaks silently when a source adds a column, and how Delta Lake's schema enforcement catches it

Each failure case is a self-contained notebook: a dataset that triggers the problem, a diagnostic walkthrough, a fix, and an explanation of the underlying mechanism.

## Why this exists

I work on the support side of enterprise data platforms. When a Spark job fails in production, the error message is usually one or two lines above a stack trace that points somewhere unhelpful. The failure mode is rarely obvious from the message, it's the *interaction* between data distribution, cluster configuration, and query plan.

This repo is the diagnostic reference I wish existed when I started. Not "here's a Stack Overflow answer," but "here's the mechanism, here's how to identify it, here's why the fix works."

## Planned Structure

```
pyspark-troubleshooting-lab/
├── README.md
├── data-skew/
│   ├── 01_reproduce.ipynb
│   ├── 02_diagnose.ipynb
│   └── 03_fix.ipynb
├── oom-executors/
├── partition-tuning/
├── schema-drift/
└── utils/
    └── data_generators.py
```

Each folder follows the same pattern: reproduce → diagnose → fix.

## Related

- [Predictive Maintenance Pipeline](https://github.com/SonOfElle/predictive-maintenance-pipeline) - where several of these patterns show up in a real pipeline context
- [Cloud Data Platform IaC](https://github.com/SonOfElle/cloud-data-platform-iac) - provisioning the environment these labs run in

*Status: planned. Notebooks and data generators will be committed as cases are developed.*
