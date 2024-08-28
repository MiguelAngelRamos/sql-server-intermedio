```sql

-- Composion interna INNER JOIN
-- Mostrar las ventas junto con los detalles de producto y cliente

SELECT v.VentaID, c.Nombre AS Cliente, p.Nombre AS Producto, v.Cantidad, v.FechaVenta FROM Ventas v
INNER JOIN Clientes c ON v.ClienteID = c.ClienteID
INNER JOIN Productos p ON v.ProductoID = p.ProductoID;

-- LEFT JOIN 
-- Muestra todos los productos, incluyendo aquellos que no tienen ventas asociadas
SELECT p.Nombre AS Producto, v.Cantidad, c.Nombre as Cliente, v.FechaVenta
FROM Productos p
LEFT JOIN Ventas v ON p.ProductoID = v.ProductoID
LEFT JOIN Clientes c ON  v.ClienteID = c.ClienteID; 

-- RIGHT JOIN
-- Muestra todos los clientes, incluidas aquellas filas donde no hay ventas asociadas.
SELECT c.Nombre AS Cliente, v.VentaID, p.Nombre AS Producto, v.Cantidad, v.FechaVenta
FROM Ventas v
RIGHT JOIN Clientes c ON v.ClienteID = c.ClienteID
LEFT JOIN Productos p ON v.ProductoID = p.ProductoID;

-- Queremos mostrar todos los productos, incluyendo aquellos que no tienen ventas y para los productos que si tienen ventas, obtener la informacion del cliente
-- Que realizo la compra
SELECT p.Nombre AS Producto, v.Cantidad, c.Nombre AS Cliente, v.FechaVenta FROM Productos p
LEFT JOIN Ventas v ON p.ProductoID  = v.ProductoID -- Incluye todos los productos, incluso lo que no tienen ventas
LEFT JOIN Clientes c ON v.ClienteID = c.ClienteID;

-- FULL OUTER JOIN
-- Muestra todas la ventas, todos los productos y clientes, independiente de si estan asociados o no.
SELECT v.VentaID, c.Nombre AS Cliente, p.Nombre AS Producto, v.Cantidad, v.FechaVenta FROM Ventas v
FULL OUTER JOIN Clientes c ON v.ClienteID = c.ClienteID
FULL OUTER JOIN Productos p ON v.ProductoID = p.ProductoID;
```