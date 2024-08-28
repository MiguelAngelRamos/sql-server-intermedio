```sql
CREATE DATABASE VentasProductos;
GO

USE VentasProductos;
GO
-- Tabla Productos
CREATE TABLE Productos (
    ProductoID INT IDENTITY(1,1) PRIMARY KEY,
    Nombre NVARCHAR(100) NOT NULL,
    Precio DECIMAL(10, 2) NOT NULL
);

-- Tabla Clientes
CREATE TABLE Clientes (
    ClienteID INT IDENTITY(1,1) PRIMARY KEY,
    Nombre NVARCHAR(100) NOT NULL,
    Email NVARCHAR(100) NOT NULL
);

-- Tabla Ventas
CREATE TABLE Ventas (
    VentaID INT IDENTITY(1,1) PRIMARY KEY,
    ProductoID INT FOREIGN KEY REFERENCES Productos(ProductoID),
    ClienteID INT FOREIGN KEY REFERENCES Clientes(ClienteID),
    Cantidad INT NOT NULL,
    FechaVenta DATETIME DEFAULT GETDATE()
);


-- Insertar Productos
INSERT INTO Productos (Nombre, Precio) VALUES 
('Laptop', 1200.00),
('Mouse', 25.50),
('Teclado', 45.00),
('Monitor', 300.00),
('Tablet', 150.00),
('Impresora', 200.00),
('Auriculares', 50.00),
('Cámara', 400.00),
('Micrófono', 70.00),
('Altavoces', 120.00);

-- Productos sin ventas asociadas
INSERT INTO Productos (Nombre, Precio) VALUES 
('Smartwatch', 250.00),
('Proyector', 450.00);

-- Insertar clientes
INSERT INTO Clientes (Nombre, Email) VALUES 
('Juan Pérez', 'juan.perez@academy.com'),
('Ana Gómez', 'ana.gomez@academy.com'),
('Luis Rodríguez', 'luis.rodriguez@academy.com'),
('María López', 'maria.lopez@academy.com'),
('Pedro Fernández', 'pedro.fernandez@academy.com'),
('Laura Martínez', 'laura.martinez@academy.com'),
('Carlos Sánchez', 'carlos.sanchez@academy.com'),
('Marta Díaz', 'marta.diaz@academy.com'),
('Sofía Torres', 'sofia.torres@academy.com'),
('Javier González', 'javier.gonzalez@academy.com');

-- Cliente sin ventas  asociadas
INSERT INTO Clientes (Nombre, Email) VALUES 
('Ricardo Mendoza', 'ricardo.mendoza@academy.com');

-- Insertar ventas
INSERT INTO Ventas (ProductoID, ClienteID, Cantidad) VALUES 
(1, 1, 2),  -- Juan Pérez compra 2 Laptops
(2, 2, 5),  -- Ana Gómez compra 5 Mouses
(3, 3, 3),  -- Luis Rodríguez compra 3 Teclados
(4, 4, 1),  -- María López compra 1 Monitor
(5, 5, 2),  -- Pedro Fernández compra 2 Tablets
(6, 6, 1),  -- Laura Martínez compra 1 Impresora
(7, 7, 4),  -- Carlos Sánchez compra 4 Auriculares
(8, 8, 2),  -- Marta Díaz compra 2 Cámaras
(9, 9, 6),  -- Sofía Torres compra 6 Micrófonos
(10, 10, 3), -- Javier González compra 3 Altavoces
(1, 2, 1),  -- Ana Gómez compra 1 Laptop
(3, 4, 2),  -- María López compra 2 Teclados
(5, 6, 1),  -- Laura Martínez compra 1 Tablet
(7, 8, 1),  -- Marta Díaz compra 1 Auricular
(2, 9, 3),  -- Sofía Torres compra 3 Mouses
(4, 10, 1), -- Javier González compra 1 Monitor
(6, 1, 1),  -- Juan Pérez compra 1 Impresora
(8, 3, 2),  -- Luis Rodríguez compra 2 Cámaras
(9, 5, 1),  -- Pedro Fernández compra 1 Micrófono
(10, 7, 2); -- Carlos Sánchez compra 2 Altavoces
```