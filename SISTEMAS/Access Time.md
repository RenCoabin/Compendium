- ¿Qué es **Access Time**?
Access Time hace referencia al comando [[Find]] como **atime**.

- ¿Cuando cambia?
Al usar comandos como `cat, less, grep, tail` o `head` o cuando un script lee el fichero.

### !Nota:
En sistemas modernos, los discos se montan con la opción `relatime`, que significa que el **atime** solo se actualiza si el fichero se ha modificado desde el último acceso o un tiempo determinado (normalmente 24h).