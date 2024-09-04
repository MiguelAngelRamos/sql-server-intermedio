```sql

-- MEDIA (PROMEDIO - AVERAGE)
SELECT AVG(Salario) FROM Empleados; -- 3022.85

-- Mediana (Percentil 50)

SELECT DISTINCT PERCENTILE_CONT(0.5) WITHIN GROUP(ORDER BY Salario) OVER () AS MedianaSalario FROM Empleados;

-- MODA 
SELECT TOP 1 WITH TIES Salario FROM Empleados GROUP BY Salario ORDER BY COUNT(*) DESC;

-- VARIANZA
SELECT VAR(Salario) AS VarianzaSalario FROM Empleados;

-- DESVIACION ESTANDAR "Cuanto varian los salarios respecto al promedio(media)"
SELECT STDEV(Salario) AS DesviacionEstandarSalario FROM Empleados; -- 296.13

-- PERCENTILES

SELECT DISTINCT PERCENTILE_CONT(0.90)  WITHIN GROUP(ORDER BY Salario) OVER () AS Percentil90Salario FROM Empleados;
-- Esto significa que el 90% de los empleados ganan menos que este valor 3500

-- Contar Count(*)
SELECT COUNT(*) AS TotalEmpleados FROM empleados;

-- Valor maximo y valor minimo de los salarios
SELECT MAX(Salario) AS Salario_Max, MIN(Salario) AS Salario_Min FROM Empleados
```