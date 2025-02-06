# <CONFIGURAR MYSQL EN DJANGO>

# 1.- <INSTALAR LIBRERIA O DEPENDENCIA EXTRA Y PERMITA CONECTAR A MYSQL>

* py -m pip install mysqlclient

# 2. <CREAR BASE DE DATOS EN EL GESTOR DE BD>

* usar la herramienta en la que se acomoden para manipular los datos y crear la bd

# 3. <CONFIGURAR EL ARCHIVO DE SETTINGS.PY QUE ESTA EN LA CARPETA CORE PARA CONFIGURAR MYSQL>  

* Agregar la sig. configuración.

<DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'prueba',
        'USER': 'hm9474',
        'PASSWORD': 's3cr3t00!',
        'HOST': "127.0.0.1",
        'PORT': '3307',
        'OPTIONS': {
            'sql_mode': 'traditional',
        }
    }
}>

# 4. <CONFIGURAR VARIABLES DE ENTORNO EN ARCHIVO .ENV>

* Crear archivo .env
   - <echo > .env

- Agregar lo sig. a el archivo .env

 DB_HOST=127.0.0.1
 DB_NAME=nombreBaseDatos
 DB_USER=hm9474
 DB_PASSWORD=s3cr3t00!      
 DB_PORT=3307    

# 5. <CONFIGURAR ARCHIVO SETTINGS.PY CONEXIÓN A LA BD>
- Importar la libreria os
     import os

- Modificar la conexión a la base de datos

<DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': os.environ.get('DB_NAME'),
        'USER': os.environ.get('DB_USER'),
        'PASSWORD': os.environ.get('DB_PASSWORD'),
        'HOST': os.environ.get('DB_HOST'),
        'PORT': os.environ.get('DB_PORT'),
         'OPTIONS': {
            'sql_mode': 'traditional',
        }
    }
}>

# 6. <INICIAR EL SERVIDOR DJANGO>
  - <py manager.py runserver

 # ERROR AL INICIAR

# 7. <CONFIGURAR ARCHIVO SETTINGS.PY VARIABLES DE ENTORNO>

- Instalar la libreria 
   <py -m pip install python-dotenv>

- Agregar lo siguiente en el archvio <settings.py>

<from dotenv import load_dotenv

<load_dotenv()

- Volver iniciar el servidor
- <py manager.py runserver
 