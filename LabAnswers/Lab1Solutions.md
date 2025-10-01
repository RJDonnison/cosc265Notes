# Lab 1

## Task 1: Review the REGISTRATION Database Requirements

The REGISTRATION database consists of eight tables, the relational schemas of which are
as follows:
  VEHICLE_TYPE (make, model, power, no_pass, cap, cc)
  VEHICLE (plates, year, Eng_No, Ch_No, type, make, model)
  OWNER (Dr_Lic, IRD, fname, init, lname, address, bdate, gender, employer, phone)
  OWNS (plates, ownerid, purchase_date, DRR, DateSold)
  COLOR (plates, color)
  REG_ORG (number, street, street_no, city, manager)
  EMPLOYEE (fname, init, lname, IRD, gender, bdate, office, reg_org, SDate)
  REGISTRATION (plates, emp, reg_org, reg_date, country, DRR, amount)
This database was developed from the following requirements:
The REGISTRATION database stores data about vehicles, their owners and registration
details. The following data should be stored for each vehicle: make, model, plates, year of
manufacture, engine number, chassis number, type (one of: p for private car, r for rental car, t
for taxicab, l for truck and m for motorcycle), cc rating, number of passengers and/or capacity,
motive power (p for petrol, g for gas and d for diesel), colour(s). Each owner of a car is
described by his/her name, address, drivers licence number, phone, IRD number, gender,
birthdate and the employer (if applicable). A car can have just one owner at a given point in
time, but the database should record information about previous owners as well. For each
owner of a vehicle, the database should store the date of purchasing the vehicle, the distance
recorder reading at the time of purchase and (when appropriate) the date when the vehicle was
sold. We store the following information about each registration of the vehicle: date,
organisation, amount paid and the employee who registered the vehicle, distance recorder
reading, and in the case of the first registration of a vehicle, information about whether it is a
new vehicle or an imported one (the name of the country it is imported from is stored in that
case).

There are several organisations which are licensed to register vehicles, and we know their
names, managers, addresses and employees. Each employee is known by the name, IRD
number, starting date, gender (f, m or x), birthdate and office number.
Four tables (VEHICLE_TYPE, OWNER, REG_ORG and EMPLOYEE) have already been
created and populated. You have access to these tables, and therefore do not need to
recreate them. The statements used to create these four tables are given below:
```

create table VEHICLE_TYPE
(make /* Make of a vehicle */ varchar(10) not null,
model /* Model of a vehicle */ varchar(10) not null,
power /* Motive power (petrol, gas, diesel) */ char(1)
 constraint check_power check (power in ('p','g','d')),
no_pass /* Number of passengers */ integer
 constraint check_pass check (no_pass between 0 and 6),
cap /* Capacity */ float constraint check_cap check (cap >= 0),
cc /* Volume of the motor */ integer constraint check_cc check (cc >= 0),
primary key (make,model));
```

```
create table OWNER
(dr_lic /* Driver's licence number */ char(8) not null primary key,
IRD /* IRD number of the owner */ char(8),
fname /* Owner's first name */ varchar(15) not null,
init /* Middle initial */ char(1),
lname /* Owner's last name */ varchar(15) not null,
address /* Owner's address */ varchar(30) not null,
bdate /* Owner's birthdate */ date,
gender /* Owner's gender */ char(1),
employer varchar(30),
phone /* Owner's phone number */ varchar(15));
```

```
create table EMPLOYEE
(fname /* Employee's first name */ varchar(15) not null,
init /* Employee's middle initial */ char(1),
lname /* Employee's last name */ varchar(15) not null,
IRD /* Employee's IRD number */ varchar(10) not null primary key,
gender/* Employee's gender */ char(1)
 constraint check_gender check (gender in ('f','m','F','M','x','X')),
bdate /* Employee's birthdate */ date,
office /* Employee's office */ varchar(5),
reg_org /* The number of the registration office the employee works for */
 varchar(10),
sdate /* Starting date in the organization */ date);
```

```
create table REG_ORG
(org_number /* The number of the registration organization */ varchar(10)
 not null primary key,
street /* Street name */ varchar(15) not null,
st_num /* Number in the street */ varchar(6) not null,
city /* City */ varchar(15) not null,
manager /* The manager's IRD number */ varchar(10) references employee);
```

Note that the EMPLOYEE table and the REG_ORG table both contain foreign keys referring
to each other. The EMPLOYEE table was initially created without the foreign key, because at
that time the REG_ORG table did not exist. After creating the REG_ORG table, and
populating both tables, the EMPLOYEE table was modified to add the foreign key with the
following statement:
```
alter table EMPLOYEE
add foreign key (reg_org) references REG_ORG;
```

If the alteration of the EMPLOYEE table is done before the tables are populated, populating
either table becomes impossible, as each table needs to match its foreign key against the
equivalent primary key of the other table.

## Task 2: Creating Tables

Create the four remaining tables (VEHICLE, OWNS, COLOR, REGISTRATION) from the
REGISTRATION database, using the CREATE TABLE statement discussed in lectures.
Choose appropriate data types, by viewing the data for these tables available in Learn.
Remember to match data types with their counterparts (primary or foreign keys) in existing
tables (VEHICLE_TYPE, OWNER, REG_ORG and EMPLOYEE). Declare all the necessary
integrities. It is a good idea to name constraints that you use, so they are easily identified for
later use.

```
create table VEHICLE
(plates /* Plate number */ varchar(6) not null primary key,
year /* Year of manufacture */ char(4)
      constraint check_year check (year between '1900' and '2019'),
eng_no /* Engine number */ varchar(9) not null unique,
ch_no /* Chassis number */ varchar(7) not null unique,
type /* Type of the vehicle (taxi, private, truck, ...) */ char(1)
      constraint check_veh_type check (type in ('p','m','t','r','l')),
make /* Make of a vehicle */ varchar(10),
model /* Model of a vehicle */ varchar(10),
foreign key (make,model) references vehicle_type);
```

```
create table OWNS
(plates /* Owner's plates number */ varchar(6) not null references vehicle,
ownerid /* Owner's id number */ char(8) not null references owner,
purchase_date /* The date of purchase */ date,
drr /* The mileage */ char(6),
DateSold /* The date the vehicle was sold */ date default null,
primary key (plates,ownerid));
```

```
create table COLOR
(plates /* The plate number */ varchar(6) not null references vehicle,
color /* Color of the vehicle */ varchar(10) not null,
primary key (plates,color));
```

```
create table REGISTRATION
(plates /* Plates */ varchar(6) not null references vehicle,
emp /* IRD of the employee who registered the vehicle */ varchar(10) not null references employee,
reg_org /* Organization number */ varchar(10) not null references reg_org,
reg_date /* Registration date */ date not null,
country /* The country */ varchar(10),
drr /* mileage */ char(6),
amount /* the price */ number,
primary key (plates,emp,reg_org,reg_date));
```
