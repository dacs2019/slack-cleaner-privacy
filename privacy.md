# Politica de privacidad - Slack Cleaner

Ultima actualizacion: 2026-06-13

Slack Cleaner ayuda al usuario a borrar sus propios mensajes en el chat de Slack Web que tiene abierto. La extension no esta afiliada, respaldada ni mantenida por Slack Technologies, Salesforce ni Google.

## Datos que procesa

La extension puede procesar localmente:

- URL de la pestana activa de Slack Web.
- ID del canal o mensaje directo abierto.
- Conteo de mensajes visibles y conteo de mensajes propios encontrados en el historial disponible.
- Timestamps de mensajes propios necesarios para solicitar su eliminacion.
- Credenciales internas de la sesion local de Slack Web, solo durante la operacion de deteccion, vista previa o borrado.
- Estado local del trabajo de borrado, como progreso, cantidad borrada, cantidad omitida y registros tecnicos.

La extension no solicita al usuario que copie tokens ni contrasenas.

## Uso de los datos

Los datos se usan solo para:

- Detectar el chat de Slack Web abierto.
- Confirmar que mensajes pertenecen al usuario actual.
- Mostrar una vista previa del rango de mensajes que se borraria.
- Enviar solicitudes a Slack para borrar mensajes propios seleccionados por el usuario.
- Mantener el progreso local si el popup se cierra durante el trabajo.

## Almacenamiento

La extension usa `chrome.storage.local` para guardar progreso y configuracion local. No guarda el token de Slack en almacenamiento persistente. El token se mantiene solo en memoria temporal del service worker mientras se necesita para llamar a Slack, y se limpia cuando el trabajo termina, se detiene o la credencial deja de ser valida.

Los registros locales no guardan el texto de los mensajes. Solo guardan informacion tecnica como timestamps, conteos y errores.

## Compartir datos

La extension no vende datos ni los usa para publicidad. La extension se comunica con:

- Slack, para leer el historial necesario y borrar mensajes propios.
- ExtensionPay, cuando el usuario consulta o activa funciones Pro.

No se transfiere contenido de Slack a servidores del desarrollador.

## Limited Use

El uso de la informacion recibida se limita a proveer y mejorar la funcion principal de la extension: borrar mensajes propios en Slack Web a solicitud del usuario. La extension cumple con las restricciones de Limited Use de Chrome Web Store User Data Policy.

## Contacto

Para soporte o preguntas de privacidad, usa el correo de soporte publicado en la ficha de Chrome Web Store.
