# docs
Documentación del proceso de desarrollo de los talleres

## Raspberry PI

### entrar via ssh en osx/linux (2017-09-21).

Enlaces:

* [DOCUMENTATION > REMOTE-ACCESS > IP-ADDRESS](https://www.raspberrypi.org/documentation/remote-access/ip-address.md)
* [SSH USING LINUX OR MAC OS](https://www.raspberrypi.org/documentation/remote-access/ssh/unix.md)
* [3 Ways to Run a Remote Desktop on Raspberry Pi](https://eltechs.com/3-ways-to-run-a-remote-desktop-on-raspberry-pi/)

Lo hecho (osx 10.9.5 / Miguel/ Espe):

* Formatear tarjeta SD
* Encender PI y conectar ethernet al router
* instalar [nmap (7.60)](https://nmap.org/dist/nmap-7.60.dmg)
* buscar los que están conectados, y entre ellos donde está el PI (`System Preferences > Network > Advanced > TCPIP` dice qué ip tiene la compu: 192.168.1.39, por ejemplo) 

    nmap -sn 192.168.1.0/24

![nmap list](/img/nmap.png)

* Aparece la lista de elementos conectados al router -> apuntar la del PI (en este caso `192.168.1.40`)
* Intentar conectar:

    ssh pi@192.168.1.140  --> connection refused 

* No se puede conectar porque no tiene por defecto el `ssh` activado... para activarlo hay que poner en el directorio/partición `/boot` un fichero de nombre `ssh` (sin extensión). Una vez hecho eso, reboot el PI y ya se puede conectar:

    ssh pi@192.168.1.140

* establece conexión y el pass por defecto es `raspberry`

![ssh](/img/ssh_pi.png)

