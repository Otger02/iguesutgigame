# Finalista C · Idioma inventado

> Nombre provisional. Semilla S4 con los gestos con sensores de S3, la vigilancia de voz de S6 (solo como sabotaje presencial) y la capa social de S8 como opcionales.

## Fantasía, pitch y bucle

**Fantasía y tema.** Sois una tribu (o una tripulación, o una pandilla de extraterrestres recién aterrizada) que cada ronda amanece con un idioma nuevo: cuatro a seis signos, cada uno un gesto o un ruido, con un significado. Solo podéis entenderos con ese idioma, y el idioma se olvida al acabar la ronda. Tono: absurdo, teatral, de "¿qué me estás diciendo?".

**Pitch (12 palabras).** Cada ronda un idioma nuevo de gestos y ruidos: entendeos a tiempo.

**Bucle de una ronda (30-45 s).**

1. **Diccionario (5 s):** todas las pantallas muestran el idioma de la ronda: por ejemplo, "tocarse la nariz = azul", "¡pum! = levantar", "aletear = dos veces", "silbar = el de la izquierda". Luego desaparece; se puede volver a mirar pulsando, pero cuesta 2 s.
2. **Objetivo:** cada **emisor** recibe en su pantalla una acción que debe ejecutar su **receptor**: "levanta el móvil dos veces", "toca el azul", "pásaselo al de la izquierda". El receptor no la ve.
3. El emisor solo puede usar los signos del idioma. El receptor interpreta y actúa: lo que hace lo valida el móvil (toque en pantalla, o levantar, agitar, dar la vuelta con sensores).
4. Acierto: siguiente objetivo al instante. Fallo: el móvil del receptor muestra lo que ha entendido frente a lo que se quería decir ("Ana quería 'salta'; tú hiciste 'perro'") y sigue.
5. A mitad de ronda, un signo cambia de significado para todos (aviso de 2 s): el idioma "evoluciona". Fin de ronda: nuevo idioma, nuevas parejas, sin menú.

## Roles y escalado de 2 a 6

| Jugadores | Estructura | Quién hace qué |
|---|---|---|
| 2 | Pareja | Alternan emisor y receptor en cada objetivo (cada 8-10 s) |
| 3 | Triángulo | A emite para B, B para C, C para A: todos emiten y reciben a la vez |
| 4-6 | Anillo | Cada uno emite al de su derecha y recibe del de su izquierda, simultáneamente; con 6, el ruido cruzado es parte de la gracia |

Nadie espera: en el anillo todo el mundo está gesticulando y descifrando al mismo tiempo. Con 2, el cambio de rol cada objetivo mantiene el ritmo.

## Frescura y aprendizaje

- **Fresco:** el idioma se genera por ronda combinando un banco de signos (gestos y ruidos fáciles de hacer en un bar) con significados aleatorios; las acciones objetivo se componen de dos o tres significados. Memorizar es imposible por diseño: lo que se aprende es a "actuar" bien, y eso mejora la risa en vez de matarla. El "idioma evoluciona" a mitad de ronda remata la imposibilidad de rutina.
- **Recién llegado:** su primera ronda tiene un idioma de solo dos signos y objetivos de un solo significado; el juego lo sube a cuatro y seis en las siguientes. No hay rol de entrada clásico (emisor y receptor necesitan el idioma), así que la entrada se resuelve por tamaño del idioma, no por rol: es la hipótesis del brief que esta semilla contradice, y la prueba en papel dirá si basta.

## Entrar y salir

- Unirse: entre rondas; el anillo se rehace.
- Irse o desconectarse: el anillo se cierra sin él (su emisor pasa a emitir al siguiente). Si está a mitad de objetivo, el objetivo se cancela sin penalización. Nadie es imprescindible.

## Sensores y sabotajes

| Sensor | Uso | Por qué |
|---|---|---|
| Acelerómetro y giroscopio | Validar acciones del receptor (levantar, agitar, dar la vuelta, inclinar hacia alguien) | Hace que la respuesta sea física y visible; respaldo: botón en pantalla |
| Micrófono | Opcional en presencial: sabotaje "el guardia" (3 s en los que si se detecta voz cerca del emisor, pierde el objetivo) | Fuerza gestos puros durante unos segundos; nunca es el centro, porque en un bar el micro no es fiable (ver viabilidad técnica) |
| Cámara | No en el MVP | Decodificar gestos por cámara sustituiría al humano, que es justo lo que no queremos; lo decodifica el receptor |

**Sabotajes** (2-4 s): el guardia (sin voz), eco (el receptor debe repetir el signo antes de actuar), traductor borracho (un signo se intercambia por otro solo en la pantalla del emisor), apagón del diccionario (no se puede consultar). **Capa social opcional desde 3 jugadores (La tentación):** a un emisor se le ofrece "si tu receptor falla tres veces seguidas, ganas 3 puntos"; emitir mal con cara de inocente es el arte; los demás pueden señalarle.

## Momento compartible y cámara externa

- **El momento:** alguien aleteando y ladrando con total seriedad mientras su receptor le mira sin entender nada y hace lo contrario; el fallo muestra en pantalla lo que se quería decir frente a lo que se entendió. Clip automático vertical de los últimos 8 s con el "idioma" sobreimpreso (los signos y su significado) para que quien lo ve en TikTok entienda el chiste sin contexto.
- **Cámara externa:** mesa entera gesticulando y haciendo ruidos de animales en un bar. Gesto imitable: el propio idioma, que la gente puede repetir fuera del juego ("esto en mi tribu significa cerveza").

## Presencial y remoto

- **Presencial:** gestos y ruidos; el receptor decodifica con los ojos y los oídos; el ruido del bar no importa.
- **Remoto:** el juego genera idiomas solo de ruidos y palabras inventadas (sin gestos) y la voz va por la app o por la llamada del grupo. Si el grupo está en videollamada, se activan los gestos. Es el finalista con más diferencia entre modos, pero ambos funcionan.

## Test de diferenciación

| Parecido | Qué comparte | Por qué no es "lo mismo pero" |
|---|---|---|
| Charadas, Heads Up!, Guess Up | Comunicar sin palabras, cámara externa perfecta | No es adivinar una palabra por turnos: es cooperar con un código generado, todos a la vez, para ejecutar acciones físicas; el idioma cambia a mitad |
| Keep Talking / BOMBANANA! | Canal estrangulado, malentendidos, uno sabe y otro actúa | No hay manual que leer ni bomba: el "manual" cabe en una pantalla, lo ven todos 5 s y se destruye; los roles no mutilan sentidos, limitan el vocabulario |
| Spaceteam | Cada uno con su móvil, gritos, rondas cortas, órdenes que viajan | Las órdenes no se leen y se gritan: se traducen a un código inventado; el fallo es de interpretación, no de reflejos |

## Riesgos principales

1. **Percepción de originalidad:** es el finalista con más parientes ("charadas con diccionario"). El test en papel debe confirmar que la gente lo describe por el idioma inventado y no por las charadas.
2. **El diccionario de 5 s es "leer":** en un bar con copas puede ser demasiado. Mitigación: signos con icono grande y significado con icono, no texto; ronda de entrada de dos signos.
3. **Parálisis del receptor:** si no entiende, se queda parado (rompe el dinamismo). Mitigación: pista automática a los 6 s sin acción y objetivos cortos.
4. **Remoto empobrecido:** sin gestos, pierde la mitad del teatro. Aceptable si el presencial es la prioridad, pero hay que decirlo.

## Prueba en papel (15 minutos, esta semana)

**Material:** papel y bolígrafo, 10 tarjetas pequeñas (o trozos de papel), tres objetos de colores (vaso rojo, libro azul, cuchara amarilla), un cronómetro.

**Reglas:**

1. Preparar el **idioma** en un papel: cinco signos con significado, elegidos al azar entre una lista: gestos (tocarse la nariz, aletear, pulgar abajo, girar la muñeca, dar una palmada) y ruidos (¡pum!, mugir, silbar, chasquear la lengua) frente a significados (rojo, azul, amarillo, levantar, dar la vuelta, al de la izquierda, dos veces).
2. Preparar 10 **tarjetas de objetivo** combinando dos significados: "levanta el azul", "da la vuelta al rojo dos veces", "pásale el amarillo al de la izquierda".
3. Enseñar el idioma 5 segundos a todos y taparlo. Se puede destapar 2 segundos pagando una tarjeta.
4. En anillo: cada emisor coge una tarjeta y la transmite solo con signos a su receptor de la derecha; el receptor ejecuta con los objetos de la mesa. Acierto: siguiente tarjeta. 45 segundos por ronda. A los 25 segundos, el director grita "¡cambio!" y dos signos intercambian significado (anotado en el papel).
5. Con 2 personas: alternar roles en cada tarjeta. Con 4-6: todos a la vez en anillo.

**Qué medir:** objetivos acertados por ronda, fallos que hacen reír frente a fallos que frustran, cuántas veces se consulta el idioma, y cómo describe el juego alguien que lo ve desde fuera (si dice "charadas", hay que repensarlo).
