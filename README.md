# Data modeling with PostgreSql

This project created for Udacity Data Engineer course. This project is the first one. The document will discuss the following topics:

1. The purpose of this database in the context of the startup, Sparkify, and their analytical goals.
2. The database schema design and the ETL pipeline.
3. example of queries and results for song play analysis.

___
## Purpose

Sparkify asks for db for better analsys of their users listening habbits. The data was converted from json files to relational database, based on PostgreSql. The  relational database give Sparkify better analsys capabilities, compare to NoSql db.    

___
## database schema

The database scheme is star-scheme, to improve the queries logic and performance, Which fitting Sparkify request. The star-scheme strogest side is simplicity, which great for queries and aggregations, and because of that better performance. The following diagram show the db structure.  

![DB Scheme](https://i.imgur.com/IFcwVpW.png)

Songplays table is the fact table, while the artists, songs and users are dimension tables.

___
## example 

#### count of male users for each location


```SQL
SELECT 
    location, count(*) 
FROM 
    songplays 
JOIN users 
    on (songplays.user_id = users.user_id)
WHERE 
    gender = 'M'
GROUP BY 
    location;
```


| location      | count       |
| ------------- |:-------------:| 
| Tampa-St. Petersburg-Clearwater, FL | 16   |
| San Jose-Sunnyvale-Santa Clara, CA  | 25   | 
| Houston-The Woodlands-Sugar Land, TX|  9   |
| Birmingham-Hoover, AL               | 4761 | 
| San Francisco-Oakland-Hayward, CA   | 1    | 
| Yuba City, CA                       | 25   | 
| Eureka-Arcata-Fortuna, CA           | 1    | 
| Youngstown-Warren-Boardman, OH-PA   | 1    | 
| Red Bluff, CA                       | 4    | 
| New Orleans-Metairie, LA            | 16   | 
| Minneapolis-St. Paul-Bloomington, MN-WI| 16| 
| New York-Newark-Jersey City, NY-NJ-PA | 1    | 
| Dallas-Fort Worth-Arlington, TX       | 1    | 
| Columbia, SC                        | 9   | 


