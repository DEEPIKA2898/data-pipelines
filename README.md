# data-pipelines

Customer ETL pipeline using Databricks Asset Bundles.

## Pipeline flow
```
customers.csv → bronze.raw_customers → silver.customers → gold.customer_summary
```

## Structure
```
bundles/
  customer-etl/
    databricks.yml     # bundle config — jobs, clusters, targets
    notebooks/
      01_ingest_bronze.py    # CSV → bronze
      02_transform_silver.py # bronze → silver (clean + conform)
      03_aggregate_gold.py   # silver → gold (aggregations)
    data/
      customers.csv          # sample data
```

## Deploy manually
```bash
cd bundles/customer-etl
databricks bundle deploy --target dev
databricks bundle run --target dev customer_etl_pipeline
```
