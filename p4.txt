create table department13(deptid numeric(5),name varchar(20), 
constraint dp1 primary key(deptid));

create table company13(compid numeric(5),name varchar(20),city varchar(20),
no_of_employees numeric(6),e_id numeric(5),
constraint cp1 primary key(compid));

create table employee13(empid numeric(5),name varchar(20),c_id numeric(5),
designation varchar(15),salary numeric(15),city varchar(20),
constraint ep1 primary key(empid));

create table student13(studid numeric(5),sname varchar(20),class varchar(15),city varchar(20),
total_mark numeric(4),percentage numeric(4),deptid numeric(5),
constraint st13 primary key(studid),
constraint st14 foreign key(deptid) references department13(deptid));

create table staff13(staffid numeric(5),name varchar(20),deptid numeric(5),
designation varchar(20),salary numeric(15),city varchar(20),
constraint sa1 primary key(staffid),
constraint sa2 foreign key(deptid) references department13(deptid));

SQL> desc staff13;
 Name                                      Null?    Type
 ----------------------------------------- -------- ----------------------------
 STAFFID                                   NOT NULL NUMBER(5)
 NAME                                               VARCHAR2(20)
 DEPTID                                             NUMBER(5)
 DESIGNATION                                        VARCHAR2(20)
 SALARY                                             NUMBER(15)
 CITY                                               VARCHAR2(20)

SQL> desc employee13;
 Name                                      Null?    Type
 ----------------------------------------- -------- ----------------------------
 EMPID                                     NOT NULL NUMBER(5)
 NAME                                               VARCHAR2(20)
 C_ID                                               NUMBER(5)
 DESIGNATION                                        VARCHAR2(15)
 SALARY                                             NUMBER(15)
 CITY                                               VARCHAR2(20)

SQL> desc student13;
 Name                                      Null?    Type
 ----------------------------------------- -------- ----------------------------
 STUDID                                    NOT NULL NUMBER(5)
 NAME                                               VARCHAR2(20)
 CLASS                                              VARCHAR2(15)
 CITY                                               VARCHAR2(20)
 TOTAL_MARK                                         NUMBER(4)
 PERCENTAGE                                         NUMBER(4)
 DEPTID                                             NUMBER(5)

SQL> desc company13;
 Name                                      Null?    Type
 ----------------------------------------- -------- ----------------------------
 COMPID                                    NOT NULL NUMBER(5)
 NAME                                               VARCHAR2(20)
 CITY                                               VARCHAR2(20)
 NO_OF_EMPLOYEES                                    NUMBER(6)
 E_ID                                               NUMBER(5)
SQL> desc department13;
 Name                                      Null?    Type
 ----------------------------------------- -------- ----------------------------
 DEPTID                                    NOT NULL NUMBER(5)
 NAME                                               VARCHAR2(20)

 insert into department13 values(101,'MCA');
 insert into department13 values(102,'MBA');
 insert into department13 values(103,'MTech');

insert into student13 values(1001,'Thasni','s2','Trivandrum',650,95,103);
insert into student13 values(1002,'Seetha','s2','Kollam',640,90,101);
insert into student13 values(1003,'Preethi','s4','Ernakulam',580,88,102);

insert into staff13 values(201,'Jeeja',103,'Associate professor',25000,'Ernakulam');
insert into staff13 values(202,'Sreeja',101,'HOD',30000,'Kollam');
insert into staff13 values(203,'Subha',102,'Advisor',20000,'Trivandrum');
insert into staff13 values(204,'Rekha',101,'Associate professor',25000,'Ernakulam');

insert into employee13 values(3001,'Sulthan',301,'Clerk',25000,'Ernakulam');
insert into employee13 values(3002,'Anagha',302,'Manager',30000,'Trivandrum');
insert into employee13 values(3003,'Arjun',303,'Clerk',25000,'Ernakulam');

insert into company13 values(301,'TCS','Ernakulam',2,3001);
insert into company13 values(302,'Infosis','Trivandrum',10,3002);
insert into company13 values(303,'UST','Ernakulam',15,3003);

SQL>  select * from Employee13;

     EMPID NAME                       C_ID DESIGNATION         SALARY
---------- -------------------- ---------- --------------- ----------
CITY
--------------------
      3001 Sulthan                     301 Clerk                25000
Ernakulam

      3002 Anagha                      302 Manager              30000
Trivandrum

      3003 Arjun                       303 Clerk                25000
Ernakulam

SQL>  select * from staff13;

   STAFFID NAME                     DEPTID DESIGNATION              SALARY
---------- -------------------- ---------- -------------------- ----------
CITY
--------------------
       201 Jeeja                       103 Associate professor       25000
Ernakulam

       202 Sreeja                      101 HOD                       30000
Kollam

       203 Subha                       102 Advisor                   20000
Trivandrum


   STAFFID NAME                     DEPTID DESIGNATION              SALARY
---------- -------------------- ---------- -------------------- ----------
CITY
--------------------
       204 Rekha                       101 Associate professor       25000
Ernakulam

SQL> select * from department13;

    DEPTID NAME
---------- --------------------
       101 MCA
       102 MBA
       103 MTech

SQL> select * from employee13;

     EMPID NAME                       C_ID DESIGNATION         SALARY
---------- -------------------- ---------- --------------- ----------
CITY
--------------------
      3001 Sulthan                     301 Clerk                25000
Ernakulam

      3002 Anagha                      302 Manager              30000
Trivandrum

      3003 Arjun                       303 Clerk                25000
Ernakulam

SQL> select * from company13;

    COMPID NAME                 CITY                 NO_OF_EMPLOYEES       E_ID
---------- -------------------- -------------------- --------------- ----------
       301 TCS                  Ernakulam                          2       3001
       302 Infosis              Trivandrum                        10       3002
       303 UST                  Ernakulam                         15       3003



a) select s.name from student13 s,department13 d where d.name='MCA' and s.deptid=d.deptid;

NAME
--------------------
Seetha

select st.name from student13 st join department13 d on d.deptid=st.deptid 
where d.name='MCA';

NAME
--------------------
Seetha

b)select sname from student13 natural join department13;
SNAME
--------------------
Thasni
Seetha
Preethi

c)select * from employee13 where c_id in (select compid from company13 where name='TCS');

     EMPID NAME                       C_ID DESIGNATION         SALARY
---------- -------------------- ---------- --------------- ----------
CITY
--------------------
      3001 Sulthan                     301 Clerk                27000
Ernakulam

