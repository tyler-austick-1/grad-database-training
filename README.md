# Module 1 Real-Time Market Data Ingestion
### Database solution: Time Series Database

#### Reasoning:
* Designed for high-volume writes.
    - Will work best with the High-volume frequency trading feeds and Bloomberg/Reuters API data.
* Efficient data compression.
    - Time-series databases use storage engines for optimised data compression.
* Schema flexibility
    - Some Time-series database implementations allow for semi-structured JSON which could be used with the social media sentiment streams.

**Additional note**: If a certain time-series database implementation does not allow for semi-structured JSON data, then instead a hybrid approach with a time-series database and a NoSQL database would be optimal.

# Module 2  Client Portfolio Management
### Database solution: RDBMS (Postgres) & NOSQL Document Store (MongoDB) & Text Search DB (Elastic Search)

#### Reasoning:
#### 1. Structured client transaction logs (ACID compliance required).  

Primary Transaction Database: **RDBMS (Postgres)**

Reasoning:
- ACID compliance requirement is explicitly stated
- Complex joins across portfolios needed
- Financial data requires strong consistency
- Built-in audit logging capabilities
- Mature and reliable for financial systems


#### 2. Portfolio performance reports (PDF/Excel)

Document Storage: **NOSQL Document Store (MongoDB)**

Reasoning:

- Flexible schema for varying PDF/Excel report formats
- Good performance for document retrieval
- Scalable for large numbers of reports
- Built-in GridFS for large files

#### 3. Regulatory compliance documents (SEC filings) 

Search Engine: **Text Search DB (Elastic Search)**

Reasoning:

- Fast full-text search across documents
- Advanced querying capabilities
- Good for regulatory compliance searches
- Efficient document indexing

# Module 3 Research & Analytics
### Database solution: Hybrid of RDBMS and NoSQL

Primary Database: **Document Database (e.g., MongoDB)**

- Handles unstructured text (equity research reports) efficiently
- Schema flexibility for evolving data types
- Good for full-text search capabilities
- Easy integration with Python/R

Supporting database: **RDBMS (e.g., PostgreSQL)** 

For structured data like analyst ratings and consistent relationships.

Object Storage: For alternate data such as satellite imagery and logs.
- Cheaper storage for large volume of files

# Module 4 Regulatory Reporting
### Database solution: Data Warehouse

#### Reasoning:
- Scale requirement: Petabyte-scale data handling is a natural fit for data warehouses, which are designed for large-scale analytical workloads
- Batch processing: Data warehouses excel at processing large batch uploads (CSV files) efficiently, which aligns with the overnight regulatory submission needs
- Query performance: Modern data warehouses (like Snowflake, Amazon Redshift) are optimized for fast analytical queries, capable of meeting the sub-10s response requirement for auditors
- Mixed workload handling: Data warehouses can effectively manage both batch processing and interactive query workloads through workload management features

# Module 5 Fraud Detection
*Not answered; missing team member.*