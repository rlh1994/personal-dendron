---
id: rVqxyffctETdSUgYfBRnx
title: Fact Table
desc: ''
updated: 1635344503680
created: 1634745246106
---
## Definition
A fact table details a business event or event type data. This data could be something like a customer placing an order, a parcel being shipped, or a complaint being raised. These tables tend to contain quantitative information and are denormalised (i.e. not in any normal form). 

Fact tables form part of a [[datawarehouse.reference.dimensional-modelling.star-schema]] along with [[Dimenion Tables|datawarehouse.reference.dimensional-modelling.dimension-table]]. Foreign keys in the fact table allow for joining to the dimension tables for aggregation and further analysis.

