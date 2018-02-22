# docs
Documentación del proceso de desarrollo de los talleres

## Raspberry PI

### Formatear la tarjeta SD desde OS X
1. Abrir terminal, sin la tarjeta metida en el ordenador todavía `df -h`
2. Insertar tarjeta y correr `df -h` otra vez.
3. Comparando la lista de volumenes montados podemos averiguar el nombre de la tarjeta. Algo como /dev/disk3s1
4. Desmontar la tarjeta para poder escribir en ella `sudo diskutil unmount /dev/disk3s1`
5. Averiguar el nombre crudo de la tarjeta. Se hace reemplazando disk por rdisk y quitando s1 del final. -> /dev/rdisk3
6. Asegurate de que la imagen está descargada y unzipped. Hemos descargado Raspbian Stretch with Desktop de [aquí](https://www.raspberrypi.org/downloads/raspbian/).
7. Hay que hacer una copia bit-by-bit. `sudo dd bs=1m if=~/2017-09-07-raspbian-stretch.img of=~/dev/rdisk3`
8. Tarda unos minutos y no dice nada hasta que acaba.

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

`nmap -sn 192.168.1.0/24`

![nmap list](/img/nmap.png)

* Aparece la lista de elementos conectados al router -> apuntar la del PI (en este caso `192.168.1.40`)
* Intentar conectar:

`ssh pi@192.168.1.140`  --> connection refused 

* No se puede conectar porque no tiene por defecto el `ssh` activado... para activarlo hay que poner en el directorio/partición `/boot` un fichero de nombre `ssh` (sin extensión). Una vez hecho eso, reboot el PI y ya se puede conectar:

`ssh pi@192.168.1.140`

* establece conexión y el pass por defecto es `raspberry`

![ssh](/img/ssh_pi.png)

### entrar via cable ethernet conectado a mac OSX

[How to SSH into your Raspberry Pi with a Mac and Ethernet Cable](https://medium.com/@tzhenghao/how-to-ssh-into-your-raspberry-pi-with-a-mac-and-ethernet-cable-636a197d055)
