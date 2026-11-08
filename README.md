# Urban Data Analytics Platform — Microsoft Fabric

A hands-on Microsoft Fabric data engineering project integrating mobility, air-quality, and macroeconomic datasets.

## Project scope

The project follows a medallion architecture:

- **Bronze:** ingest and retain raw source data in OneLake.
- **Silver:** standardize, clean, deduplicate, and enrich the datasets using Fabric Notebooks and PySpark.
- **Gold:** publish analytical fact and dimension tables in a Fabric Warehouse.

### Data sources

| Domain | Source | Data |
|---|---|---|
| Mobility | NYC Taxi & Limousine Commission (TLC) | Monthly taxi trip Parquet files |
| Environment | OpenAQ | Air-quality measurements (for example PM2.5, NO2, O3) |
| Economy | World Bank | Country-level GDP |
| Economy | European Central Bank (ECB) | Daily USD/EUR exchange rates |

## Planned engineering workflow

1. **Foundation and workspace** — configure the Fabric workspace and core items; connect the project to GitHub where supported.
2. **Bronze — ingestion** — use Data Factory pipelines for taxi Parquet files and Dataflows Gen2 for API-based sources; land raw data in OneLake.
3. **Silver — transformation** — use Fabric Notebooks and PySpark to standardize schemas, deduplicate, normalize, enrich with date/time attributes, and write Delta tables.
4. **Gold — data modeling** — build a Warehouse star schema with:
   - `FactTaxiDaily`
   - `FactAirQualityDaily`
   - `DimDate`
   - `DimZone`
   - `DimFX`
   - `DimGDP`
5. **Finalization** — validate outputs, document the data model and lineage, and review reliability and monitoring.
6. **Power BI (later / optional)** — consider dashboards only after the data engineering solution is complete.

## Analytical questions the platform may support

- How does daily taxi activity relate to daily air-quality measurements in NYC?
- Which locations or times show the strongest relationship between taxi demand and pollution?
- What is the average taxi revenue in USD and EUR, and how do exchange-rate movements affect it?
- How do mobility and economic trends compare over time with environmental measurements?

## Repository approach

This repository will contain the implementation as it is built: project documentation, source code, SQL, notebook exports where practical, and configuration that can safely be version-controlled.

Do not commit credentials, API keys, access tokens, connection strings, or other secrets.

## Learning approach

Build one step at a time. Understand each Fabric component, implement it, validate it, and then move to the next step. Avoid creating placeholder implementation folders before they are needed.
