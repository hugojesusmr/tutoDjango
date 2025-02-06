# <ESTRUCTURAR PROYECTO>

# 0. APLICACIONES
 * Las aplicaciones ayudan a la abstracción de nuestro proyecto
 * Una aplicación es basicamente una carpeta que contiene una cantidad de archivos los cuales han sideo separados y ubicados para trabajar en las distintas partes donde hay que representar la logica.
 *Cada aplicación debe de representar una seccion de una bd y tener organizado todo y saber a donde ir directamente a modficar el codido.

# 1.-<COMO ESTRUCUTRAR UN  PROYECTO>

 1.1- Crear una carpeta que va a contener la aplicación, va a tener modelos, vistas, urls, formularios, etc... 
     * <mkdir apps

 1.2.- Acceder a la carpeta    
     * <cd apps
     

# 2. <Dentro de la carpata apps crear archivo __init__.py>
  * __init__.py = Es un enlace para reconocer que hay archivos de python

# 3. <Entrar en la carpeta apps y crear una aplicacion con el comando sig:
  * <django-admin startapp libro 

# 4. <Cargar la aplicación que se llama libro en el archivo settings que se encuentra en la carpeta core>
   
* <Nota 1:>: cada que se crea una app se recomienta registrar dentro de las configuariones settings.py
   
* <INSTALLED_APPS = [
      'django.contrib.admin',
      'django.contrib.auth',
      'django.contrib.contenttypes',s
      'django.contrib.sessions',
      'django.contrib.messages',
      'django.contrib.staticfiles',
      'apps.libro',  <-----------[<AGREGAR APPS CREADAS]
]

# 5. <Dentro de la carpeta libro editar archivo apps.y>

Dentro de la carpeta apps entrar a la carpeta libro en el archivo apps.py tambien hay que especificar donde se encuentra ubicada 

<class LibroConfig(AppConfig):
    default_auto_field = 'django.db.models.BigAutoField'
    name = 'apps.libro'   <--------------[HUBICACIÓN DE LAS APLICACIONES CREADAS]>
   

# 6.- QUE ARCHIVOS CONTIENE LA APLICACIONES CREADAS
  6.1- __init__.py = Es un enlace para reconocer que hay archivos de python
  6.2- <admin.py = Es un archivo para registrar modelos, tablas para que sean añadidas al administrador
  6.3- <apps.py = Hace referencia a la aplicacion con su nombre nativo
  6.4- <models.py = Creacion de modelos que son clases que representas tablas en una base de datos, cada atributo que tenga la tabla como nombre, apellido son varielbes en python que van a ser istanciados como objetos
  6.5. <test.py = Sirve para hacer testeo de nuestras aplicaciones, logicas de programacion aplicadas
  6.6 <views.py = Va la logica de nuestra aplicacion 