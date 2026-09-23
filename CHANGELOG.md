# Registro de cambios

Formato de [Keep a Changelog](https://keepachangelog.com/es-ES/1.1.0/); versiones según
[SemVer](https://semver.org/lang/es/).

## [2.4.0] — 2026-09-23

El lector de libros ya sirve para una novela entera: se puede buscar en el libro, dejar marcadores y
escucharlo en voz alta, también con la pantalla apagada.

### Añadido

- **Buscar en el libro**, con la lupa de arriba. No mira mayúsculas ni tildes, y los resultados salen
  por capítulo según se van encontrando, cada uno con un trozo del texto alrededor. Al tocar uno se va
  a su página, con la palabra resaltada.
- **Marcadores.** Con el botón de arriba se marca la página que se está leyendo, y se quita con el
  mismo botón. Se ven en una pestaña junto al índice, con la frase que había en ese sitio, el capítulo
  y por dónde cae en el libro. Llevan al mismo sitio aunque se cambie el tamaño de letra.
- **Leer en voz alta**, con el botón de la barra de abajo. Usa el motor de voz del teléfono, empieza
  en la página que se ve y la página va pasando detrás de la voz. Sigue con la pantalla apagada y con
  la app en segundo plano; un aviso deja pausar, pasar al capítulo siguiente o parar. Calla si entra
  una llamada o suena otra cosa, y vuelve sola después. En los ajustes de lectura se eligen la
  velocidad, el tono, el idioma de la voz y si sigue con el capítulo siguiente. Salir del libro la
  para.

### Cambiado

- **La barra de progreso del libro cuenta lo que ocupa cada capítulo.** Antes cada uno contaba igual:
  un prólogo de dos páginas pesaba lo mismo que un capítulo de cuarenta, la barra iba a saltos y
  arrastrarla hasta la mitad no llevaba a la mitad del libro.
- **El índice y los marcadores van juntos**, en dos pestañas de la misma hoja.

### Corregido

- **Con el tema oscuro, el texto de la barra de abajo del lector se veía oscuro sobre oscuro.**

## [2.3.0] — 2026-09-23

Borrar deja de ser definitivo en el teléfono y en la tarjeta: lo borrado espera en una papelera y se
puede devolver a su sitio. Y marcar muchos tomos deja de ser un toque por tomo.

### Añadido

- **Papelera.** En el teléfono y en la tarjeta, lo que se borra pasa a una papelera en lugar de irse
  del todo, y no cuesta ni un segundo más: no se copia nada, solo cambia de sitio. Justo después de
  borrar aparece un **Deshacer**; más tarde, en Ajustes › Papelera está la lista de lo que espera
  dentro, de qué carpeta salió y cuándo, con devolverlo a su sitio o borrarlo del todo.
  Se vacía sola pasados los días que elijas, treinta de fábrica.
  **En un servidor no hay papelera** y se sigue borrando de verdad: allí mover cada fichero sería un
  viaje de ida y vuelta. El aviso de borrar lo dice en cada caso, así que siempre se sabe si hay
  vuelta atrás.
- **Preguntar antes de borrar se puede apagar**, en Ajustes. Con la papelera puesta hay quien
  prefiere quitarse el diálogo de en medio.
- **Seleccionar todo e invertir la selección**, en el menú de Ver más de la pestaña Carpetas.
  Trabajan sobre lo que se ve: con una búsqueda escrita no marcan lo que está escondido.
- **Seleccionar lo de en medio.** Se marcan dos tomos y la opción rellena todo lo que hay entre
  ellos. Es la forma de llevarse una serie entera sin ir tocando uno a uno.

## [2.2.3] — 2026-09-22

Una revisión de la app entera: el zoom se ve nítido en los cómics del teléfono, las copias dicen lo
que dejan sin tocar y se corrigen varios fallos que salían con un servidor lento.

### Corregido

- **Ampliar una página de un CBZ, CB7, PDF o EPUB del teléfono la emborronaba.** Se ampliaba la
  imagen reducida a la pantalla, no la original. Ahora se ve con el mismo detalle que una imagen
  suelta, y lo mismo lo que llega de otra app con «Abrir con».
- **Copiar una carpeta dentro de sí misma** creaba una cadena de carpetas vacías y acababa en error.
  Ahora lo dice antes de empezar y no crea nada. Moverla dentro de sí misma da el mismo aviso, en
  lugar de uno que no tenía que ver.
- **Una copia de más de seis horas con la app en segundo plano cerraba la app** en Android 15 o
  posterior. Ahora se para sola y un aviso explica por qué; al repetirla se salta lo ya copiado.
- **Las miniaturas de las fotos hechas en vertical salían tumbadas** en Carpetas.
- **Borrar en el visor con un servidor lento y pasar a otra carpeta** dejaba la nueva con las páginas
  de la anterior, y dos borrados seguidos podían hacer reaparecer el primero.
- **Crear, renombrar o mover con un servidor lento y abrir otra carpeta** devolvía el navegador a la
  de antes.
- **Algunas portadas de PDF podían no salir** en una carpeta con muchos PDF.
- **Un ZIP o CBZ con contraseña, o con una compresión poco habitual, salía vacío** sin decir por qué.
  Ahora lo dice, y los comprimidos en BZip2 o Deflate64 se abren.
- **El bloqueo con huella se podía saltar atrasando el reloj del teléfono.**
- **Conectar pCloud aceptaba una vuelta del navegador sin su comprobación de seguridad**, y con eso
  otra app podía colar su cuenta mientras se conectaba la tuya.
- **«Abrir con» podía abrir otro fichero** que tuviera la misma ruta en la memoria interna y en la
  tarjeta SD.
- **«Probar conexión» podía enseñar el resultado de una prueba anterior** si se cambiaba el
  formulario mientras contestaba el servidor.
- **«Acerca de» no nombraba** SFTP, S3, pCloud, OPDS, PDF, CB7 ni EPUB.

### Cambiado

- **Al copiar, lo que ya está con el mismo nombre y otro tamaño se cuenta aparte**: «con otro
  tamaño, sin tocar». Antes se contaba como si ya estuviera copiado.
- **Copiar a un servidor SMB o FTP, o abrir un tomo que esté en uno, ya no lista la carpeta entera
  para mirar un solo fichero.** En FTP, si el servidor lo admite; si no, se hace como antes.
- **Las portadas de PDF se pintan a tamaño de portada**, y una página de PDF o CB7 ya vista no se
  vuelve a pintar ni a descomprimir al volver a ella.

## [2.2.2] — 2026-09-22

Salir de un servidor que no contesta ya no borra la carpeta que se abre después.

### Corregido

- **Un servidor que no contestaba borraba la carpeta abierta después.** Si mientras un servidor
  intentaba conectar se volvía atrás y se abría el almacenamiento del teléfono, al rendirse el
  servidor su «no se pudo conectar» sustituía al listado del teléfono. Ahora ese aviso tardío se
  descarta y la carpeta abierta sigue como estaba.

## [2.2.1] — 2026-09-22

Comprobar a mano si hay versión nueva vuelve a avisar cuando la hay.

### Corregido

- **«Comprobar ahora», en Ajustes, no hacía nada cuando había versión nueva.** Encontraba la
  versión, pero el aviso no llegaba a salir. Ahora se abre con sus notas y el enlace para bajarla.
  El aviso automático, el de una vez al día al abrir la app, sí funcionaba.

## [2.2.0] — 2026-09-21

Tebeo ya no lee solo ZIP y CBZ: abre también PDF, CB7 y EPUB, y las novelas en EPUB se leen en un
lector de libros propio.

### Añadido

- **PDF.** Cada página se abre en el visor como una imagen más: zoom, doble página, filtros,
  historial y emitir a la tele funcionan igual. Un PDF de un servidor se lee a trozos, sin bajarlo
  entero. Si tiene contraseña, la app avisa de que no lo puede abrir.
- **CB7 y 7z.** Se leen como un CBZ, también desde un servidor.
- **EPUB de cómic o manga.** Se abre en el visor, con las páginas en el orden del libro.
- **Lector de libros para las novelas en EPUB.** Reparte el texto en páginas del ancho de la
  pantalla. Se pasa página tocando los lados o deslizando, y al acabar un capítulo se sigue con el
  siguiente. Tiene índice, enlaces entre capítulos y una barra para saltar a cualquier punto del
  libro. Se elige el tamaño y el tipo de letra, el interlineado, los márgenes y los colores (claro,
  sepia u oscuro), y recuerda por dónde ibas aunque cambies la letra. El libro no sale a internet
  ni ejecuta sus propios programas.
- **Portadas de los formatos nuevos** en Carpetas y en el Historial, con su icono propio. En el
  Historial, una novela dice cuánto llevas leído.
- **«Abrir con» desde otras apps** para PDF, EPUB y CB7.
- **Los catálogos OPDS enseñan también** los libros en PDF, EPUB y CB7.

## [2.1.0] — 2026-09-18

Lo que salió al usar la 2.0 en el teléfono: volver al vídeo que suena de fondo, una barra de
edición que cabe en vertical y menús ordenados.

### Añadido

- **Franja «Reproduciendo» en Inicio.** Si un vídeo abierto con «Abrir con» sigue sonando de fondo,
  sale abajo con su nombre y play/pausa, y tocarla vuelve al reproductor.

### Cambiado

- **La barra de edición de Carpetas lleva cinco botones**: Copiar, Mover, Renombrar, Borrar y
  «Ver más», que abre Descargar. Antes eran siete y en un teléfono en vertical no cabían.
- **Crear carpeta es el «+» de arriba, junto a la lupa**, y ya no hace falta entrar en edición.
- **«N/M seleccionados» va en la barra de título**, en lugar de una barra propia que quitaba sitio al
  listado.
- **Los menús de tres puntos del visor y del reproductor van en grupos**, con lo más usado arriba y
  borrar solo, al final.

### Corregido

- **El menú del reproductor se cortaba** en vertical: ahora se desplaza.
- **La notificación de «Seguir sonando al salir» dice el nombre del vídeo** y la carpeta, en lugar
  de «Tebeo se está ejecutando».
- **Tocar esa notificación lleva al reproductor.** Antes no hacía nada.
- **Abrir Tebeo con el vídeo en miniatura ya no crea otra copia de la app**, en la que el vídeo
  seguía sonando sin forma de volver a él.

## [2.0.0] — 2026-09-18

Dos protocolos nuevos, copiar entre almacenamientos y descargar para leer sin conexión, el
reproductor en la pantalla de bloqueo y en segundo plano, bloqueo con huella y pasar página con
teclado, mando o ratón.

### Añadido

- **Servidores SFTP.** El protocolo de cualquier NAS o servidor con SSH, con contraseña o con clave
  privada. Un CBZ grande abre por cualquier página sin bajarse entero. La primera vez se guarda la
  huella del servidor, y si cambia, la app avisa en vez de conectar.
- **Catálogos OPDS: Komga, Kavita, Calibre-Web.** Se navega por series y tomos, y un tomo que el
  servidor sirve por páginas se lee página a página, sin bajar el CBZ. Las portadas las da el propio
  catálogo.
- **Copiar entre almacenamientos.** En Carpetas, en modo edición: del NAS al teléfono, del teléfono a
  pCloud, entre dos servidores. Escribe en el teléfono, SMB, FTP, SFTP, WebDAV, S3 y pCloud. Sigue
  copiando aunque salgas de la app, con aviso y botón de cancelar, y lo que ya está con el mismo
  nombre y tamaño se salta.
- **Descargar para leer sin conexión.** Baja lo marcado a `Download/Tebeo` del teléfono. Repetir la
  descarga de una serie solo baja lo que falta.
- **Reproductor en la pantalla de bloqueo y en los auriculares**: pausa, reanudar, siguiente y
  anterior.
- **Seguir sonando al salir**, en el menú del reproductor: el vídeo sigue sonando con la app en
  segundo plano o con la pantalla apagada.
- **Temporizador de apagado** en el reproductor: de 10 a 90 minutos, o al acabar el vídeo.
- **Bloqueo con huella o con el código del teléfono**, al abrir la app y al volver tras el tiempo que
  elijas: siempre, 1, 5 o 15 minutos.
- **Ocultar el contenido en Recientes**, que también impide las capturas de pantalla.
- **Aviso de versión nueva.** Una vez al día se mira si hay una publicada, y el aviso abre su página.
  Se puede apagar y comprobar a mano en Ajustes.
- **Pasar página con teclado, pasapáginas Bluetooth, mando y rueda del ratón.** Las flechas siguen el
  sentido de lectura: en manga, la izquierda avanza. Inicio y Fin van a la primera y la última.
- **Tomo siguiente o anterior también entre CBZ y ZIP** de la misma carpeta.
- **Compartir, guardar en el carrete o poner de fondo** la página que se está viendo, con los filtros
  puestos.
- **GIF y WebP animados** se mueven en el visor.
- **Portadas de CBZ y ZIP** en Carpetas, sacadas de su primera página.
- **«Abrir con» acepta CBZ y ZIP** desde otras apps, no solo imágenes y vídeos.

### Cambiado

- **«Pasar página con el volumen» pasa a ser «Pasar página con teclas y mandos».** Quien lo tenía
  apagado lo sigue teniendo apagado.
- **La pulsación larga en Carpetas dura un poco más**, para no entrar en edición por dejar el dedo
  quieto un momento sobre un tomo.
- **En Carpetas se entra en edición también en un catálogo o un servidor HTTP**, con copiar y
  descargar; lo que escribiría en él sale apagado.

### Corregido

- **Carpetas no enseñaba sus mensajes**: ni los fallos al borrar, mover o renombrar, ni los
  resultados. Ahora salen como aviso.
- **Los filtros de contraste, enfoque y reescalado** se ven también en las páginas grandes que se leen
  a trozos al hacer zoom.

## [1.9.0] — 2026-09-16

Revisión general: la app deja de cerrarse cuando falla un servidor, va más rápida por la red, es más
segura con los certificados propios y se puede usar solo con servidores, sin dar acceso a todos los
ficheros.

### Añadido

- **Servidores sin permiso de ficheros.** El acceso a todos los archivos solo hace falta para el
  teléfono y la tarjeta SD. Almacenamiento lo pide con una ficha, sin tapar los servidores, y al
  concederlo se abre la carpeta del teléfono.
- **Informe de cierres.** Si la app se cierra de golpe, al volver a abrirla ofrece compartir un
  informe de lo ocurrido o descartarlo. No se envía nada salvo que elijas a dónde.
- **Página que no carga.** En lugar de quedarse en negro, la página avisa y se reintenta con un
  toque. Si el formato no lo admite esta versión de Android, lo dice.
- **Huella del certificado.** Con «aceptar certificado autofirmado», la app confía en el certificado
  que ve la primera vez y solo en ese; si el servidor presenta otro, avisa en vez de conectar. El
  formulario enseña la huella y deja olvidarla cuando se renueva.

### Cambiado

- **Valores por defecto del visor**: disposición de páginas desactivada, separación entre páginas
  al 0 %, zonas de paso de página al 35 % y sin deslizar el salto. Quien ya los había cambiado
  conserva los suyos.
- **SMB más rápido**: lee en tramos grandes y mantiene abierto el fichero mientras se usa.
- **FTP más rápido**: hasta dos conexiones por servidor, y cortar una descarga a medias ya no obliga
  a volver a conectar.
- **HTTP** pide solo el tramo que hace falta de un fichero dentro de un CBZ.
- **Las fotos del teléfono se amplían nítidas**, sin emborronarse al hacer zoom.
- **Miniaturas del teléfono** más rápidas y guardadas entre sesiones.
- **Editar un servidor lo deja en su sitio** de la lista, en lugar de mandarlo al final.
- **La copia de seguridad de Android ya no guarda los servidores**: sus contraseñas no se podían leer
  en otro teléfono. Si una contraseña guardada no se puede leer, su fila lo avisa.

### Corregido

- **Fallos de red que cerraban la app**: en Carpetas, en el visor, al pasar a la carpeta siguiente,
  al guardar o borrar un servidor y al emitir un vídeo cuando el servidor se cae. Ahora se avisa con
  el motivo.
- **«Probar conexión» dice por qué falla**, en lugar de un error genérico.
- **SMB**: un recurso compartido mal escrito, una contraseña incorrecta o un fichero que no existe
  dan su propio mensaje.
- **HTTP**: un error del servidor ya no se lee como si fuera la imagen.
- **Fotos giradas** por la cámara se miden con su orientación real.
- **Un CBZ cambiado** en el servidor o en el teléfono se vuelve a leer, en lugar de enseñar las
  páginas viejas. Tirar para refrescar en Carpetas también olvida las imágenes que cambiaron.
- **Recursos que quedaban abiertos**: el puerto de emisión se cierra al dejar de emitir, los CBZ
  sueltan el fichero y borrar un servidor cierra sus conexiones y su historial.
- **Tocar un fichero de DLNA** en Carpetas avisa de que aún no se puede abrir.
- **Notificación de la emisión a una tele DLNA** en Android 13 o más: se pide el permiso al conectar.

## [1.8.0] — 2026-09-16

Emitir el visor: las páginas de un cómic o de una carpeta de imágenes se ven en un Chromecast o en
una tele con DLNA, pasando hoja desde el teléfono.

### Añadido

- **Botón de emitir en el visor.** Al elegir un aparato se manda la página que se está leyendo, y
  cada vez que se pasa de hoja se manda la nueva. El teléfono sigue enseñando la página.
- **Girar en la tele.** Mientras se emite, un botón gira lo que se ve en la tele a la derecha o a la
  izquierda, para que una página vertical llene una pantalla apaisada. Vale para todas las páginas
  hasta salir del visor.
- **Con los filtros puestos.** Si se lee en escala de grises, con los colores invertidos, sin luz
  azul o con reescalado, contraste o enfoque, la tele ve la página igual que el teléfono.
- **Páginas de cualquier sitio**, también de un servidor o de dentro de un CBZ. Lo que el aparato
  sabe abrir le llega tal cual, sin trabajo para el teléfono; un formato que no lee se convierte
  antes de mandarlo.
- **El pase de diapositivas también emite**: cada página que pasa se ve en la tele.
- **Al salir del visor se deja de emitir.**
- **Con doble página no se emite**: se avisa de que hay que pasar a página simple.
- **Probado en un Chromecast.** A una tele con DLNA se puede mandar, pero aún no se ha probado.

## [1.7.0] — 2026-09-15

Emitir a la tele: los vídeos se ven en un Chromecast o en una tele con DLNA, manejados desde el
teléfono.

### Añadido

- **Botón de emitir en el reproductor.** Enseña los Chromecast y las teles con DLNA que haya en la
  Wi-Fi; al elegir uno, el vídeo pasa a verse allí desde el minuto en que iba.
- **El mando es el teléfono:** reproducir, pausa, la barra de tiempo, los saltos con doble toque y
  el vídeo anterior y siguiente. El historial guarda el minuto de lo que se ve en la tele.
- **Vídeos de cualquier sitio.** También los de un servidor SMB, WebDAV, FTP, S3 o pCloud, o los que
  están dentro de un comprimido: el teléfono se los sirve a la tele por la red local.
- **Subtítulos sueltos**, con la sincronía que se haya elegido. En el Chromecast se ven los de los
  ficheros SRT, ASS y VTT, sin sus estilos; en una tele con DLNA depende del modelo.
- **Sigue emitiendo con la pantalla apagada**, con un aviso desde el que pausar o dejar de emitir.
- **Avisa cuando el aparato no puede con el vídeo**, en vez de dejar la tele en negro. Un Chromecast
  de tercera generación, por ejemplo, no reproduce vídeo HEVC.
- **Al salir del reproductor se deja de emitir**, y la tele se queda libre.

## [1.6.0] — 2026-09-15

Abrir con Tebeo: las imágenes y los vídeos se abren desde otros exploradores y desde apps de nube.

### Añadido

- **Tebeo aparece en «Abrir con»** para imágenes y vídeos, desde exploradores como CX Explorer, la
  app Archivos o apps de nube como pCloud. Una imagen va al visor y un vídeo al reproductor.
- **Anterior y siguiente, si el fichero está en el teléfono.** Un fichero de la memoria interna o de
  la tarjeta SD se abre como desde Carpetas: se pasa a la imagen o al vídeo de al lado y queda en el
  historial.
- **Ficheros de apps de nube.** Lo que no tiene carpeta en el teléfono, como un vídeo de pCloud, se
  abre suelto: se ve y se puede avanzar o retroceder dentro del vídeo, pero sin anterior ni
  siguiente y sin entrar en el historial, porque al cerrarlo deja de poder leerse.
- **Al salir se vuelve a la app que lo abrió**, aunque Tebeo estuviera abierto por detrás.

## [1.5.0] — 2026-09-14

Reproducción en miniatura: el vídeo sigue en una ventana flotante mientras se usan otras apps.

### Añadido

- **Reproducción en miniatura**, en el menú de tres puntos del reproductor. El vídeo se encoge a una
  ventana flotante con la proporción del vídeo y sigue sonando mientras se usan otras apps. Ampliar
  la ventana devuelve el reproductor a pantalla completa; cerrarla con la X deja el vídeo en pausa y
  guarda el minuto en el historial.
- **Miniatura al salir**, una casilla en el mismo menú, marcada de serie. Con un vídeo sonando, pulsar
  Inicio lo pasa a la ventana solo; en pausa, o con la casilla quitada, se pausa como antes.
- **Anterior, reproducir o pausa y siguiente** dentro de la ventana. Anterior y siguiente pasan de
  capítulo o de vídeo igual que en la barra, y salen apagados cuando no hay a dónde ir.

## [1.4.0] — 2026-09-14

Los capítulos de un vídeo: anterior y siguiente saltan entre ellos, como en los reproductores de escritorio.

### Añadido

- **Anterior y siguiente saltan entre los capítulos del vídeo**, si el archivo los trae, que es lo
  habitual en los MKV de series, con el opening y el ending aparte. Siguiente va al capítulo que
  empieza después; anterior vuelve al principio del capítulo, o al de antes si acaba de empezar.
  Desde el último o desde el primero pasan al vídeo siguiente o al anterior de la carpeta, como
  hasta ahora, y al acabar un vídeo con «Reproducir el siguiente» se sigue pasando de vídeo.
- **Marcas en la barra de tiempo** donde empieza cada capítulo.

## [1.3.1] — 2026-09-14

Bloquear la rotación ya no pasa por vertical con el giro automático del teléfono apagado.

### Corregido

- **Bloquear o desbloquear la rotación en el reproductor giraba la pantalla a vertical unos
  segundos** antes de volver a horizontal, si el teléfono tenía la rotación automática apagada.
  Cada toque al candado soltaba primero la orientación, y suelta, la pantalla tomaba la del
  sistema. Ahora solo se suelta al salir del reproductor.
- **Lo mismo en el visor de imágenes** al usar el botón de girar o cambiar el ajuste de
  orientación con la rotación automática apagada.

## [1.3.0] — 2026-09-14

Vídeos: se listan con su miniatura, se abren en un reproductor propio y se reanudan donde se dejaron.

### Añadido

- **Un reproductor de vídeo**, aparte del visor de imágenes. Abre MP4, MKV, WebM, AVI, MOV, TS y
  otros desde cualquier almacenamiento, y salta a la mitad de un fichero de red sin bajar lo de
  antes.
- **Los controles de abajo**: bloquear la rotación, vídeo anterior y siguiente de la misma carpeta,
  reproducir o pausar, y un panel de más opciones con el modo de ajuste —que cambia con cada toque
  entre ajustar, rellenar, estirar y tamaño original—, la repetición A-B, la velocidad de 0,5x a
  2x, las pistas de audio y de subtítulos, y el bloqueo de controles. Se ocultan solos pasados unos segundos sin tocarlos,
  también con el panel abierto.
- **Un menú de tres puntos** arriba con «Reproducir el siguiente», que al acabar un vídeo empieza el
  siguiente de la carpeta; los ajustes de subtítulos; cuánto tardan en ocultarse los controles
  (3, 5, 7, 10 o 15 segundos, o nunca), y la ficha de información.
- **Ajustes de subtítulos**: tamaño y color, que se guardan, y la sincronía de este vídeo, para
  adelantarlos o retrasarlos cuando no van a tiempo.
- **Volver atrás unos segundos no vuelve a leer el vídeo.** Lo reproducido en los últimos treinta
  segundos se guarda, así que un doble toque atrás o el salto de una repetición A-B no descargan
  otra vez por la red.
- **Gestos**: doble toque a la izquierda o a la derecha para retroceder o avanzar diez segundos;
  arrastrar en vertical para el brillo, a la izquierda, o el volumen, a la derecha; y arrastrar en
  horizontal para moverse en el tiempo.
- **Subtítulos** incrustados en el vídeo o sueltos a su lado: un .srt, .ass, .ssa o .vtt que se
  llame igual, con o sin el idioma detrás («peli.es.srt»).
- **Una ficha de información** con el códec de cada pista de vídeo, audio y subtítulos, y cuáles no
  sabe decodificar el teléfono.
- **Miniaturas de vídeo** en el navegador, sacadas de un fotograma sin bajarse el vídeo.
- **Los vídeos entran en el historial** con el minuto por el que se iban, mezclados por fecha con
  las lecturas. Al volver a abrir uno, desde el historial o desde la carpeta, sigue ahí.

### Cambiado

- **El historial guarda como mucho 100 entradas, sumando lecturas y vídeos.** Antes eran 200
  lecturas: quien tuviera más perderá las más antiguas la próxima vez que se guarde algo.
- **El tipo de servidor se elige en un desplegable**, en lugar de una fila de botones donde los
  nombres salían cortados.
- **El nombre de una pestaña que no cabe se encoge** en lugar de partirse en dos líneas.
- **Por FTP, un tramo de un fichero se lee de un tirón.** Una página dentro de un CBZ cuesta una
  conexión de datos en lugar de una por trozo.

### Conocido

- **No hay decodificadores propios**, así que AC-3, E-AC-3 y sobre todo DTS dependen del teléfono.
  Si ninguna pista de audio de un vídeo es compatible, se ve sin sonido y se avisa.
- **Los subtítulos se pintan como texto**: sin los estilos de un ASS y sin subtítulos de imagen
  (PGS, VobSub).
- **Los subtítulos incrustados en el vídeo solo se pueden retrasar**; los sueltos, adelantar y
  retrasar.
- **Los vídeos de un servidor DLNA se listan, pero todavía no se abren.**

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
