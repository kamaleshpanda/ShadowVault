We will use :-
- Amazon Web Services S3
- Glue
- Athena

```
Raw Company Data  
↓  
Stored in Cloud (S3)  
↓  
Cataloged/Prepared (Glue)  
↓  
Queried with SQL (Athena)  
↓  
Used for Analysis & ML
```


## What is S3 ?
Its a simple storage service where companies store data.

## Why Companies use S3 ?
because datasets can be:
- Huge
- Shared by Teams
- Updated Continuously and Needed Globally
Instead of ``` Downloads/data.csv ``` companies use ``` s3://company-data/tickets/ ```

==*We will store ticketwise_dataset.csv to S3 bucket*==

## What is Glue ?
Glue helps AWS understand your data.

It :
- read files from S3
- detects columns and data types
- can create metadata
*Without Glue, Athena won’t know your dataset structure properly.*

####  What is Glue Crawlers ?
A 'crawler' scans files automatically.
```
CSV File
   ↓
Glue Crawler scans
   ↓
Creates table schema
```

## What is Athena ?
Athena lets you run SQL queries directly on S3 data.

Without that :
- download files
- setting databases 

## Why Athena is Powerful ?
Normally SQL databases require:
- servers
- storage setup
- database management
Athena removes all that.
we can run sql there............

## WorkFlow
```
Data arrives
   ↓
Stored in S3
   ↓
Glue organizes it
   ↓
Athena queries it
   ↓
Python/ML uses it
```

## Why not just Pandas ?
We can locally use it for learning.
But Companies deal with :
- TBs of data
- distributed teams
- pipelines and automation

