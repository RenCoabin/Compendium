- ¿Qué es esto?
Estoy creando un servidor con un portátil viejo (más o menos del 2008) que tenía por ahí tirado para aprovecharlo y seguir aprendiendo nuevas cosicas.

Como curiosidad este portátil lo llevé en mi primer año de ASIR porque no tenía dinero y necesitaba un portátil, así que es lo que pude encontrar y, como no arrancaba un windows vista, cambié el disco mecánico por uno en estado sólido y, al menos con un Mint podía abrir cosas que no fuesen el navegador.

## Instalación del SO
 - La parte más sencilla
Todo el mundo ha instalado un sistema operativo alguna vez, es muy poco probable que alguien empiece a montar un servidor sin haber instalado un linux en su workstation, así que no hay excusa alguna para ponerme a explicar esto.

# Primer problema
Es un portátil antiguo, demasiado. SIEMPRE ha tenido movida con la tarjeta de red: el adaptador wifi no funciona ni aparece. Así que una vez conectado el cable UTP, me pongo manos a la obra instalando paquetes.

<hr>
apt install vim neovim neofetch tree network-manager
<!--cosas con las que suelo trabajar y las voy a necesitar sí o sí-->

systemctl start NetworkManager
systemctl enable NetworkManager <!--para poder usar "nmtui"-->
<hr>
*En consola.*

Mi primer problema con esto, es que efectivamente el adaptador de red wi-fi aparentemente no existe, así que me toca instalar el paquete "pciutils" y lanzar un comando para ver qué narices está pasando.

<hr>
lspci -nnk | grep -iA 3 net
<hr>
*En consola*

Esto filtra en lspci líneas que contengan "net", e investigando me entero de rollos que hay con drivers "b43". Te dejo aquí el chorizaco:

<hr>
¡Bingo! Tenemos al culpable: la **Broadcom BCM4312**.
Es un clásico de los portátiles viejos. El problema es que el driver que usa (llamado `b43`) requiere un **firmware** que, por cuestiones de licencia, no se incluye en la instalación estándar de Ubuntu. Sin ese firmware, la tarjeta está "sorda" y por eso `nmtui` dice que el hardware no está.
<hr>
*Gemini.*

Así que me toca instalar el paquete "firmware-b43-lpphy-installer" y cargar el módulo del kernel.

<hr>
modprobe -r b43
modprobe b43
<hr>
*En consola.*

Ahora sí, me lo puedo quitar de encima con nmtui. Y YA TENGO LISTO EL TEMA DEL WI-FI.

# Cableado
Tengo clara una cosa, y es que, salvo que esté muy deprimido, NO QUIERO TENER 50 GADGETS EN MEDIO DE MI CUARTO. Por eso mismo con un portátil abierto en un rincón no voy a ningún lado, así que tras informarme un poco:

<hr>
vim /etc/systemd/logind.conf
	<!--editar líneas-->
	HandleLidSwitch=ignore
	HandleLidSwitchExternalPower=ignore
	HandleLidSwitchDocked=ignore

systemctl restart systemd-logind
<hr>
*En consola.*

Y ya está. Si la broma es seria y va para largo, recomiendo encarecidamente tirar esta joya de comando "`setterm --term linux --blank 1`", que al minuto de inactividad apaga la pantalla, así evitas que se te queme a largo plazo, aunque tras un reinicio se pierde, si quieres que sea algo permanente, **ponlo al final de tu .bashrc**.

# Montando un DHCP
Quiero un DHCP para asignar las IP, DNS (que luego se monta) y el dominio que voy a montar en la red.

<hr>
apt install isc-dhcp-server <!--el servidor dhcp-->

vim /etc/dhcp/dhcpd.conf <!--archivo de configuracion-->
option domain-name "rathole.lan";  
option domain-name-servers 1.1.1.1;
option routers 192.168.1.1; <!-- gateway (ip router)-->
<!--he sustituido estas dos líneas por el dominio local (de mi casa) y el DNS de cloudflare (placeholder)-->

subnet 192.168.1.0 netmask 255.255.255.0 {  
range 192.168.1.100 192.168.1.200;
}
<!--he especificado las direcciones que quiero que se repartan IMPORTANTE-->
systemctl restart isc-dhcp-server

dhcpd -t <!--comando en caso de error-->
<hr>
*En consola.*

En este momento hay 2 DHCP activos: el que he montado y el que está activado en el router, así que toca ir al panel de administración y tirarlo.

Quiero que el servidor tenga una I
TEMP: 00:1d:72:d9:37:d1