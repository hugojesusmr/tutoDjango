# <CREAR TEMPLATES>

# 1.- <En la raiz de nuestro proyecto crear la carpeta templates
 * mkdir templates
# 2.- <Dentro de la carpeta templates crear una carpeta con el nombre de cada aplicacion>
   <cd templates
     * mkdir libro
# 3.- <DENTRO DE LIBRO CREAR LOS ARCHIVOS HTML>
   * <touch index.html   

# 4.- <GENERAR LA ESTRUCTURA DEL HTML> 

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    
</body>
</html>

# 5.-<IR AL ARCHIVO DE CONFIGURACION SETTINGS.PY DE LA APLICACION PRINCIPAL QUE ES CORE>
  - 5.1 Configuracion necesaria para poder usar los templates 
    * En la seccion donde dice [TEMPLATES] agregar lo siguiente en la etiqueta ['DIRS'] donde se va a ubicar nuestra carpeta con los templates:
     - agregar ['templates']

    TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
--->    'DIRS': ['templates'],
        'APP_DIRS': True,
        'OPTIONS': {
            'context_processors': [
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
            ],
        },
    },
]

# 6.- <INICIAR EL SERVIDOR PARA VER LOS CAMBIOS>
  - py manage.py runserver
  - accedr al sitio: <http://127.0.0.1:8000/libro/

# 7.- <REORGANIZAR LAS URLS DEL PROYECTO> 
  - 7.1- Ir dentro del archivo urls.py de la carpeta core e importar home 

  <from django.contrib import admin
    from django.urls import path, include
    from apps.libro.views import Home

  <urlpatterns = [
        path('admin/', admin.site.urls),
        path('libro/', include(('apps.libro.urls','libro'))),
        path('home/', Home, name='index') <-----importando el home
    ]

  - 7.2 Ir dentro del archivo urls.py de la carpeta libros y eliminar el path creado de url y la importacion del Home

  - 7.3 Ir al archivo views.py de la aplicación libro y modificar la ruta de acceso al archivo html
    <from django.shortcuts import render
     '''Funcion que renderiza mi home'''
     def Home(request):
       return render(request, 'index.html') <--------> Modificación de la ruta para acceder al index principal de la aplicación
  - 7.4 Sacar el <index.html> del la carpeta libro en templates     