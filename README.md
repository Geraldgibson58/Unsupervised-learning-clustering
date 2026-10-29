# Unsupervised Learning: World Happiness Clustering

## Overview
This project explores whether countries show similar profiles across indicators from the World Happiness Report. Instead of predicting a known label, I use **unsupervised learning** to group countries according to patterns in their standardized social, economic, and well-being measurements.

## Research Question
Can clustering identify groups of countries with similar happiness-related indicators, and how do these data-driven groups compare with the dataset's regional categories?

## Data
- **Required source workbook:** `WHR2018Chapter2OnlineData.xlsx`
- **Worksheets used:** `Table2.1` and `SupportingFactors`
- **Observations:** Country-level averages across years available in the source workbook, joined to the regional indicator
- **Clustering inputs:** `Happiness`, `LogGDP`, `Support`, `Life`, `Freedom`, `Generosity`, `Corruption`, `Positive`, and `Negative`

Rows with missing values in the selected inputs were removed. Region labels were kept for subsequent comparison, **not** used as clustering inputs.

## Methodology
1. Selected the nine quantitative indicators and averaged them by country.
2. Joined the country-level summary to regional classification data.
3. Standardized numeric indicators using `StandardScaler` so the variables were on comparable scales.
4. Visualized the standardized dataset with a heatmap.
5. Fitted a **K-means model with 10 clusters**, matching the number of regional categories in the source data.
6. Graphed cluster centroids to interpret the indicators associated with different country groups.
7. Compared K-means assignments with regional groupings using a grouped count table.

The underlying assignment notebook also includes an example of a hierarchical clustermap, but that code appears as a **non-executed markdown example** in the saved version; it should not be presented as a completed result without running it.

## Selected Findings
- The analysis formed **10 groups** based on the nine standardized indicators.
- Cluster-centroid plots made it possible to compare patterns in happiness, economic conditions, health, social support, and other variables.
- A cluster-by-region table allowed comparison of algorithm-generated groups with predefined geographic regions. These are descriptive associations and do not imply that geography causes the patterns.

Clustering results may change between runs because the saved K-means code does not set a random seed. Cluster numbers are arbitrary identifiers, not rankings of countries.

## Tools
Python, Jupyter Notebook, pandas, NumPy, Matplotlib, seaborn, scikit-learn, and openpyxl (for Excel input).

## Repository Files
```text
unsupervised-learning-clustering/
├── README.md
├── notebooks/
│   └── world_happiness_clustering.ipynb
└── data/
    └── WHR2018Chapter2OnlineData.xlsx
```

**Before uploading:** `world_happiness_clustering.ipynb` is a suggested clean name for your existing `Gerald G - Module 3 Unsupervised Learning Assignment.ipynb`. The World Happiness workbook was referenced by the notebook but was not available among the files I checked; obtain it from an authorized source and confirm that you can redistribute it. Remove or rewrite course-grading directions before publishing a polished portfolio version.

## How to Run
1. Add the authorized World Happiness workbook to `data/`.
2. Open the notebook in Jupyter Notebook or JupyterLab.
3. Update the Excel-reading path to `../data/WHR2018Chapter2OnlineData.xlsx` if using this layout.
4. Run cells in order. Results may vary slightly across library versions and K-means initializations.

## Limitations and Next Steps
The choice of 10 clusters follows the number of regions rather than an independent model-selection test. A future extension could compare values of `k` using silhouette scores, use a fixed `random_state` for reproducibility, and run hierarchical clustering as a complementary method.
