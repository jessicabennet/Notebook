[toc]

# MySQL Introduction

## Chapter 1: Installation Procedure

## Chapter 2: Database Overview

## Chapter 3: Basic Operation in MySQL

### 1. Create Database

#### Step1: Create a Database

```mysql
create database database_name; # Create a new database
show create database database_name; # Check the database
show databases; # Check all the sheet of the database
use database_name; # Before you use the sheet, you should input this statement
drop database database_name; # Delete the whole database
```

```mysql
# Template 1
create database test;
show create database test;
use test;
drop database test;
```



#### Step2: Create a table

```mysql
# Template 2
# Create a table
create database test;
use test;
create table emp(
			depid char(3) primary key,
			depname varchar(20) not null default '-',
			peoplecount int unique);

# Modify Table Content
alter table emp rename empdep; # Alter table name
alter table empdep modify depname varchar(30); # Change data type
desc empdep; # Check talbe structure
alter talbe empdep change depname dep varchar(30); # Change column name; must add the type
alter table empdep change dep depname varchar(20); # Change column name "dep->depname" and its type
alter table empdep add maname varchar(10) not null; # Add new column "maname" with type varchar(10) not null
alter table empdep modify maname varchar(10) first; # Change column "maname" as first row
alter table empdep modify maname varchar(10) after depid; # Arrange "maname varchar(10)" after "depid"
alter table empdep drop maname; # Delete column "maname"
desc empdep;
```

**Constraint Condition**

| Constraint Condition | Explanation                    | Statement                         |
| -------------------- | ------------------------------ | --------------------------------- |
| Primary Key          | Not null, unique               | column_name type PRIMARY KEY;     |
| Not Null             | <-                             | column_name type NOT NULL;        |
| Unique               | <-                             | column_name type UNIQUE;          |
| Auto_Increment       | Self Increment, Strated from 1 | column_name type AUTO_INCREMENT;  |
| Default              | Default Value                  | column_name type DEFAULT "value"; |

Data Type

#### Step3: Load Data

```mysql
# Template 3
create table fruits(
	f_id char(10) not null,
	s_id int not null,
	f_name varchar(255) not null,
	f_price decimal(8,2) not null,
	primary key(f_id)
);

# Method 1
insert into fruits(f_id,s_id,f_name,f_price)
values('a1',101,'apple',5.2),
('b1',101,'blackberry',10.2),
('bs1',102,'orange',11.2),
('bs2',105,'melon',8.2),
('t1',102,'banana',10.3),
('t2',102,'grape',5.3),
('o2',103,'coconut',9.2),
('c0',101,'cherry',3.2),
('a2',103,'apricot',25.2),
('l2',104,'lemon',6.4),
('b2',104,'berry',7.6),
('m1',106,'mango',15.6),
('m2',105,'xbabay',2.6),
('t4',107,'xbababa',3.6),
('b5',107,'xxxx',3.6);

select * from fruits; # Select all data

create table Monthly_Indicator(
	city_name varchar(20) not null,
    month_key date not null,
    aqi int(4) not null default 0,
    aqi_range varchar(20) not null default '-',
    air_quality varchar(20) not null default '-',
    pm25 float(6,2) not null default 0,
    pm10 float(6,2) not null default 0,
    so2 float(6,2) not null default 0,
    co float(6,2) not null default 0,
    no2 float(6,2) not null default 0,
    o3 float(6,2) not null default 0,
    ranking int(4) not null default 0,
    primary key(city_name,month_key)
    );

# Method 2
oad data local infile 'D:/liwork/CDA/MySQL - Li Qi/data/all.txt'  # P
	into table Monthly_Indicator 
    fields terminated by '\t'
    ignore 1 lines; # Ignore first row
```

