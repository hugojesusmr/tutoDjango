1.- <Que es Django?>

 * Es un framework Web Orientado al backend, es decir ofrece caracteristicas y herramientas que faciliten y agilicen el desarrollo de aplicaciones web.

 * Filosofia <Don't Repeat Yourself>
   - Utiliza el patron de diseño MVT(Modelo Vista Template)

2.- <Que es un framework?>
 * Son Herrameintas o secciones de codigo que ya se han hecho que facilitan el trabajo o el desarrollo de las aplicaciones.

3.- <Que son los entornos virtuales?
  * Son encapsulaciones o aislamientos de dependencias que solo existen en una carpeta, hay que activar los entornos virutales para poder trabajar con ellos y cononocer las dependencias instaladas.

4.- <QUE ES UNA APLICACIÓN>

Una aplicación nos ayuda a estructurar nuestro proyecto

""" 
    1.- dispatch(): valida la peticion y elige que metodo http se utilizo para la solicitud
    2.- http_method_not_allowed(): retorna un error cuando se utiliza un metodo http no soportado o definido
    3.- options()
    
    TemplateView(): Es una vista especificamente usada para metodos get() que nos ayuda a renderizar un template que hereda de View
    internamente tiene un metodo explicito que es get()

    ListView(): Es una vista que nos ayuda a listar que hereda de View
                  ________ 
                 |  View  |
                  --------
                     |
    _________________|____________________________
   |                 |             |               |
-------------   -------------
|TemplateView|  | ListView  |
-------------   -------------


"""