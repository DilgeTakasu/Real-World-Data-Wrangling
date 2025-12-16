# Global Analysis of Alcohol-Related Mortality & Population Trends

#� Project Overview
In this project, I gathered, assessed, and cleaned data from the **World Health Organization (WHO)** and the **United Nations (UN)** to analyze alcohol-related health risks on a global scale. 

The primary goal was to create a tidy, high-quality master dataset by merging programmatic API data with manual archives, simulating a real-world data wrangling pipe

[**Click Here to View the Full Analysis Report (HTML)**](https://dilgetakasu.github.io/Real-World-Data-Wrangling/)line.
## 🔗 Rationale: Why These Two Datasets?

**Alcohol-related disease mortality is a fundamentally population-normalized indicator.** Population size is necessary to interpret mortality risk meaningfully across countries and years. Without demographic context, raw mortality values or inconsistent indicators can lead to misleading comparisons. 

> **Therefore, combining WHO mortality data with UN population estimates allows for standardized, comparable public health insig.**

## 📊 Datasets & Gathering Methods

I utilized two distinct data sources with different gathering techniques:

### 1. WHO Alcohol-Related Disease Mortality
* **Type:** JSON data retrieved from an online API.
* **Source:** World Health Organization (WHO) - Global Health Observatory (GHO) API.
* **Gathering Method:** Programmatic Gathering (HTTP GET).
    * The dataset was gathered programmatically by sending requests to the WHO GHO API.
    * **Step 1:** Queried the list of indicators to locate the correct code.
    * **Target Indicator:** `SA_0000001473` (Alcohol-Related disease mortality per 100,000 population).
    * **Step 2:** Retrieved data from the endpoint: `https://ghoapi.azureedge.net/api/SA_0000001473`.
    * **Step 3:** The JSON response was flattened into a tabular format using `pandas.json_normalize()` and filtered to include only country-level observations (excluding regional aggregates).

### 2. UN Population Dataset
* **Type:** Excel file (`.xlsx`).
* **Source:** United Nations Department of Economic and Social Affairs (UN DESA).
* **Gathering Method:** Manual Download.
    * Downloaded directly from the official UN World Population Prospects (WPP) Download Center.
* **Content:** Annual demographic indicators from the 1950s to 2023 for all UN-recognized countries.
* **Key Variables:**
    * Total Population & Population Density.
    * Male/Female Population breakdown.
    * Births, Deaths, Crude Birth/Death Rates.
    * Life Expectancy (at birth, age 15, 65, 80).
    * ility & Mortality Indicators.

## 🛠️ The Wrangling Process

### 1. Gather
Successfully implemented a hybrid approach using **`requests`** library for the WHO API and manual handling for the complex UN Excel structure.

### 2. Assess
Evaluated the data for Quality and Tidiness issues:
* **Quality Issues:**
    * Inconsistent country naming conventions between WHO (e.g., "United States of America") and UN (e.g., "USA") datasets.
    * Missing values in historical mortality records.
    * Data types (population figures stored as objects/strings).
* **Tidiness Issues:**
    * The UN dataset contained multiple variables (Year, Type, Variant) spread across header rows.
    * **Crucial Step:** Merging the two datasets to link mortality rates with specific population demographics.

### 3. Clean
* Standardized country names using a mapping strategy to ensure a successful merge.
* Converted data types (integers/floats) for accurate calculation.
* Handled missing values and removed non-country aggregates.
* **Result A clean, merged master dataset ready for analysis.

## 📈 Exploratory Data Analysis (EDA)

After cleaning, I analyzed the data to understand global trends.

**Research Focus:**
* How do alcohol-related mortality rates correlate with life expectancy?
* Are there visible trends when comparing population density to health o Nam update if different).
* `UN_Population.xlsx`: The raw Excel file.

## ⚙️ Tools & Libraries
* **Python 3**
* **Pandas** (`json_normalize`, `merge`, `read_excel`)
* **Requests** (API Interaction)
* **OpenPyXL** (Excel file handling)
* **Matplotlib / Seaborn** (Visualization)

---
*This project was completed as part of the Udacity Data Analyst Nanodegree.*