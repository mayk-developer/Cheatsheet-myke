# Cheat Sheet: SQL Completo

Guía de referencia para consultas, diseño y conceptos avanzados de bases de datos relacionales.

## 💾 Operaciones Básicas (CRUD)

| Comando | Descripción | Ejemplo |
| :--- | :--- | :--- |
| `SELECT` | Leer datos. | `SELECT nombre FROM usuarios;` |
| `INSERT` | Crear datos. | `INSERT INTO usuarios (nombre) VALUES ('Maykol');` |
| `UPDATE` | Actualizar datos. | `UPDATE usuarios SET activo = true WHERE id = 1;` |
| `DELETE` | Borrar datos. | `DELETE FROM usuarios WHERE activo = false;` |

## 🔍 Filtrado y Ordenamiento
```sql
SELECT * FROM productos
WHERE precio > 100 AND categoria = 'Electrónica'
ORDER BY precio DESC -- Orden descendente
LIMIT 10; -- Solo los primeros 10
```

## 🔗 Joins (Uniones)
Combinar filas de dos o más tablas.

*   **INNER JOIN**: Solo filas que coinciden en ambas tablas.
*   **LEFT JOIN**: Todas las filas de la tabla izquierda + coincidencias de la derecha (o NULL).
*   **RIGHT JOIN**: Todas las filas de la tabla derecha + coincidencias de la izquierda.
*   **FULL JOIN**: Todo de ambas tablas.

```sql
SELECT u.nombre, p.pedido_id
FROM usuarios u
LEFT JOIN pedidos p ON u.id = p.usuario_id;
-- Trae todos los usuarios, tengan o no pedidos.
```

## 📊 Agregación y Grupos
```sql
SELECT pais, COUNT(*) as total_usuarios, AVG(edad) as edad_promedio
FROM usuarios
GROUP BY pais
HAVING COUNT(*) > 5; -- Filtra grupos (no filas individuales)
```

## 🚀 Conceptos Avanzados

### CTEs (Common Table Expressions)
Subconsultas limpias y reutilizables con `WITH`.
```sql
WITH VentasRecientes AS (
    SELECT * FROM ventas WHERE fecha > '2024-01-01'
)
SELECT * FROM VentasRecientes WHERE total > 500;
```

### Window Functions (Funciones de Ventana)
Cálculos a través de filas relacionadas sin agruparlas (mantiene las filas originales).
```sql
SELECT 
    nombre, 
    salario,
    -- Ranking por salario dentro de cada departamento
    RANK() OVER (PARTITION BY departamento ORDER BY salario DESC) as ranking
FROM empleados;
```

### Índices (Performance)
Acelera las búsquedas (lectura rápida, escritura más lenta).
```sql
CREATE INDEX idx_email ON usuarios(email);
```

## 📏 Normalización
Reglas para reducir redundancia y mejorar integridad.

*   **1NF (Primera Forma Normal)**: 
    *   Datos atómicos (sin listas separadas por comas en una celda).
    *   Sin grupos repetidos de columnas (tel1, tel2, tel3).
    *   Identificador único (PK).
*   **2NF (Segunda Forma Normal)**:
    *   Cumple 1NF.
    *   Sin dependencias parciales (todo atributo depende de *toda* la PK, no solo parte de ella en claves compuestas).
*   **3NF (Tercera Forma Normal)**:
    *   Cumple 2NF.
    *   Sin dependencias transitivas (atributos que dependen de otros atributos que no son la PK). *Ej: Si sabes el código postal y eso te da la ciudad, la ciudad debe ir en otra tabla.*

---
*Nota: La sintaxis puede variar ligeramente entre motores (PostgreSQL, MySQL, SQL Server).*
