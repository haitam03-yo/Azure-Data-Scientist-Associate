
# Identify Your Data Source and Format

To train a machine learning model, we need to follow six key steps:

1. **Define the problem**
2. **Get the data**
3. **Process the data**
4. **Train the model**
5. **Deploy the model**
6. **Monitor the model** (track its performance)

## Data Extraction, Transformation, and Loading (ETL/ELT)

For data preparation, it's essential to extract data from its source, transform it, and load it into a serving layer. This process is often referred to as ETL (Extract, Transform, Load) or ELT (Extract, Load, Transform).

* **E** : Extract
* **T** : Transform
* **L** : Load

Before starting the ETL process, we must identify the **data source** and the  **data format** .

---

## Data Source

A **data source** is the origin where the data you need is stored. Examples include:

* A database
* A CRM (Customer Relationship Management) service
* A company-provided dataset
* Data that you may need to collect or purchase because it is not readily available

---

## Data Format

Based on the data source, you may encounter different data formats. It is important to understand the type of data format to handle it correctly. The three main data formats are:

1. **Structured / Tabular Data**
   * Data that adheres to a specific schema where each data point has the same set of features.
   * Usually stored in files like Excel spreadsheets or CSV files.
   * **Structure:** Columns represent features, and rows represent data points.
2. **Semi-Structured Data**
   * Data stored in formats like JSON.
   * Called semi-structured because data points can have different sets of features.
   * Example: Data collected from IoT devices, where some devices may report different metrics.
3. **Unstructured Data**
   * Data stored as files, such as images, videos, or audio.
   * Cannot be queried directly in the same way as structured data.

---

## Identify the Desired Data Format

Each machine learning model requires a specific data format as input. After identifying the **data source** and its  **original format** , you need to:

1. **Convert the data into the required format** for the model.
2. **Load the transformed data** into the serving layer, where it can be used to train the model or make forecasts.

---



# Choose how to serve data to machine learning workflows
