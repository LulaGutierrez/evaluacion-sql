CREATE DATABASE IF NOT EXISTS evaluacion;
USE evaluacion;
-- DROP DATABASE IF EXISTS evaluacion;

CREATE TABLE usuarios (
id_usuario INT AUTO_INCREMENT NOT NULL,
nombre VARCHAR(45) NOT NULL,
email VARCHAR(60) NOT NULL,
PRIMARY KEY (id_usuario)
);

CREATE TABLE notas (
id_nota INT AUTO_INCREMENT NOT NULL,
id_usuario INT NOT NULL,
titulo VARCHAR(100) NOT NULL,
fecha_creacion DATE NOT NULL,
ultima_modificacion DATE NULL,
descripcion TEXT,
eliminacion BOOLEAN,
id_categoria INT,
FOREIGN KEY (id_usuario) REFERENCES usuarios (id_usuario) ON DELETE CASCADE ON UPDATE CASCADE, 
PRIMARY KEY (id_nota)
);

CREATE TABLE categorias (
id_categoria INT AUTO_INCREMENT NOT NULL,
nombre VARCHAR(45) NOT NULL,
PRIMARY KEY (id_categoria)
);

CREATE TABLE categorias_notas(
id_categorias_notas INT NOT NULL,
id_nota INT NOT NULL,
id_categoria INT NOT NULL,
FOREIGN KEY (id_nota) REFERENCES notas(id_nota) ON DELETE CASCADE ON UPDATE CASCADE,
FOREIGN KEY (id_categoria) REFERENCES categorias(id_categoria) ON DELETE CASCADE ON UPDATE CASCADE,
PRIMARY KEY (id_categorias_notas)
);
-- generar 10 registros para cada table

INSERT INTO usuarios (nombre, email) VALUES ('Gastón', 'gr@gmail.com'), ('Abril', 'aby@gmail.com'), ('Azu', 'azula@gmail.com'), ('Airton', 'air@gmail.com'), ('Lucas', 'luki@gmail.com'), ('Anto', 'anto@gmail.com'), ('Rama', 'rama@gmail.com'), ('Esteban', 'pipi@gmail.com'), ('Juli', 'juli@gmail.com'), ('Guada', 'guadis@gmail.com');

INSERT INTO notas(id_usuario, titulo, fecha_creacion, ultima_modificacion, descripcion, eliminacion, id_categoria) VALUES 
(1, 'Base de datos relacional', '2020-09-10', '2020-09-10', 'Elemento que almacena información respetando una estructura determinada y normalizada de tablas, campos y registros, usualmente relacionados entre sí, de manera tal que se mantenga la consistencia de la información allí alojada.', FALSE, 1), 
(1, 'Base de datos plana', '2020-09-11', '2020-09-11', 'La base de datos plana, a diferencia de la relacional, puede almacenar información general y depender de una o dos tablas no relacionadas entre sí. Usualmente este tipo de base de datos se utiliza para almacenar LOGs de una base de datos relacional más potente.', FALSE, 1), 
(2, 'Clave primaria', '2021-09-11', '2021-10-15', 'Es la columna o grupo de columnas de una tabla que identifica de forma exclusiva cada fila de la tabla. Impiden que los datos de dicho registro sean del tipo Nulo y agilizan la búsqueda de la información utilizando mecanismos acordes.', FALSE, 3), 
(2, 'Clave foránea', '2021-09-12', '2021-10-15', 'Es una clave específica que permite referenciar a dos o más tablas de una base de datos. La misma debe estar conformada por una clave primaria o clave candidata en la tabla de referencia.', FALSE, 3),
(3, 'Tipos de datos', '2021-11-01', '2021-11-01', 'Es la forma en la cual se define la información estructurada que se almacena en una tabla SQL. Los mismos pueden variar entre tipos de datos que almacenan texto, valores alfanuméricos, numéricos, de fecha, booleanos, entre otros tantos.', TRUE, 10),
(6, 'Inner join', '2021-11-28', '2021-11-29', 'Combina los registros de dos tablas si hay valores coincidentes en un campo común.', FALSE, 5),
(10, 'MAX()', '2022-04-28', '2022-04-31', 'La sentencia MAX() permite obtener el valor mínimo de un conjunto de datos numéricos alojados en la columna de una tabla.', TRUE, 2),
(5, 'MIN()', '2022-05-10', '2022-08-08', 'La sentencia MIN() permite obtener el valor mínimo de un conjunto de datos numéricos alojados en la columna de una tabla.', FALSE, 2),
(8, 'HAVING()', '2022-01-01', '2022-08-08', 'Es una sentencia SQL utilizada para devolver filas donde los valores agregados cumplan con condiciones previamente especificadas. Se que lo hice mal, no importa', FALSE, 4),
(7, 'Subconsultas SELECT', '2022-06-15', '2022-06-15', 'La subconsulta SELECT forma parte de DML y, utilizada dentro de una subconsulta, se ocupa de obtener información clave o adicional de otra tabla, que servirá de utilidad para complementar a la consulta SELECT principal.', TRUE, 6);

INSERT INTO categorias(nombre) VALUES ('Base de datos'), ('Funciones de agregación'), ('Claves'), ('Select'), ('Join'), ('Subconsultas'), ('Alter'),('Relaciones'), ('Relaciones'), ('Tipos de datos');