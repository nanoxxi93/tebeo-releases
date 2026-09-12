# Tebeo

Visor de cómics e imágenes para Android que lee **directamente del NAS** —WebDAV, SMB, FTP, S3,
pCloud— sin copiar los tomos al teléfono.

Este repositorio no tiene código: solo publica los APK firmados. El código fuente es privado.

### [⬇ Descargar la última versión](https://github.com/nanoxxi93/tebeo-releases/releases/latest)

## Qué hace

Abre tus cómics y tus carpetas de imágenes donde ya están, sin importarlos a ninguna biblioteca.

**De dónde lee**

- WebDAV (Nextcloud, ownCloud, servidores propios)
- SMB 2 y 3, para carpetas compartidas de Windows y NAS
- FTP y FTPS
- HTTP, sobre índices de directorio
- S3: AWS, Cloudflare R2, Backblaze B2, Wasabi, MinIO y compatibles
- pCloud, conectando la cuenta desde su propia página
- DLNA
- Memoria del dispositivo y tarjeta SD

Los ZIP y CBZ se leen página a página: abrir la última hoja de un tomo de cien megas en el NAS
cuesta lo mismo que abrir la primera, porque solo se pide la página que se va a ver.

**Cómo se lee**

Seis modos de paso de página, con salto o desplazamiento continuo. Página sencilla, doble o
automática. Zoom que se mantiene al pasar hoja, zonas de toque configurables y pase automático con
temporizador. Para escaneos regulares: escala de grises, invertir, contraste automático, reescalado
(bilineal, bicúbico y Lanczos-3) y enfoque por máscara.

Guarda por dónde ibas en cada carpeta y en cada tomo. No sube nada a ninguna parte: no hay cuentas,
ni anuncios, ni telemetría.

**Qué no hace**

- No lee RAR ni PDF
- No habla SMB1, solo SMB2 en adelante
- DLNA está implementado pero no verificado contra un servidor real
- S3, de momento, solo lee: no borra, ni mueve, ni renombra
- pCloud pide registrar tu propia app en su consola de desarrolladores

## Instalar

Requiere **Android 8.0 (API 26)** o superior.

1. Descarga el APK de la [última versión](https://github.com/nanoxxi93/tebeo-releases/releases/latest).
2. Al abrirlo, Android pedirá permiso para instalar aplicaciones de esa fuente. Es el aviso normal
   de cualquier instalación fuera de una tienda.
3. **Después de instalar, concede el acceso a todos los archivos**, en Ajustes → Aplicaciones →
   Tebeo. Es un permiso especial que no aparece como diálogo: sin él la app arranca, pero no ve
   nada.

Si ya tenías instalada una compilación anterior de Tebeo, **desinstálala antes**. A partir de la
1.2.1 los APK van firmados con la clave de publicación definitiva, y Android no deja actualizar un
paquete cambiándole la firma.

## Verificar lo que descargaste

Cada versión publica el SHA-256 de su APK en las notas. Para comprobarlo:

```bash
sha256sum tebeo-1.2.1.apk
```

En Windows, `certutil -hashfile tebeo-1.2.1.apk SHA256`.

Y para confirmar quién firmó el paquete, con las herramientas del SDK de Android:

```bash
apksigner verify --print-certs tebeo-1.2.1.apk
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
