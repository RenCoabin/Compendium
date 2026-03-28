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

Mi primer problema con esto, es que efectivamente el adaptador de red wi-fi aparentemente no existe, así que me toca instalar el paquete "pciutils"