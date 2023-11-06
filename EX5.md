# Ex. No: 5 Creating Triggers using PL/SQL

### AIM: To create a Trigger using PL/SQL.

### Steps:
1. Create employee table with following attributes (empid NUMBER, empname VARCHAR(10), dept VARCHAR(10),salary NUMBER);
2. Create salary_log table with following attributes (log_id NUMBER GENERATED ALWAYS AS IDENTITY, empid NUMBER,empname VARCHAR(10),old_salary NUMBER,new_salary NUMBER,update_date DATE);
3. Create a trigger named as log_salary-update.
4. Inside the trigger block, Insert the values into the salary_log table whenever the salary is updated.
5. End the trigger.
6. Update the salary of an employee in employee table.
7. Whenever a salary is updated for the employee it must be logged into the salary_log table with old salary and new salary.
8. Display the employee table, salary_log table.

### Program:
### Create employee table
```sql
create table employee1(empid NUMBER, empname VARCHAR(10), dept VARCHAR(10),salary NUMBER);
```
### Create salary_log table
```sql
 create table salary_log(log_id NUMBER GENERATED ALWAYS AS IDENTITY, empid NUMBER,empname VARCHAR(10),old_salary NUMBER,new_salary NUMBER,update_date DATE);
```
### PLSQL Trigger code
```sql
create or replace trigger log_salary_update
before update on employee1
for each row
declare
v_old_salary number;
v_new_salary number;
begin
v_old_salary := :old.salary;
v_new_salary := :new.salary;
if v_old_salary <> v_new_salary then
insert into salary_log(empid,empname,old_salary,new_salary,update_date)
values(:old.empid, :old.empname , v_old_salary ,v_new_salary , SYSDATE);
end if;     
end;
 /
```
### Output:
![image](https://github.com/KothaiKumar/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/121215739/fe13bfce-16c2-43c3-a833-fc309f31b482)

![image](https://github.com/KothaiKumar/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/121215739/7903ff0e-5d8f-429d-85a7-b067ee1bdb43)

![image](https://github.com/KothaiKumar/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/121215739/ebe3978a-a6c4-45d4-88b1-540c45c06c1f)

![image](https://github.com/KothaiKumar/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/121215739/74f9b399-7301-4d73-a028-90646b8ec8c5)


### Result:
Thus, a trigger is created using PL/SQL.
