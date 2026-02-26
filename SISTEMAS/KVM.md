- ¿Qué es KVM?
**KVM** es un hipervisor potentísimo y a mi parecer más sencillo que, por ejemplo, VirtualBox, ya que para abrir una máquina virtual tienes que:
	**1. Arrancar la máquina
	2. Abrir la ventana emergente**

Lo que significa que es mucho más sencillo de arrancar con comandos, es decir, **es mejor para trabajar desde SSH**.

- ¿Cómo lo hago?
Tras crear una máquina virtual (es importante tener arrancada la red creada), introducir los siguientes comandos en la shell:
<hr>
`virsh net-autostart nombre_red_kvm`<!-- hacer una vez, para no tener que levantar la red cada vez que se arranque la máquina-->

`virsh list --all` <!-- con el usuario que hizo la instalacion-->
`virsh start ubuntu` <!-- por ejemplo-->
<hr>
*En consola.*

**También puede crearse un DNS**.
- ¿Para qué?
Querrías un DNS para que, cuando crees e instales una máquina, puedas hacer ssh, en vez de con la dirección IP, como:
<hr>
`ssh usuario_maquina@nombre_maquina.dominio.lan`
<hr>
*En consola.*

- ¿Cómo?
<hr>
`virsh net-dumpxml default` <!-- nombre red de ejemplo-->
<hr>
*En consola.*

Si no tiene unas líneas como <!--<dns enable='yes' />--> y <!-- <domain name='dominio.lan' localOnly='yes'/>--> , añadirlas, después:
<hr>
`virsh net-destroy default
`virsh net-start default

<!--y reiniciamos el servicio-->
`systemctl restart libvirtd
<hr>
*En consola.*