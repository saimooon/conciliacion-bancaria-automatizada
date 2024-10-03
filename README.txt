🏦 Conciliación Bancaria - Sistema de Automatización
Este proyecto implementa un sistema automatizado para la conciliación bancaria para los bancos Banco Estado y Banco BCI. Permite subir archivos de conciliación, procesarlos y realizar la conciliación entre la cartola bancaria y el libro mayor, generando reportes y archivos de salida.
📂 Estructura del Proyecto
Archivos y Descripción:
appPage.html:
Proporciona la interfaz de usuario para la aplicación de conciliación bancaria. Permite seleccionar el banco, subir archivos, procesarlos y ejecutar la conciliación.
Incluye pestañas para cada banco con botones interactivos.
Ver detalles.

appsscript.json:
Archivo de configuración para Google Apps Script. Define las dependencias necesarias (Google Sheets, Drive, Gmail, People API) y los permisos OAuth.
Configura la zona horaria de América/Santiago.
Ver detalles.

process_bci.js:
Gestiona el procesamiento de archivos de Banco BCI. Extrae los datos de las hojas de Cartola y Libro Mayor, y mueve los archivos procesados a una carpeta de Google Drive.
Ver detalles.

process_estado.js:
Similar a process_bci.js, pero para el Banco Estado. Procesa las hojas de cartola y libro mayor del Banco Estado y prepara los datos para la conciliación.
Ver detalles.

reconciliation_bci.js:
Ejecuta la conciliación automática para el Banco BCI. Compara los registros de la cartola con los del libro mayor utilizando coincidencias exactas y aproximadas (documento, montos, fechas).
Genera un archivo de conciliación con los resultados.
Ver detalles.

reconciliation_estado.js:
Realiza la conciliación automática de registros entre cartola y libro mayor para Banco Estado. Genera un archivo con los resultados de registros conciliados y pendientes.
Ver detalles.

upload.js:
Gestiona la subida de archivos, conversión a Google Sheets, y la verificación de acceso de usuarios. Los archivos se suben a las carpetas específicas de cada banco.
Ver detalles.


⚙️ Funcionalidades Principales
Subida de Archivos: Los usuarios pueden subir archivos en formato Excel, que se convierten automáticamente a Google Sheets.
Procesamiento de Archivos: Extrae los datos relevantes de la cartola y del libro mayor para cada banco.
Conciliación Automática: Compara los registros de la cartola con los del libro mayor, conciliando automáticamente donde haya coincidencias.
Generación de Reportes: Los archivos conciliados y pendientes son generados y almacenados en Google Drive.
Notificaciones por Correo: Los usuarios reciben correos electrónicos con los resultados de la conciliación, enlaces a los archivos procesados, y notificaciones de errores.




🚀 Instalación y Despliegue
1. Configuración Inicial:
Clona o descarga este repositorio.
Sube los archivos del proyecto a un entorno de Google Apps Script.

2. Habilitar APIs y Permisos:
En Google Cloud Platform, habilita las siguientes APIs:
Google Drive API
Google Sheets API
Gmail API
People API
Asegúrate de que los permisos OAuth estén configurados en el archivo appsscript.json para permitir el acceso a estos servicios.

3. Actualizar IDs de Carpetas:
En upload.js, actualiza los IDs de las carpetas de entrada para los archivos subidos:
javascript

var folderIdInputEstado = 'ID_DE_LA_CARPETA_DE_ENTRADA_BANCO_ESTADO';
var folderIdInputBCI = 'ID_DE_LA_CARPETA_DE_ENTRADA_BANCO_BCI';

En los archivos process_bci.js y process_estado.js, actualiza los IDs de las carpetas de salida:
javascript

var folderIdOutput = 'ID_DE_LA_CARPETA_DE_PROCESADOS';



En los archivos reconciliation_bci.js y reconciliation_estado.js, actualiza los IDs de las carpetas de conciliación:
javascript

var folderIdOutputConciliados = 'ID_DE_LA_CARPETA_DE_CONCILIADOS';

4. Desplegar la Aplicación:
Pública el proyecto en Google Apps Script como una aplicación web. Configura el acceso para que "cualquiera, incluso anónimos" puedan acceder a la web, pero limita la funcionalidad de subida de archivos a usuarios con dominio @hyl.cl.

5. Notificaciones por Correo:
Los usuarios recibirán correos automáticos con los resultados de las conciliaciones, archivos procesados, y notificaciones de errores.


📊 Uso
Subir un Archivo:
Selecciona el banco correspondiente (Banco Estado o BCI).
Sube el archivo de conciliación utilizando el botón de "Subir Archivo".
Procesar el Archivo:
Tras subir el archivo, selecciona "Procesar Archivo" para extraer los datos necesarios de la cartola y el libro mayor.
Conciliar Registros:
Una vez procesado el archivo, selecciona "Conciliar Registros" para ejecutar la conciliación automática. Recibirás un correo electrónico con el archivo de resultados.



🔐 API y Permisos
Este proyecto hace uso de las siguientes APIs:
Google Drive API: Para gestionar la subida, descarga y almacenamiento de archivos.
Google Sheets API: Para la creación y modificación de hojas de cálculo.
Gmail API: Para enviar notificaciones por correo.
People API: Para obtener la información del usuario que sube los archivos.


Este README proporciona una visión completa del sistema, sus funcionalidades, y su configuración. Si tienes dudas adicionales, revisa los comentarios dentro de los archivos fuente para obtener más detalles.

