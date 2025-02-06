# <MODELOS>

* Los modelos son la representación de las tablas que conocemos como bd y estan representados
a traves de sintaxis propia de python

* Los modelos se basan en clases y son representación de las entiades o tablas

# 1.- <COMO CREAR UN MODELO>
class Autor(models.Model):
    id = models.AutoField(primary_key= True)
    nombre = models.CharField(max_length=200, blank=False, null=False)
    apellidos = models.CharField(max_length=200, blank=False, null=False)
    nacionalidad = models.CharField(max_length=100, blank=False, null=False)
    descripcion = models.TextField(blank=False, null=False)

# 2.- <Crear Migraciones
  * <py manager.py makemigrations
  * <py manager.py migrate

# 3.- <INICIAR APLICACION>
        * py manage.py runserver
# 4.- <ACCEDER AL ADMINISTRADOR>
  * http://127.0.0.1:8000/admin

# 5.- <CREAR ADMINISTRADOR>
  * py manage.py createsuperuser

  user:hm9474
  pass:hm9474