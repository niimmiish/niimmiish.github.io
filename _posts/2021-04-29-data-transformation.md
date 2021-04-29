---
title:  "What is data transformation?"
date:   2021-04-29T17:10:00-0400
show_date: true
categories:
  - data management
tags:
  - data integration
  - data transformation
  - data management
  - data science
excerpt: "What is data transformation and why it is beneficial to understand its role in preparing data for end use."
---

In today's world, quantitative analytics has been elevated to *cool* by the firehose of readily available data in almost any domain, the myriad analysis and visualization tools (many with slick point-click-drag user interfaces), the label *data science*, and the plethora of data science courses. Historically, data analysis — be it statistics or applied mathematics or mathematical modeling — has required deliberate thought and investigation for understanding the problem at hand, obtaining, analyzing, and formatting the necessary data, and iterating through assumptions and hypotheses and modeling before arriving at conclusions or deploying a model into live use.


Now, most data science courses typically teach modeling or application of machine learning methods with ready-to-use data in text files easily stored on a laptop. A condensed walk through of training and testing data and using built in packages or libraries in R or Python for building a model, and voila! You have data science results. Unfortunately, the process of sourcing, cleansing, and transforming the data to make it ready-to-use is not considered. So, students acquiring data science skills in a learning setting are unaware of the thought and effort required in a real-world setting to convert raw data (almost always from several disparate sources) into ready-to-use data; that this effort is universally pegged at about 70%-80% of the work in a data project!

To stress this point further, there are two important realities in any organization:

- Data is messy. *Very messy*. Rarely organized and cleaned and ready-to-use.
- Data when voluminous and in different formats (databases, flat files, domain-specific formats, EDI,...), does not lend itself to being stored and used meaningfully on a local machine.

As a consequence, data scientists new to the world of enterprise scale data, often find themselves with little knowledge of the upstream data preparation activity involving the procurement and transformation of raw data that must happen before it can be used for modeling or reporting. For the analytics professional who wants to be really effective in not just the narrow discipline of modeling but with designing end-to-end data solutions, it is essential to understand the most intensive work in the data solutions chain — the role and content of data transformation in getting raw data ready for use.

## What is data transformation?

At a high level, a data project typically involves:
- **sourcing** raw data
- **transforming** sourced data
- **storing** transformed data
- **managing** stored data
- **using** stored data

**Data transformation** is the activity (collection of computing tasks) for converting data in the available structure and organization (*source* data format) into that desired for a given use (*target* data format). Data transformation is (almost always) the fundamental activity in the data integration and data management processes of a data, data-based, or modeling project.

## How is data transformation done?
Data integration (of which data transformation is a part) can be performed using a few different tools:

- **Dedicated data integration vendors** Vendor software such as Informatica, SQL Server Integration Services (SSIS), Oracle Data Integrator (ODI), Pentaho, Fivetran, Talend,...provide dedicated tools for different/all aspects of the data integration life cycle.
- **Modern tools** dbt (data build tool), AWS Glue, Python,...are increasingly found in open-source stacks and cloud infrastructure.

As part of the data integration process, data transformation will be performed by using vendor software, open source tools, cloud-based / cloud-friendly software, or scripting languages. Invariably, it will involve the use of SQL or a variant of SQL, especially when working with databases.

The three V's of data – *volume, velocity,* and *variety* – will influence your choice of software / tool along with considerations for maintenance, security, and ease-of-use.

Regardless of software or tool, the work of data transformation is a process from understanding the business and data characteristics and the requirements for the end state of the data to developing and executing code for converting the data from the raw state to the target state. That is, data transformation has multiple components.

## Components of data transformation
- **Source data analysis** — Understanding and using business knowledge to conduct data profiling and obtain data characteristics:
	- descriptive statistics
	- frequencies of values
	- missing data
	- data type inconsistency
	- invalid values
	- duplication
- **Data mapping** — Formalizing rules defining how target fields will be populated from source fields
	- one-to-one, calculated,  derived, aggregated, concatenated, abbreviated, and so on from one or more fields or records.
- **Deduplication** – Establishing rules for resolving which representation (typically one of two or more records) is the version of truth when there are multiple instances of the same or similar entity or object. (Duplicate records are very common in source data capture systems depending on their storage design and data generation triggers. For example, in a front end mortgage loan application system, every update may generate a new record but you may only want the latest record based on the most recent timestamp.)
- **Data quality**[^fnote1] – Driven by what is learned in source data analysis perform checks for:
	- *Consistency*: Does data represent the same information across different data sets or sources i.e., unconflicting information? Is it in sync?
	- *Conformity/Validity*: Does the data comply with definition and business rules: type, format, values, range?
	- *Accuracy*: Does the data correctly describe the real world object or event?
	- *Integrity*: Can the data be traced and connected through relationships across sources? (e.g., accounts to customers and transactions)
	- *Currency*: Does the data represent information correctly as of the required point in time? Is it up to date as of the time needed?
	- *Timeliness/Latency*: Is the data available when needed, with the least possible delay?
- **Data cleansing** – Define formal rules for cleaning data values based on findings from source data analysis. (For instance, the Account Type field of a bank's account data may have several different coded values, where multiple codes may represent the same account type. This may be due to previous acquisitions of other banks that may have used a different coding system. The cleaned Account Type field is populated based on a rule defined for translating these codes to a finite set of distinct Account Types)
- **Error Handling** –  Define design and storage of errors found in  data transformation processing:
	-  handle errors gracefully
	-  capture original data
	-  generate logs with reason, time, and location of error
	-  create feedback loops for error correction
- **Code development, execution, and testing**
	-  create code (e.g. mappings and workflows in Informatica, scripts in Python) for performing the various checks, cleansing, and transformation routines applying the defined data mapping rules
	-  execute the code in dev and test environments
	-  verify transformed data meets requirements (done by developers, testers, end users); integrate code with other processes and push to production

## Where does data transformation happen?
As I mentioned, data transformation is arguably the most important part of the data integration process. Data integration is conventionally known as Extract-Transform-Load or ETL:
- **Extract:** Obtain data from source systems (homogenous or heterogenous)
- **Transform:** Clean and convert data to desired format for intended used (based on data characteristics and business rules)
- **Load:** Insert and/or update data in the final storage container (e.g., target database used by an application, flat files)

The classic ETL process steps are:
- Initiate batch cycle (A batch cycle is where the end-to-end data integration process with its component tasks are executed on a large set of data, which may consist of newly added data or contain only new data.[^fnote2] The interval between batch cycles is dictated by the data volumes and the latency acceptable between data refreshes.)
- Drop / delete data not necessary for the new cycle
- Build necessary lookups and references for performing data quality and referential checks
- Extract source data
- Stage source data
- Validate staged data
- Log errors
- Transform staged data
- Load transformed data to target
- Archive source and target data for audit trail

The order of some of these steps may vary depending on design decisions (e.g., you may perform validation checks before staging or split them before and after staging.)

Data transformation is closely coupled with the Extract and Load steps of ETL. With vendor based tools, the workflow is usually seamless from E to T to L. You may introduce decoupling if raw data is extracted at a frequency different from that used for data transformation, but this is not the norm.

Modern data environments (typically cloud-based) may adopt Extract-Load-Transform architecture or ELT. This is particularly attractive when source data and data structures change often and data is voluminous with a lot of variety and complexity, and  the end use case is not pre-defined. It is also made easier to do with the maturity of cloud services and low cost of storage.

The main differentiator for ELT is that it pushes the data transformation step to the end. That is, all the raw data from source is loaded as-is first (Extract and Load steps). Data transformation (Transform step) is performed last based on the requirements of a given project. Some major benefits of using ELT are:
-  A single code base to extract and load all raw data that can be maintained independently. Decoupled from data transformation.
-  Different (and new) end uses enabled by the loaded data. Data can be transformed and consumed as per individual project need.
- Up stream source data changes or load failures do not affect downstream users of transformed data. Each end user can incorporate some / all changes by updating *their* data transformation step at a time of their choosing.

Nevertheless, the concepts of data transformation remain the same.

## Get transformed
There is a lot involved in any enterprise scale data or modeling project than just training and validating machine learning models and tuning parameters to improve the confusion matrix or ROC curve. If you want to grow into a broader role of designing data solutions that scale and interact with or manage  data architects, data modelers, data engineers, and database administrators, I'd say transform your thinking to learn about how data is transformed.

[^fnote1]: Data quality analysis of source data and incorporating checks in the data transformation stage are two distinct activities. The former guides data transformation strategy. The latter is necessary to ensure data is cleaned to the best extent possible, while errors and anomalies are trapped and not allowed to corrupt the transformed data.
[^fnote2]: Processing only new data in ETL is referred to as *delta* load strategy, but I won't be discussing it here.