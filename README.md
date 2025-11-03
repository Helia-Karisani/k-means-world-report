## 🌍 K-Means Clustering on World Happiness Data

### 📖 Project Overview

This project applies **K-Means Clustering** to the *World Happiness Report* dataset to uncover groups of countries that share similar social and economic characteristics.
By analyzing factors like GDP, social support, and healthy life expectancy, this notebook explores how nations cluster based on happiness-related metrics.

---

### 📊 Dataset

**File:** `happiness_report.csv`
The dataset contains the following key features:

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

### ⚙️ Steps and Methods

1. **Data Import & Cleaning**
   Loaded and inspected the dataset using `pandas`, removed unused columns, and handled scaling with `StandardScaler`.

2. **Exploratory Data Analysis (EDA)**
   Visualized feature distributions and correlations using `matplotlib` and `seaborn` pairplots.

3. **Data Scaling**
   Standardized features for equal weighting in clustering.

4. **Elbow Method**
   Determined the optimal number of clusters (`k ≈ 3`) using the Within-Cluster Sum of Squares (WCSS).

5. **K-Means Clustering**
   Applied `KMeans(n_clusters=3)` to form distinct country groups.

6. **Cluster Analysis**
   Identified cluster centers and interpreted their feature patterns.

7. **Geographical Visualization**
   Created a **choropleth map** using `plotly` to display clusters globally, with the `azimuthal equal area` projection for a planet-like appearance.

---

### 🧠 Key Findings

* **Cluster 0:** High GDP, strong social support, high life expectancy, low corruption — *most developed countries*.
* **Cluster 1:** Medium GDP and social support, moderate life expectancy — *transitional economies*.
* **Cluster 2:** Low GDP, lower social support, high corruption — *developing nations*.

---

### 🛠️ Technologies Used

* **Python 3**
* **pandas**, **numpy**
* **matplotlib**, **seaborn**
* **scikit-learn**
* **plotly**

---

### 📸 Visualization Example

```python
# Example: Choropleth Map of Clusters
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

### 🧩 File Structure

```
├── happiness_report.csv
├── K-Means clustering-world-report.ipynb
└── README.md
```

---

### 🚀 How to Run

1. Clone the repository:

   ```bash
   git clone https://github.com/yourusername/world-happiness-kmeans.git
   cd world-happiness-kmeans
   ```
2. Install dependencies:

   ```bash
   pip install -r requirements.txt
   ```
3. Open the notebook:

   ```bash
   jupyter notebook "K-Means clustering-world-report.ipynb"
   ```
4. Run all cells to reproduce results and plots.

