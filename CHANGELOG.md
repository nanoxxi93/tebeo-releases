# Registro de cambios

Formato de [Keep a Changelog](https://keepachangelog.com/es-ES/1.1.0/); versiones según
[SemVer](https://semver.org/lang/es/).

## [1.2.1] — 2026-09-12

Abrir la pestaña Almacenamiento ya no espera a la red.

### Corregido

- **La lista de almacenamientos tardaba unos cinco segundos en salir, en cada arranque.** Antes de
  pintar nada se buscaban servidores DLNA por la red local, y esa búsqueda escucha cuatro segundos
  fijos aunque no conteste nadie. Ahora el dispositivo, la tarjeta SD y los servidores dados de alta
  aparecen de inmediato, porque ninguno de ellos necesita salir a la red para saberse.
- **Abrir una carpeta pagaba esa misma espera.** Resolver de qué almacenamiento venía obligaba a
  recorrer la lista completa, y la lista completa incluía lo que había que ir a buscar. Afectaba
  también al visor y a las miniaturas, que lo hacen una vez por página.
- **Armar la lista descifraba la contraseña de cada servidor nueve veces**, y cada descifrado abría
  el almacén de claves del sistema por su cuenta. Iba además en el hilo de la interfaz, así que no
  solo tardaba: bloqueaba.
- **Una búsqueda de servidores DLNA que no encontraba nada no se recordaba**, de modo que quien no
  tiene ninguno —lo normal— la repetía entera en cada recarga, para siempre.

### Añadido

- **Una fila para buscar servidores en la red local**, al final de la lista. Enseña la búsqueda en
  marcha y busca de verdad cada vez, sin contestar con lo de hace un rato: si acabas de encender el
  servidor, aparece. Antes esto pasaba solo, sin decirlo y cuando no venía a cuento.

### Cambiado

- **Tirar hacia abajo recarga, y ya no busca por la red.** Buscar tarda, así que es su propia acción.
- **La pestaña ya no se tapa con una rueda mientras carga.** El atajo a lo último abierto y el botón
  de añadir servidor se pueden tocar desde el primer momento.

### Conocido

- **Un servidor DLNA no se resuelve hasta haberlo buscado en esa sesión.** Si cierras la app con una
  carpeta DLNA abierta, al volver dará «almacenamiento no disponible» hasta que toques «Buscar
  servidores en la red». Con un servidor dado de alta a mano no pasa.

## [1.2.0] — 2026-09-10

Dos almacenamientos en la nube: S3, con todo lo que habla su protocolo, y pCloud.

### Añadido

- **S3 y compatibles: AWS, Cloudflare R2, Backblaze B2, Wasabi, DigitalOcean Spaces, MinIO y
  Storj.** Se da de alta con la dirección que enseña la consola del proveedor, tal cual —el bucket
  en la ruta o en el host—, y la clave de acceso y la secreta. La región se deduce del host; si no
  se parece a nada conocido, se escribe en la propia dirección con `?region=`. Los CBZ se leen por
  rangos, sin bajarse el tomo entero. Probado contra Cloudflare R2.
- **pCloud, conectando la cuenta por el navegador.** Se entra en la página del propio pCloud, que
  es donde se resuelve la verificación en dos pasos, y a Tebeo solo vuelve el permiso: la
  contraseña no pasa por la app. La región, Estados Unidos o Europa, se averigua sola.
- **Miniaturas que sirve el propio servidor.** Con pCloud, pintar una carpeta de portadas ya no
  obliga a bajarse cada fichero entero para reducirlo en el teléfono: se pide la miniatura hecha.
- **Un ojo para ver la contraseña mientras se escribe.** El teclado sigue siendo de contraseña, para
  que no la aprenda ni la sugiera luego en otra app.

### Corregido

- **Cambiar solo la contraseña de un servidor WebDAV no surtía efecto hasta reiniciar la app.** El
  cliente guardado se reutilizaba mirando solo la dirección, y la contraseña vieja seguía dentro.

### Conocido

- **S3 es de solo lectura.** Borrar, mover y renombrar se encienden de golpe, y un borrado de
  carpeta contra almacenamiento que se paga por transferencia merece su propia tanda.
- **pCloud pide registrar una app propia** en su consola de desarrolladores y escribir su
  `client_id` al conectar. Esa app decide al registrarse si ve todas las carpetas o solo
  `/Applications/<nombre de la app>`, y no se puede cambiar después: con la segunda, los cómics
  tienen que estar dentro de esa carpeta. La app tiene que tener dadas de alta las dos direcciones
  de vuelta, `com.nanoxxi93.tebeo://oauth2redirect` y `com.nanoxxi93.tebeo.debug://oauth2redirect`.
- **Leer páginas y ver miniaturas desde pCloud está sin probar contra una cuenta real.** La
  conexión, el listado y crear carpetas, sí.

## [1.1.0] — 2026-09-09

Leer un tomo comprimido en red. Funcionaba ya; lo que faltaba era que no se notara.

### Añadido

- **Aviso de carga sobre el negro del visor.** Mientras la página baja se enseña el tanto por
  ciento, y cuando ya está bajada y lo que falta es descomprimirla y decodificarla, un girador
  con «Cargando…». Son dos tramos y solo el primero se puede medir, así que el número deja paso al
  girador en vez de quedarse clavado en cien, que se lee como atascado. No aparece hasta pasado un
  cuarto de segundo: en el móvil y en la tarjeta la espera casi nunca llega, y un parpadeo por
  página molesta más de lo que informa.

### Cambiado

- **Una página dentro de un comprimido se pide de una vez, no a trozos.** El directorio central ya
  dice dónde empieza y cuánto ocupa, así que se pide ese tramo entero y se descomprime según llega,
  igual que una imagen suelta. De siete peticiones por página a dos. Contra un servidor con 150 ms
  de ida y vuelta son medio segundo menos por página; en red local no se nota, porque no hay espera
  que ahorrar.
- **La página que se está mirando baja sola.** Lo que se adelanta espera a que esté. Bajar varias a
  la vez no las trae antes —reparten la misma conexión— y sí hacía que acabaran en desorden: con
  páginas de varios megas se veía aparecer la siguiente antes que la actual. Abrir un tomo de 32
  páginas de 8,8 MB pasó de nueve segundos de negro a cinco.
- **El adelanto va de una en una.** Se piden en el orden en que van a hacer falta, así que dos a la
  vez solo consigue que la siguiente —la única que urge— llegue a mitad de velocidad.
- **Cambiar de página ya no corta la descarga que estaba en marcha.** Cortarla no la ahorraba, la
  repetía desde cero: al llegar a una página que se estaba adelantando, el aviso saltaba del 57 %
  al 7 %. Ahora se reemplaza lo que queda por pedir y lo que ya está bajando termina.
- **El comprimido se lee pidiendo trozos que se van doblando** cuando el protocolo no sabe servir
  un tramo de un tirón. Antes eran veinticuatro peticiones por página, todas de 64 KB.

### Corregido

- **La página de al lado se descargaba dos veces, a la vez.** El visor compone la vecina y el
  adelanto la pide también; como la caché de disco solo deja escribir a uno, el otro se cansaba de
  esperar y se la bajaba otra vez para nada, quitándole ancho de banda a la que se estaba mirando.
  Ahora espera a la que ya está en marcha.
- **Dentro de un comprimido no se medía ninguna página.** Se preguntaba al almacenamiento por una
  referencia que solo entiende el lector de comprimidos, y el fallo se tragaba en silencio: la
  ficha de información enseñaba un guión en las dimensiones, las páginas dobles ya escaneadas no se
  detectaban y en lectura vertical continua cada página ocupaba una pantalla entera en lugar de su
  altura real.
- **Pasar páginas deprisa podía decir «no se pudo conectar».** Al adelantarse el lector, se
  interrumpe la decodificación de la página que se deja atrás, y esa interrupción se traducía como
  un fallo de red con el servidor perfectamente sano.
- **El contador decía «1 / 0» mientras se abría el tomo.** Ahora no dice nada hasta que hay páginas
  que contar.

## [1.0.1] — 2026-09-09

Arreglos sobre 1.0.0. No cambia nada de lo que se sabe hacer.

### Corregido

- **Carpetas con `+` en el nombre daban «no existe».** La ruta que devuelve el servidor se
  decodificaba con `URLDecoder`, que es el formato de los formularios y convierte `+` en espacio:
  la app acababa pidiendo una carpeta con otro nombre. Afectaba a WebDAV y a los índices HTTP.
- **Atrás en Historial cerraba la app.** Se consultaba el estado del navegador estuviera la pestaña
  que estuviera, y desde Historial nadie se ocupaba del botón. Ahora Historial vuelve a Carpetas.
- **Atrás con el filtro abierto no llegaba a la app.** Con el teclado desplegado se lo quedaba el
  teclado para cerrarse, y la búsqueda no se enteraba de que se había pulsado. Ahora la tecla se
  intercepta antes que el teclado y se deshace de uno en uno: el primer toque baja el teclado
  dejando el filtro puesto, y el segundo es el que lo quita.
- **El filtro se arrastraba al entrar en una carpeta.** Lo escrito para el listado anterior seguía
  puesto en el nuevo, que aparecía enseñando cuatro nombres de los cuarenta que tiene, o el aviso
  de que no hay coincidencias. Cambiar de carpeta lo reestablece, se llegue entrando, volviendo
  atrás, subiendo o desde el historial.
- **Las portadas de red no llegaban a generarse.** El fichero de trabajo de la miniatura se creaba
  con un prefijo de dos letras, menos del mínimo que exige el sistema: fallaba antes de escribir
  nada y en el navegador no salía ni una portada de red. Y un tropiezo al hacer la miniatura ya no
  tapa la imagen: se cae al camino de siempre y se trae la entera.
- **La posición del listado se colaba de una carpeta a otra.** Al abrir una carpeta se seguía
  viendo el listado de la anterior mientras llegaba el nuevo, y con él su posición. Ahora una
  carpeta nueva empieza por el principio y volver atrás devuelve a donde se estaba.
- **Salir del visor devolvía a la carpeta por la que se empezó**, no a aquella en la que se
  terminó tras saltar a la siguiente.

### Cambiado

- **Guardar y borrar un servidor se ven mientras pasan.** La fila aparece en el acto y se marca
  como que se está comprobando, sin tapar la pantalla, y la conexión se prueba sola al guardar.
- **Miniaturas cacheadas en disco, aparte de las páginas.** Recorrer una carpeta de red guardaba
  las imágenes enteras en la caché de páginas, expulsaba de ahí lo que se estaba leyendo y al
  volver no quedaba nada: parecía que no se cacheara. Ahora se guarda la miniatura reescalada, que
  ocupa decenas de kilobytes, y ojear una carpeta ya no compite con la lectura.

## [1.0.0] — 2026-09-07

Primera versión completa. Lo que sigue es lo que hay, no lo que cambió: antes de esto no había
versión publicada.

### Lectura

- Visor con paso de página en seis variantes —derecha, izquierda y vertical, cada una con su
  desplazamiento continuo—, disposición sencilla, doble o automática con detección de páginas
  dobles ya escaneadas, y ajuste a pantalla en cuatro modos.
- Zoom con doble toque, zoom fijado entre páginas, separación entre páginas y zonas de toque
  configurables para pasar hoja.
- Filtros de imagen: escala de grises, invertir, luz azul, contraste automático, reescalado
  (bilineal, bicúbico, Lanczos-3) y enfoque por máscara.
- Pase de diapositivas con temporizador, vuelta al principio y continuación en la carpeta
  siguiente.
- Ficha de información de la página, borrado con confirmación, giro, brillo, mantener la pantalla
  encendida y paso de página con las teclas de volumen.
- Pantalla completa siempre: las barras del sistema van y vienen con los controles del visor.

### Orígenes

- Dispositivo y tarjeta SD por ruta directa, más acceso por SAF.
- **WebDAV** con cliente propio sobre OkHttp, con PROPFIND y peticiones por rango.
- **SMB 2/3** con smbj, lecturas posicionales y sesiones reutilizadas.
- **FTP y FTPS** con Apache Commons Net.
- **HTTP** de solo lectura sobre índices de directorio autogenerados.
- **DLNA** con descubrimiento SSDP y ContentDirectory escritos a mano. Implementado, sin verificar
  contra un servidor real.
- **ZIP y CBZ** sobre cualquiera de los anteriores, leyendo solo las páginas que hacen falta y con
  la codificación de nombres configurable para los cómics en Shift_JIS.

### Navegación

- Tres pestañas: almacenamientos, carpetas e historial.
- Listado en rejilla, iconos o miniaturas, con orden configurable, búsqueda, selección múltiple y
  operaciones de crear, renombrar, mover y borrar.
- Portada de carpeta con su primera imagen.
- Posición del listado recordada por carpeta, tirar para refrescar y barra de posición.
- Historial reanudable en Room, con memoria de la última carpeta y opción de continuar leyendo al
  arrancar.

### Rendimiento

- Prefetch de páginas vecinas al tamaño que ocupan en pantalla.
- Límites de descarga y decodificación simultáneas, con descargas interrumpibles.
- Caché de páginas en disco con presupuesto configurable y caché de comprimidos con caducidad.
- Baseline profile incluido, y módulo `:baselineprofile` para grabar uno medido.

### Conocido

- DLNA no está verificado contra un servidor real.
- SMB1 no está soportado; smbj solo habla SMB2 en adelante.
- No hay RAR ni PDF.
- El APK de release va firmado con la clave de depuración.
