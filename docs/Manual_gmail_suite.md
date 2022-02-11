



# Gmail G Suite
  
Módulo para realizar acciones en Gmail  
  
![banner](imgs/Banner_gmail_suite.png)
## Como instalar este módulo
  
__Descarga__ e __instala__ el contenido en la carpeta 'modules' en la ruta de rocketbot.  




# Como usar este modulo
Para trabajar con este modulo es necesario activar la API de gmail. Para esto, debes seguir los siguientes pasos.
* Ir a [Consola de Google](https://console.cloud.google.com/projectcreate?previousPage=%2Fhome%2Fdashboard%3Fproject%3Dprueba-312216%26hl%3Des&folder=&organizationId=777182023349&hl=es) para crear un nuevo proyecto (Si ya tienes uno creado, omita este paso) y complete los datos indicados en el formulario

![](imgs/proyectonuevo.png)

En la barra superior verás el nombre del proyecto. Si no se visualiza, cambie al proyecto creado haciendo click en la en el menu que se encuentra remarcado en la imagen.

![](imgs/seleccionarproyecto.png)

Si tienes el mensaje "No cuentas con los permisos suficientes para ver esta página." como se muestra en la imagen anterior, de click en **API y Servicios** del panel izquierdo, y luego de cambiar a la página, hacer click en **HABILITAR API Y SERVICIOS**

![](imgs/habilitarapiyservicios.png)

Dentro del buscador "Buscar API y servicios" escriba **Gmail API**. Luego, habilitar la API dando click en **Habilitar**

![](imgs/gamialapi.png)

Tardará un momento en cargar y la página redireccionará a la página de configuración de la API.

* Haga click en **CREAR CREDENCIALES**, para crear las credenciales

![](imgs/crearcredenciales.png)

El primer paso es seleccionar el tipo de credencial. Seleccionamos **Gmail API** y tildamos la opción **Datos del usuario**. A continuación haga click en siguiente.

![](imgs/tipocredencial.png)

En la pantalla de consentimiento, escribir un nombre para la aplicación y seleccionar un correo electrónico.

![](imgs/pantallaconsentimiento.png)

En la pantalla de permisos, haga click en **AGREGAR O QUITAR PERMISOS**. Se abrirá un modal para seleccionar los permisos. En el filtro escriba **Gmail API**, click en el menu desplegable **Filas por pagina** y seleccione **100** para poder ver todas las opciones, seleccione todas tildando **API**, luego click en **Actualizar**.


![](imgs/agregarpermisos.png)

![](imgs/actualizar.png)

Una vez se agreguen los permisos seleccionados, da click en **GUARDAR Y CONTINUAR**

![](imgs/guardarycontinuar.png)

Finalmente, en la pantalla de OAuth, seleccionar el tipo de aplicación **APP de escritorio**, y agregar un nombre. Finalizamos dando click en crear.

![](imgs/oauth.png)

Nos creará las credenciales, damos click en descargar y luego en listo. Es importante mantener el archivo descargado. Se utilizará más adelante en el módulo.

![](imgs/descargar.png)

En el menú de la izquierda, al dar click en **Pantalla de consentimiento**, si tienes una cuenta corporativa de gmail, podrás utilizar la API indefinidamente y verás que el tipo de usuario es **Interno**. Si cuentas con una cuenta gmail gratuita, tendrás que dar el consentimiento una vez a la semana para poder conectarte a tu cuenta de correo y verás que tu tipo de usuario es **Externo** y deberás agregar usuarios de prueba.

![](imgs/interno.png)

![](imgs/externo.png)

Para prevenir confirmar cada semana, puedes publicar la aplicación para que google la apruebe y puedas usarla indefinidamente.



## Descripción de los comandos

### Configurar Servidor
  
Configurar el servidor del mail que se va a usar
|Parámetros|Descripción|ejemplo|
| --- | --- | --- |
|Credenciales|Ruta del archivo json descargado en el paso anterior|credentials.json|
|User|Email que se usará para enviar correos. Puede estar en blanco si no enviarás emails.|user@example.com|
|Sesión|Nombre de la sesión que le vamos a asignar|session1|
|Asignar resultado a Variable|Resultado de la conexion|Variable|

### Enviar Email
  
Envia un email, previamente debe configurar el servidor
|Parámetros|Descripción|ejemplo|
| --- | --- | --- |
|Sesión|Nombre de la sesión que va a usar.|session1|
|Para|Destinatarios del mensaje. Deben estar separados por coma|to@mail.com, to2@mail.com|
|Copia|Destinatarios enviados por copia. Deben ir separados por coma|cc@mail.com, cc2@mail.com|
|Copia Oculta|Destinatarios enviados por copia oculta. Deben ir separado por coma|bcc@mail.com, bcc2@mail.com|
|Asunto|Asunto del mensaje|Nuevo mail|
|Mensaje|Cuerpo del mail. Se pueden usar etiquetas html|Hi from Rocketbot!|
|Archivo Adjunto|Ruta del archivo que se desea adjuntar|C:\User\Desktop\test.txt|
|Carpeta (Varios archivos)|Ruta de la carpeta con los archivos que se desa adjuntar|C:\User\Desktop\Files|

### Lista todos los email
  
Lista todos los email, se puede especificar un filtro
|Parámetros|Descripción|ejemplo|
| --- | --- | --- |
|Filtro|Puedes usar todas las opciones de filtro de gmail.|subject:COMPRA|
|Carpeta|Carpeta desde donde se desa listar todos los emails|INBOX|
|Sesión|Nombre de la sesión que se va a usar|session1|
|Ordenar por||{}|
|Asignar a variable|Nombre de la variable donde se guardará la lista de email|Variable|

### Lista emails no leídos
  
Lista emails no leídos, se puede especificar un filtro
|Parámetros|Descripción|ejemplo|
| --- | --- | --- |
|Filtro|Puedes usar todas las opciones de filtro de gmail|subject:COMPRA|
|Carpeta|Especificar nombre de la carpeta desde donde se quiere obtener los emails, por defecto inbox|inbox|
|Sesión|Nombre de la sesión que va a usar|session1|
|Ordenar por||{}|
|Asignar a variable|Nombre de la variable donde se guardará la lista de email|Variable|

### Leer email por ID
  
Se puede especifiacar el ID de un email para leerlo
|Parámetros|Descripción|ejemplo|
| --- | --- | --- |
|ID del email|Id obtenido en los comandos para listar email|345|
|Sesión|Nombre de la sesión que va a usar|session1|
|Asignar a variable|Nombre de la variable donde se guardará el contenido del mail leído|Variable|
|Ruta para descargar adjuntos|Ruta de la carpeta donde se guardarán los archivos adjuntos|C:\User\Desktop|

### Crear Etiqueta
  
Se puede crear una etiqueta con el nombre que desees
|Parámetros|Descripción|ejemplo|
| --- | --- | --- |
|Nombre Etiqueta|Nombre de la etiqueta a crear|Ingrese nombre de la etiqueta|
|Sesión|Nombre de la sesión que va a usar|session1|

### Mover email a etiqueta
  
Mover email de una etiqueta a otra
|Parámetros|Descripción|ejemplo|
| --- | --- | --- |
|ID del email|ID obtenido en los comandos para listar email|Ingrese ID del email|
|Nombre de la etiqueta|Etiqueta a dónde se moverá el email|test|
|Sesión|Nombre de la sesión que va a usar|session1|
|Asignar resultado a variable|Variable donde se guardará. True si se movió el mail. Caso contrario, retomará False|Variable|

### Marcar email como no leído
  
Se puede marcar como no leido cualquier email previamente abierto
|Parámetros|Descripción|ejemplo|
| --- | --- | --- |
|ID del email|ID obtenido en los comandos para listar email|Ingrese ID del email|
|Sesión|Nombre de la sesión que va a usar|session1|

### Cerrar Conexión
  
Cierra la conexión del servidor
|Parámetros|Descripción|ejemplo|
| --- | --- | --- |
|Sesión|Nombre de la sesión que va a usar|session1|

### Lista todas las etiquetas
  
Obtiene una lista de todas las etiquetas del mail y las almacena en una variable
|Parámetros|Descripción|ejemplo|
| --- | --- | --- |
|Sesión|Nombre de la sesión que va a usar|session1|
|Asignar a variable|Variable donde se guardaran las etiquetas|Variable|

### Reenviar
  
Reenviar an email
|Parámetros|Descripción|ejemplo|
| --- | --- | --- |
|Sesión|Nombre de la sesión que va a usar|session1|
|ID Mail|ID obtenido en los comandos para listar email|321|
|Para|Destinatarios del mensaje. Deben estar separados por coma|to@mail.com, to2@mail.com|
|Copia|Destinatarios enviados por copia. Deben estar separados por coma|cc@mail.com, cc2@mail.com|
|Copia Oculta|Destinatarios enviados por copia oculta. Deben estar separados por coma|bcc@mail.com, bcc2@mail.com|
|Asunto|Asunto del mensaje|Nuevo mail|

### Descargar adjuntos por ID
  
Descarga los archivos adjuntos de un correo y los guarda en una carpeta
|Parámetros|Descripción|ejemplo|
| --- | --- | --- |
|ID del email|ID del email a leer|345|
|Sesión|Sesión de Gmail|Default|
|Ruta para descargar adjuntos|Ruta donde se guardarán los adjuntos|C:/User/Desktop|