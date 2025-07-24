Of course. Here is a README for your script.

-----

# Databricks vs. CSV Impression Discrepancy Reporter

This is an interactive reporting tool designed to run in a Databricks notebook. It compares impression data from a Databricks database against impression counts provided in a user-uploaded CSV file.

The script generates a detailed discrepancy report, calculating both the overall variance and the specific differences for each matching ID.

## Features

  * **Interactive UI**: Uses `ipywidgets` to create a user-friendly interface directly within the notebook.
  * **Flexible Filtering**: Filter the Databricks query by Campaign ID and a specific date range.
  * **Customizable IDs**: Compare data based on different ID types, such as `placement.id`, `creative.id`, or `publisher.id`.
  * **Dynamic CSV Handling**: Users specify the exact name of the ID column in their uploaded file.
  * **Discrepancy Analysis**: Calculates absolute and percentage differences for each ID, and provides a total overall discrepancy percentage.
  * **Visual Reporting**: Displays the final report as a table, with an optional color-coded heatmap to quickly identify the largest discrepancies.
  * **Report Export**: Allows the user to download the final, detailed report as a CSV file.

-----

## Requirements

  * **Environment**: Must be run in a Databricks notebook environment that has a pre-configured `spark` session.
  * **Database Access**: Access to a Databricks table located at `dsm.measurement.vw_impressions`.
  * **Python Libraries**: `pandas`, `numpy`, `ipywidgets`, `jinja2`. The script includes a command to install `jinja2`.

-----

## CSV File Format

To ensure the script runs correctly, your uploaded file **must** adhere to the following format:

1.  It must be a **`.csv`** file.
2.  It must contain a column named exactly **`Impressions`**. The values in this column should be the impression counts.
3.  It must contain an **ID column** (e.g., `Placement ID`, `Creative ID`). The name of this column must be entered exactly into the `CSV ID Column` input field in the tool's UI. The values in this column will be used to match records from the Databricks query.

**Example CSV:**

```csv
Placement ID,Impressions,Other Data
12345,50000,abc
12346,75200,def
12347,10500,ghi
```

-----

## How to Use

1.  Place the entire script into a single cell in a Databricks notebook.
2.  Run the cell by selecting **"Run all"**. The interactive user interface will appear.
3.  **Input Campaign ID**: Enter the campaign ID you want to query.
4.  **Select Date Range**: Use the slider to define the start and end dates for the query.
5.  **Select DB ID Type**: Choose whether to group the Databricks data by Placement, Creative, or Site ID.
6.  **Input CSV ID Column**: Type the exact name of the ID column from your `.csv` file (e.g., `Placement ID`).
7.  **Toggle Heatmap**: Choose whether you want the final report table to have color-coded visuals.
8.  **Upload CSV File**: Click the button to upload your prepared `.csv` file.
9.  **Run Comparison**: Click the **`Run Comparison`** button to start the analysis.
10. **Review and Download**: The results will be displayed below the buttons. If the run is successful, click the **`Download Report`** button, and then click the generated link to save the report to your computer.
