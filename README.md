# 🌍  Urban Sustainability Index (USI) – 2023
The Urban Sustainability Index (USI) is a composite metric assessing national sustainability across environmental, social, economic, and urban dimensions. Using normalized 2023 global data, it enables transparent cross-country comparison and analysis of development–sustainability trade-offs.


This index is designed to support:

  Cross-country sustainability comparison.
  Identification of development–environment trade-offs.
  Exploratory policy and urban planning analysis.
  
The entire workflow is implemented in Python using widely adopted data science libraries.

# Objectives

  Build a transparent and reproducible urban sustainability index.
  
  Integrate multidimensional sustainability indicators into a single score.
  
  Analyze the relationship between urbanization and sustainability outcomes.
  
  Provide clear visualizations to support interpretation.

# Dataset

File: world-data-2023.csv

Scope: Global, country-level indicators (2023)

Key variables used:

  Country
  Population
  CO₂ emissions
  Forest area (%)
  Life expectancy
  Physicians per 1,000 people
  Gross Domestic Product (GDP)
  Unemployment rate
  Urban population
  Land area

The script dynamically detects column names to ensure robustness across dataset variants.

# Data Cleaning & Preprocessing

Standardized column names (lowercase, underscores, no special characters)

Removed commas, percentage symbols, and non-numeric characters

Converted invalid values ("", "-", "--") to missing values

Replaced infinite values caused by division by zero with NaN

This step ensures consistency and prevents bias during normalization.

# Feature Engineering

To improve comparability across countries, several derived indicators were created:

Feature	Description

CO₂ per capita = Total CO₂ emissions ÷ population

GDP per capita =	GDP ÷ population

Urban population (%) = Urban population ÷ total population × 100

Population density =	Population ÷ land area

# Sustainability Dimensions

Indicators were grouped into four equally weighted dimensions:

🌱 Environmental Dimension

  CO₂ emissions per capita (negative indicator)
  
  Forest area (%)

👥 Social Dimension

  Life expectancy
  
  Physicians per 1,000 people

💰 Economic Dimension

GDP per capita

  Unemployment rate (negative indicator)

🏙️ Urban Dimension

  Urban population (%)
  
  Population density (negative indicator)

Negative indicators were inverted after normalization so that higher values always represent better sustainability.

# Normalization Method

  Min–Max Scaling applied to each indicator.
  
  Scaled values range from 0 (worst) to 1 (best).
  
  Indicators with insufficient data were excluded automatically.
  
  Negative indicators were reversed post-scaling.

This ensures comparability across different units and scales.

# Dimension Scoring

Each dimension score is calculated as the mean of its normalized indicators:

  Environmental Score.
  
  Social Score.
  
  Economic Score.
  
  Urban Score

This approach maintains transparency and avoids subjective weighting.

# Urban Sustainability Index (USI)

The final Urban Sustainability Score is computed as:

  USI = Mean(Environmental, Social, Economic, Urban)


All four dimensions contribute equally to the final score.

# Visualizations
 Sustainability Score by Country

  A bar chart ranking countries by their Urban Sustainability Score, highlighting top and bottom performers.

 Radar Chart (Top, Median, Bottom Countries)

  Radar plots compare dimension-level performance, revealing sustainability imbalances even among high-ranking countries.

 Urbanization vs Sustainability

  A scatter plot illustrating the relationship between urban population share and sustainability outcomes, showing that urbanization alone does not guarantee sustainability.

 Environmental Trade-Offs

  A scatter plot of CO₂ emissions per capita versus forest coverage, demonstrating the tension between economic development and environmental preservation.

# Key Findings

  High-income countries tend to perform well economically and socially but often face environmental challenges.
  
  Several mid-income countries achieve balanced sustainability profiles across dimensions.
  
  High population density can negatively impact urban sustainability when not supported by infrastructure.
  
  Urbanization must be accompanied by strong healthcare, employment, and environmental policies to be sustainable.

# Limitations

  Country-level aggregation masks regional and city-level disparities.
  
  Equal weighting may not reflect real-world policy priorities.
  
  Data availability restricts indicator selection.
  
  Emissions data is production-based, not consumption-based.

# Future Enhancements

  Introduce custom or policy-driven weights.
  
  Extend analysis to multiple years (time series).
  
  Include renewable energy and air quality indicators.
  
  Add geospatial mapping using GeoPandas.
  
  Apply the framework to city-level datasets.

# Conclusion

The Urban Sustainability Index provides a clear, systematic, and reproducible framework for assessing sustainability at the national level.
While simplified, the index captures essential trade-offs between development, urbanization, and environmental impact, making it a useful tool for exploratory research, policy discussion, and comparative analysis.

The framework is flexible and can be expanded as better data and new indicators become available.

#Technologies Used

  Python
  
  Pandas
  
  NumPy
  
  Scikit-learn
  
  Matplotlib
  
  GeoPandas
