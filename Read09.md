## Intro to Database Normalization

* This describes the process to organize a database into tables that are focused on a specific topic and supporting topics. 

* Better to have another database than a bloated database. This simplifies queries and lowers the risks of creating anomalies or having redundant data. 

*The three normal forms of database normalization are:

    * The info is stored in a table with each column containing atomic values, with no repeating columns.

    * The table has first form normalization and the columns depend on the table's key.

    * First and second forms plus the columns are not transitively dependant on the key from second form.