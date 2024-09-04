```sql
-- Crear la tabla de Empleados
CREATE TABLE Empleados (
    EmpleadoID INT IDENTITY(1,1) PRIMARY KEY,
    Nombre NVARCHAR(50),
    Apellido NVARCHAR(50),
    Departamento NVARCHAR(50),
    Salario DECIMAL(10, 2)
);

-- Crear la tabla de Productos
CREATE TABLE Productos (
    ProductoID INT IDENTITY(1,1) PRIMARY KEY,
    NombreProducto NVARCHAR(100),
    Precio DECIMAL(10, 2)
);

-- Crear la tabla de Ventas
CREATE TABLE Ventas (
    VentaID INT IDENTITY(1,1) PRIMARY KEY,
    ProductoID INT FOREIGN KEY REFERENCES Productos(ProductoID),
    EmpleadoID INT FOREIGN KEY REFERENCES Empleados(EmpleadoID),
    Cantidad INT,
    FechaVenta DATETIME DEFAULT GETDATE()
);

-- Insertar registros en la tabla de Empleados
INSERT INTO Empleados (Nombre, Apellido, Departamento, Salario)
VALUES 
('Juan', 'Perez', 'Ventas', 3000.00),
('Maria', 'Lopez', 'Marketing', 3500.00),
('Carlos', 'Garcia', 'Ventas', 2800.00),
('Ana', 'Martinez', 'Soporte', 2500.00),
('Luis', 'Gonzalez', 'Ventas', 3200.00),
('Elena', 'Rodriguez', 'Marketing', 3400.00),
('Pedro', 'Sanchez', 'Ventas', 3100.00),
('Sofia', 'Jimenez', 'Soporte', 2700.00),
('Jose', 'Ramos', 'Ventas', 2900.00),
('Laura', 'Morales', 'Marketing', 3300.00);

-- Insertar más empleados con salarios repetidos para evidenciar la moda
INSERT INTO Empleados (Nombre, Apellido, Departamento, Salario)
VALUES 
('Carlos', 'Diaz', 'Ventas', 3000.00),  -- Repetido
('Marta', 'Suarez', 'Ventas', 3000.00),  -- Repetido
('Julio', 'Castro', 'Soporte', 2800.00),  -- Repetido
('Ana', 'Lopez', 'Marketing', 2800.00),  -- Repetido
('Luis', 'Ramirez', 'Ventas', 3500.00),  -- Repetido
('Paula', 'Martinez', 'Soporte', 3500.00); -- Repetido

INSERT INTO Empleados (Nombre, Apellido, Departamento, Salario)
VALUES 
('Sofia', 'Araya', 'Ventas', 3000.00);  -- Repetido
-- Insertar más empleados con salarios repetidos para evidenciar la moda por departamento
INSERT INTO Empleados (Nombre, Apellido, Departamento, Salario)
VALUES 
('Francisco', 'Gutierrez', 'Ventas', 3000.00),  -- Repetido
('Monica', 'Fernandez', 'Ventas', 3000.00),  -- Repetido
('Diego', 'Mora', 'Ventas', 3500.00),  -- Repetido
('Carla', 'Vega', 'Soporte', 2800.00),  -- Repetido
('Esteban', 'Ruiz', 'Soporte', 2500.00),  -- Repetido
('Tomas', 'Navarro', 'Soporte', 3500.00),  -- Repetido
('Sandra', 'Reyes', 'Marketing', 2800.00),  -- Repetido
('Veronica', 'Diaz', 'Marketing', 3400.00),  -- Repetido
('Felipe', 'Torres', 'Marketing', 3500.00);  -- Repetido


-- Insertar más empleados con salarios repetidos para hacer evidente la moda por departamento
INSERT INTO Empleados (Nombre, Apellido, Departamento, Salario)
VALUES 
-- Marketing
('Cristina', 'Hernandez', 'Marketing', 2800.00),  -- Repetido
('Paola', 'Soto', 'Marketing', 2800.00),  -- Repetido
('Javier', 'Martinez', 'Marketing', 2800.00),  -- Repetido

-- Soporte
('Camila', 'Paredes', 'Soporte', 2800.00),  -- Repetido
('Miguel', 'Figueroa', 'Soporte', 2800.00),  -- Repetido
('Pablo', 'Ortiz', 'Soporte', 2800.00),  -- Repetido

-- Ventas
('Daniel', 'Rojas', 'Ventas', 3000.00),  -- Repetido
('Nicolas', 'Silva', 'Ventas', 3000.00),  -- Repetido
('Andres', 'Vargas', 'Ventas', 3000.00);  -- Repetido

-- Insertar registros en la tabla de Productos
INSERT INTO Productos (NombreProducto, Precio)
VALUES 
('Laptop', 1200.00),
('Mouse', 25.00),
('Teclado', 45.00),
('Monitor', 300.00),
('Impresora', 150.00),
('Tablet', 250.00),
('Smartphone', 500.00),
('Cargador', 20.00),
('Auriculares', 75.00),
('Cámara', 600.00);

-- Insertar registros en la tabla de Ventas
INSERT INTO Ventas (ProductoID, EmpleadoID, Cantidad)
VALUES 
(1, 1, 5), -- Juan vendió 5 laptops
(2, 2, 20), -- Maria vendió 20 mouses
(3, 3, 10), -- Carlos vendió 10 teclados
(4, 4, 3), -- Ana vendió 3 monitores
(5, 5, 8), -- Luis vendió 8 impresoras
(6, 6, 6), -- Elena vendió 6 tablets
(7, 7, 12), -- Pedro vendió 12 smartphones
(8, 8, 15), -- Sofia vendió 15 cargadores
(9, 9, 7), -- Jose vendió 7 auriculares
(10, 10, 4), -- Laura vendió 4 cámaras
(1, 2, 2), -- Maria vendió 2 laptops
(3, 3, 5), -- Carlos vendió 5 teclados
(4, 5, 7), -- Luis vendió 7 monitores
(6, 6, 3), -- Elena vendió 3 tablets
(7, 7, 9), -- Pedro vendió 9 smartphones
(8, 8, 10), -- Sofia vendió 10 cargadores
(9, 9, 6), -- Jose vendió 6 auriculares
(2, 1, 25), -- Juan vendió 25 mouses
(5, 10, 10), -- Laura vendió 10 impresoras
(6, 5, 4); -- Luis vendió 4 tablets

-- Consultar los datos insertados
SELECT * FROM Empleados;
SELECT * FROM Productos;
SELECT * FROM Ventas;


```