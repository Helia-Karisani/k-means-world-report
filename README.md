## K-Means Clustering on World Happiness Data

### Project Overview

This project applies **K-Means Clustering** to the *World Happiness Report* dataset to find groups of countries with similar social and economic characteristics.
Using factors like GDP, social support, and healthy life expectancy, the notebook explores how countries cluster based on happiness-related metrics.

---

### Dataset

**File:** `happiness_report.csv`

| Feature                        | Description                          |
| ------------------------------ | ------------------------------------ |
| `Country or region`            | Name of the country                  |
| `Score`                        | Overall happiness score              |
| `GDP per capita`               | Economic production per person       |
| `Social support`               | Perceived social support in society  |
| `Healthy life expectancy`      | Average life expectancy              |
| `Freedom to make life choices` | Individual freedom index             |
| `Generosity`                   | Measure of social generosity         |
| `Perceptions of corruption`    | Trust in government and institutions |

---

### Steps and Methods

1. **Data Import & Cleaning**
   Loaded and inspected the dataset with `pandas` and removed unused columns.

2. **Exploratory Data Analysis (EDA)**
   Plotted feature distributions and correlations with `matplotlib` and `seaborn` pairplots.

3. **Data Scaling**
   Standardized features with `StandardScaler` so they have equal weight in clustering.

4. **Elbow Method**
   Chose the number of clusters (`k ≈ 3`) using the Within-Cluster Sum of Squares (WCSS).

5. **K-Means Clustering**
   Applied `KMeans(n_clusters=3)` to group the countries.

6. **Cluster Analysis**
   Looked at the cluster centers and their feature patterns.

7. **Geographical Visualization**
   Made a **choropleth map** with `plotly` to show the clusters on a world map, using the `azimuthal equal area` projection.

---

### Key Findings

* **Cluster 0:** High GDP, strong social support, high life expectancy, low corruption (most developed countries).
* **Cluster 1:** Medium GDP and social support, moderate life expectancy (transitional economies).
* **Cluster 2:** Low GDP, lower social support, high corruption (developing countries).

---

### Technologies Used

* Python 3
* pandas, numpy
* matplotlib, seaborn
* scikit-learn
* plotly

---

### Choropleth Map Code

```python
data = dict(type='choropleth',
            locations=happy_df_cluster["Country or region"],
            locationmode='country names',
            colorscale='RdYlGn',
            z=happy_df_cluster['cluster'],
            text=happy_df_cluster["Country or region"],
            colorbar={'title':'Clusters'})

layout = dict(title='Geographical Visualization of Clusters',
              geo=dict(showframe=True, projection={'type':'azimuthal equal area'}))

choromap = go.Figure(data=[data], layout=layout)
iplot(choromap)
```

---

### File Structure

```
├── happiness_report.csv
├── K-Means clustering-world-report.ipynb
└── README.md
```

---

### How to Run

1. Clone the repository:

   ```bash
   git clone https://github.com/Helia-Karisani/k-means-world-report.git
   cd k-means-world-report
   ```
2. Install the libraries listed above.
3. Open the notebook:

   ```bash
   jupyter notebook "K-Means clustering-world-report.ipynb"
   ```
4. Run all cells.
