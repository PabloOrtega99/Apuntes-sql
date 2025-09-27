# Indices

Creamos índices cuando solemos utilizar un campo específico siempre en nuestras consultas. Al tener creado un índice, lo que hacemos es que mejore el rendimiento en la base de datos y que las consultas se realicen más rápido.

Por ejemplo, si tenemos una tabla con varios campos y vemos que la mayoría de nuestras consultas siempre contienen el campo "name", sería bueno crear un índice para ese campo. Para ello, utilizamos CREATE INDEX + "nombre del índice" ON "nombre de la tabla" (nombre de la columna)

```sql
CREATE INDEX idx_name ON users(name);
```
