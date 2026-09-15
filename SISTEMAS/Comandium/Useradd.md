- ¿Qué es useradd?
**Useradd** es un comando para añadir usuarios, disponible también en RHEL, que permite, a su vez, añadir al nuevo usuario a grupos, definir la shell...

- ¿Cómo se utiliza y cómo se comporta?
**Useradd** crea un usuario y almacena la informacion en el fichero /etc/passwd en el orden:
	*nombre:x:UID:GIDcampo_de_GECOS:directorio_home:shell*
#### **!!!Para omitir tener que llenar el campo GECOS, se recomienda utilizar la opción `--gecos ""`. 

- **EJEMPLO:**
<hr>
`useradd -m -s /bin/bash -aG grupo --gecos "" usuario
<hr>
*En consola.*