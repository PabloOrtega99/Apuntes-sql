# Vistas en SQL

Crear vistas sirve para crear versiones de nuestras tablas con las columnas que queramos. Sólo tenemos que utilizar "CREATE VIEW" + "NOMBRE DE LA VISTA QUE QUERAMOS PONERLE" AS y seleccionamos las columnas específicas que queramos de nuestra tabla. Por ejemplo, si mi tabla tiene 10 columnas, en este caso sólo estoy seleccionando 6.

```sql
CREATE VIEW EMPSALARY AS 
SELECT EMP_ID, F_NAME, L_NAME, B_DATE, SEX, SALARY
FROM EMPLOYEES;
```
Cuando queramos acceder a la vista sólo tenemos que hacer un select con el nombre que le hayamos puesto a la vista

```sql
SELECT * FROM EMPSALARY;
```

Para borrar una vista sólo tenemos que usar DROP + VIEW

```sql
DROP VIEW SALARY;
```

# Procedimientos almacenados

Los procedimientos almacenados son como una "especie de script" ya que nos permiten almacenar una o varias conjuntas específicas para ejecutarlas sin tener que hacerlas todo el rato.

Por ejemplo, podemos crear una consulta que se llame "RETRIEVE ALL" que lleve dentro un SELECT de toda la tabla.

```sql
DELIMITER //
CREATE PROCEDURE RETRIEVE_ALL()
BEGIN
  
   SELECT *  FROM PETSALE;
   
   
END //
DELIMITER ; 
```

# Procedimiento `UPDATE_SALEPRICE`

## ¿Para qué sirve?
Este procedimiento almacenado (`Stored Procedure`) modifica el precio de venta (`SALEPRICE`) de un animal en la tabla `PETSALE`, según el estado de salud (`Animal_Health`) que reciba como parámetro:

- Si `Animal_Health = 'BAD'` → aplica un descuento del **25%** (el precio final queda al 75%).  
- Si `Animal_Health = 'WORSE'` → aplica un descuento del **50%** (el precio final queda al 50%).  
- Si es otro valor → no cambia el precio.  

---

## Código del procedimiento
```sql
DELIMITER @
CREATE PROCEDURE UPDATE_SALEPRICE ( 
   IN Animal_ID INTEGER, IN Animal_Health VARCHAR(5) )     
BEGIN 
   IF Animal_Health = 'BAD' THEN                           
       UPDATE PETSALE
       SET SALEPRICE = SALEPRICE - (SALEPRICE * 0.25)
       WHERE ID = Animal_ID;
   
   ELSEIF Animal_Health = 'WORSE' THEN
       UPDATE PETSALE
       SET SALEPRICE = SALEPRICE - (SALEPRICE * 0.5)
       WHERE ID = Animal_ID;
       
   ELSE
       UPDATE PETSALE
       SET SALEPRICE = SALEPRICE
       WHERE ID = Animal_ID;
   END IF;                                                 
   
END @
DELIMITER ;
```
# Transacciones (Mirar en YT para completar apuntes)


