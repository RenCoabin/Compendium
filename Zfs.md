crear un sistema de ficheros:
	zfs create tank

crearlo en home.
	zfs create -o mountpoint=/home tank/home

crear instantánea
	zfs snaphot
	para listar:
		zfs