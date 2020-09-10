# Delete-Duplicate-Row-in-SQLite3

## Create Employee Table

    CREATE TABLE Employee (
         id INTEGER PRIMARY KEY,
         first_name TEXT,
         last_name TEXT,
         country TEXT
     )
 
 ## Insert Data to Employee Table
 
    insert into Employee ([first_name],[last_name],[country] )values('Jone','Chris','Taiwan'),
    ('John','Chris','Taiwan'),
    ('Steve','Jobs','USA'),
    ('James','Bond','UK'),
    ('James','Bond','UK'),
    ('James','Bond','UK')

## Display Data

    select * from Employee
    
    //result
    ID first_name last_name country
    1	Jone	Chris	Taiwan
    2	John	Chris	Taiwan
    3	Steve	Jobs	USA
    4	James	Bond	UK
    5	James	Bond	UK
    6	James	Bond	UK

## remove Duplicate Row

     DELETE FROM Employee
     WHERE ID NOT IN
     (
         SELECT MAX(ID) AS MaxRecordID
         FROM Employee
         GROUP BY [first_name],
                  [last_name],
                  [country]
     );
 
 
 ## Display Data

    select * from Employee

    //result
    ID first_name last_name country
    1	Jone	Chris	Taiwan
    2	John	Chris	Taiwan
    3	Steve	Jobs	USA
    6	James	Bond	UK
