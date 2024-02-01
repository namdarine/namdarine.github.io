---

layout: post

title: Database Intro

date: 2022-09-12 20:00:00

description: Concepts and understanding of Database

tags: WIL

categories: Database

toc:
  sidebar: left

---

# What is a 'Database'?
A 'database' is an organized collection of structured information, or data, typically stored electronically in a computer system. A database is usually controlled by a database management system (DBMS)❇︎. Together, the data and the DBMS, along with the associated applications, are referred to as a database system, often shortened to just a database.

Data within the most common types of databases in operation today is typically modeled in rows and columns in a series of tables to make processing and data querying efficient. The data can then be easily accessed, managed, modified, updated, controlled, and organized. Most databases use structured query language (SQL) for writing and querying❇︎❇︎ data.

## What is DBMS?
- Database Management Systems (DBMS) are software systems used to store, retrieve, and run queries on data. A DBMS serves as an interface between an end-user and a database, allowing users to create, read, update, and delete data in the database.

- DBMS manages the data, the database engine, and the database schema, allowing for data to be manipulated or extracted by users and other programs. This helps provide data security, data integrity, concurrency, and uniform data administration procedures.

- DBMS contains information about a particular domain, collection of interrelated data, a set of programs to access the data, and an environment that is convenient and efficient.

- DBMS optimizes the organization of data by following a database schema design technique called normalization, which splits a large table into smaller tables when any of its attributes have redundancy in values. DBMS offers many benefits over traditional file systems, including flexibility and a more complex backup system.

- Database can be very large and touch all aspects of our lives.

- Database management systems can be classified based on a variety of criteria such as the data model, the database distribution, or user numbers. The most widely used types of DBMS software and relational, distributed, hierarchical, object-oriented, and network.

### Database Applications
- Banking: transactions
- Airlines: reservations, schedules
- Universities: registration, grads
- Sales: customers, products, purchases
- Online retailers: order tracking, customized recommendations
- Manufacturing: production, inventory, orders, supply chain
- Human resources: employee records, salaries, tax deductions

### Cons of using file systems to store data
- Data redundancy and inconsistency
	- Multiple file formats, duplication of information in different files
- Difficulty is accessing data
	- Need to write a new program to carry out each new task
- Data isolation - multiple files and formats
- Integrity problems
	- Integrity constraints become "buried" in program code rather than being stated explicitly
	- Hard to add new constraints or change existing ones
- Atomicity of updates
	- Failures may leave the database in an inconsistent state with partial updates carried out
    ex) Transfer of funds from one account to another should either complete or not happen at all -> All or Nothing
	- Atomicity of transaction requires that all operations constituting the transaction be executed normally or none. If the task is not completed due to a failure while performing the transaction, the processing of all the operations performed so far should be canceled and the database should be returned to the state before the transaction. (The results of processing only a part of the operation should not be reflected in the database.) Therefore, <U>a recovery function is required</U>.
- Concurrent access by multiple users
	- Concurrent access is needed for performance
	- Uncontrolled concurrent accesses can lead to inconsistencies
		ex) Two people reading a balance and updating it by withdrawing money at the same time.
- Security problems
	- Hard to provide user access to some, but not all, data


## Reference
- What is a database? Oracle. (n.d.). Retrieved September 11, 2022, from <a href="https://www.oracle.com/database/what-is-database/">oracle</a> 
- AppDynamics. (2022, June 17). What is a database management system: DBMS: Monitoring. AppDynamics. Retrieved September 11, 2022, from <a href="https://www.appdynamics.com/topics/database-management-systems#~1-what-is-dbms">appdynamics</a> 
- IIT CS425 Fall 2022 prof.Boris Glavic