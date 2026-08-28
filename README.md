# 📁 RASTRO-PHONE

**Herramienta OSINT de investigación de números de teléfono — Normalización, metabúsqueda y pivote por categoría**

🔗 **Demo en vivo:** [https://s3gad3.github.io/rastro-phone/](https://s3gad3.github.io/rastro-phone/)

Tercera pieza del kit de ciberinteligencia junto a [RASTRO-GH](https://s3gad3.github.io/rastro-gh/) (GitHub → email) y [RASTRO-USER](https://s3gad3.github.io/rastro-user/) (username/email → redes). **RASTRO-PHONE** parte de un **número de teléfono** y construye automáticamente su normalización internacional, sus variantes ofuscadas y los enlaces de pivote hacia motores de búsqueda, redes sociales, mensajería, anuncios, documentos, listas de spam/estafa e imágenes asociadas.

---

## ⚙️ Características

- **Archivo único, sin backend.** Todo el código (HTML + CSS + JS) vive en un solo `.html`. No hay servidor, no hay claves de API, no se envía ni almacena ningún dato del objetivo fuera del propio navegador del investigador.
- **Normalización internacional automática:** detecta el prefijo de llamada entre más de 150 países, calcula el tipo de línea estimado (móvil/fijo en España, NANP en EE.UU./Canadá, internacional genérico) y genera todas las variantes de formato habituales (`+34600123456`, `600 123 456`, `600-123-456`, `00346...`, etc.).
- **Variantes ofuscadas:** genera automáticamente formas parcialmente ocultas (`600***456`, `600 XXX 456`, etc.) tal y como aparecen en anuncios, foros o documentos filtrados, con su propia query de búsqueda entre comillas.
- **Metabúsqueda en 9 motores:** Google, Bing, DuckDuckGo, Yandex, Brave, Startpage, Ecosia, Mojeek y Yahoo, con selector de query activa (exacta / ofuscada / exacta + contexto) y botón para lanzar todos a la vez.
- **Acceso directo a mensajería:** enlace `wa.me/` para WhatsApp y prueba `t.me/+<número>` para Telegram, con aviso de que la disponibilidad depende de la configuración de privacidad de la cuenta.
- **Playbook OSINT por categoría** (desplegable, botones grandes estilo sello):
  - Identidad / contacto
  - Redes sociales (Facebook, Instagram, X/Twitter, LinkedIn, TikTok, Reddit/foros)
  - Mensajería (menciones indexadas de Telegram, WhatsApp, Signal, Discord)
  - Anuncios y compraventa (Wallapop, Milanuncios, Idealista/Fotocasa, eBay/Etsy)
  - Documentos (PDF, Office, CV/directorios, número ofuscado)
  - Repositorios y técnico (GitHub/GitLab, pastes/gists, configs/logs)
  - **Listas de spam/estafa en España** — Tellows y ListaSpam con enlace directo verificado; TelefonoSpam, ¿Quién me llama? y Responderono vía dork
  - **Imágenes asociadas** — Google/Bing/Yandex Imágenes con la query exacta
  - **Archivo web** — Internet Archive y Wayback Machine
- **Enlace directo vs. dork, diferenciados visualmente:** 🔵 azul = URL directa o consulta general verificada; 🟢 verde = dork `site:` dirigido cuando la plataforma no ofrece pivote directo por número.
- **Checklist de investigación** con progreso automático según las categorías consultadas, más validación manual final.
- **Libreta de hallazgos:** registro manual de URLs/referencias con fecha y observación, sin scraping ni descarga de contenido de terceros.
- **Notas de investigador** con autoguardado local.
- **Exportación de expediente** en HTML (informe legible), JSON y TXT, generada íntegramente en el navegador.
- **Historial de sesiones locales**, recuperables por número sin perder el trabajo previo.
- **Estética "expediente":** carpeta de papel kraft, cinta adhesiva, textura de papel, tipografía Special Elite (títulos) + Courier Prime (cuerpo), botones con sombra desplazada tipo sello de goma — mismo lenguaje visual que RASTRO-GH y RASTRO-USER.

---

## 📞 Fuentes cubiertas

**Metabúsqueda:** Google, Bing, DuckDuckGo, Yandex, Brave, Startpage, Ecosia, Mojeek, Yahoo

**Mensajería directa:** WhatsApp (`wa.me`), Telegram (`t.me/+`)

**Redes sociales — vía dork:** Facebook, Instagram, X/Twitter, LinkedIn, TikTok, Reddit/foros

**Mensajería — vía dork:** Telegram, WhatsApp, Signal, Discord

**Anuncios — vía dork:** Wallapop, Milanuncios, Idealista, Fotocasa, eBay, Etsy

**Documentos y técnico — vía dork:** PDF, Office, CV/directorios, GitHub/GitLab, Pastebin/Gist, configs/logs

**Listas de spam/estafa (España) — enlace directo:** Tellows España, ListaSpam

**Listas de spam/estafa (España) — vía dork:** TelefonoSpam, ¿Quién me llama?, Responderono

**Imágenes — enlace directo:** Google Imágenes, Bing Imágenes, Yandex Imágenes

**Archivo web — enlace directo:** Internet Archive, Wayback Machine

> Los patrones de URL directa (Tellows, ListaSpam, WhatsApp, Telegram) se verificaron manualmente antes de implementarlos. Donde no se pudo confirmar un patrón fiable, se optó por un dork de Google en lugar de un enlace potencialmente roto.

---

## 🚀 Uso

1. Abre `index.html` en cualquier navegador (o entra en la [demo en vivo](https://s3gad3.github.io/rastro-phone/)).
2. Introduce el número en formato internacional (`+34 600 123 456`) y, si los conoces, alias, email o contexto adicional.
3. Pulsa **Analizar objetivo**: se calculan prefijo, tipo estimado, variantes y variantes ofuscadas.
4. Lanza la metabúsqueda en uno o todos los motores, o despliega cada categoría del playbook y pulsa cualquier botón para abrir la comprobación en una pestaña nueva.
5. Registra hallazgos relevantes en la libreta y anota tus observaciones en notas.
6. Exporta el expediente en HTML, JSON o TXT cuando termines.

No requiere instalación, dependencias de build ni configuración. Es un sitio estático — puede alojarse en GitHub Pages, abrirse localmente con doble clic, o integrarse en cualquier flujo de trabajo interno.

---

## 🛠️ Stack técnico

- HTML5 + CSS3 (sin frameworks)
- JavaScript vanilla (sin librerías externas)
- Google Fonts (Special Elite, Courier Prime) vía CDN — única dependencia externa, solo tipografía

---

## ⚠️ Uso previsto

Herramienta de **uso interno autorizado** para investigación de ciberinteligencia y cibercrimen. Únicamente construye y abre enlaces a información pública o motores de búsqueda públicos; no accede, automatiza scraping ni almacena datos de terceros. El investigador es responsable de verificar visualmente cada resultado y de operar dentro del marco legal aplicable a su investigación. Una coincidencia del número no constituye atribución suficiente: debe corroborarse con identidad, temporalidad, contexto y fuentes independientes.

---

## 🔗 Proyectos relacionados

- [RASTRO-GH](https://s3gad3.github.io/rastro-gh/) — pivote OSINT desde GitHub hacia emails y perfiles asociados.
- [RASTRO-USER](https://s3gad3.github.io/rastro-user/) — pivote OSINT desde username/email hacia redes globales y plataformas españolas.
