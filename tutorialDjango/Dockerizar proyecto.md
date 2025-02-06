2. <ESPESIFICAR EN QUE DIRECTORIO QUEREMOS TRABAJAR>

* <WORKDIR /app

3. <INSTALAR LOS PROGRAMAS NECESARIOS Y ACTUALIZAR PROGRAMAS PARA PODER CORRER LA APLICACION>
<RUN = Nos permite correr comandos dentro del contenedor

* <RUN apk update \ ---ACTUALIZAR PAQUETES D ELA DISTRIBUCION
  && apk add --no-cache gcc musl-dev python3-dev libffi-dev \  ---AGREGAR PROGRAMAS
  && pip  install  --upgrade pip   ---- SE ACTUALIZAN PAQUETES DE REQUERIMETS.TXT

4. <CACHE DE DOCKER>
 
 DOCKER PARA NO CONSTRUIR TODO DESDE CERO GUARDA UN CACHE , DEPENDIENDO DE DONDE SE GENERO EL CAMBIO
 SE COMIENZA A CONSTRUIR EL ARCHIVO

5. <COPIAR LOS ARCHIVOS NECECESARIOS PARA PODER PREPARAR EL EQUIPO>
____________________________________________________________________
|Vamos a copiar archivos de nuestro directorio origen a             |
| nuestro contenedor destino de este directorio                     |
|-------------------------------------------------------------------|                
                |               |            ______________________________________________
                |               |-----------|que lo pegue en directorio actual que es /app |
                |               |            ----------------------------------------------
                |               |        --------------------------------------------------------------
* <COPY ./requeriments.txt     ./ ----- |COMO ESTE ARCHIVO TIENE VARIOS CAMBIOS LO PASAMOS HASTA ABAJO |
                                         --------------------------------------------------------------

6. <INSTALAR PAQUETES>
  * <RUN pip install -r  requeriments.txt 

7. <COPIAR EL PROYECTO
  ______________________________
 |copia del origen los archivos |
 | del proyecto                 |
  ------------------------------       ________________________________________
      |    ___________________________|Copia al directorio destino que es /app |
      |   |                           | del contenedor docker                  |
<COPY ./ ./                            ----------------------------------------

8. <EJECUTAR PROYECTO>
* Con la instrucción CMD ejecutamos un comando
  - 8.1 <Solo para que sea visible en mi equipo
      * CMD["python","manage.py","runserver"]>
  
  - 8.2 <Para que sea visible por cualquier Equipo
      * CMD["python","manage.py","runserver","0.0.0.0:8000"]>

9. <CONSTRUIR IMAGEN>
[-t] = (tag) para etiquetar al contenedor
* docker build -t nombreDeImagen

10. <CORRER IMAGEN>
* docker run -p 8000:8000 nombreDeImagen

11. <MOSTRAR LOG>

* Agregar despues de FROM
<ENV PYTHONUNBUFFERED=1

12. <EVITAR CONTRUIR LA IMAGEN OTRAVEZ Y REDUCIR EL TIEMPO DE CONSTRUCCIÓN>
 ---------------------------------------                             --------------------------------------------------------
|directorio donde se encuetra elproyecto|                           | directorio donde se creo la aplicacion en el contenedor |
 ---------------------------------|-----                              -------------------------------------------------------  
                                  |                                   |
docker run -v \Users\HugodeJesúsMeloRange\Documents\TUTORIALDJANGO:\app -p 8000:8000 nombreImagen                  
