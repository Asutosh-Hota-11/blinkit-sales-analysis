# Blinkit Sales Analysis \| Python EDA

An exploratory data analysis project examining Blinkit's sales
performance across product categories and outlet characteristics. The
notebook uses Python and data-visualization libraries to calculate key
performance indicators (KPIs), clean inconsistent category labels, and
visualize sales patterns.

> **Project brief:** The supplied PowerPoint defines the business
> requirements and specifies the KPI cards and charts to build. It
> mentions Power BI as the intended reporting tool. The supplied
> notebook implements the analysis and visualizations in Python using
> Pandas, Matplotlib, and Seaborn.

## Business Objective

Conduct a comprehensive analysis of Blinkit's sales performance,
customer satisfaction, and inventory distribution to identify insights
and opportunities for optimization using KPIs and visualizations.

## KPIs

The notebook calculates the following measures:

  -----------------------------------------------------------------------
  KPI                     Meaning                 Notebook calculation
  ----------------------- ----------------------- -----------------------
  Total Sales             Overall revenue         `df['Sales'].sum()`
                          generated from items    
                          sold                    

  Average Sales           Average sales value per `df['Sales'].mean()`
                          record                  

  Number of Items Sold    Number of non-null      `df['Sales'].count()`
                          records in the `Sales`  
                          column                  

  Average Rating          Average customer rating `df['Rating'].mean()`
  -----------------------------------------------------------------------

**Metric note:** In the notebook, "Number of Items Sold" is calculated
using the count of non-null `Sales` records. Confirm whether this
matches the business definition of item count in the dataset before
publishing final KPI values.

## Visualizations and Business Questions

The PowerPoint brief lists these chart requirements. The notebook
creates corresponding Python visualizations:

1.  **Total Sales by Fat Content --- Pie Chart**\
    Compares sales contribution by item fat-content category. The
    notebook standardizes `LF` and `low fat` to `Low Fat`, and `reg` to
    `Regular`.

2.  **Total Sales by Item Type --- Bar Chart**\
    Compares total sales across item types and sorts categories from
    highest to lowest sales.

3.  **Fat Content by Outlet for Total Sales --- Grouped Bar Chart**\
    Compares sales for `Regular` and `Low Fat` items across outlet
    location tiers. The PowerPoint asks for a stacked column chart; the
    notebook currently uses a grouped bar chart.

4.  **Total Sales by Outlet Establishment --- Line Chart**\
    Shows total sales grouped by outlet establishment year.

5.  **Sales by Outlet Size --- Pie Chart**\
    Shows each outlet-size category's share of total sales.

6.  **Sales by Outlet Location --- Horizontal Bar Chart**\
    Compares total sales across outlet location types. The PowerPoint
    specifies a "Funnel Map"; the notebook currently uses a horizontal
    bar chart.

## Tools and Libraries

-   **Python** --- analysis
-   **Pandas** --- data loading, cleaning, grouping, and aggregation
-   **NumPy** --- numerical operations
-   **Matplotlib** --- chart creation and formatting
-   **Seaborn** --- statistical visualization
-   **Jupyter Notebook** --- interactive development environment

## Repository Structure

Suggested GitHub repository layout:

``` text
blinkit-sales-analysis/
├── Blinkit Analysis.ipynb
├── Blinkit Analysis.pptx
├── blinkit_data.csv
├── README.md
└── requirements.txt
```

The notebook reads the dataset using the relative path
`blinkit_data.csv`. Keep the CSV in the same directory as the notebook,
or update the path in the notebook.

**Dataset availability:** The notebook references `blinkit_data.csv`,
but the CSV was not included among the files reviewed for this README.
Add it only if you have permission to share it; otherwise, explain how
to obtain the data from its source.

## How to Run the Project

### 1. Clone the repository

``` bash
git clone <your-github-repository-url>
cd blinkit-sales-analysis
```

Replace the placeholder with your actual repository URL.

### 2. Install dependencies

``` bash
pip install pandas numpy matplotlib seaborn jupyter
```

Or install from `requirements.txt` if you add the file.

### 3. Place the dataset

Put `blinkit_data.csv` in the project directory alongside the notebook.
If the dataset is stored elsewhere, change the path in the data-loading
cell.

### 4. Start Jupyter Notebook

``` bash
jupyter notebook
```

Open `Blinkit Analysis.ipynb` and run the cells from top to bottom.

## Data Cleaning

The notebook checks the unique values in `Item Fat Content` and
standardizes inconsistent labels:

``` python
df['Item Fat Content'] = df['Item Fat Content'].replace({
    'LF': 'Low Fat',
    'low fat': 'Low Fat',
    'reg': 'Regular'
})
```

This makes the categories more consistent for grouping and charting.

## Example: Calculate the KPIs

``` python
# Total Sales
total_sales = df['Sales'].sum()

# Average Sales
avg_sales = df['Sales'].mean()

# Number of non-null sales records
no_of_items_sold = df['Sales'].count()

# Average Rating
avg_rating = df['Rating'].mean()

print(f"Total Sales: ${total_sales:,.0f}")
print(f"Average Sales: ${avg_sales:,.0f}")
print(f"Number of Items Sold: {no_of_items_sold:,.0f}")
print(f"Average Rating: {avg_rating:,.1f}")
```

The currency symbol and number formatting above follow the notebook's
current output. Confirm the dataset's currency/unit before interpreting
the values.

## Key Deliverables

-   KPI calculations for total sales, average sales, record count, and
    average rating.
-   Sales comparison by item fat content and item type.
-   Sales analysis by outlet location tier, establishment year, and
    size.
-   Visualizations intended to support business review and identify
    areas for further investigation.

This README describes the implemented notebook and the supplied
requirements. It does not report specific numeric findings because the
source CSV was not available to independently calculate and verify them.

## Suggested Next Steps

-   Align the two charts that currently differ from the brief: use a
    **stacked column chart** for fat content by outlet and a suitable
    **map visual** for geographic sales if the required location fields
    support mapping.
-   If delivering in Power BI, recreate the requested visuals and KPI
    cards in a Power BI report.
-   Validate the definition of "Number of Items Sold" and use an
    item-quantity field if that is the intended business measure.
-   Add data-quality checks for missing values, duplicates, and
    inconsistent categories.
-   Add screenshots of the final dashboard or charts to the repository
    README.
-   Add a `requirements.txt` file and document the dataset source.

## Author

**Asutosh Hota**

## License and Data Use

Add a license if you want others to reuse your code. Check the dataset's
license and sharing terms separately before uploading the CSV. Licensing
your code does not automatically grant permission to redistribute the
data.
