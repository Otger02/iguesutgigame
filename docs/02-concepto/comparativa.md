# Comparativa de finalistas y recomendación

**Recomendación.** Probar los tres en papel esta semana con el mismo grupo (una hora en total: 15 minutos por finalista más descansos) y llevar a prototipo digital **A · La mudanza**, con **B · Bichos alrededor** como segundo candidato y **C · Idioma inventado** como plan B barato y como posible tipo de ronda dentro de A o B. Motivo corto: A es el único finalista con valoración alta en todas las casillas, su momento compartible (la caída) tiene culpable automático y se ve desde fuera, y su único riesgo serio (la sensación de acoplamiento con latencia) se despeja con un prototipo de dos móviles en una semana. B depende de hardware que no controlamos (giroscopio en Android barato) y C depende de una percepción (que no suene a charadas) que solo el playtest puede confirmar.

## 1. Finalistas frente a innegociables

| Innegociable | A · La mudanza | B · Bichos alrededor | C · Idioma inventado |
|---|---|---|---|
| I1 Cada uno con su móvil, crossplay | Alta | Alta | Alta |
| I2 Descarga gratuita | Alta (decisión de producto; ninguna mecánica exige pago) | Alta | Alta |
| I3 2-6: funciona con 2, con 6 nadie mira | **Alta**: 2 = un mueble; 6 = tres parejas o dos tríos | **Alta**: 2 = ojo y mano; 6 = tres y tres | **Alta**: 2 = pareja alterna; 6 = anillo simultáneo |
| I4 Cero explicación con profundidad | **Alta**: inclinar = subir; profundidad en obstáculos coordinados | **Alta**: girar para mirar; profundidad en direcciones cruzadas y bichos de dos redes | **Media**: 5 s de diccionario por ronda; profundidad en el idioma que evoluciona |
| I5 Instantáneas, no se repiten | **Alta**: recorridos generados, habilidad compartida | **Alta**: posiciones aleatorias, roles rotando | **Alta**: idioma generado por ronda |
| I6 Entrar y salir | **Alta**: asa → carrito automático | **Alta**: red o visión se redistribuye en la siguiente rotación (≤ 20 s) | **Alta**: el anillo se cierra |
| I7 Presencial primero, remoto intacto | **Alta**: idéntico en remoto | **Alta**: mejor en remoto si cabe | **Media**: en remoto pierde los gestos (solo ruidos y palabras inventadas) |
| I8 Bar: sin auriculares, silencio ni objetos | **Alta** | **Media**: girar el móvil sentado sí; de pie en bar lleno, con cuidado | **Alta** |
| I9 Original de verdad | **Alta** | **Alta** (riesgo de parecido estructural con "uno ve, otro hace") | **Media-alta** (riesgo de "charadas con diccionario") |

## 2. Finalistas frente a criterios de éxito

| Criterio | A · La mudanza | B · Bichos alrededor | C · Idioma inventado | Cómo lo validaremos |
|---|---|---|---|---|
| C1 Frase de < 15 palabras sin otros juegos | **Alta**: "Cada móvil es un asa: subid el piano entre todos sin que caiga" | **Alta**: "Unos ven los bichos alrededor de la mesa, otros tienen la red" | **Media-alta**: "Cada ronda un idioma nuevo de gestos y ruidos: entendeos a tiempo" | Decir la frase a 5 personas que conozcan BOMBANANA!, Keep Talking o Spaceteam y anotar si dicen "es como…" |
| C2 Cámara externa sin pantallas | **Alta**: cuerpos en espejo y la caída | **Alta**: gente girando y señalando | **Alta**: gestos y ruidos | Grabar 15 s de cada prueba en papel y enseñárselos a alguien que no estaba: ¿entiende qué pasa? ¿se ríe? |
| C3 Nuevo a mitad de partida completa su ronda | **Alta**: asa de atrás | **Alta**: mano | **Media**: idioma de 2 signos | En cada playtest, meter a alguien sin explicarle nada en la segunda ronda y cronometrar hasta su primera acción válida |
| C4 Dinamismo | **Alta**: control continuo | **Alta**: bichos en movimiento, rotación cada 20 s | **Media-alta**: el receptor puede atascarse (pista automática a los 6 s) | Medir "tiempo máximo sin actuar" por jugador en el prototipo (objetivo abajo) |
| C5 Con 2 y con 6 todos ocupados toda la ronda | **Alta** | **Alta** | **Alta** (en anillo) | Playtest con 2 y con 6; contar segundos en que alguien "mira" |
| Esencia (dependencia, comunicación, malentendido, culpable) | **Alta** con la información repartida delante/atrás | **Alta** | **Alta** | Contar risas y frases del tipo "¡que te he dicho que…!" en el vídeo |
| Riesgo técnico (según `../01-investigacion/viabilidad-tecnica.md`) | **Medio**: giroscopio sin permiso y trivial; lo crítico es la latencia entre asas (objetivo < 150 ms) con sala autoritativa a 10-20 Hz y predicción local | **Medio-alto**: giroscopio ausente o con deriva en parte de los Android baratos; respaldo por acelerómetro o arrastre táctil | **Bajo**: casi sin sensores; validación por toque | Prototipo web (PWA) con 2 móviles por 4G en una semana |
| Momento TikTok diseñado | **Alta**: la caída con culpable y gráfica | **Alta**: el mapa de "dónde apuntaba cada uno" | **Alta**: "quería decir X, entendiste Y" con el idioma sobreimpreso | Clip generado desde el estado del juego (sin grabar pantalla ni cámara, como recomienda viabilidad técnica) |

## 3. Objetivos de dinamismo y de tiempo hasta jugar

Propuestas para los tres finalistas; se validan en el prototipo y se ajustan.

| Métrica | Objetivo | Justificación |
|---|---|---|
| Tiempo máximo que un jugador pasa sin actuar | **5 s** (A y B: 0 s en la práctica, el control es continuo; C: pista automática a los 6 s) | Lo que nos gusta de la esencia es "nadie espera"; la crítica a BOMBANANA! y a los juegos de deducción es el tiempo muerto (reuniones, muertos que miran). Cinco segundos es el umbral en el que alguien saca el móvil propio para mirar otra cosa; es una hipótesis a medir en playtest |
| Duración de ronda | **A: 60-75 s · B: 45-60 s · C: 30-45 s** | Un clip = una ronda: el clip útil son los últimos 8-15 s y la ronda entera tiene que caber en un vídeo de TikTok sin cortes. Rondas cortas permiten que el invitado lento entre en la siguiente sin esperar más de un minuto. Las rondas de BOMBANANA! (niveles de minutos) son justo lo que no queremos |
| Reinicio entre rondas | **≤ 3 s**, sin menú: pantalla de culpable (2 s) y nueva ronda | "Sin menús entre rondas" es innegociable; el culpable es el momento compartible y no puede durar más de lo que dura una risa |
| Abrir la app → jugando, anfitrión | **≤ 30 s** hasta sala creada; primera ronda con un invitado en ≤ 2 min | Datos y razonamiento en `../01-investigacion/mercado-y-cliente.md` §4.4 |
| Abrir la app → jugando, invitado con la app | **≤ 15 s** (QR, abrir, dentro) | Listón de Jackbox por navegador y del antiguo Instant de Google |
| Invitado sin la app | **≤ 90 s** desde el QR, con app ≤ 50 MB (objetivo < 20 MB en Android) | Descarga 10-20 s + instalación 10-20 s + entrar ≤ 20 s; con wifi de bar se dobla, por eso la ronda empieza sin él y entra en la siguiente |

## 4. Qué finalista exige qué (implicaciones técnicas y visuales)

| | A · La mudanza | B · Bichos alrededor | C · Idioma inventado |
|---|---|---|---|
| Sensores | Giroscopio y acelerómetro continuos; micro opcional | Giroscopio (vista 360°) con respaldo; micro opcional | Acelerómetro para validar acciones; nada más |
| Sala | Autoritativa a 10-20 Hz con predicción local (Colyseus o Durable Objects) | Autoritativa a 5-10 Hz (posiciones de bichos) | Autoritativa a baja frecuencia (eventos) |
| Motor probable | Godot 4 o web + Capacitor tras medir 60 fps en WebView | Godot 4 o web + Capacitor | Web + Capacitor |
| Estilo visual | 2D o 2.5D con "peso" físico y objetos reconocibles | 2D con criaturas simples y mapa de 360° legible | 2D de iconos grandes: signos y significados |
| Peso del invitado | < 20-50 MB (sin modelos 3D) | < 20-50 MB | < 20 MB |
| Modo para beber futuro (fuera del MVP) | Retos "sin alcohol por defecto" como obstáculos extra | Igual | Igual (significados "brindis") |

## 5. Recomendación razonada

1. **Orden de pruebas en papel esta semana:** A, B y C en la misma sesión con el mismo grupo de 4-6 amigos, en ese orden (A y B son físicas y calientan al grupo; C es la más "mental" y funciona mejor cuando ya hay confianza). Grabar 15 s de cada una y enseñárselos a alguien que no estaba. Repetir con un segundo grupo distinto antes de decidir.
2. **Concepto para el prototipo digital: A · La mudanza**, salvo que el papel diga lo contrario. Criterio de cambio: si en papel A no produce risas ni "¡que lo tiras!" en dos grupos, pasa B al frente; si B tampoco, C.
3. **C como tipo de ronda, no solo como finalista:** si A o B ganan, el idioma inventado puede ser una "ronda especial" dentro del mismo juego (cada tres muebles, una entrega solo con el idioma), lo que conserva su esencia sin apostar la app a él. Decisión para después del papel.
4. **Capa social común (La tentación)** desde 3 jugadores en cualquiera de los tres; **no** saboteador fijo (hipótesis del brief descartada en `filtro.md` por originalidad).
5. **Lo que hay que decidir ahora** (ver `../DECISIONES.md`): qué finalistas se prueban en papel y cuándo; qué concepto va a prototipo; qué dirección visual (Fase C).
