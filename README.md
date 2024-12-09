


1. Listar alunos ordenados por nome e data de nascimento.

SELECT first_name, last_name, hire_date 
FROM hr.employees 
ORDER BY first_name ASC, hire_date ASC; 

//

2. Listar professores e suas especialidades em ordem decrescente.

SELECT last_name, job_id 
FROM hr.employees 
ORDER BY last_name DESC; 

//

3. Listar disciplinas ordenadas por carga horária.

SELECT department_name, location_id 
FROM hr.departments 
ORDER BY location_id DESC; 

//

4. Contar o número de alunos em cada status de matrícula.

SELECT job_id, COUNT(*) AS num_employees 
FROM hr.employees 
GROUP BY job_id; 

//

5. Listar cursos com a soma total da carga horária de suas disciplinas.

SELECT d.department_name, SUM(e.salary) AS total_salary 
FROM hr.departments d 
JOIN hr.employees e ON d.department_id = e.department_id 
GROUP BY d.department_name; 

//

6. Contar quantos professores estão lecionando mais de 3 turmas.

SELECT department_id, COUNT(*) AS num_employees 
FROM hr.employees 
GROUP BY department_id 
HAVING COUNT(*) > 3; 

//

7. Listar os alunos matriculados em mais de uma disciplina.

SELECT e.first_name, e.last_name, e.salary 
FROM hr.employees e 
JOIN (SELECT department_id, AVG(salary) AS avg_salary 
   FROM hr.employees 
      GROUP BY department_id) d_avg 
ON e.department_id = d_avg.department_id 
WHERE e.salary > d_avg.avg_salary; 

//

8. Listar cursos com mais de 2000 horas de carga horária.

SELECT d.department_name 
FROM hr.departments d 
JOIN hr.employees e ON d.department_id = e.department_id 
GROUP BY d.department_name 
HAVING SUM(e.salary) > 50000; 

//

9. Contar o número total de turmas e listar por professor.

SELECT department_id, COUNT(*) AS num_employees 
FROM hr.employees 
GROUP BY department_id 
ORDER BY num_employees DESC; 

//

10. Listar disciplinas e a média da carga horária por curso.

SELECT d.department_name, AVG(e.salary) AS avg_salary 
FROM hr.departments d 
JOIN hr.employees e ON d.department_id = e.department_id 
GROUP BY d.department_name; 

//

11. Exibir os alunos e seus respectivos status de matrícula, ordenados pelo status e pela data de matrícula.

SELECT last_name, job_id, hire_date 
       FROM hr.employees 
       ORDER BY job_id, hire_date DESC;
       
//

12. Exibir a idade dos alunos ordenados da maior para a menor idade.

SELECT last_name, FLOOR((SYSDATE - hire_date) / 365.25) AS idade_aproximada 
FROM hr.employees 
ORDER BY idade_aproximada DESC; 

//

13. Exibir as disciplinas e o número de alunos matriculados em cada uma. 

SELECT job_id, COUNT(*) AS num_employees 
FROM hr.employees 
GROUP BY job_id 
ORDER BY num_employees DESC; 

//

14. Listar as turmas com o nome dos professores e disciplinas, ordenadas por horário. 

SELECT e.last_name, e.job_id, d.department_name 
FROM hr.employees e 
JOIN hr.departments d ON e.department_id = d.department_id 
ORDER BY e.job_id; 

//

15. Contar quantas disciplinas têm carga horária superior a 80 horas.

SELECT COUNT(DISTINCT job_id) AS high_salary_jobs 
FROM hr.employees 
WHERE salary > 10000; 

//

16. Listar os cursos e a quantidade de disciplinas que cada curso possui. 

SELECT d.department_name, COUNT(e.employee_id) AS num_employees 
FROM hr.departments d 
JOIN hr.employees e ON d.department_id = e.department_id 
GROUP BY d.department_name; 

//

17. Exibir os professores que têm mais de 2 disciplinas com carga horária maior que 100 horas. 

SELECT job_id 
FROM hr.employees 
WHERE salary > 8000 
GROUP BY job_id 
HAVING COUNT(employee_id) > 2; 

// 

18. Listar disciplinas que tenham pelo menos 5 alunos matriculados.

SELECT job_id 
FROM hr.employees 
GROUP BY job_id 
HAVING COUNT(*) >= 5; 

//

19. Exibir o número de alunos por status, ordenando pelos status com mais alunos.

SELECT department_id, COUNT(*) AS num_employees 
FROM hr.employees 
GROUP BY department_id 
ORDER BY num_employees DESC;

//

20. Listar professores e a soma da carga horária das disciplinas.

SELECT job_id, SUM(salary) AS total_salary 
FROM hr.employees 
GROUP BY job_id 
ORDER BY total_salary DESC; 
