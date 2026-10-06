# Mercado y cliente: party games para móvil

> Fase A · Investigación. Fecha de consulta de todas las fuentes: 2026-10-06. Las cifras llevan referencia numerada a la lista final. **[hipótesis]** = criterio propio, no dato; **no verificado** = no se ha podido comprobar. Nota de método: el proxy de la sesión bloqueaba las fichas de App Store y Google Play y la mayoría de prensa, así que varios precios proceden de resúmenes de búsqueda y no de la ficha española.

## Resumen

1. El móvil es la plataforma mayoritaria (56 % del gasto mundial en 2025 [1]; 18 M de jugadores en España [4]), pero las descargas llevan dos años cayendo (−7,2 % en 2025 [2]) y el 1 % de editores se queda el 92,5 % de los ingresos [2]: para un equipo de dos, la única adquisición viable es orgánica (TikTok y boca a boca).
2. En España el party game dominante es Splash/El Impostor (gratis + suscripción semanal, un solo móvil que se pasa) [7][8]; el formato "cada uno con su móvil" lo ocupa Among Us (online, no presencial): ahí está el hueco, pero con una fricción extra que Splash no tiene: todos deben instalar.
3. Recomendación de monetización para el MVP: gratuito total, sin anuncios y sin registro; en fase 2, una compra única del anfitrión que desbloquea contenido para toda la sala (modelo Jackbox/Kahoot) y cosméticos opcionales; nada de suscripción semanal hasta tener retención medida.
4. La experiencia del invitado decide la viralidad: cada +6 MB de app resta ~1 % de conversión a instalación [14], el registro obligatorio expulsa a 1 de cada 5 [17] y con 5 invitados la probabilidad de que todos entren es p⁵. Objetivo: invitado jugando en menos de 90 s desde el QR (app ≤ 50 MB), anfitrión en menos de 2 min.
5. Lanzamiento: español de España e inglés desde el día 1; segunda ola Latinoamérica (mismo idioma, 372 M de jugadores [5]) y Brasil; Italia y Francia solo si el juego tiene poco texto, que es justo nuestro caso (voz y gestos).

## 1. Mercado de party games para móvil

### 1.1 Cifras globales (2025)

| Indicador | Valor | Fuente |
|---|---|---|
| Ingresos mundiales de videojuegos 2025 | 201.600 M $ (+9,1 %); móvil 113.300 M $ (+10,7 %), 56 % del total; previsión móvil 2026: 121.100 M $ | Newzoo, informe anual publicado junio 2026 [1] |
| Ingresos por compras dentro de la app (móvil) 2025 | 81.750 M $ (+1,3 %) | Sensor Tower, State of Gaming 2026 [2] |
| Descargas de juegos móviles 2025 | 50.400 M (−7,2 %, segundo año consecutivo de caída; 95.000 por minuto) | Sensor Tower [2] |
| Concentración | El 1 % de editores acumula el 92,5 % de los ingresos IAP y el 79,8 % de descargas | Sensor Tower [2] |
| Subgénero que más crece en gasto | Híbrido casual: de 3.500 a 4.200 M $ (+17,1 %) | Sensor Tower [2] |
| Saturación de oferta | En 2025 se publicaron un 25 % más de apps que en 2024; los juegos son el 72 % de los lanzamientos | AppMagic, Mobile Market Landscape 2026 [3] |
| Tamaño del subgénero "party" en móvil | **No verificado**: ni Sensor Tower ni AppMagic publican gratis una cifra por subgénero party/social deduction. El único dato público es antiguo: en el 1.er semestre de 2021 el gasto en juegos "de impostor" creció un 2.554 % hasta 8,4 M $, el 94 % de Among Us [6] | — |

Newzoo y Sensor Tower no son comparables (Newzoo incluye venta directa y minijuegos de China; Sensor Tower solo compras en tienda). Lo relevante es la tendencia: **gasto que crece poco y se concentra, descargas que caen, oferta que se dispara**. Statista y data.ai solo dan estas cifras bajo pago: **no verificado**.

### 1.2 España

| Indicador | Valor | Fuente |
|---|---|---|
| Jugadores | 22,8 M (47,5 % de la población); 48,5 % mujeres, 51 % hombres | AEVI, Anuario 2025 (publicado julio 2026) [4] |
| Por dispositivo | 18 M en móvil/tableta, 11,3 M en consola, 6,9 M en PC | AEVI [4] |
| Tiempo | 8,5 h/semana de media | AEVI [4] |
| Facturación del sector | 2.293 M € (−3,2 %) | AEVI [4] |
| Posición mundial | 13.º mercado, 2.380 M $ (año del dato **no verificado**) | Newzoo vía MCV/Develop [9] |
| Motivación de pago | 48 % de la población online paga; motivos: ofertas y "jugar con amigos o familia" | Newzoo, perfil del jugador español 2022 (dato antiguo) [10] |

### 1.3 Quién domina en España y en mercados hispanohablantes

Los rankings de categoría (Juegos de mesa / Party) de App Store y Google Play España a fecha de hoy: **no verificado** (fichas bloqueadas). La única afirmación pública reciente es de Applesfera: El Impostor de Splash era "el juego más descargado en iPhone y Android" en España [8]; Xataka Móvil titula "En casa ya no usamos tableros: el Impostor ha hecho que el móvil también sea imprescindible para jugar" [11].

| Juego | Formato | Modelo | Datos verificados | Fuente |
|---|---|---|---|---|
| **Splash – El Impostor** (Hannes & Jeremy) | Un móvil que se pasa; 3–12 jugadores | Gratis + "Splash Plus" (suscripción semanal) | 4,7★ con 14,3 K reseñas; ingresos estimados 550 k$ (periodo **no verificado**); oferta anual de recuperación 19,99 € en lugar de 29,99 €/año (tienda alemana). Precio semanal en España: **no verificado** | [7][8][12][13] |
| Clones de impostor (Imposter Game – Party Edition, Impostor: Juego Espía, Faky, TopTop…) | Un móvil | Gratis + IAP/suscripción | "Party Edition" llegó al n.º 2 de Juegos (país **no verificado**), 48,5 K reseñas. Decenas de clones en 2025: el formato está saturado | [12] |
| **Psych!** (Warner Bros., origen en el programa de Ellen) | Cada uno con su móvil + código | Gratis + 10 IAP de 0,99 a 2,99 $ ("Remove Ads" 2,99 $, mazos 0,99–1,99 $) | Precios en dólares (tienda EE. UU.); en euros **no verificado** | [15] |
| **Heads Up!** (Warner Bros.) | Un móvil en la frente | 1,99 $ en iOS (gratis en Google Play); mazos 0,99 $; paquete de 50+ mazos por 120 $ según usuarios | Quejas recurrentes por anuncios ("full of ads") | [16] |
| **Preguntados** (Etermax, Argentina) | Cada uno con su móvil, asíncrono | Gratis + IAP + anuncios | 600 M descargas, 150 M usuarios activos anuales (datos de 2023) | [20] |
| **Among Us** (Innersloth) | Cada uno con su móvil, online | Gratis en móvil: cosméticos + anuncios | +200 M descargas [32]; ~60 M $ acumulados; MAU feb. 2025 ≈ 20,3 M; ingresos mensuales estimados 100–150 k$ | [21][32] |
| **Brawl Stars** (Supercell), referencia de social | Cada uno con su móvil, online | Gratis + cosméticos/pases | 14–17 M MAU (mayo 2025); ~205 M $ en 2025 | [22] |
| **Picolo** (Marmelapp, Francia) | Un móvil | Gratis + suscripción semanal (prueba 3 días), mensual y anual; ~50 $/año según reseñas | Precio en euros **no verificado** | [23] |
| **Guess Up / Charadas y mímica** | Un móvil en la frente | Gratis + packs + VIP (todo el contenido y sin anuncios) | 25 idiomas, 100+ categorías | [24] |
| **Yo Nunca** (apps varias) | Un móvil | Suscripción 6,99 $/semana (ficha EE. UU.) | — | [25] |
| **Drink Roulette** | Un móvil | Gratis + premium (22 modos) | Precio **no verificado** | [26] |
| **Evil Apples** (tipo Cards Against Humanity) | Cada uno con su móvil + código | Gratis + IAP + anuncios; "Mega Pass" 4,99 $ | ~10 k$/mes estimados, 79 % por anuncios | [27] |
| **Spaceteam** | Cada uno con su móvil, local | Gratis + IAP opcionales ("bote de propinas") | Las IAP dieron 12 k$ de más de 25 k$ (2013) | [28] |
| **Jackbox** | Anfitrión en PC/consola/iOS; invitados por navegador en jackbox.tv | Pago único: packs 24,99–34,99 $; apps iOS 25–30 $; Party Starter 19,99 $ | Código de sala de 4 letras, sin app ni cuenta para invitados | [29][30] |

Stumble Guys, "Mentiroso", apps de Spyfall y Truth or Dare: **no verificado** (sin datos accesibles).

Lectura: en España y Latinoamérica el party game de masas es **de un solo móvil** (Splash, Picolo, Heads Up!, Guess Up). Los de "cada uno con su móvil" o son online (Among Us, Preguntados) o de pago/nicho (Jackbox, Spaceteam). Nadie domina "presencial + cada uno con su móvil + gratis": es nuestro hueco y también nuestra fricción.

### 1.4 Tendencias que nos afectan

- **Adquisición de pago inviable**: con descargas cayendo y el top 1 % acaparando [2], una app indie solo crece por viralidad. El Impostor se hizo viral en directos y TikTok porque se entiende sin ver la pantalla [7][8].
- **Suscripción semanal como norma en party apps** (Splash, Picolo, Yo Nunca): monetiza rápido, genera reseñas negativas y es incompatible con un invitado que no eligió el juego. [hipótesis] "Gratis de verdad para el invitado" es también un argumento de marketing.
- **Apple vigila los juegos para beber**: la directriz 4.3(b) cita los "drinking games" como categoría de baja calidad [33]. Ver sección 6.

## 2. Modelos de monetización con ejemplos reales

| Modelo | Ejemplo real | Precio | Qué funciona | Riesgo para el invitado | Compatibilidad con viralidad |
|---|---|---|---|---|---|
| Pago por descarga | Jackbox (iOS 25–30 $), Heads Up! (1,99 $ iOS) [16][29] | 2–35 $ | Ingresos predecibles, sin anuncios, público que valora | Máximo: cada invitado paga o no juega. Jackbox lo esquiva con jackbox.tv (invitados sin app) [30] | Baja para una app que todos instalan |
| Gratis + packs/categorías | Psych! (0,99–2,99 $) [15], Guess Up [24], Splash (packs dentro de Plus) [7] | 1–3 € por pack | El núcleo es gratis; el pack es un capricho del anfitrión | Medio: el invitado ve candados; si el pack lo compra uno y lo ven todos, nulo | Alta si el núcleo gratuito ya es divertido |
| Suscripción | Splash Plus (semanal; 29,99 €/año de tarifa regular en DE) [13], Picolo (semanal con prueba de 3 días, ~50 $/año) [23], Yo Nunca (6,99 $/semana) [25], Guess Up VIP [24] | 1–7 €/semana | ARPU alto; las tiendas la favorecen | Alto: pruebas semanales que se renuevan, reseñas de 1★; un invitado jamás se suscribe | Media: funciona para el anfitrión fiel, penaliza al grupo |
| Anuncios | Heads Up! (intersticiales) [16], Evil Apples (79 % de ingresos) [27], Among Us (anuncios + cosméticos) [21] | Gratis | Monetiza al 95 % que nunca paga | Alto si cortan la partida; los recompensados (opt-in) fuera de ronda se toleran | Baja con intersticiales: rompen el ritmo y el clip |
| Paga el anfitrión, juega la sala | Jackbox PC/consola: 1 compra, hasta 8 jugadores por navegador [30]; Kahoot: el anfitrión paga, los participantes entran gratis con PIN; gratis hasta 10 participantes [31] | 20–35 $ única (Jackbox); 3–19 $/mes (Kahoot!+) [31] | Alinea incentivos: paga quien propone, nadie se queda fuera | Nulo | Alta: el invitado solo ve juego |
| Cosméticos | Among Us, Brawl Stars [21][22] | 1–10 € | Identidad y estatus en partidas repetidas | Nulo | Alta, pero exige retención y perfil persistente |
| "Bote de propinas" | Spaceteam [28] | Voluntario | Cero fricción | Nulo | Alta; ingresos muy bajos |

Apps móviles de party con el modelo "paga el anfitrión y desbloquea para toda la sala" explícito: **no verificado** (no se ha encontrado ninguna con búsqueda; Kahoot y Jackbox son los referentes, uno educativo y otro de sobremesa).

### Recomendación para el MVP (y justificación)

**MVP: gratis total. Sin anuncios, sin registro, sin candados visibles.** Razones: (1) con 2 personas y sin presupuesto, el único activo es la tasa de invitación y cada muro la reduce; (2) la viralidad de El Impostor se construyó sobre "abres y juegas" [7][8]; (3) las party apps de suscripción semanal arrastran reseñas negativas [16][23] y necesitamos reseñas buenas para el ASO orgánico; (4) Among Us llegó a 200 M de descargas monetizando flojo [21][32]: primero alcance, luego caja.

**Fase 2 (tras medir D1, D7 e invitaciones por partida):**

1. **Pase de sala del anfitrión** [hipótesis]: compra única (2,99–4,99 €) o packs de modos (1,99 €) que desbloquean contenido **para todos los que estén en esa sala**, sin que el invitado haga nada. Es el modelo Jackbox trasladado a "todos con app".
2. **Cosméticos** cuando exista perfil persistente opcional.
3. **Anuncios recompensados solo opt-in, entre partidas y solo al anfitrión** ("ver un anuncio desbloquea este modo hoy para la sala"). Nunca intersticiales.
4. **Suscripción**: solo si la retención a 30 días lo justifica y con alternativa de compra única.

Riesgo: el pase de sala exige que el servidor sepa quién es el anfitrión y qué ha comprado; que las tiendas acepten que un invitado disfrute contenido que no ha pagado es práctica habitual en Jackbox y Kahoot, pero para una app móvil: **no verificado**.

## 3. Cliente ideal y personas

Dos clientes con incentivos opuestos:

- **El anfitrión** descubre el juego (TikTok, un amigo), lo instala a solas, explora y propone jugar. Invierte tiempo y es quien pagará. Tolera 2–5 minutos.
- **El invitado** no ha elegido el juego; se lo imponen en un bar o una cena. Tolera menos de un minuto, tiene la batería al 30 %, datos limitados y cero ganas de crear una cuenta. **Decide si el grupo juega hoy y si se recomienda mañana.**

**Por qué el invitado decide la viralidad** [cálculo propio]: una sala de 6 necesita 5 invitados que instalen y entren. Si cada uno lo completa con probabilidad p, la sala arranca completa con probabilidad p⁵: con p = 90 %, un 59 %; con p = 70 %, un 17 %. Cada fricción se multiplica por cinco. Y el invitado de hoy es el anfitrión de mañana: el único canal de crecimiento gratis.

### Personas

| | Marta, 22 · anfitriona | Dani, 29 · invitado escéptico | Laura, 36 · anfitriona familiar | Pol, 19 · invitado a distancia |
|---|---|---|---|---|
| Contexto | Terraza de bar en Valencia con 5 amigas, jueves noche | Cena en piso compartido en Madrid, le ponen un QR delante | Comida de Navidad con cuñados y sobrinos; iPhone y Android mezclados, algunos viejos | Residencia universitaria; juega con amigos del pueblo por Discord/WhatsApp |
| Cómo llega | Vio tres clips en TikTok (72 % de la generación Z usa TikTok [18]) | No lo ha buscado; su amigo insiste | Un sobrino lo propone; ella organiza | Enlace en el grupo de WhatsApp |
| Motivación | Reírse y grabar algo que subir | Que no le hagan perder el tiempo | Que jueguen todos, de 10 a 70 años, sin explicar nada | Sentirse en la misma mesa aunque esté a 300 km |
| Fricción | Datos móviles, ruido, batería; explicar el juego a 5 personas | Peso de la app, permisos (cámara, micro), registro, "¿esto es gratis?" | Móviles lentos, tiendas con contraseñas olvidadas, miedo a pagar sin querer | Voz: Discord ya abierto; micro del juego en conflicto; latencia |
| Recomienda si… | Hay un momento gracioso en los primeros 5 minutos y un clip listo para compartir | Entra en menos de un minuto y nadie le pide nada | Nadie se queda mirando y la abuela se ríe | El modo remoto funciona sin configurar nada |
| Abandona si… | La primera partida se atasca por un invitado que no entra | Descarga > 1 min, cuenta obligatoria, anuncio o pantalla de pago antes de jugar | Reglas que leer; fallo en un móvil viejo | Le piden otra app para la voz |

Datos demográficos: el 83 % de los internautas españoles de 12 a 74 años usa redes sociales (32,4 M); TikTok tiene un 35 % de uso mensual entre ellos y un 72 % en la generación Z; las mujeres lideran en Instagram y TikTok; edad media del usuario de redes: 43 años [18]. En videojuegos el reparto es paritario (48,5 % mujeres) y 18 M juegan en móvil [4]. Datos de "party games en España" por edad: **no verificado** (no hay fuente pública).

## 4. Fricción de "todos descargan"

### 4.1 Datos

| Factor | Dato | Fuente |
|---|---|---|
| Peso de la app | Por cada +6 MB de APK, −1 % de conversión a instalación (estudio UX de Google Play); en mercados emergentes el 70 % mira el tamaño antes de instalar y −10 MB ≈ +2,5 % de conversión (India, Brasil) | Google Play [14] |
| Velocidad móvil en España | Mediana de descarga móvil 54,49 Mbps en enero de 2025 (+31,2 % interanual) | Ookla vía DataReportal [35] |
| Velocidad por red | 4G por operador 24–35 Mbps (fecha del dato **no verificado**); 5G 120–260 Mbps según operador y año | Opensignal [36] |
| Wifi de bar | **No verificado**; [hipótesis] asumir 5–20 Mbps compartidos y a menudo peor que el 4G |  |
| Registro obligatorio | 18 % abandona una compra si le obligan a crear cuenta; la tasa media de completar formularios es 51,7 %; el campo contraseña es el que más abandono provoca (10,5 %) | Baymard, FluentForms [17] |
| Primeros minutos | Mediana de retención D1 ≈ 22 % (top 10 %: 40 %); D7 < 4 %; "20 % abandona en los dos primeros minutos" (cita secundaria, **no verificado** en la fuente primaria) | GameAnalytics 2025 [19] |
| App Clips (iOS) | 10 MB (iOS 15 o anterior), 15 MB para invocación física (NFC, QR, código App Clip; iOS 16+), 50 MB solo para invocación digital (enlace, Safari, Mensajes; iOS 17+) | Apple, WWDC23 [37] |
| Google Play Instant (Android) | Límite 15 MB; objetivo "jugando en < 15 s por LTE". **Discontinuado: desde diciembre de 2025 no se pueden publicar Instant Apps**; Google recomienda deep links a la app normal | Google [38] |
| Tamaño máximo en Play | 4 GB comprimidos con App Bundle: la restricción real no es la tienda, es la conversión | Google [39] |
| Contraste | Among Us pesa 997,9 MB en iOS (tienda DE) y 618–650 MB el APK de 2025; viral pese a ello, pero se juega online, no en un bar con prisa | [21] |
| Local sin internet | Multipeer Connectivity es solo Apple (no habla con Android) [40]; Nearby Connections de Google: **no verificado** (documentación bloqueada). Crossplay P2P local = riesgo técnico alto | Apple [40] |

Tiempos de descarga derivados [cálculo propio, sin instalación]: 50 MB → 7 s a 54 Mbps, 13 s a 30 Mbps (4G), 40 s a 10 Mbps (wifi de bar hipotética). 150 MB → 22 / 40 / 120 s. 500 MB → 74 / 133 / 400 s. Súmese la instalación (10–20 s en gama media, **no verificado**) y el primer arranque.

### 4.2 Cómo lo resuelven otros

| Juego | Invitado necesita | Cómo se une | Cuenta | Lección |
|---|---|---|---|---|
| Jackbox [30] | Solo navegador | jackbox.tv + código de 4 letras + nombre | No | El invitado nunca instala nada; el anfitrión paga |
| Kahoot [31] | Navegador o app | PIN de partida | No para jugar | Igual que Jackbox, pero con app opcional |
| Among Us [21] | App de 600–1.000 MB | Código de sala | No obligatoria | Viral pese al peso porque se juega desde casa |
| Spaceteam [28] | App ligera | Misma red wifi/Bluetooth, detección automática (según conocimiento previo, **no verificado** hoy) | No | Cero códigos en presencial; pero sin modo remoto |
| Splash [7] | Nada (un móvil) | Se pasa el móvil | No | Fricción cero: es el listón que nos van a comparar |

### 4.3 Qué hacer nosotros

1. **Peso ≤ 50 MB en la descarga inicial** (menos de 30 MB si el motor lo permite), con contenido extra en segundo plano. Pasar de 50 a 150 MB cuesta ~−17 % de conversión según la regla de Google [14] y de 15 a 40 s en 4G.
2. **Cero registro**: alias y avatar generados por defecto; perfil opcional tras la tercera partida [hipótesis].
3. **Unirse por QR en presencial, por enlace en remoto y por código de 4–6 caracteres como respaldo.** La cámara nativa de iOS y Android lee el QR y abre el enlace; si la app no está, lleva a la tienda y un *deferred deep link* mete al invitado en la sala sin teclear. Las mejoras de conversión por deep link son reclamos de proveedores (**no verificado**; "+50 %") [41].
4. **App Clip en iOS como "probar sin instalar"**: por QR el límite es 15 MB; por enlace (WhatsApp), 50 MB [37]. [hipótesis] Cabe el lobby y una ronda de prueba, no el juego completo; evaluar en viabilidad técnica. En Android ya no hay equivalente [38].
5. **Compartir por WhatsApp**, la red más usada en España [18]: el botón "invitar" genera un enlace con el código de sala incrustado.
6. **Descartar Bluetooth/P2P local como requisito**: sin crossplay nativo [40]; servidor con internet (como Among Us y Jackbox), que es lo que ya sabemos hacer con Supabase Realtime.
7. **Entrar entre rondas** (innegociable 6 del brief) es también anti-fricción: el invitado lento no bloquea al resto.

### 4.4 Objetivo de "abrir la app → jugando"

| Quién | Objetivo | Justificación |
|---|---|---|
| Anfitrión (primera vez) | Sala creada en ≤ 30 s; primera ronda con al menos un invitado en ≤ 2 min | Google fijaba "< 15 s hasta interactuar" para Instant [38]; la mediana de abandono de los primeros minutos [19] y la impaciencia del grupo que mira |
| Invitado sin la app (desde QR/enlace) | ≤ 90 s hasta estar en ronda: descarga 10–20 s (≤ 50 MB, 4G/5G), instalación 10–20 s, abrir y entrar ≤ 20 s con alias y código automáticos | Con wifi de bar o móvil viejo se dobla; por eso la ronda debe poder empezar sin él y admitirlo en la siguiente |
| Invitado con la app | ≤ 15 s (escanear, abrir, dentro) | Es la cifra de Instant [38] y el listón de Jackbox por navegador [30] |

## 5. Mercados e idiomas de lanzamiento

| Mercado | A favor | En contra | Prioridad |
|---|---|---|---|
| **España** | Mercado propio, 18 M jugando en móvil [4], cultura de bar y sobremesa, demanda demostrada por El Impostor [8], playtests presenciales | Mercado mediano (13.º, 2.380 M $ [9]); el formato impostor está saturado | 1.ª ola |
| **Inglés (global, UK/EE. UU.)** | Idioma de TikTok global y del ASO; coste casi nulo si el texto es mínimo | Máxima competencia (Psych!, Heads Up!, Jackbox, Evil Apples); no hacer marketing allí al principio | 1.ª ola como idioma, 3.ª como marketing |
| **Latinoamérica (México, Argentina, Colombia, Chile)** | Mismo idioma (léxico neutro); 372,3 M de jugadores, 8.300 M $, móvil +7,8 %, Android mayoritario, 46 % pagan [5]; TikTok fuerte; Preguntados demuestra apetito social [20] | ARPU bajo (48,5 $/jugador/año [5]); redes más lentas: el peso de la app importa aún más [14]; lanzamiento escalonado por tienda | 1.ª–2.ª ola (misma build, revisar modismos) |
| **Brasil (pt-BR)** | 3.º país del mundo en descargas (9.400 M en 2024), 11.º en ingresos (1.600 M $) [42]; 82,8 % de la población juega [43] | pt-BR ≠ pt-PT; cultura de party distinta; sin equipo local | 2.ª ola |
| **Portugal** | Cercanía y cultura de bar parecida; aprovecha la localización pt | Mercado pequeño (cifras **no verificado**) | 2.ª ola con Brasil |
| **Italia y Francia** | Cultura de aperitivo; Newzoo los cuenta entre los 6 grandes de Europa [1]; Picolo nació en Francia [23] | Coste y revisión de localización; competencia local (Picolo) | 3.ª ola |
| Alemania y resto de la UE | Europa: 33.100 M $ [44] | Fuera de alcance de 2 personas | Posterior |

**Coste de localización**: 0,09–0,14 €/$ por palabra en agencia para FR, IT, DE y PT-BR [45]. Un juego con 500 palabras de interfaz cuesta 50–70 € por idioma; lo caro es el contenido (listas de palabras, retos culturales, humor) y cualquier locución. [hipótesis] Un juego de voz y gestos con iconos y pocas palabras en pantalla se localiza por decenas de euros y, más importante, su clip de TikTok se entiende sin subtítulos: ventaja de diseño, no solo de coste. El coste real es el playtest con nativos por idioma.

## 6. Nota sobre el futuro modo para beber

- **Qué hacen en España**: Picolo (gratis + suscripción semanal/mensual/anual, ~50 $/año [23]), Drink Roulette (gratis + premium [26]) y Yo Nunca (6,99 $/semana [25]) viven de suscripción con prueba; público 18+, uso en prepartida y en casa más que en bar. Precios en euros: **no verificado**.
- **Riesgo de clasificación**: el nuevo sistema de Apple (24-07-2025) tiene cinco tramos (4+, 9+, 13+, 16+, 18+); referencias "infrecuentes" al alcohol dan 13+ y "frecuentes" dan directamente **18+** [34]. En Google Play (IARC/PEGI) referencias frecuentes son PEGI 16 y representaciones frecuentes PEGI 18 (fuente secundaria [46]). Un modo para beber en la misma app puede arrastrar **toda la app a 18+** en iOS: menos visibilidad y sin menores ni familias.
- **Riesgo de rechazo**: la directriz 1.4.3 prohíbe apps que fomenten "el consumo excesivo de alcohol" y la 4.3(b) cita los "drinking games" entre las apps de baja calidad [33]. Picolo existe, luego no es absoluto, pero una app cuyo núcleo sea beber está en zona gris.
- [hipótesis] El modo debe ser un módulo activable (o una app aparte) con la alternativa sin alcohol por defecto. El detalle legal va en `requisitos-publicacion.md`.

## 7. Implicaciones para nuestro juego

1. **El competidor real es Splash, no Among Us**: el listón de fricción es "un móvil que se pasa". Cada pantalla, permiso o segundo extra que pidamos al invitado se mide contra cero.
2. **El hueco existe**: presencial + cada uno con su móvil + gratis sin muros no lo ocupa nadie con escala en España; el impostor de un móvil está saturado de clones [12].
3. **Monetización del MVP: ninguna.** Diseñar desde ya el "pase de sala" del anfitrión y medir invitaciones por partida antes de cobrar. Sin anuncios en partida, sin suscripción semanal.
4. **Peso ≤ 50 MB y cero registro** son decisiones de producto que condicionan motor y assets (`viabilidad-tecnica.md`).
5. **Unirse por QR y enlace de WhatsApp con deep link**, código como respaldo; servidor con internet; sin depender de Bluetooth/P2P.
6. **Entrar entre rondas** hace tolerable la descarga: la partida empieza con los que están y el lento entra en la siguiente ronda.
7. **Diseñar para la cámara externa y el clip**: la viralidad de El Impostor vino de clips donde se ve a la gente, no la pantalla [7][8]; un juego de voz y gestos lo hace de serie y se localiza barato.
8. **Idiomas desde el día 1: es-ES e inglés**; es-419 en la primera actualización; pt-BR y Portugal en la segunda ola; IT/FR después. Marketing solo en España hasta tener retención.
9. **Modo para beber como módulo aparte** que no cambie la clasificación, o asumir 18+ en iOS.
10. **Métricas desde el prototipo**: tiempo QR→ronda por invitado, % de invitados que completan la entrada, invitaciones por partida, D1/D7 (mediana de referencia 22 % / <4 % [19]).

## Fuentes (consultadas el 2026-10-06)

1. Newzoo, Global Games Market Report 2025 (junio 2026), vía Premortem Games: https://premortem.games/2026/06/22/global-games-market-surpasses-200-billion-for-the-first-time-in-2025-according-to-newzoo/ y PocketGamer.biz: https://www.pocketgamer.biz/global-games-revenue-surpasses-200bn-for-the-first-time-mobile-generates-113bn/
2. Sensor Tower, State of Gaming 2026, vía PocketGamer.biz: https://www.pocketgamer.biz/over-95000-mobile-games-were-downloaded-every-minute-in-2025 y nota de prensa: https://www.bolsamania.com/nota-de-prensa/mercados/sensor-tower-state-of-gaming-gaming-drove-94-billion-in-revenue-in-2025-downloads-reached-52-billion--21828650.html
3. AppMagic, Mobile Market Landscape 2026: https://appmagic.rocks/files/view/upload/Reports/EN_MobileMarkeLandscape2026.pdf
4. AEVI, Anuario 2025 (julio 2026), vía Menorca.info: https://www.menorca.info/actualidad/tecnologia-videojuegos-1/2026/07/20/2673835/espana-tiene-millones-personas-juegan-videojuegos-dedican-media-horas-semana-jugar.html y Merca2: https://www.merca2.es/2026/07/28/espanoles-juega-videojuegos-2425797/
5. Newzoo, Latinoamérica 2025, vía GamesBeat: https://gamesbeat.com/?p=320213
6. Sensor Tower, juegos de impostor 1S 2021, vía Game World Observer: https://gameworldobserver.com/2021/09/02/imposter-themed-games-see-2554-increase-in-player-spending-due-to-among-us-success
7. Ficha de Splash – Impostor Game en App Store (texto de la ficha vía búsqueda; ficha española bloqueada): https://apps.apple.com/app/id6744290388
8. Applesfera, "El juego del Impostor es el más descargado en iPhone y Android": https://www.applesfera.com/juegos-ios/duda-no-que-impostor-juego-descargado-iphone-pregunta-que-no-iba-a-serlo
9. MCV/Develop, Territory Report: Spain (Newzoo): https://mcvuk.com/business-news/events/territory-report-spain/
10. Newzoo, Key insights into Spanish gamers 2022, vía Game Industry Library: https://gameindustrylibrary.com/documents/key-insights-into-spanish-gamers-2022/read
11. Xataka Móvil, "En casa ya no usamos tableros…": https://www.xatakamovil.com/movil-y-sociedad/casa-no-usamos-tableros-impostor-ha-hecho-que-movil-tambien-sea-imprescindible-para-jugar
12. Estimaciones de reseñas y ranking de apps de impostor: https://screensdesign.com/apps/splash-impostor-game/ y https://apppricinglab.com/compare/apple/6745120053/742625884
13. Oferta Splash Plus 12 meses (19,99 € vs 29,99 €), mydealz: https://www.mydealz.de/deals/splash-party-spiele-12-monate-splash-plus-ruckgewinnungsangebot-personalisiert-2836820
14. Google Play, "Shrinking APKs, growing installs": https://medium.com/googleplaydev/shrinking-apks-growing-installs-5d3fcba23ce2
15. Psych! compras dentro de la app (USD): https://apppricinglab.com/app/apple/1005765746
16. Heads Up! precios y quejas por anuncios: https://unitq.com/unitq-scorecards/headsup y https://mwm.ai/apps/heads-up/623592465
17. Abandono por registro (Baymard, 18 %) vía Webtonic: https://www.webtonic.io/blog/abandonment-rate-statistics ; estadísticas de formularios, FluentForms: https://fluentforms.com/?p=63553
18. IAB Spain, Estudio de Redes Sociales 2025, vía Marketing4eCommerce: https://marketing4ecommerce.net/estudio-redes-sociales-en-espana-2025/ y PPC Land: https://ppc.land/spains-social-media-users-jump-to-7-2-platforms-but-42-quit-at-least-one/
19. GameAnalytics, Mobile Gaming Benchmarks 2025: https://investgame.net/wp-content/uploads/2025/02/2025-GameAnalytics-Mobile-Gaming-Benchmarks.pdf ; cita del 20 % en dos minutos: https://adriancrook.com/?p=8151
20. Preguntados, 10 años (iProUP): https://www.iproup.com/innovacion/38756-gaming-preguntados-a-diez-anos-de-su-lanzamiento
21. Among Us: Udonis (MAU e ingresos estimados): https://blog.udonis.co/mobile-marketing/mobile-games/among-us-player-count ; tamaño iOS: https://www.netzwelt.de/software-chooser/25940-among-us.html ; APK 2025: https://apkmirror.com/apk/innersloth-llc/among-us/
22. Brawl Stars: https://www.esports.net/br/noticias/quantas-pessoas-jogam-brawl-stars/ y Statista: https://www.statista.com/statistics/1221278/supercell-top-grossing-mobile-games
23. Picolo, modelo y precios según reseñas: https://tuapppara.com/beber y https://alittlebithuman.com/13-best-drinking-game-apps-for-your-phone-free-and-paid/
24. Guess Up / Charadas y mímica (ficha MX): https://apps.apple.com/MX/app/id1160484607
25. Yo Nunca (ficha EE. UU., 6,99 $/semana): https://apps.apple.com/us/app/id6446645540?l=es-MX
26. Drink Roulette: https://alittlebithuman.com/13-best-drinking-game-apps-for-your-phone-free-and-paid/
27. Evil Apples: https://appgoblin.info/apps/645705454 y https://eastside-online.org/showcase/the-app-evil-apple-vs-humanity-attracts-many-users/
28. Spaceteam, entrevista a Henry Smith (PocketGamer.biz): https://www.pocketgamer.biz/i-couldnt-have-made-spaceteam-if-id-prioritised-money-says-sleeping-beasts-smith ; reseña Macworld: https://www.macworld.com/article/220322/review-spaceteam-for-ios-is-equal-parts-laughter-and-yelling-at-your-friends.html
29. Precios Jackbox: https://www.dekudeals.com/items/the-jackbox-party-starter ; https://apppricinglab.com/app/apple/1170646222 ; https://appshunter.io/ios/app/the-jackbox-party-starter/id6501958739
30. Jackbox, "How do I join a game": https://support.jackboxgames.com/hc/en-us/articles/15794759479959-How-do-I-join-a-game
31. Kahoot! precios (USD, fuentes secundarias): https://nibble-app.com/blog/kahoot-cost y https://www.wooclap.com/en/blog/kahoot-pricing/
32. Among Us, más de 200 M de descargas, 3DJuegos: https://www.3djuegos.com/juegos/among-us/noticias/among-us-continua-imparable-mas-de-100-millones-de-200929-108163/amp
33. Apple, App Store Review Guidelines (1.4.3 y 4.3(b)): https://developer.apple.com/app-store/review/guidelines/
34. Apple, App Store Connect: clasificaciones por edad: https://developer.apple.com/help/app-store-connect/reference/age-ratings ; anuncio del nuevo sistema (24-07-2025): https://ppc.land/apple-updates-app-store-age-ratings-system-with-granular-controls/
35. DataReportal, Digital 2025: Spain (Ookla): https://datareportal.com/reports/digital-2025-spain
36. Opensignal, Spain Mobile Network Experience (2024, 2025 y mayo 2026): https://insights.opensignal.com/reports/2025/02/spain/mobile-network-experience y https://insights.opensignal.com/reports/2026/05/spain/mobile-network-experience ; 4G por operador: https://www.xatakamovil.com/mercado/espana-cuenta-con-las-redes-4g-mas-rapidas-del-mundo-segun-opensignal
37. Apple, WWDC23 "What's new in App Clips" (límites 10/15/50 MB): https://developer.apple.com/videos/play/wwdc2023/10178/
38. Google, Play Instant: requisitos técnicos y aviso de discontinuación (diciembre 2025): https://developer.android.com/topic/google-play-instant/tech-requirements
39. Google, Android App Bundle (límite 4 GB): https://developer.android.com/guide/app-bundle
40. Apple, Multipeer Connectivity: https://developer.apple.com/documentation/multipeerconnectivity
41. Reclamo de conversión por deep links (proveedor): https://adapty.io/blog/markdown/deferred-deep-linking.md
42. Sensor Tower, Brasil 2024 (descargas e ingresos), vía MacMagazine: https://macmagazine.com.br/post/2025/01/23/sensor-tower-brasil-foi-o-terceiro-pais-que-mais-baixou-apps-em-2024/
43. Pesquisa Game Brasil 2025 (82,8 %): https://criticalhits.com.br/games/jogos-para-celular-vs-plataformas-de-jogos-no-brasil-quem-vence-em-2025/
44. Newzoo, previsión 2025 por regiones (Europa 33.100 M $): https://gameworldobserver.com/2025/09/09/newzoo-in-2025-more-than-half-of-the-gaming-markets-revenue-will-come-from-two-countries-china-and-the-united-states
45. Tarifas de localización: https://centus.com/blog/localization-costs y https://allcorrectgames.com/localization-pricing/
46. Guía de clasificaciones por edad (PEGI/IARC, fuente secundaria): https://capgo.app/blog/app-store-age-ratings-guide/
