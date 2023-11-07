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
create table employeee(empid number,empname varchar (10), dept varchar (10) ,salary
number);
### Create salary_log table
create table salary_log(log_id number,empid NUMBER,empname VARCHAR(10),old_salary
NUMBER,new_salary NUMBER,update_date DATE);

### PLSQL Trigger code
CREATE OR REPLACE TRIGGER log_salary_update
BEFORE UPDATE ON employee
FOR EACH ROW
DECLARE
v_old_salary NUMBER;
v_new_salary NUMBER;
BEGIN
v_old_salary := :OLD.salary;
v_new_salary := :NEW.salary;
IF v_old_salary <> v_new_salary THEN
INSERT INTO salary_log
(empid,empname,old_salary,new_salary,update_date)
VALUES(:OLD.empid, :OLD.empname,v_old_salary,v_new_salary,
SYSDATE);
END IF;
END;
/

### Output:
![image](https://github.com/dineshgl/Ex-5-Creating-Triggers-using-PL-SQL/assets/118668751/e0357cac-2cf4-485b-a8e1-6bf2c899adda)
![image](https://github.com/dineshgl/Ex-5-Creating-Triggers-using-PL-SQL/assets/118668751/e568f622-4d22-4602-8d4c-da566ae5bc70)
![image](https://github.com/dineshgl/Ex-5-Creating-Triggers-using-PL-SQL/assets/118668751/cdeea9d4-af44-4f92-bbc4-50819df56546)

### Result:
THE PROGRAM FOR TRIGGER WAS CREATED AND EXECUTED SUCCESSFULLY.
