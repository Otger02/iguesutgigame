# Brief del proyecto (v2, 2026-10-06)

> Mensaje íntegro de Iñaki que arranca la fase de descubrimiento y concepto. Se guarda tal cual (numeración incluida) para que sirva de referencia a ambas sesiones. No es un documento editable: si el brief cambia, se guarda este como `00-brief-v1.md` y el nuevo sustituye a este archivo (ver `docs/DECISIONES.md`).

---

Somos Iñaki y Otger y vamos a crear desde cero un party game para móvil (Google Play y App Store). Tú trabajas en la sesión de Iñaki; Otger trabaja en paralelo con su propia sesión de Claude Code sobre este mismo repositorio, así que la coordinación forma parte del trabajo.
Fase actual: descubrimiento y concepto. En esta sesión no se escribe código del juego. Todo en español de España.
0. La idea en una línea
No vamos a hacer una réplica de BOMBANANA! ni un "BOMBANANA! para móvil". Queremos partir de lo que lo hace divertido para crear un juego nuevo y propio, más dinámico y más divertido, pensado de verdad para el móvil.

1. Primero: base de coordinación
2. Haz git pull. Si ya existen README.md, CLAUDE.md o docs/, léelos antes de crear nada: Otger puede haber empezado. No dupliques ni sobrescribas su trabajo.
3. Guarda este mensaje íntegro en docs/00-brief.md. Si ya existe una versión anterior, este brief la sustituye: guarda la anterior como docs/00-brief-v1.md, anota el cambio en docs/DECISIONES.md y reaprovecha lo ya hecho que siga siendo válido en lugar de empezar de cero.
4. Crea o actualiza CLAUDE.md (breve) con estas reglas. Van aquí porque Claude Code carga CLAUDE.md automáticamente al iniciar cada sesión y el README no:
   * Al empezar sesión: git pull y lee README.md y docs/DECISIONES.md. Si es tu primera sesión, lee también docs/00-brief.md.
   * Antes de empezar una tarea (cada entregable o encargo, no cada edición menor): anótala en "En curso" del README (sesión, tarea, fecha) y haz push.
   * Al terminar CADA tarea: añade una entrada arriba del "Registro de cambios" del README con fecha y hora, sesión (Iñaki u Otger), qué has hecho, qué archivos has creado o modificado y qué queda pendiente de decidir. Quítala de "En curso". Commit y push.
   * Solo se añaden entradas: nunca se borran ni se reescriben las de la otra sesión. Si hay conflicto en el README, conserva ambas entradas en orden cronológico.
   * Lo que se decide va a docs/DECISIONES.md (fecha, decisión, alternativas descartadas y motivo). Nada está decidido si no está ahí.
   * Si vas a tocar algo que la otra sesión tiene "En curso", para y avisa.
   * Idioma: español de España. Nunca subas claves ni credenciales al repo.
5. Crea o actualiza README.md con una descripción del proyecto en un párrafo y, justo debajo, un bloque destacado con esta regla: "Cualquier sesión de Claude (Iñaki u Otger) debe escribir en este README cada tarea que termine: qué ha hecho y qué ha cambiado. Así la otra sesión se entera. Esta regla también está en CLAUDE.md." Después: Estado actual (máximo 5 líneas), En curso, Registro de cambios (lo más reciente arriba) y estructura de carpetas.
6. Crea docs/DECISIONES.md y las carpetas docs/01-investigacion/, docs/02-concepto/ y docs/03-visual/ si no existen.
7. Commit y push de esta base antes de seguir. Si el repo no tiene remoto, avísalo y continúa en local.
8. Punto de partida
Lo que nos gusta de BOMBANANA! (Lefto Studio, Steam, septiembre 2026)
Un cooperativo en el que la información está repartida y solo comunicándoos bien salís adelante. Nos gustan la tensión contra el reloj, los malentendidos que dan risa, el caos y las tonterías físicas, como tirarle algo a un compañero. Esa es la esencia que queremos conservar, no su forma.
Lo que no nos gusta

* Es de pago y solo de ordenador.
* Su campaña son 30 niveles fijos y cada nivel tiene siempre el mismo módulo: cuando lo aprendes, pierde la gracia.
* Es poco dinámico.
* Los apagones duran demasiado y siempre son iguales.
* Explicárselo a alguien nuevo lleva mucho rato y le exige mucha atención.
* Exige exactamente 3 jugadores.

Contexto competitivo

* BOMBANANA! ha anunciado versión para móvil (y Roblox): verifica fecha y detalles.
* Ya tiene un modo infinito con oleadas generadas proceduralmente, así que "sin niveles" por sí solo no nos diferencia.
* Ya existen juegos parecidos en PC y en móvil: Keep Talking and Nobody Explodes, Spaceteam, Tick Tock, The Past Within, Operation: Tango, We Were Here, Among Us y BombSquad, entre otros. Verifica plataformas y amplía la lista, incluidos los que hayan salido a raíz de BOMBANANA!.
* Conclusión: competir en "desactivar algo con la información repartida" es entrar en el terreno más ocupado. La originalidad tiene que estar en el núcleo (fantasía, mecánica principal y dinámica social), no en la estética.

Referencias de "abres y juegas sin contexto"
Splash (El Impostor) y Guess Up. A diferencia de ellos, en el nuestro cada jugador juega desde su móvil, como en Among Us.
3. Qué tiene que cumplir
Innegociables

1. Cada jugador con su móvil y la app instalada. Crossplay iOS–Android.
2. Descarga gratuita.
3. De 2 a 6 jugadores: tiene que funcionar bien con 2 y, con 6, nadie puede quedarse mirando.
4. Cero explicación: un jugador nuevo entiende el juego jugando, sin vídeos, sin leer reglas y sin que nadie le explique. Sin que sea simple: profundidad sin reglas complejas.
5. Partidas que se arrancan al momento y no se repiten. Aprenderse algo no puede matar la gracia.
6. Entrar y salir:
   * Alguien puede unirse entre rondas y jugar sin explicaciones.
   * Alguien puede irse de la partida sin perjudicar al resto.
   * Si un móvil se desconecta a mitad de ronda, la ronda no se rompe.
   * Ningún jugador puede ser imprescindible.
7. Presencial y a distancia (cada uno desde su casa). Prioridad de diseño: el mismo espacio (bar, sofá), sin romper el modo a distancia. Si la investigación sugiere otra prioridad, argumenta.
8. Jugable casi en cualquier sitio, incluido un bar: nada que exija auriculares, gorras, silencio ni objetos externos.
9. Original de verdad:
   * La fantasía y la mecánica principal no pueden ser un reskin de BOMBANANA!, Keep Talking ni Spaceteam. Cambiar los monos por otro animal no cuenta como original.
   * Nada de bombas por defecto: solo si la reinventas de forma evidente y lo justificas.
   * Nada de monos, ni la tríada ciego/sordo/mudo, ni su estética.
   * No uses nombres de otros juegos en el nuestro, en keywords ni en anuncios.

Qué significa "dinámico" y "divertido" para nosotros

* Dinámico: nadie espera; la situación cambia durante la ronda; rondas cortas con reinicio inmediato y sin menús entre ellas; se juega también con el cuerpo y la voz, no solo con el dedo.
* Divertido: la risa como métrica. Malentendidos, tonterías físicas, culpables, casi-victorias y sorpresas. Fallar tiene gracia y dura poco.

Deseables (úsalos si encajan y descártalos con criterio si no)

* Giroscopio: mover la vista por el entorno, pruebas físicas, lanzar objetos a otros jugadores.
* Micrófono: pruebas o sabotajes. Por ejemplo, caen globos y hay que soplar para que no toquen el suelo mientras resuelves otra cosa.
* Cámara: detectar gestos o posición de los dedos para transmitir símbolos al equipo.
* Sabotajes que entorpezcan, pero cortos, variados y aleatorios.
Si algo de lo que pedimos rompe una idea de juego muy buena, sáltatelo: dilo y explica por qué.

Futuro (fuera del MVP, pero que la arquitectura no lo impida)

* Modo para beber, con estas condiciones:
   * Sin retos de cantidad ni de velocidad.
   * Con alternativa sin alcohol siempre disponible.
   * Validando antes qué permiten Apple y Google, incluida la clasificación por edad.
* Modos por equipos.

Hipótesis (evalúalas; no son obligatorias)

* Saboteador oculto: el equipo coopera contra el reloj, pero desde 4 jugadores uno puede estar saboteando en secreto, camuflado entre los errores honestos de la comunicación. Al final de la ronda, acusación y revelación. Mezcla nuestras dos referencias (BOMBANANA! y El Impostor). Con 2-3 jugadores, cooperativo puro.
* Restricciones de comunicación sin atrezo que cambian cada ronda ("solo gestos", "solo sí o no", "una palabra"), en lugar de roles de sordo o ciego que en un bar no funcionan.
* Rol de entrada: siempre hay un rol que no necesita saber nada, el que ejecuta lo que le dicen. El recién llegado entra con ese rol y aprende jugando.
* Soluciones generadas en cada partida: los gestos son siempre los mismos (fáciles de aprender) y las soluciones cambian (imposibles de memorizar).
* En presencial, el juego sabe quién se sienta a tu izquierda y a tu derecha (un paso al crear la sala), así que lanzar o pasar algo con el móvil llega a la persona real de al lado.
* Pantalla de culpable al fallar y clip vertical automático de los segundos previos, listo para compartir (con consentimiento si sale la cara de alguien).
* Monetización que nunca ponga un muro al invitado (p. ej. paga el anfitrión y desbloquea para toda la sala) y sin anuncios a mitad de partida.

Contexto

* Objetivo: que se vuelva viral, sobre todo en TikTok. El momento compartible tiene que estar diseñado, no confiado a la suerte.
* Equipo de 2 personas que desarrollará principalmente con Claude Code. Experiencia previa: juegos web multijugador para móvil con Next.js + Supabase Realtime.
* Presupuesto limitado: prioriza opciones gratuitas o baratas y señala cualquier coste.
* Mercado de partida: España. Recomienda mercados e idiomas de lanzamiento.
* Podemos organizar a menudo playtests presenciales con grupos de amigos. También tenemos previsto abrir canales de Twitch (gaming y streams sociales): tenlo en cuenta cuando lleguemos a comunicación.
* Velocidad: BOMBANANA! va camino del móvil, así que priorizamos validar pronto la diversión frente a documentarlo todo.

4. Criterios de éxito (diseña para cumplirlos e indica cómo los validaremos)

* Diferenciación: el juego se explica en una frase de menos de 15 palabras que no menciona ningún otro juego, y nadie que conozca BOMBANANA!, Keep Talking o Spaceteam diría "es lo mismo pero...".
* Cámara externa: si grabas al grupo sin enseñar las pantallas, se entiende qué pasa y hace gracia.
* Un jugador nuevo, incluso si entra a mitad de partida, completa su primera ronda sin ayuda.
* Dinamismo: propón el tiempo máximo que un jugador puede pasar sin actuar y la duración ideal de ronda, y justifícalos.
* Tiempo desde abrir la app hasta estar jugando: propón un objetivo realista y justifícalo.
* Con 2 y con 6 jugadores, todos tienen algo que hacer durante toda la ronda.

5. Trabajo de esta sesión
Fase A · Investigación (docs/01-investigacion/)
Puedes paralelizarla con subagentes. Cada documento empieza con un resumen de 5 líneas y acaba con "Implicaciones para nuestro juego". Si ya existe investigación de una versión anterior del brief, reaprovéchala y complétala.
6. esencia-y-competencia.md
   * BOMBANANA! deconstruido:
      * Qué lo hace divertido (la esencia) y qué es solo su implementación.
      * Qué alaban y qué critican sus reseñas de Steam.
      * Modos, jugadores, precio y plataformas.
      * Qué se sabe de su versión móvil.
   * Mapa competitivo de juegos parecidos en móvil y PC, posicionados en ejes como:
      * Mismo espacio frente a online.
      * Cooperativo frente a deducción social.
      * Pantalla frente a cuerpo y voz.
      * Número de jugadores.
      * Gratis frente a de pago.
   * De cada juego del mapa, qué resolvió y qué no.
   * El hueco: dónde hay sitio para algo nuevo y qué está saturado.
7. juegos-virales.md
   * Entre 8 y 12 juegos virales en TikTok en los últimos 24 meses, priorizando los más recientes y los sociales, party y cooperativos, de móvil y de PC.
   * Punto de partida (verifica y amplía): El Impostor de Splash, BOMBANANA!, PEAK y R.E.P.O. Investiga también el fenómeno "friendslop".
   * De cada uno: jugabilidad, estética, precio y monetización, comunicación en redes, si tiene web, gancho en TikTok (qué se ve en los primeros segundos y por qué dan ganas de jugarlo) y si el contenido lo crea la marca o los jugadores.
   * Cierra con los patrones comunes y qué podemos aplicar sin copiar.
   * No puedes ver vídeos de TikTok: trabaja con fuentes secundarias y añade al final una checklist para que nosotros revisemos TikTok a mano en unos 30 minutos (búsquedas y hashtags concretos y qué anotar).
8. mercado-y-cliente.md
   * Mercado de party games para móvil y modelos de monetización con ejemplos reales: de pago, gratis con compras, suscripción, anuncios, paga el anfitrión.
   * Cliente ideal y personas, separando a quien descarga primero y propone jugar del invitado que tiene que descargarse la app para unirse. La experiencia del invitado decide la viralidad.
   * Cuantifica la fricción de "todos descargan" y cómo minimizarla (peso de la app, sin registro, unirse por QR o código).
9. viabilidad-tecnica.md
   * Repos y librerías públicas para:
      * Detección de manos y dedos (MediaPipe y alternativas).
      * Detección de soplido con ruido ambiente.
      * Giroscopio y acelerómetro.
      * Multijugador por salas con entrada y salida en caliente y reconexión (servidor autoritativo frente a P2P).
      * Chat de voz para el modo remoto, incluido su conflicto con usar el micro como mecánica.
   * De cada opción: licencia (marca GPL/AGPL como riesgo para una app comercial), madurez, soporte iOS/Android, rendimiento en Android de gama media y coste.
   * Primera comparativa de motores: Unity, Godot, Unreal y un stack web empaquetado como app. Criterios:
      * Lo bien que se trabaja con Claude Code (escenas y lógica en texto frente a editores visuales).
      * Peso de la app y rendimiento en gama media.
      * Crossplay, sensores y cámara.
      * SDK de multijugador, voz, compras y anuncios.
      * Curva de aprendizaje para nuestro perfil.
   * Blender no es un motor: valóralo solo para crear assets. No cierres la decisión; dependerá del concepto y del estilo visual.
10. requisitos-publicacion.md: qué hace falta para publicar en App Store y Google Play.
   * Cuentas, costes y tipo (personal o empresa).
   * Pruebas cerradas obligatorias de Google Play para cuentas nuevas (número de testers y días, porque condicionan el calendario).
   * Clasificación por edad, privacidad y RGPD, y permisos de cámara y micrófono.
   * Obligaciones de comerciante en la UE.
   * Límites relevantes para el futuro modo para beber.

Fase B · Ideación en embudo (docs/02-concepto/)

6. semillas.md: entre 10 y 12 ideas de juego muy distintas entre sí, de 5 líneas cada una. Cada semilla incluye:
   * Fantasía y verbo principal.
   * Por qué es divertida y por qué es dinámica.
   * Qué vería una cámara externa.
   * Juego existente más parecido y en qué se diferencia.
Requisitos de variedad:
   * Al menos 3 que no se basen en información repartida.
   * Al menos 3 donde el móvil como objeto físico (sensores) sea central.
   * Al menos 2 con giro social (saboteador, traidor o rivalidad dentro del equipo).
   * Al menos 3 que rompan nuestras hipótesis.
7. filtro.md: tabla de las semillas contra los innegociables y los criterios de éxito, con valoración razonada (alta, media o baja; sin puntuaciones inventadas). Elige 3 finalistas y explica por qué descartas el resto.
8. Un archivo de una página por finalista, con:
   * Fantasía y tema, frase de pitch y bucle de una ronda.
   * Roles y cómo escalan de 2 a 6.
   * Cómo se mantiene fresco partida a partida y cómo aprende un recién llegado.
   * Cómo se entra y se sale.
   * Uso de giroscopio, micro y cámara (o por qué no) y sabotajes.
   * Momento compartible para TikTok y qué ve la cámara externa.
   * Modo presencial y remoto.
   * Test de diferenciación frente a los 3 juegos más parecidos del mapa competitivo.
   * Riesgos principales.
   * Prueba en papel de 15 minutos: reglas y material improvisable con objetos de casa, para probar el núcleo sin código esta misma semana.
9. comparativa.md: tabla de los 3 finalistas frente a los innegociables y los criterios de éxito, con tu recomendación razonada.

Fase C · Direcciones visuales (docs/03-visual/)

10. Entre 3 y 4 direcciones de estilo, aplicables a cualquier finalista e indicando con cuál encaja mejor cada una. Ninguna puede recordar a BOMBANANA! ni a los juegos del mapa competitivo.

* Una página HTML autocontenida por dirección, con paleta, tipografía, siluetas de personajes en SVG y una pantalla de muestra del juego en móvil.
* Un markdown por dirección con:
   * Referencias, legibilidad en pantalla pequeña y potencial en TikTok.
   * Potencial de un personaje o mascota propia que pueda ser la cara de la marca.
   * Coste de producción para 2 personas con ayuda de IA.
   * Accesibilidad: ninguna mecánica puede depender solo del color.
   * Implicaciones técnicas (2D, 2.5D o 3D).
   * 3 prompts para generar concept art con IA.

6. Reglas de trabajo

* No inventes datos. Descargas, ingresos, visualizaciones, precios y fechas, siempre con fuente (URL y fecha de consulta); si no lo encuentras, escribe "no verificado". Separa hechos de hipótesis.
* Ten criterio: recomienda, señala riesgos y di sin rodeos lo que no merece la pena, también si una idea nuestra se parece demasiado a algo que ya existe.
* Documentos escaneables: conclusión arriba, tablas para comparar, sin relleno.
* Registra en el README cada fase terminada, no solo al final.

7. Punto de parada
Cuando termines la Fase C, para. No avances a motor, GDD, marca, monetización ni marketing. Déjame en el chat:

* Un resumen de 10 líneas como máximo.
* Las decisiones que necesitas de nosotros, con tu recomendación. Como mínimo: qué finalistas probamos en papel primero, qué concepto y qué dirección visual.
* Lo que no hayas podido verificar.

Fases siguientes, para que tengas la visión completa (no las hagas ahora):

1. Prototipo digital jugable del núcleo, desechable y en la tecnología más rápida, para validar la diversión con gente que nunca haya jugado.
2. Motor y arquitectura definitivos y documentación completa del juego (GDD), incluidas seguridad y moderación si hay voz o nombres de usuario.
3. Negocio y lanzamiento:
   * Marca y naming, con disponibilidad de marca registrada, dominio y redes.
   * Monetización, estrategia de marketing y plan de comunicación y de lanzamiento.
   * Analítica y métricas (retención, invitaciones por partida).
   * Checklist de titularidad del juego y acuerdo entre socios, para validar con un profesional.
