# Instalando ghost.org

Seguir las instrucciones [aquí](https://primoz.xyz/running-ghost-on-scaleway-node-js-instance/)

Carpeta recomendada para instalar ghost
```
root@blogs:~# mkdir /var/www
root@blogs:~# cd /var/www
```
Lo instalo en subcarpeta por si queremos tener dos instancias de ghost instaladas en el servidor
```
root@blogs:/var/www# mkdir talleres
root@blogs:/var/www# cd talleres
```

Descargar última versión
```
root@blogs:/var/www/talleres# wget https://ghost.org/zip/ghost-latest.zip
root@blogs:/var/www/talleres# unzip ghost-latest.zip
```
Instalar Node.js
```
root@blogs:/var/www/talleres# curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash
sudo apt-get install -y nodejs
```
Instalamos los paquetes de package.json
```
root@blogs:/var/www/talleres# npm install --production
```
