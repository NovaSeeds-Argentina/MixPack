# NOVA Seeds — versión actualizada

Sitio estático. Publicar el contenido del ZIP, sin una carpeta contenedora adicional, en el directorio del sitio. No requiere dependencias para funcionar.

## Archivos activos

- `index.html`: página de inicio.
- `tutorial.html`: página secundaria existente.
- `css/styles.css`: estilos compartidos; al final se encuentra el bloque de ajustes visuales 2026.
- `js/app.js`: carrusel y galería existentes.
- `js/pwa.js`: instalación y registro de service worker.
- `sw.js`: caché versionada, recursos locales y fallback de navegación.
- `manifest.webmanifest`: manifiesto único, con rutas relativas.
- `img/`: recursos gráficos (se mantienen los iconos de instalación PNG y la vista previa social JPG).

## Cambios

- Compresión de imágenes mediante WebP a calidad 90, sin reducir dimensiones.
- Corrección de declaraciones CSS con errores de sintaxis y eliminación de declaraciones idénticas dentro de una misma regla, reglas vacías y fragmentos CSS huérfanos.
- Ajustes de espaciado, superficies, separadores, encabezado y distribución adaptable. El carrusel conserva su desplazamiento móvil y muestra las tres tarjetas en escritorio.
- Registro PWA relativo, sin referencias a una ubicación antigua; caché versionada y limitada al sitio. Los recursos externos como el mapa no están disponibles sin conexión.
- Se retiraron los scripts y hojas de estilo antiguos que no eran referenciados por las páginas activas. El ZIP original sigue siendo el respaldo.
- Se conservaron los textos, datos, precios y contactos existentes.

- Se restauró la animación original de aparición y desaparición del distintivo 20% OFF en las tarjetas 01 y 02 (ciclo de 4 segundos).

- Vista de escritorio de las galerías 01 y 02: panel de imagen con tamaño estable, seis miniaturas siempre visibles, fichas técnicas con desplazamiento independiente y dos columnas en pantallas a partir de 1400 px. El diseño móvil no cambia.

## Publicación y verificación

Para comprobar en local, servir por HTTP desde la raíz del proyecto, por ejemplo con `python -m http.server 8000`. La PWA requiere HTTPS en producción (localhost es una excepción). Para publicar, mantener la estructura original de carpetas y eliminar del alojamiento los archivos obsoletos reemplazados por esta versión. Para futuras actualizaciones de recursos, cambiar `CACHE_NAME` en `sw.js` para invalidar la versión anterior. No requiere instalar bibliotecas.

Validación efectuada: sintaxis JavaScript y CSS, manifiesto, rutas locales y ZIP. Se verificaron las dos galerías en Chromium con HTML, CSS, JavaScript e imágenes locales integrados en una página de prueba (1728 × 864, 1440 × 900, 1280 × 720, 1024 × 768 y 390 × 844). En escritorio se comprobó el cambio de las seis miniaturas, la estabilidad del área de imagen y la ausencia de superposición de botones. La navegación HTTP está bloqueada en este entorno, por lo que falta comprobar el sitio publicado y la instalación PWA en dispositivos reales.

- Ajuste v9: las cuatro fichas técnicas de las galerías 01 y 02 ocupan toda la altura disponible a partir de 1400 px, en dos filas iguales; los detalles se reparten verticalmente sin cambiar el contenido ni la vista móvil.

- Ajuste v10: galería 03 en escritorio (desde 901 px) en una sola columna centrada, con imagen de proporción estable, tres miniaturas y descripción debajo. Se elimina la división horizontal y la altura sobrante. Las otras galerías y la vista móvil mantienen sus estilos. Caché v10.
Verificación v10: Chromium con recursos locales incrustados (1920 × 1080, 1728 × 864, 1366 × 768, 1280 × 600, 1024 × 768 y 390 × 844). Se verificó la distribución vertical, el cambio de miniaturas, el cierre y la conservación de las cuatro fichas de las galerías 01 y 02 a 1920 y 1728 px. En pantallas bajas se mantiene el scroll. HTTP y PWA en producción pendientes.

- Ajuste v11: distintivos de las tarjetas 01 y 02 sincronizados en un único reloj de documento, con pausa de 5 s, entrada de 0,6 s, permanencia de 3 s y salida de 0,5 s. Se conserva el gráfico existente y la vista de las galerías. Se desactiva el movimiento del distintivo cuando el sistema solicita reducir animaciones. Caché v11.
Verificación v11: sintaxis de JavaScript y CSS; prueba aislada del ciclo en Chromium con CSS, función de sincronización y gráfico del proyecto, a 1728 × 864 y 390 × 844. Se comprobó el reloj común, la opacidad en cada fase y la repetición. También se probó la preferencia de movimiento reducido. La navegación HTTP y la PWA publicada quedan pendientes.

- Ajuste v12: ciclo sincronizado de 8,6 s; pausa de 5 s, entrada y rebote de 320 ms, permanencia de 3 s con dos pulsos breves y salida de 280 ms. Se conserva el reloj común, la preferencia de movimiento reducido y el resto del sitio. Caché v12.

- Ajuste v13: pausa sin distintivo reducida de 5 s a 2 s. Ciclo de 5,6 s; se mantienen entrada de 320 ms, permanencia de 3 s, dos pulsos, salida de 280 ms y sincronización. Caché v13.

- Ajuste v14: animación del banner al entrar en pantalla (400 ms), destello diagonal, escala máxima de 1,015, pulso del X3 y subrayado animado. Ciclo sincronizado interno de 4,8 s con aproximadamente 4 s de reposo; solo activo en pantalla y con respeto a la preferencia de movimiento reducido. No cambia el ciclo v13 de las tarjetas. Caché v14.
Verificación v14: Chromium con la sección, la hoja CSS completa y la función de observación local, a 1728 × 864 y 390 × 844; se comprobó la activación y detención por scroll, el reposo del destello y el modo de movimiento reducido. Navegación HTTP bloqueada en el entorno; publicación y PWA pendientes.

- Ajuste v15: alternancia de Llevate 3 (4,4 s por turno) y Red Line (8,4 s por turno), con tres imágenes aportadas por el usuario, sin agregar una tarjeta de producto. En escritorio se muestran las tres imágenes y rota el destaque; en móvil se muestra una por vez. Controles de selección, pausa y navegación manual, gestos táctiles y detención fuera de pantalla. Se respeta la preferencia de movimiento reducido. Caché v15. Prueba aislada en Chromium a 1728, 390 y 320 px de ancho: altura estable y controles manuales; alternancia automática verificada a 390 px. Publicación y PWA real pendientes.

- Ajuste v16: eliminación de los tres botones de selección y pausa de anuncios, cambio del subtítulo visible de Red Line a 2027. Se mantienen las flechas e indicadores de sus imágenes y el ciclo automático de 4,4 / 8,4 s. La rotación se pausa durante el foco visible de teclado; en movimiento reducido alterna sin transiciones. Caché v16. Prueba aislada del ciclo en Chromium a 1728 y 390 px; publicación pendiente.

- Ajuste v18: separación entre secciones en pantallas de hasta 900 px. Márgenes verticales de los separadores de 14 a 24 px y margen entre el bloque rotativo y la guía de 14 a 28 px. Escritorio sin cambios. Caché v18. Comparación de geometría en Chromium con HTML y estilos locales integrados a 320, 390, 465, 768 y 1440 px: sin desbordamiento horizontal ni cambio de altura del bloque rotativo; escritorio idéntico. Prueba HTTP y PWA publicada pendientes.

- Ajuste v19: las tres imágenes del carrusel Red Line ocupan el ancho interno del panel en pantallas de hasta 600 px, con superficie cuadrada estable y ajuste contain para evitar recortes. Se agrega luz roja móvil detrás del encabezado, con ciclo de 2,8 s, activa solo cuando Red Line está visible; la preferencia de movimiento reducido conserva únicamente una luz fija. El espacio de ambas publicidades crece en móvil para mantener la misma altura durante la alternancia. Caché v19. Verificación en Chromium con HTML y recursos locales integrados a 320, 390, 465, 600, 768 y 1440 px: dimensiones estables entre anuncios, ausencia de desbordamiento horizontal, selección manual y movimiento reducido a 390 px. Navegación HTTP bloqueada; web publicada y PWA real pendientes.

- Ajuste v20: sección Envíos compacta en móvil y escritorio, con ambos logos originales en dos columnas, separación vertical sutil y anchos compensados por el espacio transparente del logo Andreani. Caché v20. Verificación de HTML y CSS con imágenes locales integradas en Chromium a 320, 390, 465, 600, 768 y 1440 px: ambos logos cargados, alineados y sin desbordamiento; altura de 122 a 148 px. Navegación HTTP bloqueada por el entorno, PWA y web publicada pendientes.

- Ajuste v21: se reemplaza la composición monolítica de Llevate 3 por capas HTML/CSS independientes: fondo, iluminación, líneas diagonales, partículas, destello, textos y cifra x3. Se conserva el mensaje, la rotación de 4,4 / 8,4 s con Red Line, la altura estable durante el cambio y el modo de movimiento reducido. Se conserva img/f1.webp como recurso original, aunque ya no se utiliza en el banner. Caché v21. Verificación aislada en Chromium con el HTML de la sección, CSS completo, imágenes locales integradas y función original de rotación a 320, 390, 465, 600, 768 y 1440 px: contenido dentro del panel sin desbordamientos, animación activa, ciclo completo y altura estable a 390 px, movimiento reducido sin animaciones. Web publicada y PWA real pendientes.

- Ajuste v22: fondo más oscuro con menor intensidad de luz, líneas y partículas; animación de texto en dos fases independientes (introducción y bloque inferior), con entradas escalonadas y un pulso adicional. Se conserva el ciclo de rotación de 4,4 / 8,4 s, Red Line y el movimiento reducido. Caché v22. Validación aislada en Chromium a 320, 390, 465, 600, 768 y 1440 px: fases, contenido sin desbordamiento, alternancia y altura estable a 390 px, movimiento reducido. Publicación y PWA real pendientes.

- Ajuste v23: Llevate 3 se integra con el fondo negro de la página, sin borde visible, esquinas de tarjeta ni sombra interior. Las luces, líneas y partículas se agrupan en una capa decorativa con máscara gradual para desvanecerse hacia los bordes. Se conserva el contenido, la altura de la sección y las animaciones v22; el destello queda dentro de la capa ambiental, detrás del texto. Caché v23. Validación visual aislada en Chromium a 320, 390, 600, 768 y 1440 px con movimiento reducido; sin desbordamiento en el contenedor. Web publicada y PWA real pendientes.

- Ajuste v24: ciclo de 14 s con dos turnos consecutivos de 4,5 s del panel Llevate 3 y un turno de 5 s de Red Line. Entre las dos apariciones se desvanece el bloque de texto durante 220 ms y se reinician las animaciones de entrada; no se muestra Red Line entre ellas. Las tres imágenes de Red Line reparten su turno. Caché v24.

Verificación v24: prueba aislada del orden, tiempos con reloj controlado y reinicio de animaciones en Chromium a 390 y 1440 px. Sintaxis JavaScript validada. Web publicada y PWA real pendientes.

- Ajuste v25: dos turnos de 7 s del panel Llevate 3 (antes 4,5 s cada uno), seguidos por 5 s de Red Line. Ciclo de 19 s. Se mantiene el reinicio de animaciones y el desvanecimiento de 220 ms incluido en el primer turno. Caché v25.
Verificación v25: prueba aislada del orden, tiempos y reinicio de animaciones mediante reloj controlado en Chromium a 390 y 1440 px; sintaxis de JS validada. Web publicada pendiente.

- Ajuste v26: reemplazo de img/red-line/portada.webp por la imagen suministrada (PNG convertido a WebP, 1254 × 1254 px). Caché v26. Sin cambios en las animaciones ni en la distribución.

- Ajuste v27: eliminación exclusiva del separador entre el carrusel principal y el bloque rotativo. Se conservan los demás separadores y las animaciones. Caché v27.


- Ajuste v28: transición fusionada entre Llevate 3 y Red Line: barrido diagonal rojo sobre un escenario de altura constante, salida/entrada superpuestas, título e imágenes de Red Line con entrada escalonada y Llevate 3 con secuencia escalonada de texto y premio. Se conservan dos apariciones de 7 s y una de Red Line de 5 s (ciclo de 19 s), contenido, flechas y carrusel. Preferencia de movimiento reducido respetada. Caché v28.

- Ajuste v29: reestructuración **solo en móviles y tablets (≤900 px)** de las galerías Dealer Deal XXL y Psycho XXL: imagen/miniaturas a la izquierda y fichas técnicas a la derecha, igual que la organización en escritorio; imagen sin deformación y panel de información con desplazamiento vertical propio. En pantallas de 559 px o menos los atributos se apilan en una columna dentro de cada ficha para mantenerlos legibles. En pantallas de 560 a 900 px se reparten en dos columnas. Se respetan la tercera galería, los botones, las fotografías, los datos, las promociones y los estilos de escritorio. Caché PWA v29.
