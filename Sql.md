# 🗄️ Guía Completa de SQL

Bases de datos relacionales desde cero

---

## 💡 ¿Qué es SQL?

**SQL** (Structured Query Language) es el lenguaje para comunicarte con bases de datos relacionales. Te permite crear, leer, actualizar y eliminar datos.

**Operaciones CRUD**
<div style="text-align: center; background: #f8f9fa; border: 2px solid #e9ecef; border-radius: 10px; padding: 20px; margin: 15px 0;">
  <span style="display: inline-block; padding: 8px 16px; border-radius: 6px; font-weight: bold; margin: 5px; color: white; background: #28a745;">C - Create (INSERT)</span>
  <span style="display: inline-block; padding: 8px 16px; border-radius: 6px; font-weight: bold; margin: 5px; color: white; background: #007bff;">R - Read (SELECT)</span>
  <span style="display: inline-block; padding: 8px 16px; border-radius: 6px; font-weight: bold; margin: 5px; color: #333; background: #ffc107;">U - Update (UPDATE)</span>
  <span style="display: inline-block; padding: 8px 16px; border-radius: 6px; font-weight: bold; margin: 5px; color: white; background: #dc3545;">D - Delete (DELETE)</span>
</div>

> [!INFO] ℹ️ Bases de datos populares que usan SQL:
> *   **MySQL** - Gratis, muy popular en web
> *   **PostgreSQL** - Gratis, muy potente
> *   **SQLite** - Ligera, ideal para apps móviles
> *   **SQL Server** - De Microsoft
> *   **Oracle** - Empresarial

---

## 📊 Estructura de una base de datos

Una base de datos se organiza en **tablas**, como hojas de Excel:

<div style="background: #fff; border: 2px solid #336791; border-radius: 8px; overflow: hidden; margin: 15px 0;">
  <div style="background: #336791; color: white; padding: 10px 15px; font-weight: bold;">📋 Tabla: usuarios</div>
  <div style="padding: 10px;">
    <table style="width: 100%; border-collapse: collapse; font-size: 14px;">
      <thead style="background: #f8f9fa;">
        <tr>
          <th style="padding: 10px; border: 1px solid #dee2e6; background: #e9ecef; color: #333;">id</th>
          <th style="padding: 10px; border: 1px solid #dee2e6; background: #e9ecef; color: #333;">nombre</th>
          <th style="padding: 10px; border: 1px solid #dee2e6; background: #e9ecef; color: #333;">email</th>
          <th style="padding: 10px; border: 1px solid #dee2e6; background: #e9ecef; color: #333;">edad</th>
          <th style="padding: 10px; border: 1px solid #dee2e6; background: #e9ecef; color: #333;">ciudad</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td style="padding: 10px; border: 1px solid #dee2e6;">1</td>
          <td style="padding: 10px; border: 1px solid #dee2e6;">Juan Pérez</td>
          <td style="padding: 10px; border: 1px solid #dee2e6;">juan@mail.com</td>
          <td style="padding: 10px; border: 1px solid #dee2e6;">28</td>
          <td style="padding: 10px; border: 1px solid #dee2e6;">Lima</td>
        </tr>
        <tr>
          <td style="padding: 10px; border: 1px solid #dee2e6;">2</td>
          <td style="padding: 10px; border: 1px solid #dee2e6;">María García</td>
          <td style="padding: 10px; border: 1px solid #dee2e6;">maria@mail.com</td>
          <td style="padding: 10px; border: 1px solid #dee2e6;">34</td>
          <td style="padding: 10px; border: 1px solid #dee2e6;">Bogotá</td>
        </tr>
        <tr>
          <td style="padding: 10px; border: 1px solid #dee2e6;">3</td>
          <td style="padding: 10px; border: 1px solid #dee2e6;">Carlos López</td>
          <td style="padding: 10px; border: 1px solid #dee2e6;">carlos@mail.com</td>
          <td style="padding: 10px; border: 1px solid #dee2e6;">25</td>
          <td style="padding: 10px; border: 1px solid #dee2e6;">Lima</td>
        </tr>
      </tbody>
    </table>
  </div>
</div>

<table style="width: 100%; border-collapse: collapse; margin: 15px 0; font-size: 14px;">
  <thead style="background: #336791; color: white;">
    <tr>
      <th style="border: 1px solid #dee2e6; padding: 10px;">Término</th>
      <th style="border: 1px solid #dee2e6; padding: 10px;">Descripción</th>
      <th style="border: 1px solid #dee2e6; padding: 10px;">Ejemplo</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="border: 1px solid #dee2e6; padding: 10px;"><strong>Base de datos</strong></td>
      <td style="border: 1px solid #dee2e6; padding: 10px;">Contenedor de todas las tablas</td>
      <td style="border: 1px solid #dee2e6; padding: 10px;"><code>mi_tienda</code></td>
    </tr>
    <tr style="background: #f8f9fa;">
      <td style="border: 1px solid #dee2e6; padding: 10px;"><strong>Tabla</strong></td>
      <td style="border: 1px solid #dee2e6; padding: 10px;">Colección de datos relacionados</td>
      <td style="border: 1px solid #dee2e6; padding: 10px;"><code>usuarios</code>, <code>productos</code></td>
    </tr>
    <tr>
      <td style="border: 1px solid #dee2e6; padding: 10px;"><strong>Columna (Campo)</strong></td>
      <td style="border: 1px solid #dee2e6; padding: 10px;">Un atributo de los datos</td>
      <td style="border: 1px solid #dee2e6; padding: 10px;"><code>nombre</code>, <code>email</code>, <code>edad</code></td>
    </tr>
    <tr style="background: #f8f9fa;">
      <td style="border: 1px solid #dee2e6; padding: 10px;"><strong>Fila (Registro)</strong></td>
      <td style="border: 1px solid #dee2e6; padding: 10px;">Una entrada de datos</td>
      <td style="border: 1px solid #dee2e6; padding: 10px;">Un usuario específico</td>
    </tr>
    <tr>
      <td style="border: 1px solid #dee2e6; padding: 10px;"><strong>Primary Key (PK)</strong></td>
      <td style="border: 1px solid #dee2e6; padding: 10px;">Identificador único de cada fila</td>
      <td style="border: 1px solid #dee2e6; padding: 10px;"><code>id</code></td>
    </tr>
    <tr style="background: #f8f9fa;">
      <td style="border: 1px solid #dee2e6; padding: 10px;"><strong>Foreign Key (FK)</strong></td>
      <td style="border: 1px solid #dee2e6; padding: 10px;">Referencia a otra tabla</td>
      <td style="border: 1px solid #dee2e6; padding: 10px;"><code>usuario_id</code></td>
    </tr>
  </tbody>
</table>

---

## 🔤 Tipos de datos comunes

<table style="width: 100%; border-collapse: collapse; margin: 15px 0; font-size: 14px;">
  <thead style="background: #336791; color: white;">
    <tr>
      <th style="border: 1px solid #dee2e6; padding: 10px;">Tipo</th>
      <th style="border: 1px solid #dee2e6; padding: 10px;">Descripción</th>
      <th style="border: 1px solid #dee2e6; padding: 10px;">Ejemplo</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="border: 1px solid #dee2e6; padding: 10px;"><code>INT / INTEGER</code></td>
      <td style="border: 1px solid #dee2e6; padding: 10px;">Números enteros</td>
      <td style="border: 1px solid #dee2e6; padding: 10px;">1, 42, -100</td>
    </tr>
    <tr style="background: #f8f9fa;">
      <td style="border: 1px solid #dee2e6; padding: 10px;"><code>DECIMAL(p,s)</code></td>
      <td style="border: 1px solid #dee2e6; padding: 10px;">Números decimales precisos</td>
      <td style="border: 1px solid #dee2e6; padding: 10px;">19.99, 1234.56</td>
    </tr>
    <tr>
      <td style="border: 1px solid #dee2e6; padding: 10px;"><code>VARCHAR(n)</code></td>
      <td style="border: 1px solid #dee2e6; padding: 10px;">Texto variable (máx n caracteres)</td>
      <td style="border: 1px solid #dee2e6; padding: 10px;">'Hola', 'Juan'</td>
    </tr>
    <tr style="background: #f8f9fa;">
      <td style="border: 1px solid #dee2e6; padding: 10px;"><code>TEXT</code></td>
      <td style="border: 1px solid #dee2e6; padding: 10px;">Texto largo</td>
      <td style="border: 1px solid #dee2e6; padding: 10px;">Descripciones, artículos</td>
    </tr>
    <tr>
      <td style="border: 1px solid #dee2e6; padding: 10px;"><code>DATE</code></td>
      <td style="border: 1px solid #dee2e6; padding: 10px;">Solo fecha</td>
      <td style="border: 1px solid #dee2e6; padding: 10px;">'2024-01-15'</td>
    </tr>
    <tr style="background: #f8f9fa;">
      <td style="border: 1px solid #dee2e6; padding: 10px;"><code>DATETIME / TIMESTAMP</code></td>
      <td style="border: 1px solid #dee2e6; padding: 10px;">Fecha y hora</td>
      <td style="border: 1px solid #dee2e6; padding: 10px;">'2024-01-15 14:30:00'</td>
    </tr>
    <tr>
      <td style="border: 1px solid #dee2e6; padding: 10px;"><code>BOOLEAN</code></td>
      <td style="border: 1px solid #dee2e6; padding: 10px;">Verdadero/Falso</td>
      <td style="border: 1px solid #dee2e6; padding: 10px;">TRUE, FALSE</td>
    </tr>
  </tbody>
</table>

---

## 1. Crear base de datos y tablas

**Crear base de datos:**
```sql
CREATE DATABASE mi_tienda;

-- Usar la base de datos
USE mi_tienda;
```

**Crear tabla:**
```sql
CREATE TABLE usuarios (
    id          INT PRIMARY KEY AUTO_INCREMENT,
    nombre      VARCHAR(100) NOT NULL,
    email       VARCHAR(150) UNIQUE NOT NULL,
    edad        INT,
    ciudad      VARCHAR(50),
    activo      BOOLEAN DEFAULT TRUE,
    created_at  TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

> [!TIP] 💡 Restricciones comunes:
> *   `PRIMARY KEY` - Identificador único
> *   `NOT NULL` - No permite valores vacíos
> *   `UNIQUE` - No permite duplicados
> *   `DEFAULT` - Valor por defecto
> *   `AUTO_INCREMENT` - Se incrementa automáticamente

**Crear tabla con Foreign Key:**
```sql
CREATE TABLE pedidos (
    id          INT PRIMARY KEY AUTO_INCREMENT,
    usuario_id  INT NOT NULL,
    producto    VARCHAR(100),
    cantidad    INT DEFAULT 1,
    precio      DECIMAL(10,2),
    fecha       DATE,
    FOREIGN KEY (usuario_id) REFERENCES usuarios(id)
);
```

**Modificar tabla existente:**
```sql
-- Agregar columna
ALTER TABLE usuarios ADD telefono VARCHAR(20);

-- Eliminar columna
ALTER TABLE usuarios DROP COLUMN telefono;

-- Modificar tipo de columna
ALTER TABLE usuarios MODIFY nombre VARCHAR(200);

-- Eliminar tabla
DROP TABLE usuarios;
```

---

## 2. INSERT - Insertar datos

```sql
-- Insertar una fila
INSERT INTO usuarios (nombre, email, edad, ciudad)
VALUES ('Juan Pérez', 'juan@mail.com', 28, 'Lima');

-- Insertar múltiples filas
INSERT INTO usuarios (nombre, email, edad, ciudad)
VALUES 
    ('María García', 'maria@mail.com', 34, 'Bogotá'),
    ('Carlos López', 'carlos@mail.com', 25, 'Lima'),
    ('Ana Torres', 'ana@mail.com', 30, 'México');
```

> [!WARNING] ⚠️ Nota
> El campo `id` no se incluye porque es `AUTO_INCREMENT`.

---

## 3. SELECT - Consultar datos

**Consultas básicas:**
```sql
-- Seleccionar todas las columnas
SELECT * FROM usuarios;

-- Seleccionar columnas específicas
SELECT nombre, email FROM usuarios;

-- Renombrar columnas (alias)
SELECT nombre AS 'Nombre Completo', email AS 'Correo' 
FROM usuarios;
```

**WHERE - Filtrar resultados:**
```sql
-- Condición simple
SELECT * FROM usuarios WHERE ciudad = 'Lima';

-- Múltiples condiciones (AND / OR)
SELECT * FROM usuarios 
WHERE ciudad = 'Lima' AND edad > 25;

SELECT * FROM usuarios 
WHERE ciudad = 'Lima' OR ciudad = 'Bogotá';

-- Operadores de comparación
SELECT * FROM usuarios WHERE edad >= 18;        -- Mayor o igual
SELECT * FROM usuarios WHERE edad <> 30;        -- Diferente
SELECT * FROM usuarios WHERE edad BETWEEN 20 AND 30;

-- Buscar en lista
SELECT * FROM usuarios 
WHERE ciudad IN ('Lima', 'Bogotá', 'México');

-- Buscar valores NULL
SELECT * FROM usuarios WHERE telefono IS NULL;
SELECT * FROM usuarios WHERE telefono IS NOT NULL;
```

**LIKE - Búsqueda de patrones:**
```sql
-- Empieza con "Juan"
SELECT * FROM usuarios WHERE nombre LIKE 'Juan%';

-- Termina con "@gmail.com"
SELECT * FROM usuarios WHERE email LIKE '%@gmail.com';

-- Contiene "García"
SELECT * FROM usuarios WHERE nombre LIKE '%García%';

-- Un solo carácter comodín (_ )
SELECT * FROM usuarios WHERE nombre LIKE '_uan';
```

> [!TIP] 💡 Comodines de LIKE:
> *   `%` = Cualquier cantidad de caracteres
> *   `_` = Un solo carácter

---

## 4. Ordenar y limitar resultados

```sql
-- Ordenar ascendente (A-Z, menor a mayor)
SELECT * FROM usuarios ORDER BY nombre ASC;

-- Ordenar descendente (Z-A, mayor a menor)
SELECT * FROM usuarios ORDER BY edad DESC;

-- Ordenar por múltiples columnas
SELECT * FROM usuarios 
ORDER BY ciudad ASC, edad DESC;

-- Limitar resultados
SELECT * FROM usuarios LIMIT 5;

-- Paginación (OFFSET = saltar filas)
SELECT * FROM usuarios LIMIT 10 OFFSET 20;
-- Muestra filas 21-30 (salta las primeras 20)

-- Combinado: Los 5 usuarios más jóvenes
SELECT * FROM usuarios 
ORDER BY edad ASC 
LIMIT 5;
```

---

## 5. UPDATE - Actualizar datos

```sql
-- Actualizar un registro específico
UPDATE usuarios 
SET email = 'nuevo@mail.com'
WHERE id = 1;

-- Actualizar múltiples campos
UPDATE usuarios 
SET ciudad = 'Santiago', edad = 29
WHERE id = 1;

-- Actualizar basado en condición
UPDATE usuarios 
SET activo = FALSE
WHERE edad < 18;

-- Incrementar valor
UPDATE productos 
SET precio = precio * 1.10  -- Aumentar 10%
WHERE categoria = 'electrónica';
```

> [!CAUTION] 🚨 ¡CUIDADO!
> Si olvidas el `WHERE`, actualizarás TODOS los registros:
> `UPDATE usuarios SET activo = FALSE;` ← ¡Esto afecta a TODOS!

---

## 6. DELETE - Eliminar datos

```sql
-- Eliminar un registro específico
DELETE FROM usuarios WHERE id = 5;

-- Eliminar con condición
DELETE FROM usuarios WHERE activo = FALSE;

-- Eliminar TODOS los registros (mantiene la tabla)
DELETE FROM usuarios;

-- Eliminar TODO más rápido (reinicia AUTO_INCREMENT)
TRUNCATE TABLE usuarios;
```

> [!CAUTION] 🚨 ¡CUIDADO!
> DELETE sin WHERE elimina TODO:
> `DELETE FROM usuarios;` ← ¡Elimina TODOS los usuarios!

> [!TIP] 💡 Buena práctica:
> Antes de UPDATE o DELETE, ejecuta un SELECT con la misma condición para verificar qué registros se afectarán.

---

## 7. Funciones de agregación

```sql
-- Contar registros
SELECT COUNT(*) FROM usuarios;
SELECT COUNT(*) FROM usuarios WHERE ciudad = 'Lima';

-- Suma
SELECT SUM(precio) FROM pedidos;

-- Promedio
SELECT AVG(edad) FROM usuarios;

-- Mínimo y Máximo
SELECT MIN(edad), MAX(edad) FROM usuarios;

-- Valores únicos
SELECT DISTINCT ciudad FROM usuarios;
```

---

## 8. GROUP BY - Agrupar datos

```sql
-- Contar usuarios por ciudad
SELECT ciudad, COUNT(*) AS total
FROM usuarios
GROUP BY ciudad;

-- Promedio de edad por ciudad
SELECT ciudad, AVG(edad) AS edad_promedio
FROM usuarios
GROUP BY ciudad;

-- Total de ventas por producto
SELECT producto, SUM(cantidad) AS total_vendido, SUM(precio) AS ingresos
FROM pedidos
GROUP BY producto;

-- HAVING: Filtrar grupos (como WHERE pero para grupos)
SELECT ciudad, COUNT(*) AS total
FROM usuarios
GROUP BY ciudad
HAVING COUNT(*) > 5;  -- Solo ciudades con más de 5 usuarios
```

> [!INFO] ℹ️ WHERE vs HAVING:
> *   `WHERE` filtra filas ANTES de agrupar
> *   `HAVING` filtra grupos DESPUÉS de agrupar

---

## 9. JOINs - Unir tablas

Los JOINs combinan datos de múltiples tablas relacionadas.

<div style="background: #f8f9fa; border: 2px solid #e9ecef; border-radius: 10px; padding: 20px; margin: 15px 0;">
  <p style="text-align: center; margin-bottom: 15px;"><strong>Tablas de ejemplo</strong></p>
  <div style="display: flex; gap: 20px; justify-content: center; flex-wrap: wrap;">
    <div style="background: #fff; border: 2px solid #336791; border-radius: 8px; overflow: hidden; width: 200px;">
      <div style="background: #336791; color: white; padding: 10px 15px; font-weight: bold;">usuarios</div>
      <div style="padding: 10px;">
        <table style="width: 100%; border-collapse: collapse; font-size: 12px;">
          <thead>
            <tr><th style="padding: 6px; border: 1px solid #dee2e6; background: #e9ecef; color: #333;">id</th><th style="padding: 6px; border: 1px solid #dee2e6; background: #e9ecef; color: #333;">nombre</th></tr>
          </thead>
          <tbody>
            <tr><td style="padding: 6px; border: 1px solid #dee2e6;">1</td><td style="padding: 6px; border: 1px solid #dee2e6;">Juan</td></tr>
            <tr><td style="padding: 6px; border: 1px solid #dee2e6;">2</td><td style="padding: 6px; border: 1px solid #dee2e6;">María</td></tr>
            <tr><td style="padding: 6px; border: 1px solid #dee2e6;">3</td><td style="padding: 6px; border: 1px solid #dee2e6;">Carlos</td></tr>
          </tbody>
        </table>
      </div>
    </div>
    <div style="background: #fff; border: 2px solid #336791; border-radius: 8px; overflow: hidden; width: 250px;">
      <div style="background: #336791; color: white; padding: 10px 15px; font-weight: bold;">pedidos</div>
      <div style="padding: 10px;">
        <table style="width: 100%; border-collapse: collapse; font-size: 12px;">
          <thead>
            <tr><th style="padding: 6px; border: 1px solid #dee2e6; background: #e9ecef; color: #333;">id</th><th style="padding: 6px; border: 1px solid #dee2e6; background: #e9ecef; color: #333;">usuario_id</th><th style="padding: 6px; border: 1px solid #dee2e6; background: #e9ecef; color: #333;">producto</th></tr>
          </thead>
          <tbody>
            <tr><td style="padding: 6px; border: 1px solid #dee2e6;">1</td><td style="padding: 6px; border: 1px solid #dee2e6;">1</td><td style="padding: 6px; border: 1px solid #dee2e6;">Laptop</td></tr>
            <tr><td style="padding: 6px; border: 1px solid #dee2e6;">2</td><td style="padding: 6px; border: 1px solid #dee2e6;">1</td><td style="padding: 6px; border: 1px solid #dee2e6;">Mouse</td></tr>
            <tr><td style="padding: 6px; border: 1px solid #dee2e6;">3</td><td style="padding: 6px; border: 1px solid #dee2e6;">2</td><td style="padding: 6px; border: 1px solid #dee2e6;">Teclado</td></tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</div>

**1. INNER JOIN** (solo coincidencias):
```sql
SELECT usuarios.nombre, pedidos.producto
FROM usuarios
INNER JOIN pedidos ON usuarios.id = pedidos.usuario_id;
-- Resultado:
-- Juan  | Laptop
-- Juan  | Mouse
-- María | Teclado
```

**2. LEFT JOIN** (todos de la izquierda + coincidencias):
```sql
SELECT u.nombre, p.producto
FROM usuarios u
LEFT JOIN pedidos p ON u.id = p.usuario_id;
-- Resultado:
-- Juan   | Laptop
-- Juan   | Mouse
-- María  | Teclado
-- Carlos | NULL
```

**3. RIGHT JOIN** (todos de la derecha + coincidencias):
```sql
SELECT u.nombre, p.producto
FROM usuarios u
RIGHT JOIN pedidos p ON u.id = p.usuario_id;
```

**Visualización de JOINs**

<div style="background: #f8f9fa; border: 2px solid #e9ecef; border-radius: 10px; padding: 20px; margin: 15px 0;">
  <table style="width: 100%; border-collapse: collapse; font-size: 13px;">
    <thead style="background: #336791; color: white;">
      <tr>
        <th style="border: 1px solid #dee2e6; padding: 10px;">Tipo</th>
        <th style="border: 1px solid #dee2e6; padding: 10px;">Descripción</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td style="border: 1px solid #dee2e6; padding: 10px;"><strong>INNER JOIN</strong></td>
        <td style="border: 1px solid #dee2e6; padding: 10px;">Solo filas que coinciden en AMBAS tablas</td>
      </tr>
      <tr style="background: #f8f9fa;">
        <td style="border: 1px solid #dee2e6; padding: 10px;"><strong>LEFT JOIN</strong></td>
        <td style="border: 1px solid #dee2e6; padding: 10px;">TODAS las filas de la izquierda + coincidencias de la derecha</td>
      </tr>
      <tr>
        <td style="border: 1px solid #dee2e6; padding: 10px;"><strong>RIGHT JOIN</strong></td>
        <td style="border: 1px solid #dee2e6; padding: 10px;">TODAS las filas de la derecha + coincidencias de la izquierda</td>
      </tr>
      <tr style="background: #f8f9fa;">
        <td style="border: 1px solid #dee2e6; padding: 10px;"><strong>FULL JOIN</strong></td>
        <td style="border: 1px solid #dee2e6; padding: 10px;">TODAS las filas de ambas tablas</td>
      </tr>
    </tbody>
  </table>
</div>

---

## 10. Subconsultas

```sql
-- Usuarios con edad mayor al promedio
SELECT * FROM usuarios
WHERE edad > (SELECT AVG(edad) FROM usuarios);

-- Usuarios que han hecho pedidos
SELECT * FROM usuarios
WHERE id IN (SELECT DISTINCT usuario_id FROM pedidos);

-- Usuarios que NO han hecho pedidos
SELECT * FROM usuarios
WHERE id NOT IN (SELECT DISTINCT usuario_id FROM pedidos);

-- Producto más vendido
SELECT producto, SUM(cantidad) AS total
FROM pedidos
GROUP BY producto
ORDER BY total DESC
LIMIT 1;
```

---

## ⚡ Índices - Mejorar rendimiento

Los índices hacen las búsquedas más rápidas (como el índice de un libro).

```sql
-- Crear índice simple
CREATE INDEX idx_email ON usuarios(email);

-- Crear índice único
CREATE UNIQUE INDEX idx_email_unique ON usuarios(email);

-- Índice compuesto (múltiples columnas)
CREATE INDEX idx_ciudad_edad ON usuarios(ciudad, edad);

-- Ver índices
SHOW INDEX FROM usuarios;
```

> [!TIP] 💡 Cuándo crear índices:
> *   Columnas usadas frecuentemente en WHERE
> *   Columnas usadas en JOINs
> *   Columnas usadas en ORDER BY

---

## 📋 Referencia rápida

<table style="width: 100%; border-collapse: collapse; margin: 15px 0; font-size: 14px;">
  <thead style="background: #336791; color: white;">
    <tr>
      <th style="border: 1px solid #dee2e6; padding: 10px;">Operación</th>
      <th style="border: 1px solid #dee2e6; padding: 10px;">Sintaxis</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="border: 1px solid #dee2e6; padding: 10px;">Crear BD</td>
      <td style="border: 1px solid #dee2e6; padding: 10px;"><code>CREATE DATABASE nombre;</code></td>
    </tr>
    <tr style="background: #f8f9fa;">
      <td style="border: 1px solid #dee2e6; padding: 10px;">Usar BD</td>
      <td style="border: 1px solid #dee2e6; padding: 10px;"><code>USE nombre;</code></td>
    </tr>
    <tr>
      <td style="border: 1px solid #dee2e6; padding: 10px;">Crear tabla</td>
      <td style="border: 1px solid #dee2e6; padding: 10px;"><code>CREATE TABLE t (col TIPO, ...);</code></td>
    </tr>
    <tr style="background: #f8f9fa;">
      <td style="border: 1px solid #dee2e6; padding: 10px;">Insertar</td>
      <td style="border: 1px solid #dee2e6; padding: 10px;"><code>INSERT INTO t (cols) VALUES (vals);</code></td>
    </tr>
    <tr>
      <td style="border: 1px solid #dee2e6; padding: 10px;">Consultar</td>
      <td style="border: 1px solid #dee2e6; padding: 10px;"><code>SELECT cols FROM t WHERE cond;</code></td>
    </tr>
    <tr style="background: #f8f9fa;">
      <td style="border: 1px solid #dee2e6; padding: 10px;">Actualizar</td>
      <td style="border: 1px solid #dee2e6; padding: 10px;"><code>UPDATE t SET col=val WHERE cond;</code></td>
    </tr>
    <tr>
      <td style="border: 1px solid #dee2e6; padding: 10px;">Eliminar</td>
      <td style="border: 1px solid #dee2e6; padding: 10px;"><code>DELETE FROM t WHERE cond;</code></td>
    </tr>
    <tr style="background: #f8f9fa;">
      <td style="border: 1px solid #dee2e6; padding: 10px;">Ordenar</td>
      <td style="border: 1px solid #dee2e6; padding: 10px;"><code>ORDER BY col ASC/DESC</code></td>
    </tr>
    <tr>
      <td style="border: 1px solid #dee2e6; padding: 10px;">Limitar</td>
      <td style="border: 1px solid #dee2e6; padding: 10px;"><code>LIMIT n OFFSET m</code></td>
    </tr>
    <tr style="background: #f8f9fa;">
      <td style="border: 1px solid #dee2e6; padding: 10px;">Agrupar</td>
      <td style="border: 1px solid #dee2e6; padding: 10px;"><code>GROUP BY col HAVING cond</code></td>
    </tr>
    <tr>
      <td style="border: 1px solid #dee2e6; padding: 10px;">Unir tablas</td>
      <td style="border: 1px solid #dee2e6; padding: 10px;"><code>JOIN t2 ON t1.col = t2.col</code></td>
    </tr>
  </tbody>
</table>

**Orden de ejecución de una consulta:**
`FROM` → `JOIN` → `WHERE` → `GROUP BY` → `HAVING` → `SELECT` → `ORDER BY` → `LIMIT`

---

## ✓ Checklist de aprendizaje

- [ ] Entiendo qué es una base de datos relacional
- [ ] Sé crear tablas con tipos de datos apropiados
- [ ] Puedo insertar datos con INSERT
- [ ] Domino SELECT con WHERE, ORDER BY, LIMIT
- [ ] Sé usar LIKE para búsquedas de texto
- [ ] Puedo actualizar datos con UPDATE
- [ ] Sé eliminar datos con DELETE (¡con cuidado!)
- [ ] Uso funciones de agregación (COUNT, SUM, AVG)
- [ ] Entiendo GROUP BY y HAVING
- [ ] Puedo unir tablas con JOINs
- [ ] Sé cuándo usar índices
