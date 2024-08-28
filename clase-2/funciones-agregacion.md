```sql

-- FUNCIONES DE AGREGACION
-- Contar el numero de ventas realizadas
SELECT COUNT(*) AS TotalVentas FROM VENTAS;

-- Calcular la suma total de las cantidades vendidas por producto
SELECT ProductoID, SUM(Cantidad) AS TotalVendido FROM Ventas GROUP BY ProductoID;

SELECT p.ProductoID, p.Nombre AS Producto, SUM(v.Cantidad) AS TotalVendido
FROM Ventas v
INNER JOIN Productos p ON v.ProductoID = p.ProductoID
GROUP BY p.ProductoID, p.Nombre;
```