crear un sistema de ficheros:
	zfs create tank

crearlo en home.
	zfs create -o mountpoint=/home tank/home

crear instantánea
	zfs snaphot
	para listar:
		zfs list -t snapshot
			V.g.
			zfs snapshot tank/home/ASIR@mi-snap-$(date +%F +%H +%M +%S)

cargarse snapshot:
	zfs destroy ficherosnap

rollback:
	zfs rollback fichero