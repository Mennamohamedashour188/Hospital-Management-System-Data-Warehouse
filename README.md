Hospital Data Warehouse Project
Overview
This project presents the design and implementation of a Data Warehouse (DWH) for a hospital system. The objective is to transform raw transactional healthcare data into structured, analyzable data that supports decision-making.

The system is based on a dimensional modeling approach and implemented using SQL Server and SSIS.

Source System (OLTP)
The source system represents the operational database of a hospital and contains transactional data.

Main tables:

Patients: demographic information about patients
Encounters: each visit or interaction between a patient and the hospital
Procedures: medical procedures performed during encounters
Organizations: hospital or healthcare providers
Payers: insurance companies
Each encounter represents a complete event that may include multiple procedures and is associated with a patient, an organization, and a payer.

Business Objectives
The data warehouse is designed to answer the following analytical questions:

Encounters Overview
How many total encounters occurred each year?
For each year, what percentage of encounters belongs to each encounter class (ambulatory, emergency, inpatient, wellness, urgent care, outpatient)?
What percentage of encounters lasted more than 24 hours versus less than 24 hours?
Cost and Coverage Analysis
How many encounters had zero payer coverage, and what percentage of total encounters does this represent?
What are the top 10 most frequent procedures performed and their average base cost?
What are the top 10 procedures with the highest average base cost and how often were they performed?
What is the average total claim cost for encounters by payer?
Patient Behavior Analysis
How many unique patients were admitted each quarter over time?
How many patients were readmitted within 30 days of a previous encounter?
Which patients had the highest number of readmissions?
Data Warehouse Architecture
The solution is structured into three layers:

Source Layer
Contains raw transactional data from the hospital system.

Staging Layer
Used as an intermediate layer to prepare data before loading into the warehouse. It is responsible for basic transformations such as:

Standardizing formats
Cleaning data
Preparing fields for dimensional modeling
Data Warehouse Layer
The data warehouse follows a Star Schema design.

Fact Tables
F_Encounters
Represents each hospital encounter at the encounter level.

It is used to analyze:

encounter volume
encounter duration
distribution of encounter types
overall cost per visit
Key measures include:

Base_Encounter_Cost
Total_Claim_Cost
EncounterDurationHours
F_Procedures
Represents each medical procedure performed during encounters.

It is used to analyze:

procedure frequency
procedure cost
Key measures include:

Base_Cost
ProcedureDurationMinutes
F_Insurance
Represents the financial aspect of each encounter from the payer perspective.

It is used to analyze:

insurance coverage
patient financial responsibility
payer behavior
Key measures include:

Payer_Coverage
Coverage_Percentage
Patient_Responsibility
Dimension Tables
The warehouse includes the following dimensions:

DimPatient
DimDate
DimTime
DimOrganization
DimPayer
DimEncounterType
DimProcedure
Conclusion
This data warehouse enables structured analysis of hospital operations, financial performance, and patient behavior by organizing transactional data into a dimensional model suitable for reporting and analytics.
