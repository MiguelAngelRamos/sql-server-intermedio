```sql
SELECT * FROM Empleados;
SELECT * FROM Productos;
SELECT * FROM Ventas;

-- Calcular el salario Promedio por departamento y Comparar cada empleado con el promedio

SELECT 
	EmpleadoID, 
	Nombre, 
	Apellido, 
	Departamento, 
	Salario,
	AVG(Salario) OVER (PARTITION BY Departamento) AS Salario_Promedio_Departamento,
	Salario - AVG(Salario) OVER (PARTITION BY Departamento) AS Diferencia_Promedio
FROM Empleados;

-- Clasificar (RANGO) a los empleados segun su salaario dentro de cada departamento

SELECT 
	EmpleadoID, 
	Nombre, 
	Apellido, 
	Departamento, 
	Salario,
	RANK() OVER (PARTITION BY Departamento ORDER BY Salario DESC) AS Rango_Salario_Deparamento
FROM Empleados;

-- Calcular la Mediana de Salarios por Deparamento 
-- 
SELECT DISTINCT
Departamento,
PERCENTILE_CONT(0.5) WITHIN GROUP (ORDER BY Salario) OVER (PARTITION BY Departamento) AS Mediana_Salario_Deparamento
FROM Empleados;

SELECT * FROM Empleados;
-- Mostrar el top 3 de Empleados con Mayor Salario en cada Deparamento
WITH EmpleadosConRango AS (
SELECT 
	EmpleadoID, 
	Nombre, 
	Apellido, 
	Departamento, 
	Salario,
	ROW_NUMBER() OVER (PARTITION BY Departamento ORDER BY Salario DESC) AS Row_Num
FROM Empleados
)
SELECT 
	EmpleadoID, 
	Nombre, 
	Apellido, 
	Departamento, 
	Salario
FROM EmpleadosConRango
WHERE Row_Num <=3
ORDER BY Departamento, Row_Num;
```