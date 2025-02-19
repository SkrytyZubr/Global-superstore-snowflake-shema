# Global Superstore BI Snowflake shema

## Table of Contents
- [Project Overview](https://github.com/SkrytyZubr/Global-superstore-snowflake-shema?tab=readme-ov-file#project-overview)
- [Schema Design](https://github.com/SkrytyZubr/Global-superstore-snowflake-shema?tab=readme-ov-file#schema-design)
- [ETL Process](https://github.com/SkrytyZubr/Global-superstore-snowflake-shema?tab=readme-ov-file#etl-process)
- [Power BI Dashboards](https://github.com/SkrytyZubr/Global-superstore-snowflake-shema?tab=readme-ov-file#power-bi-dashboards)
- [Deployment](https://github.com/SkrytyZubr/Global-superstore-snowflake-shema?tab=readme-ov-file#deployment)
- [How to Use the Project](https://github.com/SkrytyZubr/Global-superstore-snowflake-shema?tab=readme-ov-file#how-to-use-the-project)

## Project Overview
This project involves the development of a data warehouse following the Snowflake Schema. The warehouse is built to support business intelligence (BI) analytics and reporting. The ETL process is handled using SQL Server Integration Services (SSIS), and data visualization is performed with Power BI.

### Schema Design
The data warehouse follows a **Snowflake Schema**, with a central fact table and multiple normalized dimension tables:
![image](https://github.com/user-attachments/assets/bffd1563-11ac-4e2e-a5da-6283b470f98a)

- **Fact Table:** `factSales`
- **Dimension Tables:**
  - `dimCustomer`
  - `dimCity`
  - `dimState`
  - `dimCountry`
  - `dimRegion`
  - `dimMarket`
  - `dimOrder`
  - `dimOrderPiority`
  - `dimProduct`
  - `dimShipping`
  - `dimShipMode`
  - `dimTime`
  - `dimMonth`
  - `dimQuarter`

## ETL Process (SSIS)

### Steps:
1. **Extract:** Data is extracted from the `Stage` table.
2. **Transform:** Data is cleaned, transformed, and mapped to dimension tables.
3. **Load:** Data is inserted into dimension tables and the fact table.
4. **Foreign Key Updates:** Using `SQL Task`, foreign keys are updated in dimension tables.

## SSAS Cube
A **multidimensional cube** is built using **SQL Server Analysis Services (SSAS)**.

- **Dimensions:** Built from snowflake schema dimension tables.
- **Attributes:** Relevant attributes are added from all related tables.
- **Measures:** Aggregated KPIs are defined in the cube.

## Power BI Dashboards

### Dashboard 1: **Sales Overview**
### Dashboard 2: **Customer & Market Analysis**
### Dashboard 3: **Order & Shipping Analysis**

## Deployment

### Local Deployment
- **SQL Server** for data storage
- **SSIS** for ETL
- **SSAS** for OLAP Cube
- **Power BI** for visualization


## How to Use the Project

1. Clone this repository:
   ```bash
   git clone https://github.com/SkrytyZubr/Global-superstore-snowflake-shema.git
2. Prepare the Environment
   - Ensure that Microsoft SQL Server, Visual Studio (Integration and Analysis extentions) are installed on your machine.
   - Restore the raw data into a staging database if necessary.
3. Update Connection Strings
   - Open the project in Visual Studio.
   - Navigate to the Connection Managers section in each SSIS package.
   - Update the connection strings to match your local SQL Server instance and database settings.
4. Run the SSIS Project
   - Execute the SSIS packages in the following order to initialize and populate the data warehouse:
       - Stage Data Load: Transfers raw data into the staging tables.
         ![image](https://github.com/user-attachments/assets/5fddeb59-7b19-428d-8666-3c8ab40f8ac5)
         
       - Dimension Tables Creation: Automatically creates dimension tables and fact.
         ![image](https://github.com/user-attachments/assets/9bc274ef-9234-41c6-b42b-3453c4edb714)

       - Filling out dimension tables (steps 3 to 6)
         ![image](https://github.com/user-attachments/assets/8f927ae8-8db3-4a3f-965e-d4f4edddde38)
         ![image](https://github.com/user-attachments/assets/1eed27c0-95c9-42f1-b0de-759d5f3f9d6f)

       - Fact Table: Ppopulates the fact table with data from dimensions and stage tables.
         ![image](https://github.com/user-attachments/assets/f68f3df0-4d81-4511-afb4-f1028cb19ae2)


5. Deploy and Use the SSAS Cube
   ![image](https://github.com/user-attachments/assets/a0d727d4-2143-48a0-99a2-1a1a651832a3)

   - Deploy the SSAS project to your Analysis Services instance.
   - Process the cube to make the data available for analysis.

6. Power BI Visualization
   ### Dashboard 1: **Sales Overview**
    - Total revenue, sales trends over time.
    - Top-selling products and categories.
   ![image](https://github.com/user-attachments/assets/fc962222-c823-49a5-8eed-2f4dc072e224)
   ### Dashboard 2: **Customer & Market Analysis**
    - Sales distribution by region, country, and customer segment.
    - Customer acquisition trends.
   ![image](https://github.com/user-attachments/assets/4493a074-2e8a-4891-9c04-c0f56b12f942)
   ### Dashboard 3: **Order & Shipping Analysis**
   ![image](https://github.com/user-attachments/assets/86362dce-28be-429b-b828-375ba55f82a1)

   - Open the provided Power BI file (.pbix).
   - Update the data source settings to match your database instance.
   - Refresh the data to view the updated visualizations.
