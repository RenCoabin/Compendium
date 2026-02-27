- ¿Qué es un servidor de correo?

Lo común es tener un relay de correo, para que sea la unica maquina que puede enviar correos.

- ¿Cómo monto un servidor de correo?
	**Se necesita el paquete postfix**.
El primer 
- SE CONFIGURA EL SERVIDOR COMO SATELLYTE SYSTEM
- SE CONFIGURA EL FICHERO /ETC/POSTFIX/MAIN.CF
- EDITAR FICHERO /ETC/POSTFIX/SASL_PASSWORD

Una vez configurado /etc/postfix/sasl_password:
<hr>
`[smtp.gmail.com]:587 tu_correo@gmail.com:APP_PASSWORD
<hr>
*En consola.*
