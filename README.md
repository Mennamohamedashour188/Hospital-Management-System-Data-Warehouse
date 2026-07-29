# Hospital Management System Data Warehouse

## Overview

This project presents the design and implementation of a Data Warehouse (DW) for a hospital system. The objective is to transform raw transactional healthcare data into structured, analyzable data that supports decision-making.

The system is based on a dimensional modeling approach and implemented using SQL Server and SSIS.

## Source System (OLTP)

The source system represents the operational database of a hospital and contains transactional data.

### Main Tables

- Patients: demographic information about patients.
- Encounters: each visit or interaction between a patient and the hospital.
- Procedures: medical procedures performed during encounters.
- Organizations: hospitals or healthcare providers.
- Payers: insurance companies.

Each encounter represents a complete event that may include multiple procedures and is associated with a patient, an organization, and a payer.

## Business Objectives

The data warehouse is designed to answer the following analytical questions:

### Encounters Overview

- How many total encounters occurred each year?
- What percentage of encounters belongs to each encounter class?
- What percentage of encounters lasted more than 24 hours?

### Cost and Coverage Analysis

- How many encounters had zero payer coverage?
- What are the top 10 most frequent procedures?
- What are the top 10 procedures with the highest average base cost?

### Patient Behavior Analysis

- How many unique patients were admitted each quarter?
- How many patients were readmitted within 30 days?
- Which patients had the highest number of readmissions?

## Data Warehouse Architecture

The solution is structured into three layers:

### Source Layer

Contains raw transactional data from the hospital system.

### Staging Layer

Used as an intermediate layer to prepare data before loading into the warehouse.

Responsibilities include:

- Standardizing formats
- Cleaning data
- Preparing fields for dimensional modeling

### Data Warehouse Layer

The data warehouse follows a Star Schema design.

## Fact Tables

### F_Encounters

Represents each hospital encounter at the encounter level.

**Measures:**

- Base_Encounter_Cost
- Total_Claim_Cost
- EncounterDurationHours

### F_Procedures

Represents each medical procedure performed during encounters.

**Measures:**

- Base_Cost
- ProcedureDurationMinutes

### F_Insurance

Represents the financial aspect of each encounter from the payer perspective.

**Measures:**

- Payer_Coverage
- Coverage_Percentage
- Patient_Responsibility

## Dimension Tables

- DimPatient
- DimDate
- DimTime
- DimOrganization
- DimPayer
- DimEncounterType
- DimProcedure

## Technologies Used

- SQL Server
- SSIS
- Data Warehouse
- ETL
- Star Schema
- Dimensional Modeling

## Author

Menna Mohamed
