# Apple Product Purchase Analysis

[![PySpark](https://img.shields.io/badge/PySpark-3.1.2-orange.svg)](https://spark.apache.org/docs/3.1.2/)
[![Delta Lake](https://img.shields.io/badge/Delta%20Lake-1.0.0-blue.svg)](https://delta.io/)
[![Databricks](https://img.shields.io/badge/Databricks-Runtime-red.svg)](https://databricks.com/)

## Project Overview

This data engineering project analyzes Apple product purchasing patterns using PySpark and Databricks. The analysis focuses on customer behaviors around purchasing iPhones and AirPods, identifying cross-sell opportunities and purchase timing patterns.

## Key Analysis Tasks

1. **AirPods after iPhone Analysis**: Identify customers who purchased AirPods after buying an iPhone
2. **iPhone and AirPods Only**: Find customers who exclusively purchased iPhones and AirPods (no other products)
3. **Average Time to AirPods**: Calculate the average time customers take to purchase AirPods after buying an iPhone

## Project Structure

The project is organized into several Databricks notebooks that follow a modular ETL architecture:

- **Apple Analysis.ipynb** - Main orchestration notebook that runs the ETL workflow
- **Create Delta Table.ipynb** - Sets up Delta tables from source data
- **Extract.ipynb** - Handles data extraction logic 
- **Transform.ipynb** - Contains transformation logic and business rules
- **Load.ipynb** - Manages loading data to destinations
- **Factory Notebooks** - Implement design patterns for flexible data operations

## Technical Architecture

This project implements a modular ETL (Extract, Transform, Load) architecture using object-oriented programming principles:

### Design Patterns

- **Factory Pattern**: Used for creating data readers and loaders with different strategies
- **Strategy Pattern**: Different implementation strategies for extraction, transformation, and loading
- **Template Method Pattern**: Base abstract classes define workflow, child classes implement specific behaviors

### Data Flow

1. **Extract**: Read data from various sources (CSV files, Delta tables)
2. **Transform**: Process data with specific business logic:
  - Window functions for sequential purchase analysis
  - Array operations for product set analysis
  - Aggregation functions for metrics calculation
3. **Load**: Write results to multiple destinations (Delta tables, partitioned file storage)

## Key Insights

- Identified customers who follow the iPhone → AirPods purchase pattern
- Calculated the average number of days between iPhone and AirPods purchases
- Segmented customers by location and purchase patterns

## Technical Highlights

- **Window Functions**: Used lead() function to analyze sequential purchases
- **Broadcast Joins**: Optimized join performance for small dimension tables
- **Delta Lake**: Leveraged ACID transactions and time travel capabilities
- **Modular Architecture**: Designed for reusability and maintainability
- **Databricks Integration**: Seamless notebook workflow execution

## How to Run

1. Import the notebooks to your Databricks workspace
2. Upload the CSV files to Databricks FileStore
3. Run the "Create Delta Table" notebook first to set up delta tables
4. Execute the "Apple Analysis" notebook to run the complete workflow

## Future Enhancements

- Add product price analysis to calculate revenue impact
- Implement customer segmentation based on purchase patterns
- Create visualizations for key metrics and trends
- Deploy workflow for automated scheduled execution

## License

[MIT](https://opensource.org/licenses/MIT)
