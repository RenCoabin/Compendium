- ¿Qué es **DDL**?
DDL hace referencia a una función de [[SQL]]. Esta función se encarga de definir los datos con comandos como:
	CREATE: Se utiliza para crear objetos desde cero (por ejemplo tablas, o bases de datos).  
	ALTER: Se utiliza para modificar la estructura de un objeto sin tener que recrearlo (como añadir una fila a una tabla ya creada).
	DROP: Elimina todo el contenido y estructura de un objeto (como una tabla, una vista o una base de datos completa).
	TRUNCATE: Hace lo mismo que drop, pero no elimina la estructura, es decir, vacía **todo** el contenido de una tabla.
	RENAME: Se utiliza para cambiar el nombre de una tabla sin alterar su contenido y funcionamiento (mucho ojo si la tabla es usada en un script).