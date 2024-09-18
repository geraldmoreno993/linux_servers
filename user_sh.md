# Crear usuario de servidor LINUX con/sin poderes sudo para conexión remota en área local (misma red)
 
```
#!/bin/bash
#Pasos para crear usuario con/sin poderes sudo, si no deseas darle sudo power entonces debes obviar la parte de ##sudo usermod -aG sudo nombre_de_usuario##
#Primero: debes ser el admin de tu servidor y ubicandote en la terminal del servidor, pegas estas líneas de comandos
#Solamente por el momento es útil cuando se desea conectar con la misma red pública en la que está el servidor, es decir
#Conección remota parcial, para una conexión remota total, se debe revisar las actualiaciones de este código.
#Añadir un nuevo usuario
sudo adduser nombre_de_usuario
#Agregar el usuario al grupo sudo
sudo usermod -aG sudo nombre_de_usuario
#Verificar los usuarios del sistema
cat /etc/passwd
#Crear un directorio .ssh para el usuario y authorized_keys
sudo mkdir /home/nombre_de_usuario/.ssh
sudo touch /home/nombre_de_usuario/.ssh/authorized_keys
#Cambiar la propiedad del directorio y los archivos del usuario
sudo chown -R nombre_de_usuario:nombre_de_usuario /home/nombre_de_usuario
#Instalar y habilitar el servidor SSH
sudo apt install openssh-server
sudo systemctl enable ssh
#Obtener la dirección IP del servidor
ip a #Una vez ejecutes esto, debes buscar con ayuda de chatgpt el numero de IP del servidor, te diriges a tu pc o laptop conectada a la msiam
#red que el sercidor y coloca
ssh nombre_de_usuario@IP

```

