**Strengthening Government Transparency through Data Quality Control and Wrangling: A Cloud-Based Analytics Pipeline for City of Vancouver Council Voting Records**

**Exploratory Data Analysis**

**Project Description:** 

This project analyzes the City of Vancouver's council voting records using AWS cloud services to uncover trends in meeting frequency, voting behavior, and decision-making. By building an automated ETL pipeline with Amazon S3, Glue, and Athena, the project ensures clean, organized data is available for analysis. It supports government transparency by offering clear insights into how council members vote, what topics are most discussed, and how meetings are conducted—enabling data-driven governance and public accountability.

**Project Title:** Enhancing Government Transparency: Descriptive Analysis of Council Voting Records – City of Vancouver.

**Objective:** To design and implement a cloud-based analytics pipeline that ingests, cleans, transforms, and analyzes council voting data to:
  
  •	Identify voting trends across members and meeting types
  
  •	Detect agenda topics with high recurrence
  
  •	Support transparency and evidence-based decision-making using descriptive statistics

**Dataset:** 

**1. vote_date**

•	Type: Date

•	Description: The exact date when the council vote was held.

•	Example: 2025-02-27

**2. meeting_type**

•	Type: String

•	Description: The type of council meeting (e.g., Public Hearing, Regular Meeting).

•	Purpose: Helps identify the context in which the vote was conducted.

•	Example: Public Hearing

**3. vote_number**

•	Type: Integer

•	Description: A unique identifier or sequence number for each vote taken in a meeting.

•	Purpose: Useful for referencing individual votes and tracking voting order.

•	Example: 10548

**4. agenda_description**

•	Type: Text

•	Description: A summary or title of the agenda item being voted on.

•	Purpose: Provides context about the subject matter of the vote.

•	Example: CD-1 Rezoning: 1171 West 12th Avenue

**5. vote_start_date_time**

•	Type: Timestamp

•	Description: The exact date and time the vote began.

•	Purpose: Supports time-based analysis such as vote duration or scheduling patterns.

•	Example: 2025-02-27T18:54:38-08:00

**6. council_member**

•	Type: String

•	Description: The name of the council member who cast the vote.

•	Purpose: Allows analysis of individual voting behavior.

•	Example: Councillor P Fry

**7. vote**

•	Type: Categorical (String)

•	Description: The decision made by the council member. Common values include In Favour, Opposed, Abstain, or Absent.

•	Purpose: Central to understanding voting patterns and outcomes.

•	Example: In Favour

**8. decision**

•	Type: String

•	Description: The final decision outcome of the vote on the agenda item (e.g., Carried, Not Carried).

•	Purpose: Indicates whether the motion passed or failed.

•	Example: Carried

**9. dataset_id**

•	Type: String (Unique ID)

•	Description: A unique identifier for each record in the dataset.

•	Purpose: Used for internal tracking, versioning, and referencing each entry.

•	Example: cov_vote_2025_0001

**Methodology:**

**1.	Data Ingestion:** Uploaded to Amazon S3 under structured path: cov-raw-shw/Council-Voting-lst/year=2025/

**2.	Data Profiling & Cleaning:** AWS Glue DataBrew is used to detect and clean duplicates and validate data types. The Final cleaned dataset had 624 records

**3.	Data Transformation:** AWS Glue Studio ETL job created to summarize meeting frequencies, vote patterns, and agenda topics

**4.	Data Cataloging:** Transformed dataset cataloged in AWS Glue under cov_trf_system, stored in Parquet format

**5.	Query & Analysis:** Amazon Athena is used for SQL-based descriptive analysis (vote averages, meeting type distribution, etc.)

**6.	Data Governance & Monitoring:** KMS encryption, S3 versioning, CloudWatch dashboards, and CloudTrail enabled for auditing and security.

**Recommendations:**

Here are 10 key recommendations for the Descriptive Analysis of City of Vancouver – Council Voting Records project:

**1. Enable Time-Series Analysis**: Analyze voting trends across multiple years to identify seasonal or long-term patterns in council decisions.
   
**2. Use Advanced Data Visualizations**: Implement Amazon QuickSight dashboards to visualize vote distributions, member participation, and agenda category trends.
   
**3. Automate Alerts for Data Issues:**  Integrate AWS Lambda and SNS to trigger alerts on data quality failures, missing records, or unusual voting behavior.

**4. Integrate External Data Sources:** Combine council records with public sentiment, citizen feedback, or policy outcomes for enriched insights.

**5. Partition Data for Performance:** Partition Athena tables by `vote_year` and `meeting_type` to improve query speed and efficiency.

**6. Apply Metadata for Deeper Analysis:** Add attributes like political affiliation, district, or vote type to enable detailed breakdowns of voting behavior.
  
**7. Enhance Data Governance and Security:** Use IAM roles, KMS encryption, S3 bucket policies, and versioning for secure and compliant data handling.

**8. Highlight Data Anomalies in Reports:** Identify and report on spikes in abstentions, absences, or conflicting voting patterns for deeper transparency.

**9. Scale the Pipeline for More Datasets:** Plan to include related datasets (e.g., budgets, rezoning applications) and manage them using AWS Lake Formation.

**10. Share Results with Stakeholders:** Publish insights through dashboards or summary reports to support public transparency and informed decision-making by city officials.

**Tools and Technologies:**

•  Amazon S3 – Storage for raw and processed data

•  AWS Glue (Studio & DataBrew) – ETL transformation and cleaning

•  AWS Glue Data Catalog – Metadata management

•  Amazon Athena – SQL-based analysis

•  AWS KMS – Encryption

•  Amazon CloudWatch – Monitoring and dashboarding

•  AWS CloudTrail – Activity logging

•  Amazon SNS – Optional alert notifications

•  Draw.io – Architecture diagram creation

**Deliverables:**

•  AWS Architecture Diagram

•  Cleaned and cataloged dataset (Parquet format)

•  ETL pipeline in AWS Glue Studio

•  SQL query results and descriptive statistics via Amazon Athena

•  CloudWatch monitoring dashboard

<img width="275" alt="image" src="https://github.com/user-attachments/assets/c14b3056-db76-4eb2-aeb4-d011c49eec7c" />

**Data Wrangling**

**Project Description:** This project focuses on data wrangling of the City of Vancouver's council voting records to ensure the dataset is accurate, complete, and structured for meaningful customer (citizen) analytics. The goal is to clean and transform the dataset to support insights on council member performance, meeting efficiency, public engagement patterns, and voting trends—enabling transparency and informed civic participation.

**Project Title:** Data Wrangling for Customer Analytics: Council Voting Records – City of Vancouver.

**Objective:** To clean, standardize, and prepare the council voting records dataset for downstream analytics that highlight voting behaviors, meeting trends, and decision-making transparency. The wrangled data supports dashboarding, policy review, and citizen engagement through accurate and accessible civic insights.

**Background:** The City of Vancouver publishes council voting data to promote transparency. However, raw datasets often contain duplicates, inconsistent formats, and missing or misclassified data, making analysis difficult. For effective citizen-facing analytics and governance, the dataset must undergo thorough data wrangling to improve its reliability and usability.

**Dataset:**

•  Source: City of Vancouver Open Data Portal

•  Year: 2025

•  File: council-voting-records.csv

•  Total Rows: 656 (624 after cleaning)

•  Key Columns: vote_date, meeting_type, vote_number, agenda_description, vote_start_date_time, council_member, vote, decision, dataset_id

**Methodology:**

**1.Data Collection:** Ingested raw CSV file into Amazon S3 (cov-raw-shw/) with structured year-based folder hierarchy.

**2.Data Profiling:** Used AWS Glue DataBrew to detect data quality issues such as missing values, duplicates, and inconsistent data types.

**3.Data Cleaning:** Removed 32 duplicate entries. Validated and standardized columns like vote, meeting_type, and vote_start_date_time. Addressed inconsistent naming and date/time formatting.

**4.Data Transformation:** Used AWS Glue Studio Visual ETL to categorize agenda topics, format fields, and structure the output for analysis.

**5.Data Storage:** Cleaned data stored in Parquet format under cov-trf-shw/Quality_Check/Passed/. Failed records stored under Quality_Check/Failed/ for auditability.

**6.Governance & Security:** Enabled bucket versioning, KMS encryption, and IAM access policies. Monitored using AWS CloudWatch and logged via AWS CloudTrail.

**Tools and Technologies:**

•	Amazon S3 – Secure storage

•	AWS Glue DataBrew – Profiling and cleaning

•	AWS Glue Studio – Data transformation pipeline

•	AWS Glue Data Catalog – Metadata management

•	Amazon Athena – Post-wrangling validation and querying

•	AWS KMS – Data encryption

•	AWS CloudWatch & CloudTrail – Monitoring and auditing

•	IAM – Access control

**Deliverables:**
**1.	Cleaned and Transformed Dataset:** A high-quality version of the council voting records, free from duplicates and inconsistencies, stored in Parquet format in Amazon S3 for efficient querying and future analysis.

**2.	Failed Records Log:** Entries that didn’t meet quality standards (e.g., missing data or invalid formats) were stored separately in a Failed/folder. This supports auditability and transparency in data processing.

**3.	Data Profiling and Quality Report:** A report generated using AWS Glue DataBrew summarizing issues found (like missing values or duplicates), helping to track data health before and after cleaning.

**4.	ETL Pipeline Diagram and Logic:** Visual representation and configuration of the Glue Studio ETL job that shows how the raw data was cleaned, filtered, and transformed into usable analytics-ready format.

**5.	Athena SQL Scripts:** A collection of validated SQL queries used to test and extract insights from the cleaned dataset. These confirm that the wrangling process produced usable data.

**6.	Monitoring and Security Logs:** Logs and metrics from AWS CloudWatch (for Glue jobs and S3 activity) and CloudTrail (for tracking API calls), proving that the data pipeline was executed securely and successfully.

**7.	Final Summary Report:** A concise document that outlines the project goals, process, findings, and recommendations—ready for sharing with stakeholders, instructors, or including in your portfolio.

**Timeline:**

**Week	Activity**

Week 1	Data ingestion to S3, IAM & KMS setup

Week 2	Data profiling using AWS Glue DataBrew

Week 3	Data cleaning (duplicates, types, formats)

Week 4	Transformation using Glue Studio

Week 5	Data validation via Athena, store to S3

Week 6	Set up monitoring (CloudWatch, CloudTrail)

Week 7	Deliverables preparation (logs, scripts, report)

<img width="333" alt="image" src="https://github.com/user-attachments/assets/c0b57c02-d743-4932-b515-ab934be1256a" />

**Data Quality Control**

**Project Description:** This project focuses on implementing a robust Data Quality Control (DQC) framework for the City of Vancouver’s council voting records. The aim is to ensure the dataset is accurate, consistent, complete, and reliable for use in civic analytics and public transparency initiatives. The DQC process is built on AWS cloud services, combining automated validation, monitoring, and governance practices.

**Project Title:** Implementing Data Quality Control for Council Voting Records – City of Vancouver

**Objective:** To build a cloud-native, automated data quality control framework that identifies, corrects, and monitors data issues within the council voting records dataset. This ensures the dataset supports transparency, trust, and informed decision-making for governance and public engagement.

**Background:** Council voting data is a vital source of public accountability and policy analysis. However, the raw dataset may include duplicates, missing values, incorrect formats, or inconsistent labeling, which can distort insights. Ensuring the integrity and quality of this data is crucial before it’s used for analysis, reporting, or visualization.

**Scope:** The project will focus on the following key areas:

•	Data profiling for completeness, accuracy, and consistency

•	Data cleansing (e.g., removing duplicates, handling missing values)

•	Data validation using automated rules

•	Secure data governance (encryption, versioning, access control)

•	Real-time monitoring and alerting for quality assurance

•	Final documentation and training for long-term sustainability.

**Methodology:**

**Phase 1:** Data Ingestion & Storage (Week 1)

•	Upload raw CSV dataset to Amazon S3 (cov-raw-shw/)

•	Configure S3 versioning, encryption (KMS), and IAM policies

**Phase 2:** Data Profiling (Week 2)

•	Use AWS Glue DataBrew to assess data completeness, uniqueness, and formatting

•	Identify null values, format mismatches, and duplicate records

**Phase 3:** Data Cleaning (Weeks 3–4)

•	Remove 32 duplicate records

•	Fill or flag missing fields (e.g., vote, decision)

•	Standardize categorical fields (vote, meeting_type) and timestamp formats

**Phase 4:** Data Validation (Week 5)

•	Create validation rules using Glue (e.g., all vote_number must be numeric, vote must be from approved list)

•	Run validation scripts using Athena to confirm integrity

**Phase 5:** Data Monitoring & Protection (Week 6)

•	Enable AWS CloudWatch to monitor ETL and data changes

•	Use AWS CloudTrail for API and access logging

•	Set up optional SNS alerts for failed data checks

**Phase 6:** Reporting & Documentation (Week 7)

•	Generate dashboards and quality reports

•	Summarize key quality KPIs (e.g., error rate, completeness %)
 
**Deliverables:**

•  Cleaned and validated dataset stored in S3 (cov-trf-shw/)

•  Failed record logs for audit trail

•  Data quality metrics report (duplicates, missing values, format issues)

•  Data validation rules and results

•  Monitoring dashboard via CloudWatch

•  CloudTrail logs for audit purposes

•  Final project report with documentation

•  SNS notification setup for quality alerts

**Timeline:**

**Week	Activity**

Week 1	S3 ingestion, IAM policy setup, encryption

Week 2	Data profiling using Glue DataBrew

Week 3–4	Data cleaning and transformation

Week 5	Validation rule setup and Athena queries

Week 6	Enable CloudWatch, CloudTrail, and alerts

Week 7	Reporting, metrics, and project documentation

<img width="368" alt="image" src="https://github.com/user-attachments/assets/3883514e-8cb3-4b21-9d7f-c74378bde0d0" />

**Course Completion Badge**

[AWS_Academy_Graduate___AWS_Academy_Cloud_Foundations_Badge20250327-27-ekvp8p.pdf](https://github.com/user-attachments/files/19480044/AWS_Academy_Graduate___AWS_Academy_Cloud_Foundations_Badge20250327-27-ekvp8p.pdf)





