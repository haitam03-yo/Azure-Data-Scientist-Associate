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

# Choose How to Serve Data to Machine Learning Workflows

To access data when training machine learning models, it is essential to serve the data by storing it in a cloud data service. Storing data separately from your compute resources helps to:

* **Minimize costs**
* **Increase flexibility**

---

## Best Practice: Separate Compute from Storage

It is a best practice to separate data storage and model training into different services. This ensures that:

* If you need to shut down or scale a compute resource, your data remains safe and accessible.

---

## Storing Data for Model Training Workloads

For services like  **Azure Machine Learning** ,  **Azure Databricks** , and  **Azure Synapse Analytics** —which are commonly used for model training—you can serve and store data using these popular options:

1. **Azure Blob Storage**
   * Best for files, images, and other unstructured data.
2. **Azure Data Lake Storage (Gen 2)**
   * Similar to Blob Storage but designed for larger-scale, more advanced use cases and make use of the **hierarchical namespace** to have more granular control over who has access to what.
3. **Azure SQL Database**
   * Suitable for structured data that requires relational database support.

---

## Loading Data into These Solutions

To load data into one of these storage solutions, you can use a **pipeline** to perform the ETL (Extract, Transform, Load) process.

---


# Design a Data Ingestion Solution

To move and transform data, we use a  **pipeline** , which is a sequence of tasks that take raw data and process it into the desired result.

---

## Creating a Data Ingestion Pipeline

In the cloud (specifically Azure), there are three key services to build a data ingestion pipeline. These services allow for flexibility, scalability, and seamless integration:

1. **Azure Synapse Analytics**
   * Enables creating pipelines using a user interface (UI) or JSON definitions.
   * Supports adding transformations through the UI or programming languages such as Python, R, and SQL.
   * Offers multiple compute options:
     * **Serverless SQL pools**
     * **Dedicated SQL pools**
     * **Spark pools**
2. **Azure Databricks**
   * Ideal for a code-first approach.
   * Allows you to write code in notebooks and schedule them for execution.
   * Utilizes **Spark clusters** to distribute computational resources effectively, making it suitable for large-scale data processing.
3. **Azure Machine Learning**
   * Primarily designed for training machine learning models.
   * Can also be used for moving and transforming data.
   * Note: While Azure Machine Learning is useful, **Azure Synapse Analytics** and **Azure Databricks** are better suited for scalable data transformations as they distribute tasks across compute nodes.

---

## Designing a Data Ingestion Solution

One of the key benefits of using cloud platforms is their  **flexibility** . Depending on your needs, you can design an architecture combining multiple techniques and services.

### Example Workflow for a Data Ingestion Solution:

1. **Extract Raw Data**
   * Retrieve data from its source, such as a CRM system, IoT device, or other databases.
2. **Transform Data**
   * Use **Azure Synapse Analytics** to copy and transform the raw data.
3. **Store Prepared Data**
   * Save the processed data in **Azure Blob Storage** for easy access.
4. **Train the Model**
   * Leverage **Azure Machine Learning** to train your machine learning model using the prepared data.
