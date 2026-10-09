# Politica de privacidad - Own Message Cleaner for Slack

Ultima actualizacion: 2026-10-08 (version 0.7.0)

Own Message Cleaner for Slack ayuda al usuario a borrar sus propios mensajes en Slack Web: en el chat abierto, en varios chats elegidos o de forma programada. La extension no esta afiliada, respaldada ni mantenida por Slack Technologies, Salesforce ni Google.

## Datos que procesa

Todo el procesamiento ocurre en el navegador del usuario. La extension puede procesar:

- URL de las pestanas de Slack Web, para reconocer el workspace y el chat abierto.
- Lista de chats del usuario (canales, grupos y mensajes directos): ID, nombre, tipo y, en mensajes directos, el ID y el nombre de la otra persona.
- Conteo de mensajes propios por chat y, en el chat abierto, conteo de mensajes de otras personas.
- Timestamps de los mensajes propios, necesarios para pedir su eliminacion.
- Fecha y hora de los mensajes leidos, para las graficas de actividad (por mes, hora y dia de la semana).
- ID de los archivos que el usuario subio, solo cuando activa la opcion de borrar archivos.
- Datos de miembros del chat abierto, solo cuando el usuario pulsa copiar miembros: nombre, nombre real, ID, avatar, rol admin/owner y zona horaria.
- Credenciales internas de la sesion de Slack Web del propio usuario (token de sesion), para llamar a Slack en su nombre.

- Texto de los mensajes propios del chat abierto, solo cuando el usuario abre «Ver y respaldar»: se muestra en el popup para que elija cuales borrar y, si lo pide, se guarda en un archivo CSV en su equipo.
- Texto de los mensajes propios de varios chats o de todos, solo cuando el usuario pulsa «Respaldar» o activa «Respaldo antes de borrar»: se reune en memoria y se guarda en un archivo CSV en su equipo.
- Texto de los mensajes propios de los chats marcados, cuando el usuario abre «Ver y respaldar» con varios chats: se muestra en el popup para que elija cuales borrar.
- Lista de los workspaces de Slack con sesion iniciada en el navegador (ID y nombre), para que el usuario elija en cual trabajar. Solo se muestra un selector cuando hay mas de uno.
- Cantidad de mensajes que el usuario escribio en los ultimos 7 dias, solo si activa el resumen semanal o abre la pestana Mas: es un numero que devuelve la busqueda de Slack.
- Reacciones (emojis) que el usuario puso en mensajes, solo cuando activa «Mis reacciones»: chat, mensaje y nombre del emoji, para poder quitarlas.

Fuera de «Ver y respaldar» y de los respaldos, la extension no usa el texto de los mensajes: Slack lo devuelve al leer el historial o al buscar, y la extension solo usa el autor, el tipo y el timestamp de cada mensaje. El texto nunca se guarda en el almacenamiento de la extension ni en los registros; al cerrar la vista se descarta.

La extension no pide al usuario que copie tokens, contrasenas ni claves API.

## Uso de los datos

Los datos se usan solo para:

- Detectar el chat de Slack Web abierto y listar los chats del usuario.
- Confirmar que mensajes y archivos pertenecen al usuario actual.
- Contar los mensajes propios por chat y mostrar una vista previa de lo que se borraria.
- Enviar a Slack las solicitudes de borrado que el usuario pidio, a mano o con la limpieza automatica que el mismo configuro.
- Simular un borrado: recorrer los chats y contar lo que se borraria sin borrar nada.
- Mostrar los mensajes propios antes de borrarlos y descargar un respaldo local, cuando el usuario lo pide.
- Mostrar graficas de actividad del usuario.
- Copiar al portapapeles una tabla de miembros del chat abierto, cuando el usuario lo solicita.
- Mantener el progreso si el popup se cierra, y avisar con una notificacion cuando un trabajo termina.

## Actividad automatica

- Al cargar una pestana de Slack Web, la extension puede listar los chats del usuario y contar sus mensajes propios en segundo plano, para que la lista este lista al abrir el popup. Es solo lectura.
- La limpieza automatica esta apagada por defecto. Si el usuario la activa, la extension borra sus mensajes propios en los chats y con la frecuencia que el eligio (desde cada hora hasta cada 7 dias), conservando los mensajes recientes que el indique, sin pedir confirmacion en cada ejecucion. Puede abrir una pestana de Slack para hacerlo.
- Los chats marcados como protegidos nunca se cuentan ni se limpian.

## Almacenamiento

En `chrome.storage.local` (disco, solo en este navegador):

- Progreso del trabajo de borrado: contadores, cola de timestamps pendientes y registro tecnico. La cola y los timestamps procesados se vacian al terminar o detener el trabajo.
- Lista de chats con su nombre y el conteo de mensajes propios.
- Chats protegidos y configuracion de la limpieza automatica (IDs y nombres de chat, y cuanto conservar en cada uno).
- Historial de los ultimos 20 trabajos: chat, fechas y cantidades. Se muestra en la pestana Mas.
- Workspace elegido, y si el resumen semanal esta activado y cuando se envio el ultimo.

Mientras un borrado esta en curso, su progreso vive en la memoria de la extension y se copia a este almacenamiento cada pocos segundos.

En `chrome.storage.session` (solo memoria, nunca en disco):

- El token de la sesion de Slack Web, junto con el ID y la URL del workspace, durante un maximo de 2 dias. Permite que la limpieza automatica funcione sin tener Slack abierto. Se borra al cerrar el navegador y cuando Slack lo rechaza; cada visita a Slack lo renueva.

El token nunca se escribe en `chrome.storage.local`, nunca llega al popup y se enmascara si aparece en un mensaje de error.

En el almacenamiento local del popup se guardan solo preferencias de interfaz: velocidad, vista de actividad, idioma y el interruptor de simulacion.

El archivo de respaldo se guarda en la carpeta de descargas del usuario y queda bajo su control; la extension no conserva copia.

Los registros no guardan el texto de los mensajes: solo conteos, nombres de chat y errores tecnicos.

Desinstalar la extension elimina todos estos datos.

## Compartir datos

La extension no vende datos, no los usa para publicidad y no los transfiere a servidores del desarrollador ni de terceros.

La extension se comunica unicamente con Slack (`slack.com` y sus subdominios) para leer el historial necesario, buscar y borrar mensajes y archivos propios, y leer los miembros de un chat a solicitud del usuario. La tabla de miembros solo se copia al portapapeles del usuario.

## Pagos

La version actual no incluye compras, suscripciones ni funciones Pro. Si se agregan pagos en el futuro, esta politica se actualizara antes de publicar esa version.

## Limited Use

El uso de la informacion recibida se limita a proveer la funcion principal de la extension: gestionar y borrar los mensajes propios del usuario en Slack Web, a solicitud suya. La extension cumple con las restricciones de Limited Use de Chrome Web Store User Data Policy.

## Contacto

Para soporte o preguntas de privacidad, usa el correo de soporte publicado en la ficha de Chrome Web Store.
