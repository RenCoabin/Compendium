- ¿Qué es tar?
**Tar** es una herramienta potentísima que permite empaquetar, comprimir, descomprimir y desempaquetar, entre otras funciones en base a 4 factores.

- **Sintaxis**:
	`tar  opciones  nombre_de_archivo_resultante  fichero_a_empaquetar`
	Ejemplo:
		`tar cvf backup.tar /home`
		`c significa que va a empaquetar`
		`v significa verbose`
		`f significa file, para indicar el fichero`
		`FUN FACT: z, además, lo comprimiría`
		`FUN FACT: t, además, lo comprueba (TEST)`
		`FUN FACT: x desempaqueta`

- ¿Cómo funciona la compresión de un fichero?
Por lo general (y en ficheros grandes), hay mucho código, por tanto una herramienta de compresión intenta buscar patrones repetidos en ese código para acortarlo. Es decir, que si el código no tiene patrones, o es lo suficientemente pequeño como para que sea raro que aparezcan (por densidad), no podrá comprimir apenas ningún byte.