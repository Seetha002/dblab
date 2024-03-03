create table department13(deptid numeric(5),name varchar(20), 
constraint dp1 primary key(deptid));

create table company13(compid numeric(5),name varchar(20),city varchar(20),
no_of_employees numeric(6),e_id numeric(5),
constraint cp1 primary key(compid));

create table employee13(empid numeric(5),name varchar(20),c_id numeric(5),
designation varchar(15),salary numeric(15),city varchar(20),
constraint ep1 primary key(empid));

create table student13(studid numeric(5),name varchar(20),class varchar(15),city varchar(20),
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



a) select * from student13 order by deptid;

    STUDID NAME                 CLASS           CITY                 TOTAL_MARK PERCENTAGE     DEPTID
---------- -------------------- --------------- -------------------- ---------- ---------- ----------
      1002 Seetha               s2              Kollam                      640         90        101

      1003 Preethi              s4              Ernakulam                   580         88        102

      1001 Thasni               s2              Trivandrum                  650         95        103
b) select name from employee13;

NAME
--------------------
Sulthan
Anagha
Arjun
c) select * from staff13 where salary>20000;
   STAFFID NAME                     DEPTID DESIGNATION              SALARY CITY
---------- -------------------- ---------- -------------------- ---------- --------------------

       201 Jeeja                       103 Associate professor       25000  Ernakulam


       202 Sreeja                      101 HOD                       30000  Kollam

       204 Rekha                       101 Associate professor       25000  Ernakulam
d)  select * from student13 where percentage>80 and percentage<90;

    STUDID NAME                 CLASS           CITY                 TOTAL_MARK PERCENTAGE     DEPTID
---------- -------------------- --------------- -------------------- ---------- ---------- ----------
      1003 Preethi              s4              Ernakulam                   580         88        102

e) select e.empid,e.name,e.c_id,e.designation,e.salary,e.city from employee13 e,
company13 c where e.c_id=c.compid and c.no_of_employees>3;


     EMPID NAME                       C_ID DESIGNATION         SALARY CITY
---------- -------------------- ---------- --------------- ---------- --------------------
      3002 Anagha                      302 Manager              30000 Trivandrum

      3003 Arjun                       303 Clerk                25000 Ernakulam

f) select s.name,s.salary,s.city from staff13 s,student13 st where s.salary>25000 and s.city=st.city;
NAME                     SALARY CITY
-------------------- ---------- --------------------
Sreeja                    30000 Kollam
g)select e.empid,e.name,e.c_id,e.designation,e.salary,e.city from employee13 e,
company13 c where c.no_of_employees=(select max(no_of_employees) from company13) and e.c_id=c.compid;


     EMPID NAME                       C_ID DESIGNATION         SALARY
---------- -------------------- ---------- --------------- ----------
CITY
--------------------
      3003 Arjun                       303 Clerk                25000
Ernakulam

h)update employee13 set salary=salary+salary*(8/100) 
where empid in(select empid from employee13 e ,company13 c 
where e.city='Ernakulam'and e.designation='Clerk'and e.c_id=c.compid and e.city=c.city);

SQL> select * from employee13
  2  ;

     EMPID NAME                       C_ID DESIGNATION         SALARY
---------- -------------------- ---------- --------------- ----------
CITY
--------------------
      3001 Sulthan                     301 Clerk                27000
Ernakulam

      3002 Anagha                      302 Manager              30000
Trivandrum

      3003 Arjun                       303 Clerk                27000
Ernakulam

i)update staff13 set salary=salary+salary*(10/100) where designation='Associate professor';
SQL> select * from staff13;

   STAFFID NAME                     DEPTID DESIGNATION              SALARY
---------- -------------------- ---------- -------------------- ----------
CITY
--------------------
       201 Jeeja                       103 Associate professor       27500
Ernakulam

       202 Sreeja                      101 HOD                       30000
Kollam

       203 Subha                       102 Advisor                   20000
Trivandrum


   STAFFID NAME                     DEPTID DESIGNATION              SALARY
---------- -------------------- ---------- -------------------- ----------
CITY
--------------------
       204 Rekha                       101 Associate professor       27500
Ernakulam

j)select e.name from employee13 e,company13 c
where e.c_id=c.compid and e.city=c.city;

NAME
--------------------
Sulthan
Anagha
Arjun

k)select d.name,count(s.name) from staff13 s,department13 d where d.deptid=s.deptid group by d.name;


NAME                 COUNT(S.NAME)
-------------------- -------------
MBA                              1
MTech                            1
MCA                              2

l)delete from company13 where no_of_employees<5;
SQL> select * from company13;

    COMPID NAME                 CITY                 NO_OF_EMPLOYEES       E_ID
---------- -------------------- -------------------- --------------- ----------
       302 Infosis              Trivandrum                        10       3002
       303 UST                  Ernakulam                         15       3003
m)select d.deptid,d.name,st.name,s.name from department13 d,student13 st,staff13 s 
where d.deptid=s.deptid and d.deptid=st.deptid order by d.deptid;


    DEPTID NAME                 NAME                 NAME
---------- -------------------- -------------------- --------------------
       101 MCA                  Seetha               Sreeja
       101 MCA                  Seetha               Rekha
       102 MBA                  Preethi              Subha
       103 MTech                Thasni               Jeeja
n)select d.name,s.name,s.salary from department13 d,staff13 s 
where d.deptid=s.deptid and s.salary=(select max(salary) from staff13 where deptid=d.deptid);
NAME                 NAME                    SALARY
-------------------- -------------------- ----------
MTech                Jeeja                    27500
MCA                  Sreeja                   30000
MBA                  Subha                    20000
