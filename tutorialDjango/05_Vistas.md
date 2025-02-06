# VISTAS

# 1.- <CREAR ARCHIVO URLS EN LA APP LIBRO>
    * touch urls.py

# 2.- <COMO ENLAZAR LAS URLS DE TODAS LAS APPS CREADAS?> 
  - 2.1 
    * Dentro del archivo urls.py que esta en la carpeta core del proyecto principal hacer los ig:
  - 2.2
    * importar libreria include para poder incluir archivos pertenecientes a aplicaciones de mi propio proyecto
      <from django.urls import path, include  
  -2.3     
    * Hay que darle un identificador al conjunto de urls de mi aplicacion que englobe a todas las urls y es por seguridad para no poder acceder a una simple url

    <urlpatterns = [
    <path('admin/', admin.site.urls),
    <path('libro/', include(('apps.libro.urls','libro')))
    ]


# 3.-<PRIMERA VISTA, primera URL y primer renderizado de un template>
  - 3.1
    * Crear en la carpeta libro la siguiente configuracion:
        <from django.urls import path
        <urlpatterns=[]

# 4.-<IR AL ARCHIVO VIEWS.PY DE LA APP LIBRO Y CREAR UNA VISTA CON LO SIG:>

  - 4.1
    * Crear la siguiente funcion llamanda Home que recibe un parametro <requests> toda funcion debe de recibir este parametro cuando vamos a trabajar con peticiones que vengan del navegador

    * <requests> es el paramatro que va a obtener el cual va a ser recibido la interaccion que haga el usuario con el navegador, cunado uno navega en una url estas haciendo una <peticion> que va a llegar al lado der servidor por medio del parametro requests
   * <render>: es una funcion que recibe parametros <render(la petición,template a usar)> 
     <Que hace>: pinta en un template la informacion que le indiquemos

<from django.shortcuts import render
<def Home(requests):
 <return render(request, 'libro/index.html')

  - 4.2
   * Asignar la funcion creada a una url en el archivo urls.py que se encuentra en libro/urls.py
   * <path>: La funcion path recive tres parametros que son los sig:
      - texto que va uno a escrivir en la barra de direcciones para acceder a la logica de la funcion o clase
      - funcion que tiene la logica
      - identificador para toda la url

<from django.urls import path
'''Importar la vista creada'''
from .views import Home
'''Especificar ruta de acceso a la url'''
   urlpatterns= [
    path('', Home, name='index'),
    ]



             