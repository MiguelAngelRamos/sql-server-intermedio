```sql
-- Crear tabla de ventas
CREATE TABLE ventas (
    id INT PRIMARY KEY,
    producto NVARCHAR(50) NOT NULL,
    cantidad INT NOT NULL,
    precio DECIMAL(10, 2) NOT NULL,
    fecha_venta DATE NOT NULL
);

-- Insertar datos en la tabla ventas
INSERT INTO ventas (id, producto, cantidad, precio, fecha_venta) VALUES
(1, 'A', 10, 100.00, '2023-01-01'),
(2, 'B', 5, 50.00, '2023-01-02'),
(3, 'A', 7, 70.00, '2023-01-03'),
(4, 'C', 3, 30.00, '2023-01-04'),
(5, 'B', 8, 80.00, '2023-01-05');

SELECT id, producto, cantidad, ROW_NUMBER() OVER (PARTITION BY producto ORDER BY fecha_venta) AS row_num FROM ventas;

INSERT INTO ventas (id, producto, cantidad, precio, fecha_venta) VALUES
(6, 'A', 7, 70.00, '2023-01-05');

SELECT id, producto, cantidad, RANK() OVER (PARTITION BY producto ORDER BY cantidad DESC) AS rank FROM ventas;

INSERT INTO ventas (id, producto, cantidad, precio, fecha_venta) VALUES
(7, 'A', 5, 50.00, '2023-01-06');

SELECT id, producto, cantidad, DENSE_RANK() OVER (PARTITION BY producto ORDER BY cantidad DESC) AS dense_rank FROM ventas;

SELECT id, producto, cantidad, NTILE(2) OVER( ORDER BY cantidad DESC) AS ntile FROM ventas;


```