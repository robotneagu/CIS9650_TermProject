# Group 5 Term Project: Arizona Home Property Value Analysis 

<a href="https://colab.research.google.com/github/robotneagu/CIS9650_TermProject/blob/main/CIS9650_Group5_Term_Project.ipynb" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>

### Project Summary
This project uses the process of data cleaning, analytics, and visualization techniques to find pricing patterns in Arizona’s real estate. By comparing property types and analyzing different ZIP codes, our notebook provides a clear breakdown of how different factors influence the overall sale price of the properties of Pinal County, Arizona. 


**Overarching Research Question:** How have home purchasing habits changed over time in Pinal County, Arizona, and what drives property values across different types and locations?

Team Members:
- Daniel Ohebshalom
- Shivani Ramdeo
- Caroline Guirand
- Robert Neagu


## Dataset

**Source:** Pinal County, Arizona real estate transactions

**Format:** CSV

**Key Columns:**
- `sale_price`
- `sale_datetime`
- `property_zip5`
- `property_city`
- `property_type`
- `property_street_address`
- `source_url`

## Methodology

### 1. Data Cleaning & Preparation

**How to start**: Make sure the CSV file is in the same directory as the notebook.

Ensure you are running the correct libraries:

- `import Numpy as np`
- `import Pandas as pd`
- `import matplotlib.pyplot as plt`

**Cleaning the Data:**

1. Perform Data Exploration to find out which columns will be used and columns will NULL values. Then create a copy of the original data which will be cleaned.
2. Convert sale_datetime to a real datetime type
3. Convert property_zip5 from float to integer-like string (ZIP codes shouldn't have decimals)
4. Fill missing property_type with "Unknown". Reason: too much data would be deleted, leading to a weaker analysis.
5. Drop columns that are completely empty (100% missing values)
6. Remove rows where sale_price is missing or not positive

Note: While NULL values still exist in the data, they are in rows that are either not important or are unaffected like property_type when performing analysis.


### Data Analysis

We explored the trends and patterns of the provided csv file using analytics and visualizations
1. Sale Price Distribution
    - Created a histogram displaying the price ranges
    - Identified a right-skewed distribution
    - Noticed that most properties sell under $500k
2. Property type breakdown
    - Counted and graphed the top 10 property types
    - Residential properties dominated
    - Highlights the impact made by the “unknown” category
3. Average sale price by ZIP code
    - Calculated the mean sale prices for each ZIP code
    - Identified the top 10 most expensive ZIP code areas
    - Noticed a big geographic difference in pricing 
4. Average sale price by property type
    - Grouped by “property-type” and calculated those averages
    - Used a bar chart to visualize the highest valued property categories
    - Compared pricing across different property types



### 2. Exploratory Data Analysis (EDA) Results:

**Question 1**: What does the Distribution of Sale Prices look like across all properties?
- Discovered basic statistics of the total dataset after cleaning data using `.describe()`
- Created price bins grouping by property type using `np.array` and `bin_idx()` 
- Generated histogram using plt.figure mapping the distribution of sale prices up $1,000,000 
**Key Finding**:  Identified the Skewness and concentration of pricing both overall and by property type.

**Question 2**: Which Property Types are Most Common?
- Applied `value_counts()` function to count occurrences of each property type
- Extracted top 10 most frequent categories using `.head(10)`
- Visualized results as a bar chart showing property type distribution 
**Key Finding**: Identified which property types dominate the Pinal County housing market

**Question 3**: How Do Average Sale Prices Vary Across ZIP Codes?
- Used `groupby("property_zip5")` to partition data by geographic location
- Calculated mean sale price for each ZIP code group using `.mean()`
- Sorted results in descending order to identify most expensive neighborhoods
- Extracted top 10 most expensive ZIP codes using `.head(10)`
- Created bar chart visualization for geographic price comparison
**Key Finding**: Revealed significant geographic price variation, showing that location is a major driver of property values

**Question 4**: Which property types tend to have higher or lower sale prices?
- Calculated the average sale price by property type using `.groupby()` and `.mean()` afterwards
- Sorted in descending order to easily identify the most expensive property types
- Take the 10 most expensive using `.head()` and create a bar chart visualizing the result
**Key Finding**: Unknown properties tend to be the most expensive, though this is skewed by the very expensive unknown property. Excluding this, the most expensive property type is Multiple Unit with an average of ~$1.6 million.

### Model Analysis 
- Grouped the dataset by property type and ZIP code
- Calculated mean sale prices for each group
- Sorted results to identify the highest-valued categories
- Interpreted relationships between property characteristics and pricing 
- Supported findings through graphs and visualizations which highlighted how location and property type influenced and affected the market value

### Saving the Cleaned Data
Saved the cleaned dataset so future and further analysis can be done without repeating all the cleaning steps:
```python
output_path = "AZ_cleaned.csv"
clean.to_csv(output_path, index=False)
```

### How to run this project
1. Download the files:
`CIS9650_Group5_Term_Project.ipynb`
`AZ.csv`
2. Place the files in the same folder (If using CoLab, make sure to put it in the *root* folder, not content)
3. Open Jupyter Notebook
4. Run the notebook in sequential order
5. A cleaned dataset (`AZ_cleaned.csv`) will be automatically generated and downloaded to the user’s computer

### Requirements:
This project uses the following Python libraries: `numpy`, `pandas`, and `matplotlib`

### Files in this project:
- `CIS9650_Group5_Term_Project.ipynb` - Complete Jupyter Notebook with all analysis, visualizations, and findings.
- `AZ_cleaned.csv` - Cleaned dataset exported from the notebook for future analysis.
- `README.md` - This documentation file.
- [Download the CSV for used for this project](https://storage.googleapis.com/msba-online-data/CIS9650/Project%2015/AZ.csv) 
