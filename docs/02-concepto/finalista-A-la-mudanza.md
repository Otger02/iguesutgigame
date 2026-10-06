# Finalista A · La mudanza

> Nombre provisional. Semilla S1 con la entrega al vecino de S2, la capa social de S8 y la interferencia de S10 incorporadas como opcionales.

## Fantasía, pitch y bucle

**Fantasía y tema.** Sois una empresa de mudanzas de poca confianza. Cada mueble tiene varias asas y cada móvil es una de ellas. Hay que meter el piano, el sofá, la pecera o la tarta de boda por puertas estrechas, escaleras, vecinos que se asoman y un gato que se cruza. Tono: comedia física, nada de bombas ni cuenta atrás con explosión; si falla, el mueble se rompe y alguien tiene la culpa.

**Pitch (12 palabras).** Cada móvil es un asa: subid el piano entre todos sin que caiga.

**Bucle de una ronda (60-75 s, "un tramo").**

1. La pantalla muestra el mueble, tu asa resaltada y el nivel: inclinar el móvil levanta o baja tu extremo. Cero texto.
2. El mueble avanza solo mientras esté equilibrado; se tambalea cuando no; cae si la inclinación supera el límite durante un segundo. Culpable automático: el asa que se movió.
3. En el camino aparecen obstáculos que exigen moverse a la vez o en orden: escalón (todos suben), puerta baja (todos bajan), giro (primero uno, luego otro), gato (agitar), vecina (congelarse 3 s), suelo mojado (controles invertidos 3 s).
4. **Información repartida natural:** el asa de delante ve el camino y los obstáculos; el asa de atrás ve el nivel con detalle y lo frágil que está el mueble. El de delante tiene que avisar; el de atrás tiene que obedecer y mantener.
5. Entrega: el mueble llega a su sitio; aparece el siguiente, con parejas nuevas, sin menú. Objetivo de ronda: entregar N muebles antes de que el camión se vaya.

## Roles y escalado de 2 a 6

| Jugadores | Reparto | Quién hace qué |
|---|---|---|
| 2 | Un mueble de dos asas | Delante (ve el camino) y atrás (ve el nivel); cambian en cada mueble |
| 3 | Piano de tres asas, o sofá (2) + caja frágil (1) | La tercera asa ve la "fragilidad"; la caja solitaria se lleva en equilibrio puro |
| 4 | Dos parejas con dos muebles a la vez | Dos tramos en paralelo; se pueden pasar una caja entre parejas (al vecino real) |
| 5 | Trío + pareja | Los repartos rotan en cada mueble para que nadie repita compañero |
| 6 | Tres parejas o dos tríos | Entregas cruzadas: una caja sale de una pareja y la recibe otra |

Nunca hay turnos: en cualquier instante todas las manos sujetan algo.

## Frescura y aprendizaje

- **Fresco:** casas, recorridos, muebles y obstáculos generados por ronda a partir de piezas (pasillo, escalera, puerta, balcón) y modificadores (lluvia, perro, mudanza nocturna). Lo que se aprende es el vocabulario físico (subir, bajar, girar, congelarse), no soluciones. Los móviles distintos y los compañeros distintos hacen que cada tramo sea nuevo.
- **Recién llegado:** entra como asa de atrás en el siguiente mueble. Solo tiene que mantener el móvil nivelado y hacer lo que le gritan. Aprende el resto viendo caer un piano.

## Entrar y salir

- Unirse: entre muebles, con QR o enlace; recibe asa en el siguiente reparto.
- Irse: su asa pasa a "carrito" (el mueble sigue, más lento y más torpe) y el reparto siguiente ya no cuenta con él.
- Desconexión a mitad de tramo: igual que irse, con 5 s de margen para volver y recuperar el asa.
- Nadie es imprescindible: ningún mueble exige a una persona concreta; cualquier asa es sustituible por el carrito.

## Sensores y sabotajes

| Sensor | Uso | Por qué |
|---|---|---|
| Giroscopio y acelerómetro | Inclinación del asa (centro del juego); agitar para espantar al gato; congelarse ante la vecina | Es la mecánica; sin él no hay juego. Respaldo para móviles sin giroscopio: acelerómetro solo (menos fino) |
| Micrófono | Opcional: "gritad ¡ya va!" cuando suena el timbre; soplar el polvo de un mueble | Tontería vocal visible desde fuera; nunca obligatorio (si no hay permiso, se sustituye por toque) |
| Cámara | No | No aporta nada al acoplamiento y pesa en rendimiento y permisos |

**Sabotajes** (cortos, aleatorios, 2-4 s): gato, vecina (congelación medida por acelerómetro), suelo mojado (controles invertidos), apagón de la escalera (solo el de atrás ve el nivel; el de delante va a ciegas 3 s), caja que cae de otra pareja y hay que esquivar. **Capa social opcional desde 3 jugadores (La tentación):** el móvil ofrece en privado "si este mueble se rompe en 10 s, ganas 3 puntos"; si alguien te señala a tiempo, los puntos son suyos.

## Momento compartible y cámara externa

- **El momento:** la caída. Al romperse un mueble, 2 s de cámara lenta en todas las pantallas con la gráfica de las dos asas y el culpable en grande ("Ana bajó su lado 40°"). Clip vertical automático de los últimos 8 s con la escena del juego (sin caras por defecto) y el nombre de la app; con permiso, grabación de la cámara frontal del culpable.
- **Cámara externa:** dos personas moviendo los brazos en espejo, una gritando "¡escalón!" y la otra agachándose tarde; se entiende sin ver pantallas porque el cuerpo cuenta la historia. Gesto propio imitable: "sujetar el piano" con el móvil en horizontal y las dos manos.

## Presencial y remoto

- **Presencial:** las parejas se forman con vecinos reales (paso opcional de asientos al crear la sala) para que se vean las manos; pasar cajas entre parejas sigue el orden de la mesa.
- **Remoto:** mecánica idéntica; las parejas se forman por orden de entrada; voz por la app (modo remoto) o por la llamada que ya tenga el grupo. No se pierde nada esencial: el acoplamiento es virtual.

## Test de diferenciación

| Parecido | Qué comparte | Por qué no es "lo mismo pero" |
|---|---|---|
| Cooperativos físicos de PC (Moving Out, Chained Together, PEAK) | Cargar o depender físicamente del otro; fallo gracioso | Sin mando ni pantalla compartida; el cuerpo real sujeta un asa real; móvil, gratis, 2-6, en un bar |
| Spaceteam | Cada uno con su móvil, gritos, rondas cortas | No hay paneles ni órdenes en pantalla; lo que se grita es "sube" y "baja" sobre un objeto compartido; control continuo, no botones |
| Keep Talking / BOMBANANA! | Uno ve lo que el otro no (camino frente a nivel) | No hay manual, ni módulos, ni roles sensoriales fijos; la información repartida nace de la posición en el mueble y cambia en cada entrega |

## Riesgos principales

1. **Sensación de acoplamiento con latencia real:** si el extremo del compañero llega con más de 150 ms de retraso, el mueble parece "flotar". Mitigación: predicción local y tolerancia; validar en prototipo digital con 2 móviles por 4G.
2. **Calibración entre móviles distintos** y posturas distintas (sentado, de pie): calibrar "nivel" al coger el asa (2 s).
3. **Fatiga de brazos** en sesiones largas: tramos de 60-75 s y muebles ligeros entre pesados.
4. **Que la fantasía se perciba como "minijuego de equilibrio":** la profundidad tiene que venir de obstáculos que exijan coordinación en orden, no solo nivel.

## Prueba en papel (15 minutos, esta semana)

**Material:** una bandeja o tabla rígida (o un libro grande), un vaso de plástico con agua hasta la mitad (o una pelota), cojines, dos sillas, un móvil con cronómetro.

**Reglas:**

1. Dos personas sujetan la bandeja por los extremos con una mano cada una; el vaso va encima. Si se cae o se derrama, el mueble se ha roto: culpable es quien movió la mano (lo decide el resto a gritos).
2. **Información repartida:** el de atrás camina de espaldas y no puede mirar atrás; el de delante ve el recorrido y tiene que avisar.
3. Recorrido de 60 s por el salón: pasar entre dos sillas juntas (puerta estrecha), subir a un cojín y bajar (escalón), pasar por debajo de una mesa o de un brazo estirado (puerta baja), dar una vuelta completa (giro).
4. Una tercera persona hace de "vecina": cuando grita "¡vecina!" los dos se congelan 3 s; quien se mueva, pierde.
5. Con 4-6 personas: dos o tres bandejas a la vez por el mismo recorrido; al cruzarse, una pareja tiene que ceder el paso. Rotar parejas cada entrega.

**Qué medir:** entregas en 60 s, caídas, cuántas veces se repite sin que lo pidamos, y si alguien que no estaba entiende el vídeo de 15 s grabado con otro móvil.
