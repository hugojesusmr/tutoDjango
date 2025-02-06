# 1. <Crear carpeta para guardar proyecto>
   * mkdir nombreProyecto

# 2. <Acceder a la carpeta creada con el nombre del proyecto>
   * cd nombreProyecto

# 3. <Crear entorno virtual dentro de la carpeta creada>
   * py -m virtualenv venv

# 4. <Activar entorno virtual>
   * .\env\Scripts\activate

# 4.1 <Desactivar entorno virtual>
   * deactivate

# 5. <Instalar Django>
   * py -m pip install Django         

# 6. <Ver las librerias instaladas>
   * pip freeze

# 7. <Crear proyecto con Django>
   * El punto [.] es para que nos cree una carpeta dentro de la misma carpeta
   * django-admin startproject core .

# 8. <Verificar el funcionamiento del proyecto>
   * python manage.py runserver

# 9. <Crear Archivo requeriments.txt> 
   * pip freeze > requeriments.txt

# <ESTRUCUTRA GENERAL DEL PROYECTO CREADO>

# 1.- <Archivo manager.py>

* Es uno de los archivos importantes que tiene todo proyecto en django, porque, porque sirve como un intermediario ya que atraves de este archivo es que vamos a poder ejecutar comandos propios de django para crear tanto los poryectos como las aplicaciones, crear super usuarios, etc.

Esta linea de codigo lo que realiza es que atraves de settings.py toma todas las configuraciones para que nuestro proyecto funcione de una manera adecuada.

 <os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'core.settings')>
  
# 2.- <NAVEGAR DENTRO DE LA CARPETA CORE>

Si vemos dentro de la carpeta existe 5 archivos:

- 2.1 <__init__.py>: Este archivo lo que hace es basicamente un indicador, por eso esta en blanco, toda carpeta que creemos en un proyecto django para ser reconocida como tal y que pueda ejecutarse y pueda reconocer los archivos que tiene la carpeta,tiene que  tener un indicador ese indicador le permite a django saber que ahi hay scripts de python que hay que ejecutarse y pertenecen al proyecto.   

- 2.2 <settings.py>: Son las configuraciones que tiene django como tal para este proyecto, aqui hay cietas caracteristicas por ejemplo:

<import os> : Accede a las configuraciones del sistema oerativo donde se esta ejecutando el proyecto, para que para indicarle la ruta donde esta nuestro proyecto y los archivos que estan dentro de el, asi puede saber donde esta la ruta inicial.

   BASE_DIR = os.path.dirname(os.path.dirname(os.path.abspath(__file__)))
   load_dotenv()


# Es unica por cada proyecto
SECRET_KEY = 'django-insecure-(n6h(k1+&80bihh01g@vveva!)91kn+bh+l!*1z6fq=pz9@^2w'

# Es basicamente para indicarnos los errores. cuando esta en true nos va a mostrar los errores y apareceran en el navegador cada vez que no encuetre una pagina o algo suceda en la logica generada en la vista y nos muestre los errores. entonces cuando este en pruduccion si se deja de esta manera es un problrema porque se puede ver lo que esta por detras de la aplicacion.

Cuando un proyecto entra en modo produccion esto se pone como False y se desactiva para evitar este problema.
DEBUG =False

# Basicamente son los host permitidos, cuando se sube a produccion le indicamos cuales son las ips, dominios validos para el cual se puede acceder al proyecto, si on esta especificado aqui no se va a poder acceder al proyecto 
ALLOWED_HOSTS = ['*']

# Son cada uno de los submodulos que tiene el proyecto como tal estas que ya estan son por defecto porque son necesarias para que funcione, para que lo hace de esta manera, para separar la logica de cada uno de los modulos creados,es decir  cada vez que se cree una nueva app se tiene que registrar en esta parte.   
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'apps.libro',
]

# los milddelware sirven como seguridad de la comunicacion que envie mi cliente hacia mi servidor y viseversa, el middleware esra en medio y va a verificar que todo este de manera correcta sin salirse de ciertas jerarquias ,niveles que ya estan establecidos y son las relgas del servidor y no sea vulnerable 
MIDDLEWARE = [
    'django.middleware.security.SecurityMiddleware',
    'whitenoise.middleware.WhiteNoiseMiddleware',
    'django.contrib.sessions.middleware.SessionMiddleware',
    'django.middleware.common.CommonMiddleware',
    <validacion de los formularios>
    'django.middleware.csrf.CsrfViewMiddleware',
    'django.contrib.auth.middleware.AuthenticationMiddleware',
    'django.contrib.messages.middleware.MessageMiddleware',
    'django.middleware.clickjacking.XFrameOptionsMiddleware',
]

# Luego tenemos ROOT_URLCONF que tiene las rutas pricipales de todo nuestro proyecto, sivemos en la estructuctura hay un archivo que se llama urls.py, ha estas urls que estan aqui son a las que gace referencia esta linea
ROOT_URLCONF = 'core.urls'

TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': ['templates'],
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

WSGI_APPLICATION = 'core.wsgi.application'

# Database
# https://docs.djangoproject.com/en/5.0/ref/settings/#databases

DATABASES = {
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
}

# Password validation
# https://docs.djangoproject.com/en/5.0/ref/settings/#auth-password-validators

AUTH_PASSWORD_VALIDATORS = [
    {
        'NAME': 'django.contrib.auth.password_validation.UserAttributeSimilarityValidator',
    },
    {
        'NAME': 'django.contrib.auth.password_validation.MinimumLengthValidator',
    },
    {
        'NAME': 'django.contrib.auth.password_validation.CommonPasswordValidator',
    },
    {
        'NAME': 'django.contrib.auth.password_validation.NumericPasswordValidator',
    },
]
# Internationalization
# https://docs.djangoproject.com/en/5.0/topics/i18n/

LANGUAGE_CODE = 'en-us'
TIME_ZONE = 'UTC'
USE_I18N = True
USE_TZ = True

# Static files (CSS, JavaScript, Images)
# https://docs.djangoproject.com/en/5.0/howto/static-files/

STATIC_URL = '/static/'
STATIC_ROOT = os.path.join(BASE_DIR, 'static')
# Default primary key field type
# https://docs.djangoproject.com/en/5.0/ref/settings/#default-auto-field

DEFAULT_AUTO_FIELD = 'django.db.models.BigAutoField'
