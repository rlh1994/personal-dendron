---
id: z5Ph9lhAFwAp221IkKZr6
title: Dimension Table
desc: ''
updated: 1635344480725
created: 1634745394927
---
## Definition
A dimension table contains data that can be thought of as lookups and information used to enhance your data dimensionaly; they contain dimension keys, values, and attributes. They tend to have a small number of rows (magnitude of 1-10,000) but can grow larger, and often can be quite wide leading to duplication - but as these are just used in logical design rather than physical this is not a concern.

Dimension tables form part of a [[datawarehouse.reference.dimensional-modelling.star-schema]] along with [[Fact Tables|datawarehouse.reference.dimensional-modelling.fact-table]]. Keys in the dimension table allow for joining to the fact tables for aggregation and further analysis.


## Slowly Changing Dimensions
When a dimension table contains data that can change over time (e.g. postcodes, customer emails etc.) at non-fixed periods these are know as slowly changing dimensions (SCDs). How these changes are dealt with and stored, or not stored, is decided by the type of SCD that it is.

In reality most SCDs are stored as Type 1, 2, or 3; 4 and 6 are not often used and are just for completeness.

For these examples we will use the following basic data table
![](/assets/images/2021-10-27-14-58-26.png)

### Type 0
The **passive** method, your dimensions do not change over time, and if they do you are at the mercy of your database God.

### Type 1
**Overwriting** the old value. No historic versions are kept and data is simply overwritten. Easy to maintain and often used for dimenions where the only changes are corrections.

![](/assets/images/2021-10-27-14-58-37.png)

### Type 2
**Creating a new record** means that all history is kept. You do this by adding a new surrogate key for each time the record changes, while you can track these through the use of a natural key (e.g. customer ID). Each records has a start date and end date (often 9999-12-31 or null for active records) and can have an `is_active` flag. 

As it can be quite expensive in the database to add a new attribute to this type of SCD it is not recommended to use with dimensions that may gain new attributes in the future.

![](/assets/images/2021-10-27-14-58-44.png)

### Type 3

**Previous Version** columns can be added to make a SCD type 3; if you are only interested in the current and previous version of a dimension then this can help reduce the size of a table when compared to type 2, but offers limited history.

![](/assets/images/2021-10-27-14-59-05.png)

### Type 4
**Historic tables** are an alternative to keeping all history in the same table as with type 2 by keeping a historic record table and having a separate live table. In this method there is no need to change your key in your live table as there is only 1 record per key, however you can add a surrogate key to the history table. Note that the live record should also be in your history table.

![](/assets/images/2021-10-27-15-00-13.png)
![](/assets/images/2021-10-27-14-59-20.png)

### Type 5
There is no type 5 SCD.

### Type 6
Type 6 SCDs are **combinations** of Type 1 + 2 + 3 (=6, get it?) SCDs. The idea is to keep history in your data as with type 2, but also have a "current" value column as with type 3, and each time your dimension changes this column is overwritten for all historic records as with type 1. 

In practise you could just use a last_value() function and this is a waste of space.
![](/assets/images/2021-10-27-14-59-38.png)
