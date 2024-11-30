
```Microsoft Windows [Version 10.0.22631.4169]
(c) Microsoft Corporation. All rights reserved.

C:\Users\Nadine>sqlplus sys as sysdba;

SQL*Plus: Release 21.0.0.0.0 - Production on Thu Oct 3 17:53:08 2024
Version 21.3.0.0.0

Copyright (c) 1982, 2021, Oracle.  All rights reserved.

Enter password:

Connected to:
Oracle Database 21c Express Edition Release 21.0.0.0.0 - Production
Version 21.3.0.0.0

SQL> show user
USER is "SYS"
SQL> SELECT instance_name FROM v$instance;

INSTANCE_NAME
----------------
xe

SQL> show pdbs;

    CON_ID CON_NAME                       OPEN MODE  RESTRICTED
---------- ------------------------------ ---------- ----------
         2 PDB$SEED                       READ ONLY  NO
         3 XEPDB1                         READ WRITE NO
SQL> ALTER PLUGGABLE DATABASE orclpdb open;
ALTER PLUGGABLE DATABASE orclpdb open
*
ERROR at line 1:
ORA-65011: Pluggable database ORCLPDB does not exist.


SQL> ALTER PLUGGABLE DATABASE xepdb open;
ALTER PLUGGABLE DATABASE xepdb open
*
ERROR at line 1:
ORA-65011: Pluggable database XEPDB does not exist.


SQL> ALTER PLUGGABLE DATABASE xepdb1 open;
ALTER PLUGGABLE DATABASE xepdb1 open
*
ERROR at line 1:
ORA-65019: pluggable database XEPDB1 already open


SQL> create pluggable database plsql_class2024db
  2  admin user pdbadmin identifies by admin
  3
SQL> SELECT CON_ID,TABLESPACE_NAME,FILE_NAME
  2  FROM CDB_DATA_FILES
  3  WHERE CON_ID=3;

    CON_ID TABLESPACE_NAME
---------- ------------------------------
FILE_NAME
--------------------------------------------------------------------------------
         3 SYSTEM
C:\APP\Nadine\PRODUCT\21C\ORADATA\XE\XEPDB1\SYSTEM01.DBF

         3 SYSAUX
C:\APP\Nadine\PRODUCT\21C\ORADATA\XE\XEPDB1\SYSAUX01.DBF

         3 UNDOTBS1
C:\APP\Nadine \PRODUCT\21C\ORADATA\XE\XEPDB1\UNDOTBS01.DBF


    CON_ID TABLESPACE_NAME
---------- ------------------------------
FILE_NAME
--------------------------------------------------------------------------------
         3 USERS
C:\APP\Nadine \PRODUCT\21C\ORADATA\XE\XEPDB1\USERS01.DBF


SQL> create pluggable database plsql_class2024db
  2  admin user pdbadmin identified by admin
  3  file_name_convert=('C:\APP\Nadine \PRODUCT\21C\ORADATA\XE\pdbseed','C:\APP\SHEMA\PRODUCT\21C\ORADATA\XE\plsql_class2024');

Pluggable database created.

SQL> alter session set container =plsql_class2024db;

Session altered.

SQL> alter pluggable database plsql_class2024db open;

Pluggable database altered.

SQL> alter pluggable database plsql_class2024db save state;

Pluggable database altered.

SQL> create user de_plsqlauca identified by Shema;

User created.

SQL> grant all privileges to de_plsqlauca;

Grant succeeded.

SQL> show pdbs;

    CON_ID CON_NAME                       OPEN MODE  RESTRICTED
---------- ------------------------------ ---------- ----------
         4 PLSQL_CLASS2024DB              READ WRITE NO
SQL> show con_name;

CON_NAME
------------------------------
PLSQL_CLASS2024DB
SQL> alter session set container =cdb$root;

Session altered.

SQL> create pluggable database ez_to_delete_pdb
  2  from orclpdb
  3  file_name_convert=('D:\restricted\oracle21c\oradata\ORCL\or
clpdb\','D:\restricted\oracle21c\oradata\ORCL\ez_to_delete_pdb\'

  4  );
create pluggable database ez_to_delete_pdb
*
ERROR at line 1:
ORA-65011: Pluggable database ORCLPDB does not exist.


SQL> create pluggable database de_to_delete_pdb
  2  from  PLSQL_CLASS2024DB
  3  file_name_convert=('C:\app\Nadine \product\21c\oradata\XE\PLSQL_CLASS2024\','C:\app\Nadine \product\21c\oradata\XE\de_to_delete_pdb\');

Pluggable database created.

SQL> alter pluggable database de_to_delete_pdb close immediate;
alter pluggable database de_to_delete_pdb close immediate
*
ERROR at line 1:
ORA-65020: pluggable database DE_TO_DELETE_PDB already closed


SQL> alter pluggable database de_to_delete_pdb unplug into 'C:\app\Nadine\product\21c\admin\XE\dpdump\DE_TO_DELETE_PDB.xml';

Pluggable database altered.

SQL> drop pluggable database de_to_delete_pdb;

Pluggable database dropped.

SQL>
```

![1](https://github.com/user-attachments/assets/373ebc6c-d403-4866-bd1e-8b3839b7630a)
![2](https://github.com/user-attachments/assets/adcbf00a-be06-4d40-a5c1-d8e41438e12b)
![3](https://github.com/user-attachments/assets/c60dc9db-7e4f-40f5-8dd3-b8b48459495f)
![4](https://github.com/user-attachments/assets/45bde1a4-2d97-4065-aee4-f5da4b3f8b67)
![5](https://github.com/user-attachments/assets/dd121be2-62a2-49cf-a5f5-82f8a782f6f4)
![6](https://github.com/user-attachments/assets/9f05260c-d80c-4873-9ecd-4bc7296f9f6a)

### 	ORACLE Screenshots
![01](https://github.com/user-attachments/assets/9d1b7164-b3f5-4bbf-b82a-f0fe45f347e4)
![02](https://github.com/user-attachments/assets/0c243ccf-2c3f-4a71-8fac-40d3626852e5)
![03](https://github.com/user-attachments/assets/8617a0bf-9657-435f-8a5f-a43695f78734)
![04](https://github.com/user-attachments/assets/05d9e96f-acd5-4dd9-b635-94cc1e3acda7)
![05](https://github.com/user-attachments/assets/beb69c15-3aaf-4ff8-9da9-6961151856ae)
