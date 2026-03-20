# Names and Computing IDs: Andrew Nguyen (fru4yr), Zaylie Tamashiro (gqv7zm)

# Walmart Hurricane Project
A new hurricane is approaching Florida, and Walmart leadership needs answers fast on what products people will want to buy and how much to actually supply.

## Data sources
Walmart Dataset: https://www.kaggle.com/datasets/andrewniscool/midterm-dataset
- Contains transactions, store locations, distribution centers, product catalog, inventory, and sales data
- Accessed March 19, 2026
- Limitations: inconsistent SKUs, product names, store IDs, and category labels

Open-Meteo Historical Weather API: https://open-meteo.com/
- Contains hourly weather data including precipitation, wind speed, and pressure
- Accessed March 19, 2026.
- Limitations: Data is location-specific (single latitude-longitude used)

## ETL & data preparation
ETL Pipeline: 
- A[Raw POS + Inventory + Weather Data] --> B[Extract]
- B --> C[Transform - Convert Transactions to Datetime]
- C --> D[Transform - Convert Quantity & Unit Price to Numeric]
- D --> E[Transform - Deduplicate]
- E --> F[Transform - Standardize Category & Product Name]
- F --> G[Transform - Align Timestamps]
- G --> H[Transform - Convert Store ID to Numeric]
- H --> I[Transform - Join Store Data with Transaction Data]
- I --> J[Load Cleaned Dataframes for Analysis]
- J --> K[Analyze]
- K --> L[Business Decision: Pre-stock Board Games]

## Analysis approach
We conducted several analyses to understand demand behavior before the hurricane:
- Category surge analysis: Compared baseline vs. pre-landfall sales to identify which product categories increased the most
- SKU consolidation analysis: Examined how inconsistent product naming (e.g., Pop-Tarts) affects demand measurement
- Weather correlation analysis: Compared sales trends with weather indicators (wind, precipitation, pressure) to detect timing relationships
- Store-level geographic analysis: Evaluated how demand varies by location and proximity to the hurricane path
- Signal vs. artifact analysis (board games): Investigated whether observed spikes were real demand or caused by data issues

These approaches allowed us to separate true behavioral patterns from data artifacts.

## Results
Based on our findings, Walmart should:
- Increase inventory of essential categories (food, emergency supplies, household goods) well before landfall
- Adjust inventory by location, as stores experience different surge timing and intensity
- Include secondary categories (e.g., entertainment items like board games) as part of hurricane preparation demand
- Improve SKU and data standardization, as inconsistent labeling can hide true demand signals

## What could be wrong?
Data quality risks
- SKU inconsistencies may still partially distort category-level demand
- Inventory database does not perfectly align with transaction data
Confounders
- Promotions or pricing changes could influence demand independently of the hurricane
- Population differences between cities (e.g., Miami vs. smaller towns)
Alternative explanations
- Some demand spikes may reflect general seasonal trends rather than hurricane preparation
- Weather data may not perfectly represent conditions at all store locations

## How to reproduce
1. Open the notebook(s)
2. Add input "https://www.kaggle.com/datasets/andrewniscool/midterm-dataset" as a dataset
3. Run all cells top-to-bottom
