---
id: macmW4BzUA6gNdgF6DZbz
title: Data Stories
desc: ''
updated: 1638374485129
created: 1638370148258
---

# Definition
**Data Stories** are the [[BEAM|datawarehouse.reference.business-event-analysis-and-modelling.data-stories]] equivalent of User Stories from Agile software development. They capture the detail relating to the story a user needs to tell, not the data they think they need.

# Event Stories
Event stories use the story of a business to pull out the BI data requirements underneath. E.g. *Jane buys a car for £75,000 on February 14th 2021* is a data story, with an event of customer purchases a product.

## Story types
There are 3 story types:  
1) **Discrete** - they happen in one step and are largely unconnected e.g. customer purchases  
2) **Evolving** - these are a series of events that form a chain but may be irregular in the time it takes per step of the chain and my have a different number of steps e.g. order through to delivery  
3) **Recurring** - these are events that occur with regular intervals between each step and each subsequent step e.g. calculation and payment of interest.

Story types relate to [[fact tables|datawarehouse.reference.dimensional-modelling.fact-table]] in the following way:

Story Type | Star Schema Type 
---------|----------|
 Discrete | Fact table 
Evolving | Accumulating Snapshot
 Recurring | Periodic Snapshot  

## Story Themes
When getting examples of data you often want to understand different possible types of data that might fit into a table; to do this you want to capture a story for every one of the 5 types of themes of data stories.

### Typical
A typical data record that you might expect in the data, a common customer or product, in a recent but relevant timeframe, with average and normal _how many_ value questions.
### Different
Next we ask for a different record, here we can ask for high and low values for dates and uncommon products to understand the ranges of our data.
### Repeat
Next, ask for a story similar to the first to understand what will uniquelly define a record - you may not ever be able to. This is to understand how similar two data stories can be e.g. can the same customer order the same product on the same day?
### Missing
Following from that we ask for a _missing_ theme data story - this helps identify mandatory columns and also how the BI users would want missing data displayed in the table (null, missing, no_data, etc.)
### Group
Finally you ask questions such as "is the customer always one person" or "can they only order one product at a time" to identify a group data story. This helps you really break down what is actually meant by a detail in your example table.
