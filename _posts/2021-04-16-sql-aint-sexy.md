---
title:  "SQL ain't sexy"
date:   2021-04-16T02:15:00-0500
show_date: true
categories:
  - opinion
tags:
  - data science
  - jobs
  - sql
excerpt: "Do you need to know SQL if you want to play with data...in the real world?"
---

If you work with data in pretty much any capacity and don't already know or use SQL, it is most likely you have come across it in some form or the other in your job or in job postings when looking for a job.

## What's that squeal?
*See-Quel*...*Ess Cue Ell*...*Structured Query Language*.

But please don't "squeal."

SQL is a language for manipulating and querying data in relational databases. SQL has been around since the 1970s. Yes it is old! And yes it is still used...widely used!

IBM scientist [Edgar F. Codd in his seminal 1970 paper proposed a relational model for data management](https://www.seas.upenn.edu/~zives/03f/cis550/codd.pdf). Building upon Codd's work, in the early 1970s [Donald D. Chamberlin and Raymond F. Boyce at IBM first proposed an English-like language for accessing and modyfing data in a relational database](https://researcher.watson.ibm.com/researcher/files/us-dchamber/sequel-1974.pdf). The birth of SQL. 

Relational databases are stacks of information organized in tables containing rows (records) and columns (fields), with rules dictating how best to organize repeating information and relationships. SQL enables you to communicate and interact with relational data using structured syntax and commands.

In 1986 SQL became a standard of the American National Standards Institute (ANSI) and of the International Organization for Standardization (ISO) in 1987.

## Do you really need to know SQL?
It is 2021. So, if SQL is so old and there are all these modern skills to be had, do you really need to know SQL? Shouldn't you just develop your toolkit with cool and shiny objects like R, Python, Julia, Scala, Spark, (enter language/software/tool of choice)?

Just to be clear, I love working with R and Python. Fundamental proficiency in these (or similar) is absolutely necessary and immensely beneficial. And I truly enjoy learning or discovering yet another thing I can do with these languages or learning yet another (preferably open source) language or software. These languages are also wonderful in how much you can do with such little coding.

But I think knowing various data manipulation and analysis tools and not knowing SQL is kind of incongruous if not somewhat paradoxical.

## Nice to have
I have looked through a lot of data science and quantitative analysis job postings over the past 10 years that required proficiency in languages like R and/or Python but listed SQL as "*nice to have*." This combination always suprises me and I have never really understood the logic.

Invariably, organizations have data warehouses, which have databases. This is how it has been since the 1980s. While many other types of database management systems have evolved since, relational databases are still ubiquitous. And so, if you might need to work with relational databases, you should know SQL. For a data scientist or any type of data analyst, I think knowledge in SQL is foundational for understanding the how and why of data modeling and data architecture not only in databases, but in general.

## When do you need SQL?
A whole lot of times.

- More often than not, data resides in relational databases. Speak SQL and you can interact with them.
- If you have to do any kind of basic database administration — create new tables, add fields, build indexes, manipulate (insert, update, delete) data.
- If you have to troubeshoot someone else's SQL code.
- If you have to understand a database without clear documentation, you will have to figure it out using SQL.
- If you have to use any ETL tools (e.g., Informatica, SQL Server, Pentaho, Talend) to write or understand data transformation flows, you will be glad you know SQL.
- While SQL can get verbose and cumbersome to write compared to R and Python, in certain cases it is simply more efficient and powerful to use SQL to get the data you want, in the format you want, in the time you want.
- Often you cannot perform the analysis you need in memory. Get that data in a database, and it becomes far more efficient to push the processing onto the database. This is especially true when you are accessing large relational databases with several tables that need to be joined with complex queries. If you try to reshape, transform, or augment data as part of your workflow by accessing a database with R or Python or tools like Tableau, Qlik, or Alteryx, you will quickly find it unweildy and the performance and maintenance cost unattractive at best and unacceptable at worst.
- If you use analytics or reporting software like Tableau or IBM Cognos to query/import data from a database, in reality all it does behind the scenes is construct SQL code. Depending on complexity, this may not be the most efficient. Knowing SQL enables you to understand the underlying SQL code. Also, such queries are often linked to various configuration options in the front-end making it tedious for someone else to verify or test or debug (the person then has to be well versed with your software of choice instead of just SQL).

## When I first learned SQL
I first learned SQL using SQL*Plus Command-line on Unix (before the advent of friendly IDEs like PL/SQL Developer or TOAD or SQL Workbench). You wrote out your query on multiple lines to have some kind of formatting for reading ease, ending the final line with a semi-colon. But if you had a simple typo or constructed a non-executable query you got an error and you had to rewrite the entire query — the longer and complex the query, the more the hair-tearing frustration. Of course, you could write your query in a script file, then run the script, and if something didn't work edit the script, rinse, repeat... Oh, and the aggravation went to another level when working with the Microsoft Access flavor of SQL.

**BUT all of this taught you discipline**. You had to develop a sensibility of patient curiosity — take time and care in understanding how your data was organized, what exactly you were trying to do, and what pieces you had to put together in a query to get the results you wanted. A forced disciplined approach to working with data.


## How does SQL benefit you?
> "However, in the long-run, I highly recommend you at least learn the basics of SQL. It’s a valuable skill for any data scientist..." — *Hadley Wickham*


- **Relational databases are everywhere**
SQL is everywhere. Whether it's blue-chip companies like IBM or Walmart, the biggest names in tech like Netflix or Google, financial services giants like Citibank or Bank of America, government organizations like Dept. of Veterans Affairs or the U.S. military, defense contractor behemoths like Lockheed Martin or Northrop Grumman, and pretty much anywhere else where data is captured, stored, transformed, managed, and used, there are relational databases and their variants.

- **Universally spoken**
Because it has been around for so long and it is used widely, chances are you can find a solution to what you are trying to achieve or how to make a query more efficient in some online forum or SQL guide. Resources are plenty. It is also very likely you may find yourself working alongside colleagues who are proficient in SQL and you have to communicate with them in SQL.

- **Millions of rows of data**
SQL can handle 1,000 records or 100 million records. To explore, analyze, and narrow down dozens of columns and millions of rows that you need for building a model or performing targeted analysis, SQL is the shiny object that can make it happen.

- **Everything uses SQL or some-form of SQL**
SQL is pervasive. Relational, NoSQL, web development, iOS, Android — it is used in some form.

- **Dialects**
SQL has many flavors — Oracle, MySQL, PostgreSQL, T(ransact)-SQL.  Big data stores or non-relational databases eventually ended up with SQL-like query tools — CQL (Cassandra), SparkSQL, HiveQL, Elasticsearch SQL, SPARQL, and many more. Even Salesforce has Salesforce Object Query Language (SOQL), its own version of SQL. The better your understanding of SQL's capabiities, the easier it is to jump between dialects (even if you haven't used one before).

- **SQL demand isn't going away**
Look through data related jobs and SQL is likely a mentioned or required skill. Real-world SQL is not always well-written or pretty to read. Legacy environments are notorious for queries ranging from complex to convoluted. It's important to have the skills to understand what such code does and even make it better when needed.

- **Translating from SQL to R/Python**
Having the mindset to operate in a SQL world helps tremendously in translating to an R or Python (or other) world. The reverse (IMO) is much harder.


## OK, sounds like I should learn SQL
While SQL may appear to be old and worn out, with suggestions that it is marginally useful if not mostly inconsequential, something only database administrators or back end legacy data engineers need to know, it is most certainly not. SQL has not yet been displaced — if anything, it is still pretty much at the core of all things software and data.

For sure, languages like R and Python are incredible in their conciseness and capabilities in data munging, data transformation, statistics, and machine learning. These types of languages make analytics easier and effective in many ways. They are essential in your analytics toolkit. But I view these and SQL as complementary, not competing.

SQL has stood the test of time. Data invariably responds to some dialect of SQL. So, to listen to and make sense of what data is saying, you should be able to speak SQL. May not be the coolest thing around, but definitely a skill ~~nice~~ *great to have*.
