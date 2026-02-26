- ¿Qué es?
Un servicio que ejecuta tareas de forma periódica.

- ¿Qué diferencia hay?
	**Cron** ejecuta las tareas especificadas, es decir, si la máquina debe ejecutar algo a las 7am, lo hace, pero si está apagada, no lo hace.
	**Anacron** hace lo mismo, solo que si a las 7am está apagada y se enciende más tarde, se da cuenta de que no la ha hecho porque estaba apagada y la ejecuta, como si tuviese*memoria*.

El formato del fichero **crontab** es:
	*Minutos, horas, dia del mes, mes, dia de la semana,* usuario, comando
	Ejemplo:
		`0 8 * * thu`


#### !!!Atención: 
El día de la semana puede verse como mon, tue.......sun o como 0,1,2,3....6, siendo DOMINGO el PRIMERO