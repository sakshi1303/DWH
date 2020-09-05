## This file provides insights of DatawareHouse Principles

Fact Tables - Facts are the measurements resulting from a business process event and are numeric.
Fact Table always contain foreign keys from each of its associated dimensions along with degenerate dimension keys and date/time stamps. They are primary target of computations 
and dynamic aggregations arising from queries.

Basic Fact Table Techniques

Additive, Semi-Additive & Non-Additive Facts - 

1. When facts can be summed across all the dimensions , those facts are called Additive Facts. For Example - credit/debit amount of a customers account.
2. When facts are summed across few dimensions but not all  , those are Semi-Additive Facts. Example - Balance cannot be summed in a particular space or time. 
   But can be summed when we need to calculate overall balance for a month/year or different accounts of a customer.
3. When facts cannot be summed at all, they are Non-Additive Facts. Example - ratios, percentages.

Nulls in Fact Table - NULLs in Fact Tables must be avoided instead use UNKNOWN/NOT APPLICABLE to avoid refrential integrity constraint if any.

Conformed Facts - When similar/same facts are stored in different fact tables, then the technical definitons must be identical if they are to be computed/compared together.

Transaction Fact Tables - 

