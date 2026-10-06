# Finalista C2 · Expedición Glifo (rediseño del idioma inventado)

> Nombre provisional. Rediseño del finalista C a petición de la sesión de esta rama: el juego se juega **desde el móvil** (no con gestos), tiene **una finalidad**, funciona de **2 a 6** y es **más rico visualmente**, con salas. Sustituye a la ficha `finalista-C-idioma-inventado.md` si se aprueba; la original se conserva como referencia. Explicador visual: `finalista-C2-expedicion-glifo.html`.

## Conclusión

**Recomendación:** la finalidad es **escapar de una ruina alienígena sala a sala** (escape room exprés), no desactivar una bomba. Cada móvil es una pieza de la ruina (un panel, una linterna, una palanca), las órdenes están escritas en **glifos alienígenas** y el diccionario está **repartido entre los móviles**. Se habla en castellano, con libertad; lo difícil (y lo gracioso) es **describir glifos que no tienen nombre**: el idioma lo acabáis inventando vosotros ("¡el tenedor tuerto!", "¡el calvo con paraguas!"). Estilo **2.5D en tinta risográfica**: ilustración 2D por capas que se mueven con el giroscopio, dos tintas por sala.

| Pregunta | Decisión que propongo | Por qué, en una línea |
|---|---|---|
| Finalidad | Escapar de una ruina alienígena (salas encadenadas) | Da progreso, variedad y un final; la bomba está vetada por el brief y es Keep Talking |
| Papel del móvil | El móvil **es** el juego: controles, sensores, glifos | Lo pedido; además arregla el modo remoto del C original |
| Canal de comunicación | Voz libre; el reto es describir glifos | Funciona en bar y en remoto; nadie tiene que hacer el ridículo para jugar, pero lo acaba haciendo |
| Jugadores | 2 a 6, información repartida por móvil | Cada móvil aporta controles + un fragmento del diccionario |
| Impostor | No fijo. Opcional desde 4: **el traductor averiado** | Culpable y revelación sin convertirlo en un juego de deducción |
| Estilo | 2.5D (capas 2D con parallax), risografía "pulp de expedición" | Rico y barato; el 3D no aporta risa y encarece todo |
| Salas | Sí: 8 tipos en el banco, 4-5 por expedición, orden aleatorio | No se repite, cada sala enseña una interacción distinta |

## 1. Finalidad: comparativa de ideas

El brief (`docs/00-brief.md`, innegociable 9) dice: "Nada de bombas por defecto: solo si la reinventas de forma evidente y lo justificas", y nada de reskins de BOMBANANA!, Keep Talking o Spaceteam. `01-investigacion/esencia-y-competencia.md` marca "desactivar algo con información repartida" como el terreno más ocupado del mapa.

| Finalidad | Encaje con el idioma | Originalidad | Variedad y progreso | Veredicto |
|---|---|---|---|---|
| Desactivar una bomba | Alta | **Baja**: describir símbolos raros para desactivar una bomba es literalmente el módulo de teclado de Keep Talking | Media | **Descartar** como marco. Queda como clímax reinventado (el núcleo que colapsa, §4) |
| Escape room | Alta | Media: hay escape rooms cooperativos (We Were Here, Escape Simulator), ninguno móvil-presencial con idioma generado | **Alta**: salas, progreso, final | Base de la propuesta |
| Encontrar al impostor | Media | Baja: deducción social saturada (Splash y clones); el filtro ya lo descartó como centro | Baja | Capa opcional, no finalidad |
| **Expedición a una ruina alienígena** (escape room + descifrado) | **Muy alta**: el idioma es la cerradura | Alta: el descifrado cooperativo de un idioma generado no aparece en el mapa competitivo (comprobar en el test de frase) | Alta | **Recomendada** |
| Embajada alienígena (traducir a un embajador en directo) | Muy alta | Alta | Baja: poca acción física, se parece a un quiz | Sala especial, no finalidad |
| Atraco a una cámara acorazada alienígena | Alta | Media | Alta | Alternativa válida si el tono "aventura" no convence; mismo esqueleto |
| Cocina para un rey alienígena (recetas en glifos) | Alta | Media: recuerda a Overcooked | Media | Descartar como marco; sirve como sala |
| Criar a una criatura que solo habla su idioma | Media | Alta | Baja: sin tensión ni final | Descartar |
| Aterrizar una nave (torre de control) | Media | Baja: Spaceteam | Media | Descartar |

**Por qué la expedición y no el atraco:** la ruina justifica que haya un idioma (es de otra civilización), que cambie de sala a sala (otra época, otro dialecto) y que se aprenda por el camino. En el atraco, el idioma sería un adorno.

## 2. Fantasía, pitch y partida

**Fantasía.** Sois una expedición de arqueólogos de pacotilla que ha caído dentro de una ruina alienígena enterrada. La ruina está viva: sus puertas, puentes y mecanismos solo obedecen órdenes en su idioma, y nadie lo habla. Cada uno lleva un trozo de la piedra Rosetta. Hay que salir antes de que se agote el oxígeno.

**Pitch (12 palabras).** Escapad de una ruina alienígena descifrando su idioma, cada uno con su móvil.

**Partida = una expedición (8-12 min).**

1. **Entrada (sala tutorial, 40 s):** dos glifos con su dibujo al lado ("piedra Rosetta" en pantalla). Se aprende jugando, sin texto de reglas.
2. **4-5 salas** sacadas al azar del banco (§4), cada una de 60-120 s, sin menús entre ellas: transición de 3 s con el mapa de la ruina.
3. **Oxígeno compartido:** un único contador para toda la expedición. Cada fallo cuesta oxígeno; cada sala superada rápido lo recupera un poco. Si se agota, derrumbe, pantalla de culpable y "otra expedición" en un toque, con idioma nuevo.
4. **Núcleo (sala final, 90 s):** la ruina colapsa y mezcla las mecánicas ya vistas en esa partida. Es la "bomba" reinventada: no se desactiva nada, se escapa.

**Bucle dentro de una sala.**

1. Aparece una **inscripción** en glifos (la orden): "girar [glifo A] hasta [glifo B]", "inclinar [glifo C]", "conectar [glifo D] con [glifo E]".
2. La inscripción está en uno o dos móviles; el **diccionario** está repartido en fragmentos entre todos; los **controles** también.
3. Se habla: "¿Quién tiene el que parece un pulpo con gorro?", "¡Yo! Significa *izquierda*", "Pues gira tu rueda a la izquierda, ¡no, tu otra izquierda!".
4. Quien tiene el control actúa en su móvil (rueda, palanca, inclinar, agitar, trazar). El juego valida al instante.
5. Acierto: la ruina se mueve (puerta que se abre, puente que se levanta). Fallo: temblor, pérdida de oxígeno y una línea en la pantalla de culpable.

## 3. El móvil en el juego

**Decisión propuesta:** el móvil no es una guía, es **un objeto de la ruina**. Cada pantalla se dibuja como un panel físico (rueda de piedra, palanca, linterna, cristal), y cada acción se hace con el dedo o con el cuerpo **sosteniendo el móvil**. Ya no hay gestos de "tocarse la nariz": la voz es el canal; el móvil es el mando y la pieza.

| Interacción | Cómo se hace | Sala típica | Sensor | Fiabilidad (ver `01-investigacion/viabilidad-tecnica.md`) |
|---|---|---|---|---|
| Girar una rueda de glifos | Arrastrar en círculo | La Puerta | Táctil | Alta |
| Deslizar una palanca, mantener pulsado | Táctil | Varias | Táctil | Alta |
| Trazar un glifo | Dibujar con el dedo lo que te describen | El Escriba | Táctil + reconocedor de trazos tipo $1/$Q | Alta (reconocedores simples y conocidos) |
| Inclinar para equilibrar | Mantener el móvil nivelado o inclinado | El Puente | Giroscopio/acelerómetro | Alta en gama media; respaldo táctil para Android barato |
| Mirar alrededor (linterna) | Mover el móvil para iluminar paredes | La Cámara Oscura | Giroscopio (vista 360°) | Media: deriva en Android barato (riesgo ya señalado para el finalista B) |
| Agitar, dar golpecitos | Sacudir el móvil | Temblor (sabotaje) | Acelerómetro | Alta |
| Pasar el móvil (presencial) / lanzar (remoto) | Darle tu móvil al de al lado; en remoto, gesto de lanzar | La Reliquia | Acelerómetro + asientos de la sala | Media: necesita saber quién está a tu lado (hipótesis del brief) |
| Juntar móviles | Ponerlos uno al lado del otro y arrastrar un cable de uno a otro | Los Conductos | Táctil sincronizado | Media: depende de la latencia; en remoto pasa a puertos con nombre de glifo |
| Ritmo a la vez | Tocar en el mismo instante que otro | El Órgano | Táctil + reloj de la sala | Media: tolerancia de ±150 ms (hipótesis a medir) |
| Soplar o gritar | — | — | Micrófono | **Fuera del MVP**: no fiable en bar y choca con la voz en remoto |
| Cámara | — | — | — | **Fuera**: no aporta y complica permisos |

**Regla de diseño:** al menos la mitad de las salas de una expedición deben tener acción corporal visible desde fuera (inclinar, pasar, agitar, juntar). Es lo que compensa que ya no haya gestos (ver riesgos).

## 4. Salas: banco inicial

| Sala | Qué hay que hacer | Interacción principal | Lo que se ve desde fuera |
|---|---|---|---|
| **La Puerta** (tutorial y básica) | Poner cada rueda en el glifo que pide la inscripción | Girar rueda | Gente gritando nombres absurdos de glifos |
| **El Puente** | Mantener tablones nivelados mientras la inscripción cambia qué lado sube | Inclinar | Toda la mesa inclinando el móvil a la vez, como un ritual |
| **La Cámara Oscura** | Solo veis lo que ilumina vuestra linterna; los glifos de la pared los ve quien no los necesita | Girar el móvil alrededor | Gente barriendo el bar con el móvil |
| **El Escriba** | Uno describe un glifo; otro lo dibuja con el dedo; la ruina lo reconoce | Trazar | Al final, los dibujos lado a lado: **el momento TikTok más fuerte** |
| **Los Conductos** | Conectar tuberías que salen de un móvil y entran en otro | Juntar móviles y arrastrar | Móviles en fila sobre la mesa |
| **La Reliquia** | La inscripción va en un móvil que hay que ir pasando a quien tenga el diccionario necesario | Pasar el móvil | Un móvil volando de mano en mano |
| **El Órgano** | Tocar los glifos de la melodía en orden, cada uno en su móvil, a tiempo | Ritmo | Golpecitos sincronizados (o no) |
| **El Núcleo** (final) | Mezcla de las salas vistas, con colapso | Todas | Caos total |

**Profundidad sin reglas:** el idioma tiene gramática que aparece sala a sala, sin explicarla: un glifo dentro de un círculo significa NO; repetido, DOS VECES; girado, AL REVÉS. Se descubre fallando una vez. En cada expedición nueva, glifos nuevos y gramática recombinada: no se puede memorizar.

**Eventos y sabotajes (2-4 s):** el idioma muta (un glifo cambia de significado, heredado del C original), interferencia (la pantalla se emborrona; agitar para limpiarla), apagón (todo negro salvo la linterna), eco (tu fragmento del diccionario aparece en espejo).

## 5. De 2 a 6 jugadores

Cada sala reparte tres cosas: **inscripción**, **diccionario** y **controles**.

| Jugadores | Reparto | Quién hace qué |
|---|---|---|
| 2 | Cada uno tiene media inscripción, medio diccionario y la mitad de los controles | Todo el rato preguntándose mutuamente |
| 3 | Inscripción en uno (rota por sala); diccionario en tres fragmentos; controles en los tres | Nadie solo lee: el que tiene la inscripción también tiene controles |
| 4-6 | Diccionario en fragmentos **con solapamiento** (cada glifo está en al menos dos móviles); dos inscripciones a la vez en salas grandes | Dos "conversaciones" cruzadas en la mesa; con 6, el ruido es parte de la gracia |

**Entrar y salir (innegociable 6):**

- **Recién llegado:** entra en la siguiente sala como **porteador**: solo tiene controles, sin diccionario ni inscripción. Ejecuta lo que le dicen y aprende escuchando (hipótesis del rol de entrada del brief).
- **Se va o se desconecta a mitad de sala:** sus glifos ya estaban duplicados en otro móvil (solapamiento); sus controles quedan fijos y la sala retira las órdenes que dependían de ellos. Nadie es imprescindible.

## 6. Capa de impostor: el traductor averiado

- **Por defecto (desde 3):** en algunas salas, el fragmento de diccionario de un jugador tiene **un glifo mal traducido**, y ese jugador **no lo sabe**. Genera malentendidos con culpable inocente. Al acabar la sala: "¡El traductor de Pau estaba averiado!". Cero deducción social; pura risa.
- **Modo traición (opcional, desde 4):** el averiado sí lo sabe y gana puntos si el equipo falla sin descubrirle. Encaja con La tentación (`filtro.md`). No es saboteador fijo: cambia cada sala y casi nunca toca.

## 7. Estilo visual

| Opción | Riqueza percibida | Coste para 2 personas | Rendimiento en Android medio | Encaje con salas y giroscopio | Veredicto |
|---|---|---|---|---|---|
| 2D plano | Media | Bajo | Excelente | Bajo: el giroscopio no "mueve" nada | Insuficiente para lo que pides |
| **2.5D (capas 2D con parallax y luz)** | **Alta** | **Medio** | Muy bueno | **Alto**: cada móvil es una ventana a la sala; al inclinar, las capas se desplazan | **Recomendado** |
| 3D low-poly | Alta | Alto (modelado, cámaras, iluminación) | Medio (riesgo de calor y batería) | Alto | No compensa: la risa la pone la gente, no el render |
| 3D realista | Muy alta | Muy alto | Malo | Alto | Fuera de alcance |

**Dirección: "Expedición en tinta"**, evolución de la dirección Risografía (`03-visual/03-risografia.md`):

- **Tintas:** papel, tinta negra y **dos tintas por sala** (La Puerta azul + amarillo, El Puente rosa + verde, La Cámara Oscura negro + amarillo fluor…). Así cada sala se reconoce al instante en un clip.
- **Glifos:** trazos gordos de tinta, con forma que **sugiera algo** (una cara, un animal, una herramienta) para que sean nombrables. Generados por combinación de piezas (base + rasgo + modificador), revisados a mano.
- **Ruina:** capas de ilustración (fondo, muro, mecanismo, primer plano) con grano risográfico; las tintas desplazadas son el "temblor".
- **Paneles del móvil:** semi-físicos (piedra, latón, cristal) con sombras planas: deben parecer objetos que se tocan, no botones de app.
- **Mascota posible:** el guardián de la ruina, una mancha con un ojo que "habla" en glifos en las transiciones (heredado de "Tinta").

**Salas y mapa:** sí. La ruina es un mapa de 5-6 cámaras que se dibuja mientras avanzáis; al final de la expedición se enseña el recorrido con los fallos marcados (buen fondo para el clip).

## 8. Momento compartible

1. **El Escriba:** "lo que te describí" frente a "lo que dibujaste", lado a lado. Se entiende sin conocer el juego.
2. **El bautizo:** al final, la app enseña los glifos de la expedición y propone escribir (opcional) cómo los habéis llamado. "En nuestra ruina, esto era *el calvo con paraguas*." Contenido creado por los jugadores.
3. **Culpable:** "Querían EL TENEDOR TUERTO (izquierda); Pau giró EL PULPO (derecha)".
4. **Cámara externa:** la mesa inclinando móviles a la vez, un móvil pasando de mano en mano, gente gritando nombres absurdos.

## 9. Presencial y remoto

- **Presencial:** voz en la mesa; ruido de bar sin problema (decodifica una persona). Salas físicas completas (pasar, juntar).
- **Remoto:** voz por llamada (de la app o externa). Pasar el móvil se convierte en lanzar; juntar móviles, en puertos con nombre de glifo. **Mejora clara sobre el C original**, que perdía los gestos en remoto.

## 10. Test de diferenciación

| Parecido | Qué comparte | Por qué no es "lo mismo pero" |
|---|---|---|
| Keep Talking (módulo de teclado) | Describir símbolos raros en voz alta | No hay experto con manual ni artificiero: todos tienen controles **y** un trozo del idioma; el idioma tiene gramática, se aprende y cambia; las acciones son físicas y pasan entre móviles |
| We Were Here, Escape Simulator | Escape cooperativo por salas | Partidas de 10 min generadas, sin puzles de un solo uso; 2-6 en la misma mesa con un móvil cada uno |
| Spaceteam | Paneles en cada móvil, órdenes que viajan | Las órdenes no se leen en castellano: hay que descifrarlas entre todos |
| Chants of Sennaar (un jugador) | Descifrar un idioma inventado | Es cooperativo, rápido, de fiesta y generado por partida |

## 11. Riesgos

1. **"Keep Talking en móvil".** El parecido con el módulo de teclado es real. Mitigación: que el gancho sea el descifrado y el bautizo, no la urgencia. Test: decir el pitch a 5 personas que conozcan KTANE; si 3 dicen "es como Keep Talking", hay que repensar.
2. **Coste de contenido.** Ocho salas son ocho minijuegos. MVP con **3 salas** (La Puerta, El Puente, El Escriba) + Núcleo simple. Es más caro que el C original y que A · La mudanza.
3. **Cámara externa más pobre que con gestos.** Mitigación: regla de "mitad de salas con cuerpo" (§3).
4. **Glifos difíciles de describir para algunas personas** (dislexia, baja visión). Glifos grandes, codificados por forma y no solo por color; opción de nombre sugerido.
5. **Cero explicación con varias interacciones distintas.** Cada sala debe enseñarse sola en sus primeros 5 s (una inscripción de un solo glifo).
6. **Sincronía.** El Puente y El Órgano piden estado en tiempo real (10-20 Hz), como A. El C original solo necesitaba eventos.

## 12. Prueba en papel (20 minutos)

**Material:** 12 glifos dibujados a rotulador en tarjetas (formas raras pero nombrables), una hoja de diccionario por jugador con 3-4 entradas (glifo = significado: izquierda, derecha, arriba, rojo, azul, NO, dos veces), tarjetas de inscripción con 2-3 glifos, tres objetos de colores en la mesa, un cronómetro.

1. Ronda 1 (La Puerta en papel): una persona tiene la inscripción y nadie más la ve; los demás tienen fragmentos del diccionario. Hay que ejecutar la orden con los objetos (mover el rojo a la izquierda, dos veces). 90 s.
2. Ronda 2 (El Escriba): uno describe un glifo que solo él ve; otro lo dibuja. Se comparan.
3. Ronda 3: se introduce "glifo en círculo = NO" sin explicarlo. ¿Lo descubren?
4. **Medir:** tiempo hasta el primer acierto, cuántos nombres inventados salen, fallos que hacen reír frente a fallos que frustran, y cómo lo describe alguien que mira desde fuera (si dice "Keep Talking" o "charadas", alerta).

## Implicaciones para nuestro juego

- C2 deja de ser "plan B barato" y pasa a competir con A · La mudanza en fantasía y riqueza visual, a cambio de más coste de contenido.
- Si se aprueba, la dirección visual recomendada para C (Risografía) se mantiene, evolucionada a 2.5D con dos tintas por sala.
- La decisión de motor (`viabilidad-tecnica.md`) no cambia: 2.5D con parallax es viable en web + Capacitor y en Godot 4; el reconocedor de trazos y el giroscopio son los puntos a medir.
- Pendiente de decidir (ver `../DECISIONES.md`): si C2 sustituye a C, si pasa a prueba en papel junto a A, y la finalidad.
