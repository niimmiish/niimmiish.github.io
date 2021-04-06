---
title: " " # provide a title here if you want a link to show in the grid on the "Portfolio" landing page.
header:
  overlay_image: /assets/images/chris-yang-1tnS_BVy9Jk-unsplash.jpg
  caption: "Photo credit: [**Chris Yang**](https://www.unsplash.com)"
permalink: /portfolio/sanctionsscreening/
toc: true
toc_label: "Contents"
---

# Validating Sanctions Screening Systems
*March 1, 2021*

> <span style="color: #596275; font-size: 15px">I have worked extensively in the FinReg and RegTech space, specifically the development and validation of software and technology for anti-money laundering (AML), combating financing of terrorism (CFT), and identifying fraud and trading risk and irregularities. Pre 9/11, I built the first generation of financial crime behavior detection models at a pioneering start up, and subsequent iterations addressing the sweeping regulatory requirements of the USA PATRIOT Act of 2001.<br><br>
The technical aspects of my work include data preparation (exploratory analysis, visualization, building ETL pipelines, cleansing, aggregating and summarizing data, and statistical analysis),  model development, and validation. I have also built solutions for householding, segmentation, collating transactions, entity resolution, text extraction, address parsing, and name matching. I have used a variety of tools, but have a bias for SQL, R, Python, and Informatica.<br><br>
Due to the sensitive and proprietary nature of this work and client confidentiality agreements I cannot provide technical details or code I've used. Instead I discuss the regulatory drivers and conceptual aspects of development and validation.</span>

## Regulatory context 
In the United States, AML efforts can be traced from the Bank Secrecy Act (BSA) of 1970, leading up to the expansive USA PATRIOT Act of 2001 passed after 9/11, to the sweeping changes of the Anti-Money Laundering Act of 2020. These and other AML regulations require every financial institution (FI) to have an AML posture providing a reasonable ability to <span style="color: #4b6584; background-color: #ecf0f1"><span style="color: #2980b9">**define, detect, decide,** and **disclose**</span> suspicious activity and targeted entities of interest</span> and typically comprises:
- **Know Your Customer (KYC)**
  - Customer Identification Program (CIP)
  - Customer Due Diligence (CDD)
  - Enhanced Due Diligence (EDD)
  - Customer Risk Rating (CRR)
  - Beneficial Ownership (BO)
- **Transaction Surveillance**  
  - Transaction Monitoring (TM) (scenario alert generation)
  - <span style="color: #4b6584; background-color: #ecf0f1">**Sanctions screening**</span> (transaction filtering)
- **Review and Resolution**
  - Alert and case management
  - Audit history and records management


## What are sanctions?
The **Office of Foreign Assets Control** (OFAC) of the US Department of the Treasury administers and enforces economic and trade sanctions, many of which are based on international agreements between allied governments. OFAC is authorized by specific legislation to enforce transaction restrictions and freeze assets under U.S. jurisdiction.

<span style="color: #4b6584; background-color: #ecf0f1">OFAC sanctions aim to **prevent access to global financial systems** to actors who conduct and benefit from nefarious activities that pose a threat to US national security or to economic interests of the United States and its allies.</span> Such sanctions typically target geographical regions, governments, individuals, business entities, and major conduits of transportation including maritime vessels and aircraft.

OFAC sanctions must be complied with by all U.S. citizens and permanent resident aliens regardless of origin or location, all persons and entities located in the U.S., and all U.S. incorporated entities and their foreign branches. 

## OFAC SDN list
OFAC targets its enforcement efforts against countries and also against groups or entities that are not country-specific by publishing a list of Specially Designated Nationals (SDNs). SDNs are individuals, groups, and entities linked to targeted countries as well as terrorists, traffickers of prohibited goods or people, and others who are not necessarily affiliated to a country. 

The SDN list includes:
- Individuals and companies owned, controlled by, or acting on behalf of a sanctioned country
- Designated terrorist organizations, narcotics, prohibited goods, and human traffickers, entities involved with proliferation of weapons of mass destruction
- Companies, banks, and vessels related to sanctioned targets

## Sanctions screening solutions 
Financial institutions, and in general, any financial services provider --- a primary and necessary channel for money laundering --- are especially vulnerable and must be extra diligent in meeting their regulatory obligations towards sanctions screening.

FIs typically rely on vendor-based screening solutions to perform transaction filtering of their payment systems and entity screening of their customers, vendors, contractors, and employees to comply with sanctions regulations and mitigate exposure to financial penalties and reputation risk. The goal of transaction filtering and entity screening is to detect and prevent the use of the FI’s payment or money transfer systems by sanctioned entities. The solutions screen transactions and entities against watch lists such as OFAC SDNs, European Union Sanctions List, internal lists, and many more. 

### Challenges
- **Correct matches**: The fundamental challenge in sanctions screening is to <span style="color: #4b6584; background-color: #ecf0f1">**correctly identify and block suspicious transactions**</span> (*true positives*) while funneling legitimate transactions (*true negatives*) through the transaction processing stream without unnecessary delay  to achieve and sustain operational efficiency and customer satisfaction.
- **Frequent watchlist updates:** Watch lists change frequently based on new sanctions regimes, narrative (implicit) sanctions, changes in government policy, or updates to threat designation. A screening solution is required to keep up with the latest applicable regulatory requirements.
- **Variety of entries:** Watch lists have thousands of entries with regional characteristics, spelling variations, and abbreviations that are not exhaustive. To be effective, a screening solution must meet the demands of partial and fuzzy name matching without unduly compromising quality of hits.
- **Variable applicability:** Not all lists are applicable to all transactions. For example, a South Korea sanction list applicable to an FI's operations in Asia may not be applicable to transactions conducted in the FI's operations in France (the FI’s compliance policy and regional requirements determine the rules of conditional applicability). 

## How do sanctions screening systems work?
Sanctions screening or name-matching systems consist of components that together enable <span style="color: #4b6584; background-color: #ecf0f1">**comparison of data from two sources**</span> --- the <font color="#2980b9">data to be screened</font> (FI data streams) and the <font color="#2980b9">data to be screened against</font> (watch lists).

The key components are:
- **watch lists** (OFAC, EU, Bank of England, AUSTRAC, region-specific, country-specific, business-specific, internal)
- **text matching methods** (mathematical algorithms for determining if two pieces of textual data represent the same information)
- **algorithms** (programmatic processes or techniques utilizing string and text matching methods to screen an input data record against watch lists)
- **business rules and overrides** (conditional logic for screening, whitelisting or exception handling)
- **alert generation and management** (workflow for blocking transactions, creating cases, managing review actions and audit history, clearing transactions for processing)

These components collectively perform as a model using **quantitative methods**.

## Text and Name Matching Methods
For any entity matching or sanctions screening system, performance may be considered effective when it accurately matches input text or data values to listed entity information and correctly does not return a match when different. In the simplest scenario, an exact string match (name, passport id, bank identifier code) to a listed entity is a true match; if the string does not match exactly it is not.

However, payment messages such as SWIFT, CHIPS, FEDWIRE or other transactional data are rarely structured and cleansed to the extent that exact string matching techniques would suffice. It is common to have name variations due to spelling errors, missing characters or words, data input errors, use of initials instead of full names, and many other orthographic errors. While an exact name match between source data and a listed entity is the easiest kind of match, detecting fuzzy or proximate matches is extremely challenging. In fact, if measured exclusively within the constraints of exact string matching, it is unlikely that any system would perform well in identifying cases where there is any variation in the name or input string (which are very common in real world conditions) matching a corresponding listed entity.

Consequently, <span style="color: #4b6584; background-color: #ecf0f1">the strength of a screening system lies in its **ability in matching non-exact strings.**</span> The measure of a robust matching process is predicated on the underlying techniques that standardize and reformat data (such as remove punctuation, parse text, handle case, special characters, and white space, transliterate), which is then exposed to processing that can accomplish exact (deterministic) or fuzzy (probabilistic) matching.

- **Deterministic**: rule driven matching based on exact string match, exact identifier match, or exact match of multiple tokens within a data element
- **Probabilistic**: scoring or weighting of partial matches of multiple data elements based on mathematical computation of “distance” between two strings and likelihood of the strings being the same subject to a distance threshold, orthographic tolerance and correction, linguistic tolerance, phonetic tolerance, and more.

## Is that a match?
While deterministic matching is relatively straightforward to measure, probabilistic matching is much more difficult to get right and challenging to measure. Human evaluation on a case-by-case basis can differentiate between subtleties like the names *“Suleiman Hafiz”* and *“Soleyman Hafeez”* or *"Mary Ann Diaz"* and *"Marianne Dias."* Phonetically, the two are very close to a software capable of phonetic and linguistic tolerance matching. So, if the two strings are matched, did the software get the match correct or incorrect given the two are distinctly different and valid names?

<caption><span style="font-size: 15px; font-weight: bold">Match classification</span></caption>

|---------------------+---------------------------------------------------------------|
| Match Type          | Interpretation of input data in relation to watch list entity|
|:--------------------|:--------------------------------------------------------------|
| **True Positive**   | matched - relevant and posing high risk                       |
| **True Negative**   | not matched - not relevant and posing no risk                 |
| **False Negative**  | not matched - <span style="color: #c0392b">**missed**; should have been detected and posing highest risk</span> |
| **False Positive**  | matched - not relevant or posing no risk                      |
|---------------------+---------------------------------------------------------------|

Adding to the difficulty in measuring performance of screening systems are opposing problems of managing *false positives* and *false negatives*. The match classification in the table above shows the risk of identifying or missing a transaction as containing information matching a listed entity.  

False positives are quantified by alerts generated that are cleared by reviewers as non-issues. <span style="color: #4b6584; background-color: #ecf0f1">**False negatives** are transactions or entities that indeed should have been detected as a match to a listed entity but were not</span>, and so the transactions are allowed to go through processing or relationships with entities are not blocked. Failure in detecting such cases could lead to adverse consequences for the FI.

## Validating sanctions screening systems
According to Supervisory Guidance on Model Risk Management, [FRB SR 11-7](https://www.federalreserve.gov/supervisionreg/srletters/sr1107.htm){: style="color: #686de0"} / [OCC 2011-12](https://www.occ.treas.gov/news-issuances/bulletins/2011/bulletin-2011-12a.pdf){: style="color: #686de0"} , issued by the Federal Reserve and Office of the Controller of Currency, quantitative models (which sanctions screening systems are) must be validated (approved for use) by <span style="color: #4b6584; background-color: #ecf0f1">reviewing and assessing the rigor and soundness of **development, implementation, use,** and **governance**.</span>

The elements of a comprehensive validation of a sanctions screening system are:
    
  - Conceptual soundness (design, construction, rationale, configuration, and documentation of components)
  - Data mappings and data quality analysis (input data, watch lists)
  - Algorithms testing (matching methods)
  - Usage and governance (outputs, user feedback, updates, change management)
  - Ongoing monitoring & outcomes analysis (performance assessment, sensitivity to data changes, continued appropriateness)

## Model risks 

Sanctions screening models are subject to several risks dependent on model definition, data inputs, and use.

<caption><span style="font-size: 15px; font-weight: bold">Model risks</span></caption>

|-------------------------------+-----------------------------------------------+|
| Risk                          | Description                                    |
|:------------------------------|:-----------------------------------------------|
| Insufficient or wrong model structure for the stated name matching objectives | Narrow context of exact string matching v. broad context of fuzzy name matching both within a single data element but without consideration of other information on the data record being screened. |
| Incomplete or inconsistent name matching methods or algorithms | Different data characteristics based on entities (individuals, companies, geographical indicators, vessels) and based on regional, language, or social factors may not be sufficiently covered by model features. This introduces a risk that model may operate well only on data with specific characteristics and poorly on others. |
| Incorrect configuration of the system parameters or incorrect use of the system | The need for name matching appears in many business contexts like: online real-time transaction processing, regular; periodic scanning of names of customers, employees, or other related parties; on-demand scanning or matching needs driven by business processes (e.g., Know-Your-Customer). The underlying screening model must be configured to correctly meet all business needs. |
| Incomplete or inconsistent watch lists | Watch lists are published by regulatory bodies or obtained from third-party vendors and are an essential component of screening models. Therefore, timeliness, lack of maintenance, their incorrect exclusion or inclusion, and redundancy may significantly impact model performance. |
| Incorrect approach to the use and maintenance of exclusion rules | A sanctions screening or name matching model is unlikely to operate at 100% accuracy. Therefore, to minimize the risk of missing matches, the model is usually configured to generate more false matches. These false matches can be minimized by special purpose rules (defined by combining criteria using one or more input data value and listed entities), such that if a rule is met then a hit should not be generated. Such exclusion rules introduce a potential risk of incorrectly excluding data from being screened. |
| Incorrect, incomplete, or poorly formatted input data | As with any model, incorrect or incomplete data will heavily impact model performance. Even the best performing screening model cannot provide good outcomes (matches) if data is missing in the data record being screened or is in the incorrect data fields. For sanctions screening, improperly mapped source-to target data, and incomplete or missing data introduce performance risk. |

## How to review?

A. Analyze model development documentation and evidence
   1. **Model documentation** Assess the documented model purpose, assumptions, and limitations. Verify model inventory. Evaluate model purpose in context of applicable regulations and internal policies and procedures. Check consistency between documentation and configuration.
   2. **Risk Assessment** Analyze risk assessment documented by model owner.
   3. **Theoretical construction** Verify key assumptions, data, and specific mathematical calculations.
   4. **Model Controls** How does the model allow for: adequate tuning? sensitivity to inputs?

B. Review implemented components of the model
   1. **Input data components and related assumptions** Review input data—data dictionaries, data specification, data mapping, and ETL processes. Analyze segmentation characteristics related to business units and geographic indicators. Determine any relationships between qualitative and quantitative inputs. Identify data deficiencies and limitations.
   2. **Processing components** Analyze and assess implemented algorithms used by the model and by the data ingestion components. Review implemented controls and filters. Verify inclusion of risk factors. Understand triggers for high-risk outputs.
   3. **Reporting components** Review model results and their relationship to supplementary analysis provided by analysts’ review of model results. Compare model’s outputs with manual application (or alternately simulated application) of model’s logic, if feasible.
   
## How to test?
The basic approach for evaluating and validating performance of a name matching system involves the following:
- Design “bad” and “good” validation samples:
  + **Bad** sample --- test data based on names on watch lists (expect to match)
  + **Good** sample --- test data that is different from names on watch lists (expect not to match)
- Generate validation samples (including cases for exact match) by performing string alteration to achieve name variations simulating a variety of scenarios. 

The table below shows these name variations:

|-------------------------------+---------------------------------------------|
| Variation                     | Description                                 |
|:------------------------------|:--------------------------------------------|
| **Identical match**           | exact name of listed entity to be matched   |
| **Initialization**            | reduction of first, middle, or last name to its initial |
| **Concatenation**             | merging of multiple words                   |
| **Extraneous text**           | concatenation or insertion of non-relevant characters or punctuation into the name |
| **Truncation**                | loss of portion of the name                 |
| **Word order**                |changing the order of words in the name      |
| **Adjacent transposition**    | swapping of adjacent characters in the name (resembling typographical errors) |
| **Misspelling**               |spelling the words in the name incorrectly   |
|-----------------------------------------------------------------------------|
| **Phonetic**                  | replacement of words or portions of a word with similar sounding words (e.g., Soundex or Metaphone 3 algorithms, which are based on the English language)              |
| **Linguistic**                | changing the name to its equivalent in a different language |
| **Language sets**             | name in native character set                |
| **Transliteration**           | convert name from one alphabet (typically a language other than English) into similar sounding characters of another (typically English)  (e.g., 광민 transliterated from Korean is *“Kwangmin”*, افتخر transliterated from Arabic is *“Iftekhar”*)                                                       |
|-----------------------------------------------------------------------------|
| **Alternative**               | spelling the name differently but to an alternate, validly used one |
| **Missing or additional spaces, hyphens or other separators** | typographical errors, conversion between character sets, difference in punctuation                                                     |
| **Missing components**        | missing words (e.g., “Shariff” v. “Al-Shariff”) |
| **Titles, Honorifics, Ranks** | inclusion and exclusion of titles (e.g., “Sir”, “General”, “Hakim”, “Imam”, “Taewi”)
| **Nicknames and Aliases**     | AKAs (also known as)                        |
|-----------------------------------------------------------------------------|


- Assign match expectation label to each data point in the sample (should match, should not match)
- Run the data sample through a screening iteration
- Compute a confusion matrix: **actual** (match expectation) v. **screening result** (match returned)
- Create a confusion matrix (discussed in the Match Classification table earlier) and calculate performance ratios
- With the same data samples, compare target screening system to alternate systems or text matching algorithms
  - Use fuzzy matching or text similarity techniques such as Levenshtein Distance, Jaro-Winkler, Metaphone 3 comparing test sample to target list
  - Compute sensitivity (true positive rate), miss rate (false negative rate), and other measures
  - Evaluate performace of alternate method to the screening system

## Conclusion

It is imperative to understand the complexities of name matching and the limitations of sanctions screening systems. Assuming a screening system works based on simplistic cases is a recipe for regulatory disaster. 

So the right mindset should be:

- <span style="color: #4b6584; background-color: #ecf0f1">Test and periodically validate input data (transactional and reference) for quality, completeness, and timeliness.</span> Address problems systematically as issues are discovered and not with bandaids.
- Extensively <span style="color: #4b6584; background-color: #ecf0f1">stress test the screening process, software, and resolution workflow.</span> Specifically, test the software as close to exhaustively as possible for entries on the watchlist. This requires developing the various name variations discussed above and their permutations for as many names on the watchlist as possible; the coverage should include at least all segments based on name characteristics (Latin names, Arabic names, Asian names, Hispanic names, short names, long names, multi word names, and so on).
- Periodically <span style="color: #4b6584; background-color: #ecf0f1">evaluate quality of hits based on true positives and false negatives</span>. Identify if deficiencies in hit quality are correlated with name characterisitcs. Address such deficiencies by using "second pass" screening logic (addiitonal logic to evaluate a subset of transactions before clearing them for processing).
