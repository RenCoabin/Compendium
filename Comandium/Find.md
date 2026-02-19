- ¿Qué es find?
Un **comando** que permite buscar archivos dentro de la estructura del sistema de ficheros con la ayuda de criterios e incluso **actuar sobre los resultados devueltos**.
	find ruta criterios opciones
		Criterios:
			**-name** permite una selección por nombres de archivos
			**-iname** igual, solo que ignora mayúsculas y minúsculas
			**-type** permite seleccionar por tipo de archivos:
				"B", archivo especial en modo bloque
				"C", archivo especial en modo carácter
				"D", directorio
				"F", archivo ordinario
				"L", enlace simbólico
				"P", tubería
				"S", socket
			**-user** y **-group** permiten búsqueda sobre propietario del archivo.
			**-size** puede usarse:
				"K", que significa 1kB (1024 bytes), con un + o un - delante
				"-empty", en sustitución de "-size 0"
			**-atime**, **-mtime** y **-ctime** 
CONTINUAR EN PAGINA 168 DE LINUX DOMINAR LA ADMINISTRACION DEL SISTEMA