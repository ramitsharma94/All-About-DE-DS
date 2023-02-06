In this article we will discuss about the fact tables, their types and how to build these tables. 

Lets first start by defining fact tables. A fact table is a part of data warehouse design and is located at the centre surrounded with multiple dimension tables. If in a datawarehouse design, there are multiple fact tables then these tables will be arranged as a fact constellation schema also known as galaxy schema, a more complex version of star schema. Fact table basically contains two type of columns:
1. Column that contains facts
2. Column that contains the foreign keys to the dimension table.

The primary key of a fact table is usually a composite key which is made up of all its foreign keys. And column that contains facts usually consist of different type of measures like additive, non-additive, and semi-additive measures. There is another term called grain which is used to define these tables. The grain of a fact table is the most atomic level by which these facts can be defined. For instance "sales volume by day and by product and by store". 

Different Measures:
1. Additive - measures that can be added across any dimension.
2. Non-additive - measures that cannot be added across any dimension.
3. Semi-additive - measures that can be added across some dimensions.

Fact table can be designed to any granularity. It can be either super detailed or it can be aggregated. Fact tables that are aggregated are also known as summary tables. 

It is also important to be very cautious when dealing with ratios and percentages. Good design rule is to never store percentages or ratios in fact tables. It makes more sense to store the numerator and denominator in the fact table, which then can be aggregated and the aggregated stored values can then be used for calculating the ratio or percentage in the data access tool.

In the real world, it is also possible to have a fact table that contains no measures or facts and has only foreign key values. These tables are called "factless fact tables", or "junction tables".

Types of Fact Tables:

There are four fundamental measurement events:
1. A transactional table is the most basic and fundamental. The grain associated with a transactional fact table is usually specified as "one row per line in a transaction", e.g., every line on a receipt. Typically a transactional fact table holds data of the most detailed level, causing it to have a great number of dimensions associated with it.

2. The periodic snapshot, as the name implies, takes a "picture of the moment", where the moment could be any defined period of time, e.g. a performance summary of a salesman over the previous month. A periodic snapshot table is dependent on the transactional table, as it needs the detailed data held in the transactional fact table in order to deliver the chosen performance output.

3. The accumulating fact table is used to show the activity of a process that has a well-defined beginning and end, e.g., the processing of an order. An order moves through specific steps until it is fully processed. As steps towards fulfilling the order are completed, the associated row in the fact table is updated. An accumulating snapshot table often has multiple date columns, each representing a milestone in the process. Therefore, it's important to have an entry in the associated date dimension that represents an unknown date, as many of the milestone dates are unknown at the time of the creation of the row.

4. By applying temporal database theory and modeling techniques the temporal snapshot fact table allows to have the equivalent of daily snapshots without really having daily snapshots. It introduces the concept of time Intervals into a fact table, allowing saving a lot of space, optimizing performances while allowing the end user to have the logical equivalent of the "picture of the moment" they are interested in.

Steps in designing a fact table:
1. Identify a business process for analysis (like sales).
2. Identify measures of facts (sales dollar), by asking questions like 'what number of X are relevant for the business process?'
3. Identify dimensions for facts (product dimension, location dimension, time dimension, organization dimension)
4. List the columns that describe each dimension (region name, branch name, business unit name).
5. Determine the lowest level (granularity) of summary in a fact table (e.g. sales dollars).


Fact Constellation Schema: Fact constellation is a measure of OLAP. It is a collection of multiple fact tables sharing dimension tables and is also seen as an extension of star schema. It is possible to create fact constellation schema by splitting original star schema into more star schema consisting of many fact tables and some common dimension table.

Factless Fact Tables: Factless fact tables are important dimensional data structures use to convey transactional information which contain no measures. These tables are occasionally necessary for capturing important dimensional relationships which are critical to the meeting the defined business reporting requirements.