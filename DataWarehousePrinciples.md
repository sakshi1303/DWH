## Insights of DatawareHouse Principles

Fact Tables - Facts are the measurements resulting from a business process event and are numeric.
Fact Table always contain foreign keys from each of its associated dimensions along with degenerate dimension keys and date/time stamps. They are primary target of computations 
and dynamic aggregations arising from queries.

Basic Fact Table Techniques

Additive, Semi-Additive & Non-Additive Facts - 

1. When facts can be summed across any of the dimensions , those facts are called Additive Facts. For Example - credit/debit amount of a customers account.
2. When facts are summed across few dimensions but not all  , those are Semi-Additive Facts. Example - Balance cannot be summed in a particular space or time. 
   But can be summed when we need to calculate overall balance for a month/year or different accounts of a customer.
3. When facts cannot be summed at all, they are Non-Additive Facts. Example - ratios, percentages.

Nulls in Fact Table - NULLs in Fact Tables must be avoided instead use UNKNOWN/NOT APPLICABLE to avoid refrential integrity constraint if any.

Conformed Facts - When similar/same facts are stored in different fact tables, then the technical definitons must be identical if they are to be computed/compared together.

Transaction Fact Tables - It correspondes to a measurement event at a point in space and time. It may be dense or sparse because rows exist only if a measurement takes place.

Periodic Snapshot Fact Tables - When measurement event occurs over a standard period such as day, week and month. These are uniformly dense as the row is inserted even if no activity takes place.

Accumulating Snapshot Fact Tables - When the measurement events occur at predictable steps between the beginning and end of the process. For example Pipeline or workflow process such as order fulfillment or claim processing that has defined starting point, standard intemediate steps and defined end point. Records are initially inserted and as and when the pipeline progress, rows are revisted and updated.

Factless Fact Table - When there are no actual measurements but still facts are present . For example a student attending a class everyday. It can be used to analyse what did not happen. It has two parts - coverage facts which has all the possiblities that might happen and activity table when the events did happen.

Aggregated Facts - Numeric rollup of atomic facts to accelerate query performance and directly available to BI layer. For example, total students in a class/school. This process known as aggregate navigation.

Consolidated Facts - When muliple process combine together to single consolidated fact to compare/analyse. For example comparing actual & predicted sales. It adds burden to ETL layer but ease the analytic burden.

Basic Dimension Table Techniques

Dimension Table Structure - Dimension Table has single primary key column and is embedded as a foreign key in any associated fact table. They are flat denormalised tables and the dimension attributes are populated with verbose descriptions. 

Dimension Surrogate Keys - Primary key columns for dimensions cannot be operational system's natural key because the natural keys can change over time. Also, they can be created by more than one system which may be incompatible or poorly administered. It is suggested to use surrogate keys which are sequentially generated.

Natural, Durable and Supernatural keys - Natural keys are created by operational source systems which are subject to business rules outside the control of DW/BI systems. For example, a employee resigns and can be rehired. So, a new durable key must be created that is persistant and does not change in this situation. This key is also refrerred to as durable supernatural key. 

Drilling Down - adding a row header to an existing query which is appended to GROUP BY clause. Example - a school, student and class entity.

Degenerate Dimensions - It has no associated dimension table. Example - invoice number but is a valid dimension key for fact tables at the line level item. These are most common with transaction and accumulating snapshot fact tables.

Denormalised Flattened Dimension - The dimension table should be denormalised and many-to-one fixed depth hierarchies into separate attributes on a flattened dimension row which supports simplicity and speed.



