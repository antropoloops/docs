# Instalando ghost.org

Seguir las instrucciones [aquí](https://docs.ghost.org/v1.0.0/docs/install)

Carpeta recomendada para instalar ghost
```
root@blogs:~# mkdir /var/www
root@blogs:~# cd /var/www
```

Creo usuario nuevo, añado privilegios de superusuario (puede hacer tareas administrativas usando sudo) y entro
```
adduser espe
usermod -aG sudo espe
```

Instalar Nginx
```
sudo apt-get install nginx
```

If ufw was activated we need to make sure that the firewall allows HTTP and HTTPS connections.
```
sudo ufw allow 'Nginx Full'
```
Cuando meto esto no reconoce ufw, así que me imagino que no se ha activado ningún firewall

Instalar mysql
```
sudo apt-get install mysql-server
```

Instalar Node.js
```
curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash
sudo apt-get install -y nodejs
```
Instalamos ghost--cli
```
sudo npm i -g ghost-cli
```

Creamos nueva carpeta
```
sudo mkdir -p /var/www/talleres/ghost
sudo chown espe:espe /var/www/ghost
cd /var/www/talleres/ghost
```

E instalamos ghost
```
ghost install
```

