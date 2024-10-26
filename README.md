# SoberEats Data Warehouse and Analytics Project

## Overview
SoberEats is a leading food delivery application in the United States, known for its seamless interface and personalized recommendations. This project aims to build a robust Data Warehouse to enable detailed analytics, improving data-driven decision-making and enhancing customer experience. By integrating a Data Warehouse with SoberEats, the project aims to streamline operations and generate valuable insights for strategic business decisions.

## Objectives
- Create a Data Warehouse to store comprehensive historical data from SoberEats.
- Enable analysis of order patterns, delivery efficiency, customer preferences, and more.
- Use the data for operational insights and strategic business decisions.
- Implement ETL (Extract, Transform, Load) pipelines for data processing.
- Provide dashboards and reports using OLAP queries for visualization.

## Data Model
### Operational Database
- A relational model storing details of customers, restaurants, delivery agents, orders, and menu items.
- Each customer is uniquely identified and categorized into:
  - **Regular Account**: Standard features.
  - **Premium Account**: Provides discount codes with expiry dates.
- Orders are linked to delivery agents, who have detailed information stored in the database.

![image](https://github.com/user-attachments/assets/740265dc-9e8b-41d3-bbd4-3d173bfa06be)


### Data Warehouse
- Designed as a Relational OLAP (ROLAP) model.
- Stores historical data for analysis, including:
  - **Menu Items**: Aggregated information on trending dishes and pricing.
  - **Order Patterns**: Analysis of peak order times, delivery efficiency, and agent performance.
  - **Customer Behavior**: User preferences, interaction data, and order history.
 
![image](https://github.com/user-attachments/assets/3c013970-d802-4d46-beea-987abdaf73c8)


## Database Implementation
- **Operational Database**: Implemented in PostgreSQL.
- **Data Warehouse**: A separate PostgreSQL database created to store aggregated data.
- **ETL Process**: Utilized Talend for ETL implementation, loading data from the operational database to the Data Warehouse.

![image](https://github.com/user-attachments/assets/9dfeb2c9-e196-493b-a9a5-6e9a985dc088)


## ETL Workflow
### Step 1: Preload of Geography and Time Dimensions
- **Country**, **State**, **City**, and **Time** dimensions loaded.
- Automated using Talend control flows.

![image](https://github.com/user-attachments/assets/4934b1cb-96a3-4b45-9dac-13c5b08c91f3)


### Step 2: Dimension Load
- Loaded dimensions for agents, accounts, addresses, restaurants, and menu items.
- Implemented using Slowly Changing Dimensions (SCD) Type 1, 2, and 3.
- Talend used for ETL with Type 2 updates, capturing changes over time.

![image](https://github.com/user-attachments/assets/b28d64ab-7089-48b9-b15c-d8104d48f745)
![image](https://github.com/user-attachments/assets/cc0d9946-c509-4584-b0a2-6dd4be5739fe)
![image](https://github.com/user-attachments/assets/1acdfaea-fd15-427f-ae7e-f716c77a4160)
![image](https://github.com/user-attachments/assets/11f8c6b0-8b59-4986-a136-03213c1e78f6)

### Step 3: Fact Load
- Incremental load of order data using Talend.
- Captured detailed order information, linking it to surrogate keys for dimensions.
- Incremental load handled using Talend context variables.

![image](https://github.com/user-attachments/assets/0a5fc7ed-852e-420e-a47b-a77b20fc5aa5)
![image](https://github.com/user-attachments/assets/f4b770ff-f4c0-4bc8-b2a2-d48c28a10b5f)
![image](https://github.com/user-attachments/assets/8f339f0d-ba2c-4e13-9234-b0f3a8314097)




## Analytical Queries (OLAP Operations)
1. **Total Order Amount by Month**
   - Aggregates total order amounts per month.
2. **Average Sales per Year**
   - Calculates the average sales of all order items per year.
3. **Top 10 Items by Total Order Amount**
   - Ranks items based on total order amount.
4. **Average Delivery Time per Month**
   - Provides insights on delivery efficiency.

## Dashboard and Analytics
Tableau was used to visualize the insights derived from the Data Warehouse. Key dashboards include:
- **Total Order Amount by Month**: Displays monthly order trends.
- **Top 10 Highest Selling Restaurants**: Analyzes restaurant performance by order count.
- **Sales by City**: Highlights the highest sales regions.
- **Average Delivery Time**: Shows the delivery efficiency trend over time.

![image](https://github.com/user-attachments/assets/a446a767-4af0-4699-887e-46e9cb7cd8b3)
![image](https://github.com/user-attachments/assets/44f69500-d6ea-4d95-b153-983f395c2f92)
![image](https://github.com/user-attachments/assets/64d32754-561d-46a0-a20a-9dc426cff2de)


## Key Performance Indicators (KPIs)
- **Order Trends**: Total sales and average delivery time analysis.
- **Customer Behavior**: Insights into user preferences and interaction data.
- **Restaurant Performance**: Analysis of popular dishes, peak order times, and restaurant efficiency.

## Technologies Used
- **Database**: PostgreSQL
- **ETL Tool**: Talend
- **Visualization**: Tableau
- **Data Warehouse Model**: MultiDim model and logical model
- **Data Modeling**: Relational OLAP

## Project Challenges
- Handling data consistency during incremental loads.
- Implementing various Slowly Changing Dimensions (SCD) types for different dimensions.
- Integrating OLAP queries with Tableau for comprehensive visualization.

## Future Work
- **Advanced Analytics**: Implement predictive models for customer behavior analysis.
- **Enhanced ETL Pipelines**: Optimize ETL workflows for faster data processing.
- **Scalability**: Migrate to cloud-based data warehousing solutions for improved scalability.


