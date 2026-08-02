1) Find the Second Highest Salary

SELECT MAX(salary)
FROM employee
WHERE salary < (SELECT MAX(salary) FROM employee);

2)5. Find Employees Having Highest Salary in Each Department

SELECT department_id,
       MAX(salary)
FROM employee
GROUP BY department_id;


