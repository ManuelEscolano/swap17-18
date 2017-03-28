#Manuel Escolano

En esta práctica, se han obtenido los siguientes resultados con ayuda del guión y 
de la resolución de dudas en clase por parte del profesor:


1. Probar el funcionamiento de la copia de archivos por ssh.
2. Clonado de una carpeta entre las dos máquinas.
3. Configuración de ssh para acceder sin que solicite contraseña. 
4. Establecer una tarea en cron que se ejecute cada hora para mantener 
actualizado el contenido del directorio /var/www entre las dos máquinas.

1. Prueba en el funcionamiento de copia

Se configuran las IP's de ambas máquinas ya que al ser clonadas ambas tenian la misma dirección IP.

Una vez solucionado el problema, ejecutamos la orden ping en ambas máquinas
seguido de la dirección IP la máquina contraria con el fin de conectarlas.

![imagen](https://github.com/ManuelEscolano/swap17-18/blob/master/imagenesP2/conexion.png)

2. Clonado de Carpetas

Una vez que ambas máquinas estan conectadas, creamos un documento en una de ellas (“hola”) 

![imagen](https://github.com/ManuelEscolano/swap17-18/blob/master/imagenesP2/hola.png)

Finalmente pasamos a volcar la información de una máquina a la otra con la orden:
“rsync -avz -e ssh root@192.168.1.100:/var/www/ /var/www/”
con esto indicamos que copiaremos lo que hay en /var/www/ de la máquina con la IP especificada
en el directorio /var/www/ de la maquina en la que ejecutamos la orden, y comprobamos 
que ha funcionado como esperabamos.

![imagen](https://github.com/ManuelEscolano/swap17-18/blob/master/imagenesP2/hola2.png)

3. Configuracion del SSH sin contraseña

Siguiendo con las indicaciones del pdf, y enfocado a la configuración del ssh, hago uso de la orden “ssh-keygen -t dsa”
para configurar la contraseña, y la orden “ssh-copy-id -i .ssh/id_dsa.pub root@192.168.1.100” 
para copiar la cofiguración de la contraseña en la máquina indicada, con el fin de poder acceder de forma
remota a esa máquina.

Para comprobar que funciona, hacemos uso de la orden: 
“ssh root@192.168.1.100”

![imagen](https://github.com/ManuelEscolano/swap17-18/blob/master/imagenesP2/contraseña.png)

4. Actualización automática entre máquinas con “crontab”

Una vez realizados los pasos anteriores, configuramos el crontab en “etc/crontab” con la orden en cuestión necesaria
para la actualización remota de una máquina conforme a la otra cada 2 horas.

![imagen](https://github.com/ManuelEscolano/swap17-18/blob/master/imagenesP2/cront.png)



