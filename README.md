# Exploratory-Data-Analysis-on-Melbourne-housing-data


Exploratory Data Analysis on Melbourne housing data using Python (Pandas, Seaborn, Matplotlib). Performed data sanity checks, univariate and bivariate analysis, missing value treatment, and outlier detection/treatment using the IQR method. 
An end-to-end exploratory data analysis (EDA) of Melbourne property sales. The goal is to uncover what drives property prices, to help with buying and selling decisions. Practiced as part of the Data Analytics Essentials program (Great Learning / UT Austin McCombs).

---

## Project Overview

The dataset contains **27,114 property sales** with **16 attributes** covering property features, location, and sale price. The notebook walks through the full EDA workflow: cleaning and validating the data, exploring distributions and relationships, and handling missing values and outliers.

## Dataset

| Column | Description |
|---|---|
| Suburb | Suburb where the property is located |
| Rooms | Number of rooms |
| Type | `h` house/cottage/villa/terrace, `t` townhouse, `u` unit/duplex |
| SellerG | Real estate agent who sold the property |
| Date | Date of sale |
| Distance | Distance from the CBD (km) |
| Postcode | Postcode of the area |
| Bedroom / Bathroom / Car | Number of bedrooms, bathrooms, and car spaces |
| Landsize | Land size (sq. m) |
| BuildingArea | Building size (sq. m) |
| YearBuilt | Year the building was built |
| Regionname | Region (e.g. Southern Metropolitan, Northern Victoria) |
| Propertycount | Number of properties in the suburb |
| Price | Sale price (AUD) |

## Analysis Workflow

1. **Data sanity checks**
   - Inspected head/tail, shape, and data types
   - Converted `Date` to datetime
   - Fixed `BuildingArea`, where `'missing'` and `'inf'` strings were stored as text, by converting them to `NaN`
   - Removed 11 duplicate rows
   - Reviewed summary statistics and categorical level counts
2. **Univariate analysis**: histograms, KDE plots, and boxplots for Distance, Landsize, BuildingArea, Price, and Rooms, plus counts by region
3. **Bivariate analysis**
   - Correlation heatmap
   - Engineered features: `Total Space` (rooms + bedrooms + bathrooms + car spaces), `Distance_bins` (Nearby / Moderately Close / Far), and `AgeofProp`
   - Price compared across distance bands, property age, property type, and region
4. **Missing value treatment**
   - Dropped one row where nearly all attributes were missing
   - Imputed `Bedroom`, `Bathroom`, `Car` with the group mean by Region and Type
   - Imputed `Landsize` with the group median by Region and Type
   - Dropped `BuildingArea`, `YearBuilt`, and `AgeofProp` because of very high missingness
5. **Outlier detection and treatment**: boxplot-based detection with the IQR method (1.5 × IQR whiskers)

## Key Insights

- **Price distribution is right-skewed**, with a mean (~AUD 1.05M) well above the median (~AUD 871K).
- **Larger properties sell for more**: Price correlates positively with rooms, bedrooms, bathrooms, and car spaces.
- **Distance matters**: properties closer to the CBD tend to be priced higher and show greater price variability.
- **Property type**: houses/villas (`h`) have the highest median price, followed by townhouses (`t`), then units/duplexes (`u`).
- **Region**: Southern and Eastern Metropolitan regions have the costliest properties.
- **Data bias**: about 98% of records are from Metropolitan regions, so conclusions for Victoria regions are less reliable.

## Tech Stack

- Python 3
- Pandas, NumPy
- Matplotlib, Seaborn
- Jupyter Notebook / Google Colab

## Repository Structure

```
├── ExploratoryDataAnalysis.ipynb   # Full EDA notebook
├── Melbourne_Housing.csv           # Dataset 
└── README.md
```

## How to Run

1. Clone the repository:
   ```bash
   git clone https://github.com/Muthu0209/Exploratory-Data-Analysis-on-Melbourne-housing-data.git
   ```
2. Install the dependencies:
   ```bash
   pip install numpy pandas matplotlib seaborn jupyter
   ```
3. Place `Melbourne_Housing.csv` in the project folder.
4. Open `ExploratoryDataAnalysis.ipynb`. The notebook was written in Google Colab and reads the data from a Google Drive path, so update the `pd.read_csv('Melbourne_Housing.csv')` path (and remove the `drive.mount` cell if running locally).

## Author

**Muthu** | Data Analyst  
[GitHub](https://github.com/Muthu0209)
