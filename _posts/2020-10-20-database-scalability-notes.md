---
title: Tips for scalable web service & database server 
date: 2020-10-20 11:14:08
categories:
  - Data Science

tags:
  - database
  - scalable

---

How to make your web service & database server scalable?

---

Why are are public web services quick? Public servers of a scalable web service are hidden behind a `load balancer`, which evenly distributes load onto your group/cluster of servers.

### First rule of scalability

Every server contains exactly the same codebase and does not store user-related data (e.g., session, profile pictures). Sessions need to be stored in a centralized data store which is accessible to all your application servers.

How do you make sure that a code change is sent to all your servers without one server still serving old code? There are tools that can solve this automatically for you (e.g., Capistrano)
You can create an image file from one of these servers (e.g., Amazon Machine Image). Using this instance as a base, whenever you start a new instance, just do an initial deployment of your latest code and you are ready. 


### The cost of denormalization

- Data retrieval becomes slower. Before normalization, all the information about one entity may be stored in one table, you can retrieve them using just one select query without “join”. However, after normalization, you probably need to collect information from multiple tables via foreign key relations among tables.

### Bottleneck at the database server

Since more web-based application has to have a database backend, the *CRUD* actions on database can generate a lot of operation overhead.

- Optimize your database.
- Hire a really good DBA.
- Do a master-slave replication (read from slaves, and write to master). Of course, if you have an application scenario that has more read than write, then you can change the configuration accordingly.
- denormalize your database and include no more joins in any database query

### How to further improve the speed of your website?

- Caching. A cache is simply a key-value store and it should function as a buffering layer between your application and your data storage. Whenever your application has to read data, it should at first try to retrieve the data from your cache. Only if it’s not in the cache should it then try to get the data from the main data storage. This is because cache holds information in RAM and this is much more faster than data that are stored on disk.
- Cached database queries. Whenever you do a query to your database, you store the result dataset in cache. A hashed version of your query is the cached key.  This mechanism brings the issue of expiration. When one piece of data changes,  you need to change all cached queries who may include that table cell. 
- Cached object. See your data as an object like you already do in your code. This allows you to easily get rid of the object whenever something did change and makes the overall operation of your code faster and more logical. What’s more, it makes asynchronous processing possible.
- Preprocess some of the popular content. For example, pages of website are pre-rendered and locally stored as static HTML files on every change. 
- Handle task asynchronously. The frontend sends a job onto a job queue and immediately signals back to the user: your job is in the work, please continue to browse the page. After the job was done, the frontend will receive a signal and render to result. 

