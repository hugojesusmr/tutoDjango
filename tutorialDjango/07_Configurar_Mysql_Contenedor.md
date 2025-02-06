<CREAR CONTENEDOR CON MYSQL>

# 0. <BUSCAR VERSION DE MYSQL>
 * podman search mysql

# 1. <DESCARGAR VERSION DE MYSQL>
  * podman pull mysql

# 2. <LISTAR LAS IMAGENES>
  * podman images

# 3.- <LISTAR LAS REDES DISPONIBLES>
  * podman network ls

# 4.- <CREAR UNA NUEVA RED>
  * podman network create testDjando

# 5. <CREAR UN VOLUMEN PARA PERSISTIR LOS DATOS>
  * podman volume create miVolumen

# 6. <LISTAR LOS VOLUMNES>
  * podman volume ls

# 7. <OBTENER MAS INFORMACIÓN HACERCA DE LOS VOLUMENES>
  * podman volumne inpsect (nombreDelVolumen o ID de volumen)

# 8. <LISTAR LA IMAGEN A UTILIZAR DE MYSQL
  * podman images

# 9. <CORRER EL SIGUIENTE COMANDO PARA CREAR E INICIAR UN CONTENEDOR CON MYSQL AGREGADO PUERTOS, VOLUMNES, REDES>
  
* podman run -d --net=testDjango --name Mysql_Prod -e MYSQL_ROOT_PASSWORD=pass123 -p 3307:3306 -v /var/lib/containers/storage/volumes/persistiendoDatos/_data:/var/lib/mysql localhost/mysql/enterprise-server:8.0
  

# 8. <LISTAR LOS CONTENEDORES EN EJECUCIÓN>
 
 * podman ps -a

# 9. <UTILIZAR ALGUNA HERRAMIENTA PARA SU FACIL GESTION POR EJEMPLO WORKBENCH, DBAVER, ETC>
 
 * Nota: Error al acceder por medio de estas Herrameintas al contenedor creado  
    <ERROR: host-is-not-allowed-to-connect-to-this-mysql-server>

# 10. <ACCEDER AL CONTENEDOR POR MEDIO DE SU ID>
  
  * Nota: hay que acceder al contenedor para cambiar los privilegios de usuario
  * podman exec -it idContenedor bash

# 11. <CONECTARSE POR MEDIO DE LA CONSOLA A MYSQL COMO ROOT>
  
  * mysql -u root -p 

# 12. <VERIFICAR EL HOST>
 
  - SELECT host FROM mysql.user WHERE User = 'root';

# 13. <CREAR UN USUARIO Y DAR ACCESO AL HOST>
  
  * NOTA: Use el comodín % para otorgar acceso

  - CREATE USER 'hm9474'@'%' IDENTIFIED BY 'some_pass';
  - GRANT ALL PRIVILEGES ON *.* TO 'hm9474'@'%';  
  - FLUSH PRIVILEGES;   

# 14. <VERIFICAR EL HOST>
 
  - SELECT host FROM mysql.user WHERE User = 'HM9474';

 
