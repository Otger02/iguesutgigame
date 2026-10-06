# Requisitos de publicación: App Store, Google Play y cumplimiento en la UE

> **No es asesoramiento legal ni fiscal**: validad con gestoría o abogado antes de constituir nada, activar compras o lanzar un modo con alcohol. Fecha de consulta de todas las fuentes: **2026-10-06**. Leyenda: **✔** página oficial leída en esta sesión; **✖** URL oficial conocida pero **no accesible desde esta sesión** (bloqueo de red): el dato viene de resúmenes de terceros o de memoria y queda **no verificado**. Fuentes numeradas al final.

## Resumen

1. Camino recomendado: cuenta **personal** de Google Play (25 USD, pago único) y cuenta **individual** de Apple (99 USD/año) a nombre de uno de los dos, con pacto escrito entre ambos; ninguna SL hasta que haya ingresos.
2. El cuello de botella es Google: una cuenta personal nueva debe superar una prueba cerrada con **12 testers inscritos 14 días seguidos** antes de pedir producción; calendario realista de 6 a 8 semanas desde el alta hasta producción en ambas tiendas.
3. Sin modo para beber, el juego encaja en **13+ en App Store** (humor grosero frecuente, chat de voz como capacidad) y previsiblemente **PEGI 12 o 16** en Play; un modo para beber sube la app entera a 18+ en App Store.
4. Privacidad de mínimo esfuerzo: sin registro ni cuentas, voz en tiempo real sin almacenar, cámara y sensores procesados en el dispositivo; aun así son obligatorios política de privacidad, Data Safety (Play), App Privacy y Privacy Manifest (Apple).
5. En cuanto haya anuncios o compras somos **comerciantes (DSA)**: dirección (en Apple vale un apartado de correos), correo y teléfono públicos en la UE, alta como autónomo, y el IVA de las ventas lo gestionan Apple y Google como agentes.

## 2. Cuentas, costes y tipo (personal o empresa)

| | Apple Developer Program | Google Play Console |
|---|---|---|
| Coste | **99 USD/año**, suscripción auto-renovable si se contrata desde la app Apple Developer [A1 ✔]. En España se muestra en euros durante el alta; los 99 €/año citados en prensa quedan **no verificados** [P1 ✖]. | **25 USD, pago único** [G1 ✖]. |
| Individual / personal | Nombre legal obligatorio: "your personal legal name will be listed as the seller on the App Store" [A2 ✔]. | Cuenta personal para "estudiante, aficionado o desarrollador amateur"; monetiza igual que una de organización [G1 ✖]. |
| Organización | Entidad legal (no nombres comerciales), **D-U-N-S**, correo con dominio propio, web pública, persona con poder de firma, posibles documentos notariados [A2 ✔]. | **D-U-N-S obligatorio** desde 2023; obtenerlo puede tardar hasta 30 días [G1 ✖]. |
| Verificación | Apple Account con 2FA, mayoría de edad, documento oficial con foto desde la app Apple Developer [A2 ✔, A3 ✔]. | Identidad con documento, correo y teléfono; documentos societarios si procede [G1 ✖]. |
| Tiempo de alta | Confirmación "within 24 hours" tras la compra; organizaciones con revisión adicional sin plazo publicado [A2 ✔]. | **No verificado**; hipótesis: de horas a una semana. |
| Datos públicos | Nombre del vendedor (persona física si cuenta individual) [A2 ✔]; si eres comerciante DSA, dirección o apartado de correos, teléfono y correo en la UE [A4 ✔]. | Nombre de desarrollador y correo; dirección si se vende, y datos de comerciante DSA en el EEE [G1 ✖, G2 ✖]. |
| Pasar a empresa después | Convertir la cuenta contactando con Apple [A2 ✔] o **transferir la app** a otra cuenta conservando reseñas, usuarios y actualizaciones (requiere una versión publicada y TestFlight apagado) [A5 ✔]. | Existe transferencia de apps; detalles **no verificados** [G3 ✖]. |

| Opción para dos personas | Coste | Pros | Contras / riesgos |
|---|---|---|---|
| **Cuenta personal de uno (recomendada)** | 25 USD + 99 USD/año | Alta en días; sin D-U-N-S; la app se transfiere a una SL después [A5 ✔]. | Titularidad en una sola persona: hace falta un **pacto privado** (reparto, salida). Nombre y apellidos visibles como vendedor en App Store [A2 ✔]. Con ingresos, alta de autónomo del titular (hipótesis fiscal). |
| SL o cooperativa | Notario, registro y gestoría (cientos de euros más 50-100 €/mes; **no verificado**) | Nombre de empresa como vendedor; titularidad compartida. | Semanas de trámites, D-U-N-S, contabilidad y coste fijo. No compensa antes de validar el juego. |

**Criterio:** cuenta personal de un titular, co-titularidad por escrito, SL solo si entra dinero. Nota: la "developer verification" de Android (2026-2027) para apps fuera de Play queda cubierta automáticamente con Play Console [G4 ✔].

## 3. Pruebas cerradas obligatorias (Google) y TestFlight (Apple)

**Google Play.** Las cuentas personales creadas después del **13 de noviembre de 2023** deben superar una prueba cerrada con **12 testers inscritos de forma continua 14 días** antes de solicitar producción. Eran 20; bajó a 12 el 11 de diciembre de 2024 según varias fuentes de terceros coincidentes; la página oficial [G5 ✖] no era accesible, así que **la cifra vigente queda no verificada**. "Inscripción continua" (mismas fuentes): el tester acepta la invitación e instala con su cuenta de Google; si desinstala o se da de baja deja de contar, y hacen falta 12 simultáneos durante todo el periodo. Después se responde el **cuestionario de acceso a producción** (qué se probó, feedback, cambios, si está lista); plazo oficial de respuesta **no verificado** (hipótesis: 1-7 días). Las revisiones de Play pueden tardar hasta 7 días o más en cuentas nuevas [G6 ✖].

**TestFlight.** Hasta **100 testers internos**, **10.000 externos**, builds válidos **90 días**, 30 dispositivos por tester y enlaces públicos [A6 ✔, A7 ✔]. El primer build de un grupo externo pasa por Beta App Review antes de poder probarse [A7 ✔]. App Review: "at least 50% of submissions in less than 24 hours and 90% in less than 48 hours" [A8 ✔].

| Semana | Google Play | App Store |
|---|---|---|
| 0 | Alta, verificación de identidad, teléfono y correo. | Alta individual con documento; confirmación ≤24 h [A2 ✔]. |
| 1 | Ficha, privacidad, Data Safety, IARC; build en **prueba cerrada** (la primera versión pasa revisión). | Build interno en TestFlight, sin revisión. |
| 2 | Invitar 20-25 testers (margen sobre 12); **el reloj de 14 días arranca** con 12 inscritos a la vez. | Grupo externo: Beta App Review y pruebas con los mismos jugadores. |
| 3-4 | Mantener ≥12 inscritos; iterar builds en la misma pista. | Iterar builds. |
| 5 | Solicitar **acceso a producción** y esperar. | Ficha, capturas, cuestionario de edad, App Privacy. |
| 6 | Enviar a producción: revisión de hasta 7 días [G6 ✖]. | Enviar a revisión: ≤48 h en el 90 % [A8 ✔]. |
| 7-8 | **En producción** (margen por rechazos). | Lanzar el mismo día que Android. |

Los playtests presenciales valen como testers si cada jugador instala desde Play con su cuenta y no desinstala en 14 días. La prueba cerrada se planifica con el primer build jugable, no al final.

## 4. Clasificación por edad

**Google Play** usa el cuestionario **IARC**, que en Europa da una etiqueta **PEGI** (3, 7, 12, 16, 18) con descriptores (lenguaje, drogas, compras, interacción entre usuarios) [G7 ✖, E1 ✖]. Qué nivel asigna PEGI a "referencias al alcohol" frente a "incitación al consumo" queda **no verificado** (hipótesis: 12/16 frente a 16/18).

**App Store.** El 24 de julio de 2025 Apple añadió **13+, 16+ y 18+** a 4+ y 9+, con preguntas nuevas (controles, capacidades, temas médicos, violencia) y plazo hasta el **31 de enero de 2026** [A9 ✔]. Mapa oficial relevante [A10 ✔]:

| Respuesta | Nivel |
|---|---|
| "User-generated content", "Messaging and chat" (incluye voz), "Advertising" | **Capacidades**: descriptor en la ficha, presentes ya en 4+. |
| "Infrequent profanity and crude humor" | 9+ |
| "Frequent profanity and crude humor" | 13+ |
| "Infrequent alcohol, tobacco, or drug use or references" | **13+** |
| "Social media" (redistribuir o amplificar contenido de usuarios en un feed) | 13+; preguntas obligatorias desde septiembre de 2026 [A11 ✔] |
| "Unrestricted web access" | 16+ |
| "Frequent alcohol, tobacco, or drug use or references" | **18+** |

Apple define "Messaging and chat" como comunicación directa entre usuarios por "text, voice and/or video chat" y UGC como distribución amplia de vídeo, foto, texto o audio de usuarios [A10 ✔]: apodo y voz en sala privada son chat, no "social media". El desarrollador puede subir la clasificación si sus condiciones exigen más edad [A9 ✔].

**Modo para beber.** La clasificación es por app, no por modo: contenido que anime a beber se declara como uso frecuente de alcohol y la app entera pasa a **18+** en App Store (PEGI 16/18 en Play, no verificado). Consecuencias: invisible con control parental, peor conversión y redes publicitarias que limitan inventario o pagan menos en 18+ (hipótesis).

**DSA y verificación de edad.** El art. 28 de la DSA obliga a las **plataformas en línea** accesibles a menores a medidas proporcionadas; la Comisión publicó directrices en julio de 2025 y pilota una app de verificación de edad en varios países, España incluida; textos y fechas **no verificados** [E2 ✖, E3 ✖]. Hipótesis a validar: un juego con salas privadas y voz efímera no es "plataforma en línea"; nos afecta como comerciante vía tiendas (sección 7). Con salas públicas o feed de clips, cambiaría.

## 5. Privacidad y RGPD

| Obligación | App Store | Google Play |
|---|---|---|
| Política de privacidad | Enlace en App Store Connect y en la app: qué datos, usos, terceros y borrado [A12 ✔]. | Obligatoria en ficha y app [G8 ✖]. |
| Formulario de datos | **App Privacy** antes de enviar; "collect" = transmitir fuera del dispositivo; lo procesado solo en el dispositivo **no cuenta** [A13 ✔]. | **Data Safety** obligatorio; "collected" = transmitido fuera; los registros de fallos se declaran siempre [G9 ✔]. |
| Manifiesto de privacidad | `PrivacyInfo.xcprivacy` con tipos de datos, dominios de tracking y **Required Reason APIs**; desde el **1 de mayo de 2024** se rechazan subidas sin razón aprobada; SDKs comunes (Firebase, Unity…) deben traer manifiesto y firma [A14 ✔, A15 ✔]. | Sin equivalente. |
| Identificador publicitario | IDFA o tracking requieren **ATT** (iOS 14.5+); un SDK que cruce datos entre apps para publicidad es tracking [A16 ✔]. | Declarar "Advertising ID" y permiso `AD_ID` [G9 ✔]. |
| Cuentas | Si hay cuenta, **borrado en la app**; sin funciones de cuenta no se puede exigir login [A12 ✔]. | Borrado de cuenta y datos [G9 ✔, G10 ✖]. |
| Contenido de usuarios | Guideline 1.2: filtro, **denuncia**, **bloqueo** y datos de contacto publicados [A12 ✔]. | Política UGC con denuncia y bloqueo; texto **no verificado** [G11 ✖]. |

**Datos que tocaríamos** (hipótesis de diseño):

- Sala y apodo: guardados en servidor son "User ID / Other user content" (Apple) y "Name / User IDs" (Play); si solo viven en la sesión, quedan fuera del "collect" de Apple, que excluye lo no retenido más allá de servir la petición en tiempo real [A13 ✔].
- Voz en tiempo real: retransmitida sin grabar, misma excepción; un clip con voz almacenado es "Audio Data" declarable y borrable.
- Giroscopio, acelerómetro y cámara: en el dispositivo, **no se declaran** [A13 ✔, G9 ✔].
- Analítica y fallos: "Product Interaction" y "Crash Data" (Apple), "App activity / App info" (Play). En la UE la analítica con identificadores entra en el art. 22.2 LSSI y la guía de cookies de la AEPD, que cubre apps; cuándo exige consentimiento queda **no verificado** [S1 ✖]. Recomendación: sin identificador persistente, o consentimiento al primer arranque.
- Clip de los últimos segundos: **solo en el dispositivo**, compartido con la hoja del sistema.

**Menores.** Con 13+ no entramos en Kids (Apple) ni en la política de familias (Play). En España el consentimiento de datos vale desde los **14 años** (art. 7 LOPDGDD; texto **no verificado**) [S2 ✖]; sin datos personales ni cuentas, queda no personalizar anuncios a menores y declarar bien la edad. Un 16+ no cambia obligaciones, solo descubrimiento.

**Mínimo esfuerzo:** sin registro, estado de partida en memoria sin persistencia (o P2P), nada de voz o vídeo almacenado, analítica mínima, correo público y botón "denunciar y expulsar" en la sala desde la primera versión con voz.

## 6. Permisos de cámara y micrófono

- iOS: `NSCameraUsageDescription` y `NSMicrophoneUsageDescription` son **obligatorios** si se usan esas API; el texto aparece en el diálogo y sin la clave la petición falla y la app puede ser rechazada [A17 ✔, A18 ✔]. 5.1.1(iv): no forzar permisos innecesarios y ofrecer alternativa a quien deniega; 2.5.14: consentimiento explícito e indicación visual o sonora al grabar [A12 ✔]. Indicador naranja (micro) o verde (cámara) desde iOS 14: página de soporte no accesible, **no verificado** [A19 ✖].
- Android: `CAMERA` y `RECORD_AUDIO` son permisos de ejecución; la guía pide **pedirlos en contexto**, explicar el motivo, **degradar sin bloquear** y recordar que tras dos denegaciones el diálogo deja de aparecer [G12 ✔]. Desde Android 12 hay icono en la barra de estado al usar micro o cámara, panel de privacidad y conmutadores globales [G13 ✔].
- Diseño que cumple ambas: el micro se pide **solo** al entrar en un minijuego de soplar o gritar o al activar la voz remota; la cámara, solo en un minijuego de gestos; pantalla previa de una frase; y **cada minijuego con variante sin sensor** (tocar, agitar), que además salva el bar ruidoso.

## 7. Obligaciones de comerciante en la UE (DSA, IVA, DMA)

**Trader.** Comerciante es quien actúa "for purposes relating to his or her trade, business, craft or profession"; Apple lista como indicios ingresos por la app (compras, pago o **anuncios**), prácticas comerciales, registro de IVA o desarrollo profesional [A4 ✔]. Desde el **16 de octubre de 2024** hay que declarar el estado para enviar apps en la UE; desde el **17 de febrero de 2025** las apps sin estado se retiraron de la App Store en la UE [A20 ✔, A21 ✔]. Google exige la declaración equivalente en Play Console para el EEE; mecánica **no verificada** [G2 ✖].

**¿App gratuita sin compras ni anuncios = no comerciante?** Apple permite "not a trader": se avisa a los usuarios de la UE de que no les aplican los derechos de consumo [A4 ✔]. Apple no prohíbe expresamente compras o anuncios a un no comerciante, pero los considera indicio de serlo [A4 ✔]: **al activar anuncios recompensados o compras, declararse comerciante** en ambas tiendas y verificar (correo y teléfono por 2FA, documento con nombre y dirección). Las personas físicas pueden mostrar **"Address or P.O. Box"** aportando un recibo que las vincule [A4 ✔]; alternativa, dirección de la gestoría si lo acepta por escrito. Si Google admite apartado de correos: **no verificado** [G2 ✖].

**IVA.** En el Paid Apps Agreement el desarrollador nombra a Apple **agente o comisionista**; Apple cobra el precio y la responsabilidad del IVA se fija región a región en el Exhibit B, solo visible en App Store Connect [A22 ✔]. Que Apple recaude e ingrese el IVA en la UE y pague neto es la práctica conocida pero **no verificada en el Exhibit B**; Google como merchant of record en la mayoría de países: **no verificado** [G14 ✖]. A prever (hipótesis fiscal): alta de autónomo antes del primer ingreso, registro de operadores intracomunitarios para facturar a Apple Distribution International y Google Ireland, IRPF e IVA trimestrales, modelo 349.

**DMA (nota).** Desde el **1 de octubre de 2026** Apple aplica en la UE términos unificados: **26 %** por compra en la app (**15 %** en Small Business Program), 20 %/10 % con pago alternativo en la app, 15 %/10 % por enlaces a la web, y Core Technology Commission del **5 %** solo fuera de la App Store; quien use solo In-App Purchase no cambia nada [A23 ✔]. Para el MVP: In-App Purchase estándar.

## 8. Compras dentro de la app y anuncios

- **Solo IAP** para contenido digital: Apple 3.1.1 prohíbe mecanismos propios y exige restaurar compras [A12 ✔]. Google exige su facturación para bienes digitales; política oficial no accesible (**no verificado**) [G15 ✖]; Billing Library 8+ obligatoria desde el 31 de agosto de 2026 [G16 ✔].
- **Comisiones.** Apple: 30 %, **15 % con Small Business Program** (hasta 1 M USD netos al año; los nuevos pueden entrar desde el inicio aceptando el Paid Apps Agreement) [A22 ✔, A24 ✔]; en la UE desde octubre de 2026, 26 %/15 % [A23 ✔]. Google: 15 % en el primer millón de USD al año y 30 % después; desde el **30 de junio de 2026** estructura distinta en EEE, Reino Unido y EE. UU. según instalación "nueva" o "existente" (15 % + 5 % de facturación en ciertos programas); todo **no verificado** [G17 ✖].
- **"Paga el anfitrión y la sala juega".** Compatible **si** el desbloqueo es propiedad de la sala del comprador: los demás lo disfrutan mientras juegan con él, sin derecho permanente en su cuenta (eso sería regalar una compra, solo permitido vía el mecanismo de regalos de Apple [A12 ✔]). Es el modelo de Kahoot! (anfitrión paga) y Jackbox (uno compra, los demás entran con código); **no verificado** [P2 ✖]. Implementación: el servidor valida el recibo del anfitrión y marca la sala "premium" mientras esté dentro.
- **Anuncios recompensados.** Permitidos si son opcionales, etiquetados y no engañosos; política de Play y AdMob **no verificada** [G18 ✖]. En la UE, desde el **16 de enero de 2024** Google exige una **CMP certificada e integrada con el TCF** (p. ej. UMP SDK) para EEE y Reino Unido [G19 ✖, E4 ✖]; en iOS, además, ATT [A16 ✔]. Sin consentimiento, anuncios limitados que pagan menos (hipótesis).

## 9. Límites para el futuro modo para beber

**Tiendas.**

- Apple 1.4.3: "Apps that encourage consumption of tobacco and vape products, illegal drugs, or **excessive amounts of alcohol** are not permitted. Apps that encourage minors to consume any of these substances will be rejected." Y 4.3(b) cita los "drinking games" entre apps "mediocre, low-quality, or low-effort" cuyo envío repetido puede suponer expulsión [A12 ✔]. En los foros oficiales hay rechazos reportados en 2020-2021, ninguna respuesta de Apple, y apps como Picolo o Drink Roulette siguen publicadas [A25 ✔, A26 ✔]. **Zona gris con aplicación inconsistente**; el criterio es "excesivo" y "menores".
- Google Play: prohibido "encourage the illegal or inappropriate use of alcohol", "depicting or encouraging the use or sale of alcohol or tobacco to minors" y "portraying excessive drinking favorably, including... excessive, binge or competition drinking" [G20 ✖, vía resumen]. Su política de anuncios restringe la publicidad irresponsable de alcohol [G21 ✖].
- Picolo, Drink Roulette y Yo Nunca están en ambas tiendas; clasificación y presentación **no verificadas** [P3 ✖]. Hipótesis: 17+/18+ en App Store, PEGI 16/18 en Play, avisos de moderación y opción sin alcohol.

**Ley española y UE.** Ley 34/1988, art. 5: prohíbe publicidad televisiva de bebidas de más de 20 grados y la dirigida a menores; texto **no verificado** [S3 ✖]. Edad legal 18 por normativa autonómica; el proyecto de ley estatal sobre alcohol y menores (tramitación desde 2025) podría limitar "juegos" que incentiven: estado **no verificado** [S4 ✖]. Con 18+ y sin anuncios de bebidas el riesgo legal es bajo; el riesgo está en las tiendas.

| Permitido con poco riesgo | Zona gris | Evitar |
|---|---|---|
| **Modo "retos"** neutro sin mencionar alcohol: la penalización la decide el grupo fuera de la app. | "Bebe un sorbo" sin cantidad ni velocidad, alternativa sin alcohol visible y app 18+. | Retos de cantidad o velocidad, rankings de bebida, menores. |
| Fiesta y humor grosero: 13+ [A10 ✔]. | Pantalla de edad en el dispositivo: Apple lista "age assurance" como control, pero **no baja** la clasificación; la app entera sube a 18+ [A10 ✔]. | Modo "camuflado" activable después: retirada y expulsión. |
| **App separada 18+** si se quiere ese público. | Anuncios recompensados en 18+: inventario limitado (hipótesis). | Mezclar modo para beber y audiencia 13+ en la misma ficha. |

Recomendación: **el MVP no menciona el alcohol**; si compensa, app hermana 18+ con la misma base técnica.

## 10. Checklist final

| # | Paso | Cuándo | Tiempo | Coste |
|---|---|---|---|---|
| 1 | Titular único y pacto escrito (reparto, salida, transferencia). | Ahora | 1 día | 0 € |
| 2 | Alta Play Console personal + verificación de identidad, correo y teléfono. | Semana 0 | 1-7 días | 25 USD |
| 3 | Alta Apple individual desde la app con DNI/pasaporte y 2FA. | Semana 0 | ≤24 h | 99 USD/año |
| 4 | Dominio y web mínima: privacidad, contacto, soporte. | Semana 0-1 | 1 día | 10-20 €/año |
| 5 | Estado DSA: "no comerciante" sin compras ni anuncios; comerciante (apartado de correos o gestoría) antes de activarlos. | Semana 1 | 1-3 días | 0-80 €/año |
| 6 | Data Safety, IARC, audiencia 13+, App Privacy y cuestionario de edad de Apple. | Semana 1 | medio día | 0 € |
| 7 | Build interno en TestFlight y pista interna de Play. | Semana 1 | 1 día | 0 € |
| 8 | Prueba cerrada con 20-25 testers reales; ≥12 inscritos 14 días seguidos. | Semanas 2-4 | 14 días mínimo | 0 € |
| 9 | TestFlight externo con los mismos jugadores (Beta App Review). | Semana 2 | 1-2 días | 0 € |
| 10 | Solicitar acceso a producción en Play y responder al cuestionario. | Semana 5 | 1-7 días | 0 € |
| 11 | Producción en ambas tiendas con fecha coordinada. | Semana 6 | Apple ≤48 h; Google hasta 7 días | 0 € |
| 12 | Antes de anuncios o compras: autónomo, Paid Apps Agreement + Small Business Program, perfil de pagos de Google, CMP y ATT. | Cuando toque | 1-2 semanas | cuota de autónomo (no verificada) |

## 11. Implicaciones para nuestro juego

1. **La prueba cerrada de Google marca el calendario**: el primer build jugable debe existir 6-8 semanas antes del lanzamiento, y los playtests presenciales se hacen con la app instalada desde Play, con cuenta de Google de cada jugador y sin desinstalar 14 días.
2. **Sin cuentas ni registro en el MVP**: apodo y sala efímeros, voz sin grabar, cámara y sensores en el dispositivo, clip solo en el móvil. Etiquetas de privacidad casi vacías y nada de borrado de cuenta.
3. **El chat de voz exige moderación desde el día uno**: silenciar, expulsar y denunciar en la sala, más correo público (Apple 1.2). Va en la UI de sala, no como añadido.
4. **Cada mecánica con micro o cámara necesita variante sin sensor**: soplar o gritar → tocar rápido; gestos → agitar. Requisito de tienda y mejor jugabilidad en bares.
5. **Objetivo 13+ / PEGI 12-16**: humor grosero sí, alcohol no. El modo para beber, si llega, en app separada 18+.
6. **Monetizar después de validar**: anuncios recompensados y "paga el anfitrión" son viables, pero activan comerciante (dirección pública), autónomo y CMP; no antes de tener retención.
7. **Titular único con pacto**: cuenta personal de uno; la app se transfiere a una SL después sin perder usuarios en Apple.

## Fuentes (consulta: 2026-10-06)

**Apple (✔ leídas salvo A19)**
- A1 https://developer.apple.com/support/purchase-activation/
- A2 https://developer.apple.com/support/enrollment/ · https://developer.apple.com/help/account/membership/program-enrollment/
- A3 https://developer.apple.com/help/account/membership/enrolling-in-the-app/
- A4 https://developer.apple.com/help/app-store-connect/manage-compliance-information/manage-european-union-digital-services-act-trader-requirements
- A5 https://developer.apple.com/help/app-store-connect/transfer-an-app/overview-of-app-transfer · …/app-transfer-criteria
- A6 https://developer.apple.com/testflight/
- A7 https://developer.apple.com/help/app-store-connect/test-a-beta-version/testflight-overview/
- A8 https://developer.apple.com/distribute/app-review/
- A9 https://developer.apple.com/news/?id=ks775ehf (24-07-2025)
- A10 https://developer.apple.com/help/app-store-connect/reference/app-information/age-ratings-values-and-definitions
- A11 https://developer.apple.com/news/?id=tlur8uvi (09-07-2026)
- A12 https://developer.apple.com/app-store/review/guidelines/ (1.2, 1.4.3, 2.5.14, 3.1.1, 4.3, 5.1.1, 5.1.2)
- A13 https://developer.apple.com/app-store/app-privacy-details/ · https://developer.apple.com/help/app-store-connect/manage-app-information/manage-app-privacy
- A14 https://developer.apple.com/documentation/bundleresources/describing-use-of-required-reason-api · https://developer.apple.com/news/?id=r1henawx · ?id=3d8a9yyh
- A15 https://developer.apple.com/support/third-party-SDK-requirements/
- A16 https://developer.apple.com/app-store/user-privacy-and-data-use/
- A17 https://developer.apple.com/documentation/bundleresources/information-property-list/nscamerausagedescription
- A18 https://developer.apple.com/documentation/bundleresources/information-property-list/nsmicrophoneusagedescription
- A19 ✖ https://support.apple.com/en-us/102512
- A20 https://developer.apple.com/news/?id=einwn76m (16-01-2025)
- A21 https://developer.apple.com/news/?id=6agg0lja (18-02-2025)
- A22 https://developer.apple.com/support/downloads/terms/schedules/Schedule-2-and-3-English.pdf (secciones 1.1, 3.1, 3.2, 3.4)
- A23 https://developer.apple.com/support/dma-and-apps-in-the-eu/
- A24 https://developer.apple.com/app-store/small-business-program/
- A25 https://developer.apple.com/forums/thread/649488
- A26 https://developer.apple.com/forums/thread/688592

**Google (✔ solo developer.android.com; ✖ support.google.com, play.google.com y developers.google.com bloqueados)**
- G1 ✖ https://support.google.com/googleplay/android-developer/answer/13628312
- G2 ✖ https://support.google.com/googleplay/android-developer/answer/14659200
- G3 ✖ https://support.google.com/googleplay/android-developer/answer/6230247
- G4 ✔ https://developer.android.com/developer-verification
- G5 ✖ https://support.google.com/googleplay/android-developer/answer/14151465
- G6 ✖ https://support.google.com/googleplay/android-developer/answer/9859751
- G7 ✖ https://support.google.com/googleplay/android-developer/answer/9859655
- G8 ✖ https://support.google.com/googleplay/android-developer/answer/10144311
- G9 ✔ https://developer.android.com/guide/topics/data/collect-share
- G10 ✖ https://support.google.com/googleplay/android-developer/answer/13327111
- G11 ✖ https://support.google.com/googleplay/android-developer/answer/9876937
- G12 ✔ https://developer.android.com/training/permissions/requesting
- G13 ✔ https://developer.android.com/about/versions/12/behavior-changes-all · https://developer.android.com/training/permissions/explaining-access
- G14 ✖ https://support.google.com/googleplay/android-developer/answer/138000
- G15 ✖ https://support.google.com/googleplay/android-developer/answer/10281818
- G16 ✔ https://developer.android.com/google/play/billing
- G17 ✖ https://support.google.com/googleplay/android-developer/answer/112622
- G18 ✖ https://support.google.com/googleplay/android-developer/answer/9857753
- G19 ✖ https://developers.google.com/admob/android/privacy
- G20 ✖ https://support.google.com/googleplay/android-developer/answer/9878810
- G21 ✖ https://support.google.com/adspolicy/answer/6012382

**UE y España (✖ no accesibles)**
- E1 https://www.globalratings.com/for-developers · https://pegi.info/what-do-the-labels-mean
- E2 https://eur-lex.europa.eu/eli/reg/2022/2065/oj (arts. 3, 28, 30, 31)
- E3 https://digital-strategy.ec.europa.eu/en/policies/eu-age-verification
- E4 https://www.google.com/about/company/user-consent-policy/
- S1 https://www.aepd.es/guias/guia-cookies.pdf
- S2 https://www.boe.es/buscar/act.php?id=BOE-A-2018-16673 (art. 7)
- S3 https://www.boe.es/buscar/act.php?id=BOE-A-1988-26156 (art. 5)
- S4 Proyecto de ley sobre alcohol y menores: sin URL verificada.

**Terceros (✖ solo vistos en resultados de búsqueda)**
- P1 Precio en euros (Cult of Mac, Applesfera). · P2 kahoot.com/pricing, jackboxgames.com. · P3 Fichas de Picolo, Drink Roulette y Yo Nunca en ambas tiendas.
