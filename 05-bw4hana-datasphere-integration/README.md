# 05 — BW/4HANA to SAP Datasphere Integration  
SAP BW/4HANA – Hybrid On-Prem & Cloud Analytics Architecture

---

## Business Objective

Design and implement a hybrid enterprise analytics architecture integrating **SAP BW/4HANA** with **SAP Datasphere**, enabling cloud-based semantic modeling while preserving a governed on-premise enterprise data warehouse foundation.

The objective was to:

- Extract delta-enabled sales data from SAP S/4HANA  
- Implement LSA++ layered modeling in BW/4HANA  
- Model harmonized InfoObjects and reporting ADSOs  
- Build CompositeProvider for semantic unification  
- Create SAP HANA Calculation View (Star Join)  
- Replicate BW data into SAP Datasphere  
- Build Fact and Dimension Views in Datasphere  
- Deliver an Analytic Model for cloud analytics  

This implementation demonstrates a **hybrid enterprise data architecture** combining BW governance with modern cloud analytics modeling.

---

## Architecture Overview

![Architecture](images/architecture/05_bw4hana_to_datasphere_end_to_end_architecture.png)

### Hybrid Architecture Flow

SAP S/4HANA  
→ BW/4HANA Data Acquisition Layer  
→ LSA++ Data Warehouse Layer  
→ CompositeProvider (Semantic Layer)  
→ SAP HANA Calculation View (Star Join)  
→ SAP Datasphere Replication Flow  
→ Datasphere Fact & Dimension Modeling  
→ Analytic Model  
→ SAP Analytics Cloud  

---

## Source System Layer

### SAP S/4HANA – Sales Data

Source objects include:

- Sales Order Header  
- Sales Order Item  
- Customer Master  
- Material Master  
- ODP Delta Extraction (Operational Data Provisioning)

![ODP Delta DataSource](images/screenshots/02-odp-delta-datasource.png)

---

## Data Acquisition Layer (BW/4HANA)

### ADSO – Staging Layer

Responsible for:

- ODP DataSource (Delta Enabled)  
- Transformations (Field Mapping & Derivations)  
- DTP Execution (Delta Load)  
- Process Chain (Scheduling & Automation)  

![ADSO Layered Design](images/screenshots/06-adso-layered-design.png)

---

## Data Warehouse Layer (LSA++)

### BW/4HANA Modeling

- ADSO (Corporate Memory)  
- ADSO (Reporting / Data Mart Layer)  
- Harmonized InfoObjects  
  - Customer  
  - Material  
  - Organization  
  - Time  
  - Units / Currency  

![LSA Mapping](images/screenshots/04-lsa-layer-mapping.png)

---

## Semantic Layer (BW/4HANA)

### CompositeProvider

- Logical join of Sales Header & Item  
- Harmonized Key Figures  
- BW Query ready structure  

![End-to-End BW Flow](images/screenshots/01-bw-sales-end-to-end-flow.png)

---

## SAP HANA Semantic Layer

### Calculation View (Star Join Model)

- Fact: Sales (Header + Item)  
- Dimensions: Customer, Material  
- SQL/Semantic Consumption Ready  

![HANA Star Join](images/screenshots/08-hana-star-join-calcview.png)

---

## SAP Datasphere – Data Ingestion

### Replication Flow

Data replicated from BW/HANA into Datasphere:

- Sales Header → Local Table  
- Sales Item → Local Table  
- Customer Master → Local Table  
- Material Master → Local Table  

![Replication Flow](images/screenshots/09_datasphere_replication_flow_sales_data.png)

---

## SAP Datasphere – Modeling

### Fact View (Sales)

- Join Header + Item  
- Filters & Calculations  
- Sales Fact structure  

![Fact View](images/screenshots/10_datasphere_fact_view_sales.png)

---

### Customer Dimension

- Master Data Modeling  
- Key & Text Attributes  

![Customer Dimension](images/screenshots/11_datasphere_dimension_view_customer.png)

---

## SAP Datasphere – Analytics Layer

### Analytic Model (Sales Analysis)

Includes:

- Measures: Net Value, Cost, Margin  
- Associations: Customer, Material  
- Ready for consumption  

![Analytic Model](images/screenshots/12_datasphere_analytic_model_sales_analysis.png)

---

## Reporting & Validation

### BW Query Preview

![Sales Query Preview](images/screenshots/07-sales-query-preview.png)

Ensures reconcili
