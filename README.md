
# DelightGourmet DB

Nombre: Tomás Olaya Pinto
Grupo: J3
Filtro SQL Campuslands 2024

Bienvenidos al proyecto de creación de la base de datos para nuestro restaurante, Gourmet
Delight. Como propietario de este restaurante, necesito una solución integral para gestionar la
información relacionada con nuestros clientes, menús, pedidos y los detalles de cada pedido. La
base de datos será crucial para organizar y mantener nuestros registros de manera eficiente,
permitiéndonos brindar un mejor servicio y tomar decisiones informadas para el crecimiento del
negocio.



## ScriptTablas

A través del siguiente script sql se muestra la creación de la base de datos
```
--- Creacion de la base de datos ---

CREATE DATABASE gourmet_Delight;

USE gourmet_Delight;

--- Creacion de las tablas correspondientes del ejercicio ---

CREATE TABLE clientes(
clienteID INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
nombre varchar(100) NOT NULL,
correo varchar(100) NOT NULL,
telefono varchar(15) NOT NULL,
fecha_registro date NOT NULL
);

CREATE TABLE pedidos(
pedidoID INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
clienteID INT NOT NULL,
fecha DATE NOT NULL,
total DECIMAL(10,2),
FOREIGN KEY (clienteID) REFERENCES clientes(clienteID)
);

CREATE TABLE menus(
menuID INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
nombre VARCHAR(100) NOT NULL,
descripcion text NOT NULL,
precio DECIMAL(10,2)
);

CREATE TABLE detallesPedido(
pedidoID INT NOT NULL,
menuID INT NOT NULL,
cantidad int NOT NULL,
precioUnitario DECIMAL(10,2),
FOREIGN KEY (menuID) REFERENCES menus(menuID),
FOREIGN KEY (pedidoID) REFERENCES pedidos(pedidoID)
);
```

## Inserciones
Las Inserciones propuestas para el ejercicio son las siguientes:
```
-- Insertar datos en la tabla Clientes --
INSERT INTO clientes (nombre, correo, telefono, fecha_registro) VALUES
('Juan Perez', 'juan.perez@example.com', '123-456-7890', '2024-01-01'),
('Maria Lopez', 'maria.lopez@example.com', '123-456-7891', '2024-01-05'),
('Carlos Mendoza', 'carlos.mendoza@example.com', '123-456-7892', '2024-01-08'),
('Ana Gonzalez', 'ana.gonzalez@example.com', '123-456-7893', '2024-02-20'),
('Luis Torres', 'luis.torres@example.com', '123-456-7894', '2024-03-05'),
('Laura Rivera', 'laura.rivera@example.com', '123-456-7895', '2024-03-15'),
('Fernando García', 'fernando.garcia@example.com', '123-456-7896', '2024-04-01'),
('Isabel Fernández', 'isabel.fernandez@example.com', '123-456-7897', '2024-04-15'),
('Ricardo Morales', 'ricardo.morales@example.com', '123-456-7898', '2024-05-01'),
('Lucía Martínez', 'lucia.martinez@example.com', '123-456-7899', '2024-05-10'),
('Santiago Jiménez', 'santiago.jimenez@example.com', '123-456-7900', '2024-05-10'),
('Patricia Romero', 'patricia.romero@example.com', '123-456-7901', '2024-05-15');
```
```
-- Insertar datos en la tabla Menus
INSERT INTO menus (nombre, descripcion, precio) VALUES
('Ensalada César', 'Ensalada con lechuga romana, crutones y aderezo César', 12.50),
('Sopa de Tomate', 'Sopa cremosa de tomate con albahaca', 8.75),
('Filete de Res', 'Filete de res a la parrilla con papas y vegetales', 25.00),
('Pasta Alfredo', 'Pasta con salsa Alfredo y pollo', 15.00),
('Tarta de Queso', 'Tarta de queso con salsa de frambuesa', 7.50),
('Café Americano', 'Café americano recién preparado', 3.00);
```
```
-- Insertar datos en la tabla pedidos --
INSERT INTO pedidos (clienteID, fecha, total) VALUES
(1, '2024-05-15', 40.00),
(1, '2024-06-01', 25.50),
(2, '2024-05-20', 35.75),
(2, '2024-06-05', 48.00),
(3, '2024-06-10', 55.00),
(4, '2024-05-30', 32.75),
(4, '2024-06-15', 28.25),
(5, '2024-06-20', 45.00), 
(6, '2024-05-25', 22.50),
(6, '2024-06-10', 33.75), 
(7, '2024-05-15', 50.50),
(7, '2024-06-25', 47.00), 
(8,	'2024-05-20', 44.75), 
(8, '2024-06-30', 39.50),
(9, '2024-05-25', 41.00),
(10,'2024-06-04', 55.75),
(11,'2024-06-09', 52.00),
(12,'2024-06-15', 46.25);
```
```
--- Insertar datos en la tabla detalles_Pedidos ---
INSERT INTO detallesPedido (pedidoID, menuID, cantidad, precioUnitario) VALUES
(1, 1, 1, 12.50),
(1, 3, 1, 25.00),
(1, 6, 3, 3.00),
(2, 2, 1, 8.75),
(2, 4, 1, 15.00),
(2, 5, 1, 7.50),
(3, 1, 1, 12.50),
(3, 4, 1, 15.00),
(3, 6, 2, 3.00),
(4, 3, 1, 25.00),
(4, 6, 1, 3.00),
(5, 1, 2, 12.50),
(5, 5, 2, 7.50),
(6, 2, 1, 8.75),
(6, 6, 3, 3.00),
(7, 1, 2, 12.50),
(7, 4, 1, 15.00),
(8, 2, 1, 8.75),
(8, 5, 2, 7.50),
(9, 3, 1, 25.00),
(9, 6, 3, 3.00),
(10, 1, 1, 12.50),
(10, 3, 1, 25.00),
(11, 4, 1, 15.00),
(11, 5, 1, 7.50),
(11, 6, 2, 3.00),
(12, 2, 1, 8.75),
(12, 4, 1, 15.00),
(12, 5, 1, 7.50),
(13, 1, 2, 12.50),
(13, 4, 1, 15.00),
(14, 2, 1, 8.75),
(14, 5, 2, 7.50),
(15, 3, 1, 25.00),
(15, 6, 3, 3.00),
(16, 1, 1, 12.50),
(16, 3, 1, 25.00),
(17, 4, 1, 15.00),
(17, 5, 1, 7.50),
(17, 6, 2, 3.00),
(18, 2, 1, 8.75),
(18, 4, 1, 15.00),
(18, 5, 1, 7.50);
```
## Consultas
Las consultas propuestas para este ejercicio son las siguientes:
```
---	1. Obtener la lista de todos los menús con sus precios ---
SELECT m.nombre, m.precio
FROM menus as m;
```
```
--- 2. Encontrar todos los pedidos realizados por el cliente 'Juan Perez' ---
SELECT p.pedidoID, p.fecha, p.total
FROM clientes AS c
right join pedidos as p ON p.clienteID = c.clienteID
WHERE c.nombre LIKE 'Juan Perez';
```
```
--- 3. Listar los detalles de todos los pedidos, incluyendo el nombre del menú, cantidad y precio unitario ---
SELECT dp.pedidoID, m.nombre, dp.cantidad, dp.precioUnitario
FROM detallesPedido as dp
JOIN menus m ON dp.menuID = m.menuID;
```
```
--- 4. Calcular el total gastado por cada cliente en todos sus pedidos ---
SELECT c.nombre AS nombreCliente, SUM(p.total) AS TotalGastado
FROM menus AS m, pedidos AS p
JOIN clientes AS c ON p.clienteID = c.ClienteID
GROUP BY c.nombre;
```
```
--- 5. Encontrar los menús con un precio mayor a $10 ---
SELECT m.nombre, m.precio
FROM menus AS m
WHERE m.precio >= 10.00;
```
```
--- 6. Obtener el menú más caro pedido al menos una vez ---
SELECT m.nombre, m.precio
FROM menus AS m
JOIN detallesPedido dp ON m.menuID = dp.menuID
GROUP BY m.nombre, m.precio
ORDER BY m.precio DESC
LIMIT 1;
```
```
--- 7. Listar los clientes que han realizado más de un pedido ---
SELECT c.nombre, c.correo
FROM clientes as c
JOIN pedidos p ON c.clienteID = p.clienteID
GROUP BY c.clienteID
HAVING COUNT(p.pedidoID) > 1;
```
```
--- 8. Obtener el cliente con el mayor gasto total---
SELECT c.nombre
FROM clientes c
JOIN pedidos p ON c.clienteID = p.clienteID
JOIN detallesPedido AS dp ON p.pedidoID = dp.pedidoID 
GROUP BY c.clienteID
LIMIT 1;
```
```
--- 9. Mostrar el pedido más reciente de cada cliente ---

SELECT c.nombre AS nombre_cliente, p.fecha, p.total
FROM clientes c
JOIN pedidos p ON c.clienteID = p.clienteID
JOIN (
    SELECT clienteID, MAX(fecha) AS fecha_reciente
    FROM pedidos
    GROUP BY clienteID
) p_max ON p.clienteID = p_max.clienteID AND p.fecha = p_max.fecha_reciente;
```
```
--- 10.Obtener el detalle de pedidos (menús y cantidades) para el cliente 'Juan Perez'.
SELECT dp.pedidoID AS id, m.nombre, dp.cantidad, dp.preciounitario 
FROM detallesPedido AS dp 
JOIN menus m ON dp.menuID = m.menuID 
JOIN pedidos p ON dp.pedidoID = p.pedidoID 
JOIN clientes c ON c.clienteID = p.clienteID
WHERE c.nombre = 'Juan Perez';
```
## Procedimientos almacenados
Los Procedimientos a realizar son los siguientes:
```
--- 1. Crear un procedimiento almacenado para agregar un nuevo cliente ---
DELIMITER //
CREATE PROCEDURE sp_agregar_nuevo_cliente(
  IN p_nombre VARCHAR(100),
  IN p_correo VARCHAR(100),
  IN p_telefono VARCHAR(15),
  IN p_fecha_registro DATE
)
BEGIN -- Agregar los valores del nuevo cliente
  INSERT INTO clientes (nombre, correo, telefono, fecha_registro)
  VALUES (p_nombre, p_correo, p_telefono, p_fecha_registro);
END //
DELIMITER ;
```
```
--- 2.Crear un procedimiento almacenado para obtener los detalles de un pedido ---
DELIMITER //
CREATE PROCEDURE ObtenerDetallesPedido(
  IN p_pedidoID INT
)
BEGIN --- Obtener los detalles del pedido
  SELECT 
    m.nombre AS nombre_menu,
    dp.cantidad,
    dp.precioUnitario
  FROM 
    detallesPedido dp
  JOIN menus m ON dp.menuID = m.menuID
  WHERE 
    dp.pedidoID = p_pedidoID;
END //
DELIMITER ;
```
```
--- 3.Crear un procedimiento almacenado para actualizar el precio de un menú --
DELIMITER //
CREATE PROCEDURE ActualizarPrecioMenu(
  IN p_menuID INT,
  IN p_nuevo_precio DECIMAL(10, 2)
)
BEGIN -- Actualizar el precio de un menu
  UPDATE menus
  SET precio = p_nuevo_precio
  WHERE menuID = p_menuID;
END //
DELIMITER ;
```
```
--- 4.Crear un procedimiento almacenado para eliminar un cliente y sus pedidos 
DELIMITER //
CREATE PROCEDURE EliminarCliente(
  IN p_clienteID INT
)
BEGIN
  -- Eliminar pedidos del cliente
  DELETE FROM pedidos
  WHERE clienteID = p_clienteID;
  
  -- Eliminar detalles de pedidos del cliente
  DELETE FROM detallesPedido
  WHERE pedidoID IN (SELECT pedidoID FROM pedidos WHERE clienteID = p_clienteID);
  
  -- Eliminar el cliente
  DELETE FROM clientes
  WHERE clienteID = p_clienteID;
END //
DELIMITER ;
```
```
--- 5.Crear un procedimiento almacenado para obtener el total gastado por un cliente ---
DELIMITER //
CREATE PROCEDURE ObtenerTotalGastado(
  IN p_clienteID INT
)
BEGIN -- Proceso de calcular el total gastado por el cliente
  SELECT SUM(p.total) AS TotalGastado
  FROM pedidos p
  WHERE p.clienteID = p_clienteID;
END //
DELIMITER ;
```