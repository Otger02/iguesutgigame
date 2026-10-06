# Dirección visual 2 · Neón de bar

**En una línea.** Noche de bar: fondo azul casi negro y todo lo importante dibujado como tubos de neón de un solo trazo que brillan; texto de tiza; lo que no brilla no importa. Página de muestra: `02-neon-de-bar.html`.

**Encaja mejor con:** B · Bichos alrededor (los bichos son luces en la oscuridad y el mapa de 360° es un rótulo). Funciona bien con C · Idioma inventado (los signos como rótulos de neón que se encienden y apagan). Con A · La mudanza encaja peor: los muebles necesitan volumen y peso, y el neón es puro contorno.

## Referencias

- Rótulos de neón de bares y de ferias; señalética nocturna; pizarras de tiza con el menú.
- Carteles de concierto con un solo trazo luminoso sobre negro; iconografía de "línea continua".
- Juegos de arcade de vectores (líneas brillantes sobre negro) como memoria lejana, no como estética retro: aquí el trazo es grueso, redondeado y actual.

Comprobación de parecido: Liar's Bar es 3D realista y oscuro (otro mundo); Spaceteam es panel retro con botones; BOMBANANA! es cartoon 3D luminoso; Among Us y Splash son planos y pastel. Ningún juego del mapa usa neón de contorno. Riesgo de parecido: con la estética "synthwave" genérica (degradado morado-azul con rejilla): se evita prohibiendo degradados de fondo y la rejilla.

## Legibilidad en pantalla pequeña

- Contraste máximo: neón sobre noche (amarillo #FFE34D sobre #0E1026 ≈ 14:1; cian ≈ 12:1; rosa ≈ 6:1, reservado a elementos grandes).
- El trazo de 4-6 px con extremos redondos se lee a 120 px de ancho; el resplandor ayuda a separar figura de fondo.
- Texto de tiza (#F2F2F0) para todo lo largo; los neones solo en titulares y estados.
- Riesgo: pantallas al sol en una terraza. El fondo oscuro pierde, pero el trazo brillante sigue siendo lo que mejor sobrevive; aun así esta dirección es "de noche" y hay que asumirlo.

## Potencial en TikTok

- El neón sobre negro es lo que mejor sobrevive a la compresión de vídeo y a grabar una pantalla de noche con otro móvil: se ve el mapa y la red aunque el bar esté oscuro.
- Los clips de noche en bar (donde se juega) coinciden con la estética: no hay salto entre lo que se graba y lo que sale en pantalla.
- Gesto visual propio: "la red" (móvil en alto con dos manos) y el mapa de 360° de la repetición, que es un gráfico que explica el chiste sin palabras.

## Personaje o mascota

**La Polilla**: una polilla de neón amarillo con gafas de sol que siempre va hacia la luz equivocada. Potencial medio-alto: contorno de un trazo (se dibuja en un gesto), expresiva por la posición de las antenas y las gafas, y con un rasgo de carácter (torpe, atraída por lo que no debe) que se puede explotar en animaciones de carga y en el culpable. Es menos "abrazable" que una mascota con volumen: como cara de marca funciona mejor como logotipo luminoso que como peluche.

## Coste de producción (2 personas con ayuda de IA)

| Partida | Esfuerzo | Cómo |
|---|---|---|
| Sistema visual | 2 días | Pocos componentes: trazo, resplandor, texto de tiza |
| Mascota y 6 poses | 2 días | Líneas vectoriales; el resplandor es un efecto, no se dibuja |
| 15-20 bichos | 2-3 días | Un trazo cada uno; variantes por alas y patas |
| Mapa de 360° y brújula | 1-2 días | Gráfico procedural (código), no ilustración |
| Animación | 2 días | Parpadeos, encendidos y apagados; pocos fotogramas |
| Pantallas de culpable, sala y QR | 1-2 días | Componentes de la interfaz |

Total orientativo: 2 semanas de una persona a tiempo parcial. Es barata porque casi todo es línea y el resplandor lo pone el motor; el coste oculto es el rendimiento del brillo en Android de gama media (hay que pre-renderizar).

## Accesibilidad

- Cada color tiene forma y comportamiento propios: rosa = red redonda (tú); cian = cuadrado (compañero); amarillo = alas (bicho); violeta = parpadeo (interferencia). Nada depende solo del color.
- Contrastes altos por diseño; el rosa se usa solo en elementos grandes (red, botón).
- Daltonismo: amarillo y cian se distinguen incluso en deuteranopia; rosa y violeta se distinguen por forma y parpadeo.
- Fotosensibilidad: nada parpadea más de 3 veces por segundo; `prefers-reduced-motion` desactiva pulsos.
- Audio: cada estado tiene sonido propio, pero ninguna mecánica depende del sonido (el bar es ruidoso).

## Implicaciones técnicas

- **2D con efecto de resplandor.** En Godot 4, un CanvasItem con "glow" en el entorno 2D cuesta poco en gama media si el número de luces es bajo; alternativa segura: sprites con el brillo horneado. En web + Capacitor, `filter: drop-shadow` o `box-shadow` sobre SVG se vuelve caro con muchos elementos; mejor sprites PNG con el brillo incluido o un canvas con PixiJS y un filtro de bloom de baja resolución.
- El mapa de 360° es código (procedural), no assets: barato y escala a cualquier número de jugadores.
- Peso muy bajo: líneas vectoriales y unos pocos PNG de brillo.
- La brújula y la "vista 360°" dependen del giroscopio; esta dirección no cambia eso, pero sí hace que el mundo sea "oscuro" por defecto, lo que disimula la falta de escenario (no hace falta dibujar el bar).

## Tres prompts para concept art con IA

1. "Ilustración de neón: sobre un fondo azul noche liso, una polilla dibujada con un solo tubo de neón amarillo brillante, con gafas de sol de neón blanco, volando hacia una bombilla apagada; trazo grueso de extremos redondeados, resplandor suave, sin degradados de fondo, sin rejilla, estilo rótulo de bar, vista frontal, apto para logotipo."
2. "Pantalla de juego para móvil en vertical, estética de rótulo de neón sobre fondo azul casi negro: una red de cazar mariposas dibujada en neón rosa en el centro, una brújula circular arriba con puntos amarillos brillantes, un bicho de neón amarillo borroso a la derecha, un aviso en tiza blanca; texto grande redondeado; sin 3D, sin degradados."
3. "Grupo de amigos en un bar de noche visto desde fuera: cada uno levanta el móvil hacia un sitio distinto del techo y la pared, uno señala con el brazo y grita, las pantallas de los móviles brillan en rosa y amarillo; estilo ilustración de línea con acentos de neón, fondo oscuro, humor, sin caras detalladas."
