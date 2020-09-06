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


