# Tebeo

Visor de cómics, imágenes y libros para Android que lee **directamente del NAS** —WebDAV, SMB, FTP,
SFTP, S3, pCloud, catálogos OPDS— sin copiar los tomos al teléfono. Y si quieres llevártelos, los
descarga para leer sin conexión.

Este repositorio no tiene código: solo publica los APK firmados. El código fuente es privado.

### [⬇ Descargar la última versión](https://github.com/nanoxxi93/tebeo-releases/releases/latest)

## Qué hace

Abre tus cómics y tus carpetas de imágenes donde ya están, sin importarlos a ninguna biblioteca.

**De dónde lee**

- WebDAV (Nextcloud, ownCloud, servidores propios)
- SMB 2 y 3, para carpetas compartidas de Windows y NAS
- FTP y FTPS
- SFTP, con contraseña o con clave privada
- Catálogos OPDS: Komga, Kavita, Calibre-Web y compatibles
- HTTP, sobre índices de directorio
- S3: AWS, Cloudflare R2, Backblaze B2, Wasabi, MinIO y compatibles
- pCloud, conectando la cuenta desde su propia página
- DLNA
- Memoria del dispositivo y tarjeta SD

Los ZIP y CBZ se leen página a página: abrir la última hoja de un tomo de cien megas en el NAS
cuesta lo mismo que abrir la primera, porque solo se pide la página que se va a ver. En un catálogo
OPDS que sirve los tomos por páginas, ni siquiera se abre el CBZ: se pide cada página suelta.

Además de ZIP y CBZ abre CB7 y 7z, PDF y EPUB. Cada página de un PDF se ve como una imagen más, con
zoom, doble página y filtros, y un PDF del servidor se lee a trozos, sin bajarlo entero. Los EPUB de
cómic o manga se abren en el visor; las novelas, en un lector de libros aparte.

Tebeo aparece también en «Abrir con» de otras apps, para imágenes, vídeos, CBZ, ZIP, CB7, PDF y EPUB.

**Cómo se lee**

Seis modos de paso de página, con salto o desplazamiento continuo. Página sencilla, doble o
automática. Zoom que se mantiene al pasar hoja, zonas de toque configurables y pase automático con
temporizador. Para escaneos regulares: escala de grises, invertir, contraste automático, reescalado
(bilineal, bicúbico y Lanczos-3) y enfoque por máscara.

Se pasa página con el dedo, con las teclas de volumen, con un teclado, con un pasapáginas Bluetooth,
con un mando o con la rueda del ratón; en manga, la flecha izquierda avanza. Al acabar un tomo se
salta al siguiente de la carpeta, sea una carpeta de imágenes o un CBZ. Los GIF y WebP animados se
mueven, y la página que se está viendo se puede compartir, guardar en el carrete o poner de fondo.

**Libros**

Las novelas en EPUB se leen en páginas del ancho de la pantalla, con índice y una barra para saltar a
cualquier punto del libro. Se elige el tamaño y el tipo de letra, el interlineado, los márgenes y los
colores —claro, sepia u oscuro—, y recuerda por dónde ibas aunque cambies la letra.

Se puede buscar en el libro sin mirar mayúsculas ni tildes, dejar marcadores y escucharlo en voz alta
con el motor de voz del teléfono, también con la pantalla apagada. El libro no sale a internet ni
ejecuta sus propios programas.

**Organizar, copiar y descargar**

Lo que se borra en el teléfono o en la tarjeta va a una papelera, de donde se recupera durante los
días que elijas; en un servidor se borra de verdad, y el aviso lo dice antes. Para marcar muchos
tomos de golpe se puede seleccionar todo, invertir la selección, o marcar dos y rellenar lo de en
medio.

Lo marcado en una carpeta se copia a cualquier otro almacenamiento: del NAS al teléfono, del teléfono
a pCloud, de un servidor a otro. Reciben copias el teléfono, SMB, FTP, SFTP, WebDAV, S3 y pCloud. La
copia sigue aunque salgas de la app, con su aviso y su botón de cancelar.

Descargar baja los tomos a `Download/Tebeo` para leerlos sin conexión. Lo que ya está se salta, así
que repetir la descarga de una serie solo baja lo que falta.

**Vídeos**

Los vídeos de las mismas carpetas se abren en un reproductor propio, que salta a mitad de un
fichero del NAS sin bajar lo anterior: pistas de audio y subtítulos, repetición A-B, velocidad,
gestos de tiempo, brillo y volumen, y paso automático al siguiente de la carpeta. Se controla desde
la pantalla de bloqueo y con los botones de unos auriculares, puede seguir sonando con la app en
segundo plano y tiene temporizador de apagado. Si el fichero trae capítulos, anterior y siguiente
saltan entre ellos, y el vídeo se puede encoger a una ventana flotante mientras usas otras apps.

**Emitir a la tele**

Los vídeos y las páginas del visor se mandan a un Chromecast o a una tele con DLNA de la red local,
estén en el teléfono, en un servidor o dentro de un CBZ. Las páginas llegan con los filtros puestos y
se pueden girar en la tele. El teléfono hace de mando, y sigue emitiendo con la pantalla apagada.

**Privacidad**

Puede pedir la huella, o el código del teléfono, al abrirla y al volver tras el tiempo que elijas. Y
puede ocultar su contenido en la vista de apps recientes, lo que también impide las capturas de
pantalla.

Guarda por dónde ibas en cada carpeta, en cada tomo y en cada vídeo. No hay cuentas, ni anuncios, ni
telemetría. Lo único que sale del teléfono sin que lo pidas es una consulta diaria a este
repositorio para saber si hay versión nueva, que no envía nada tuyo y se apaga en Ajustes.

**Qué no hace**

- No lee RAR
- No habla SMB1, solo SMB2 en adelante
- DLNA, SFTP y OPDS están implementados pero aún no verificados contra un servidor real
- Los vídeos de un servidor DLNA se listan, pero aún no se abren
- Emitir las páginas del visor solo se ha probado en un Chromecast; los vídeos, también en una tele
  LG con DLNA
- De OPDS, solo la versión 1.2; no OPDS 2.0
- S3 recibe copias, pero no borra, ni mueve, ni renombra
- pCloud pide registrar tu propia app en su consola de desarrolladores

## Instalar

Requiere **Android 8.0 (API 26)** o superior.

1. Descarga el APK de la [última versión](https://github.com/nanoxxi93/tebeo-releases/releases/latest).
2. Al abrirlo, Android pedirá permiso para instalar aplicaciones de esa fuente. Es el aviso normal
   de cualquier instalación fuera de una tienda.
3. Para abrir el teléfono y la tarjeta SD, **concede el acceso a todos los archivos** en Ajustes →
   Aplicaciones → Tebeo. Sin él la app funciona con servidores, y ella misma lo pide cuando hace
   falta.

Si ya tienes la 1.2.1 o una posterior, instala encima: va firmada con la misma clave y se conservan
servidores e historial. Si tenías una compilación anterior a la 1.2.1, **desinstálala antes**: iba
firmada con otra clave, y Android no deja actualizar un paquete cambiándole la firma.

Desde la 2.0.0, la propia app avisa cuando hay una versión nueva y abre su página para descargarla.

## Verificar lo que descargaste

Cada versión publica el SHA-256 de su APK en las notas. Para comprobarlo:

```bash
sha256sum tebeo-2.0.0.apk
```

En Windows, `certutil -hashfile tebeo-2.0.0.apk SHA256`.

Y para confirmar quién firmó el paquete, con las herramientas del SDK de Android:

```bash
apksigner verify --print-certs tebeo-2.0.0.apk
```

La huella del certificado es la misma en todas las versiones, y es esta:

```
47:D2:B2:EE:25:15:C4:B6:2D:62:F4:98:C2:19:FC:9C:23:76:F6:95:CE:F8:E6:8B:58:FE:AE:E1:50:63:E0:A3
```

Si no coincide, el archivo no salió de aquí.

## Por qué se instala a mano y no desde Google Play

Tebeo pide `MANAGE_EXTERNAL_STORAGE`, que es el permiso que permite leer la tarjeta SD por ruta
directa. Google Play lo restringe: hay que justificar por qué el acceso por SAF no basta, y solo lo
aprueban para categorías concretas —gestores de archivos, antivirus, copias de seguridad—. Un visor
puede quedarse fuera, así que la distribución es por sideload.

## Cambios

En [CHANGELOG.md](CHANGELOG.md), y en las notas de cada [versión publicada](https://github.com/nanoxxi93/tebeo-releases/releases).

## Licencia

Apache 2.0 — ver [LICENSE](LICENSE).
