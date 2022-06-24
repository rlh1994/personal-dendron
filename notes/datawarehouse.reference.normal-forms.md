---
id: yNL9F6dkqeV2aCP9DrYwk
title: Normal Forms
desc: ''
updated: 1641913170831
created: 1635348466546
---
## Definition


## Levels of Normal Forms

![](/assets/images/2021-10-27-16-39-19.png)
### First Normal Form
Data in a table can be classed as being in the first normal form (1NF) if each attribute in every record is only a single value i.e. there are no list or array type columns or comma delimited attributes.

![](/assets/images/2021-10-27-16-39-45.png)
### Second Normal Form
Data in a table can be classed as being in the second normal form (2NF) if, as well as satifying the 1NF condition it also has no attributes that depend on only part of the composite key (as opposed to all of it). Said another way, your table must have a primary key or all attributes must depend on the entire composite key not just part of it.

In the below, as name and and address are a composite key, we can create a primary key instead and split this into two tables.

![](/assets/images/2021-10-27-16-42-50.png)
![](/assets/images/2021-10-27-16-42-35.png)
### Third Normal Form
Data in a table can be classed as in the third normal form (3NF) if it satisfies the conditions of 1NF and 2NF, and also have no transitive functional dependancies i.e. no attributes depend solely on an attribute that is not the primary key. An example is in a book database, the nationality of the author depends only on the author, not on the ISBN of the book itself.

![](/assets/images/2021-10-27-16-48-52.png)
![](/assets/images/2021-10-27-16-48-39.png)
![](/assets/images/2021-10-27-16-48-59.png)

### Beyond Third Normal Form
Whilst there exist levels beyond the third normal form, the third is often enough for the vast majority of usages.

## Resources
https://www.guru99.com/database-normalization.html  
https://en.wikipedia.org/wiki/Database_normalization  
https://www.geeksforgeeks.org/normal-forms-in-dbms
