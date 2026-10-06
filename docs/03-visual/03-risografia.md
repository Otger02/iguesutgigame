# Dirección visual 3 · Risografía

**En una línea.** Un fanzine impreso en risografía: dos o tres tintas planas por pantalla, grano visible, tintas ligeramente desplazadas y formas gordas de rotulador; titulares enormes en mayúsculas. Página de muestra: `03-risografia.html`.

**Encaja mejor con:** C · Idioma inventado (los signos son pegatinas de tinta y el fallo "quería decir / entendiste" es un cartel). Funciona bien con A · La mudanza (muebles como figuras de dos tintas; el culpable como portada de fanzine). Con B · Bichos alrededor encaja peor: la vista 360° y los bichos en movimiento piden luz y profundidad, y la risografía es estática por naturaleza.

## Referencias

- Impresión risográfica: carteles y fanzines a dos tintas (azul, rosa fluor, amarillo), con el registro imperfecto y el grano del tambor.
- Cartelería de conciertos y de fiestas de barrio: tipografía negra gorda, un color de acento, papel visible.
- Pictogramas de señalética y pegatinas de reparto: formas simples que se reconocen a un metro.

Comprobación de parecido: ningún juego del mapa usa estética de impresión. Gartic Phone es garabato digital (otro registro); Splash es interfaz plana pastel; Jackbox tiene estilos distintos por juego pero todos digitales. El riesgo es parecerse a "apps de diseño con estética indie" en general, no a un competidor.

## Legibilidad en pantalla pequeña

- Titulares en Archivo Black en mayúsculas: se leen a 120 px de ancho incluso con el desplazamiento de tintas (que se reserva a textos grandes).
- Dos tintas por pantalla obligan a jerarquías claras: fondo papel, tinta principal, acento.
- Riesgo: el grano y el desplazamiento ensucian el texto pequeño; se prohíben en cuerpos menores de 18 px.
- Contraste: negro sobre papel ≈ 16:1; papel sobre azul riso ≈ 5:1 (solo en titulares grandes); negro sobre amarillo ≈ 15:1.

## Potencial en TikTok

- Es la dirección que mejor produce "texto en pantalla en los dos primeros segundos": el propio juego ya habla en carteles ("QUERÍA DECIR SALTA").
- La estética de fanzine señala "hecho por gente, no por una empresa", que es el tono que los virales de 2025 premian.
- Riesgo: es menos "espectacular" en movimiento que las otras tres; en un clip la gracia la pone la gente, y eso es exactamente lo que pide el brief, pero el vídeo del juego solo no engancha.

## Personaje o mascota

**Tinta**: una mancha de tinta azul con su fantasma rosa desplazado, ojos mal registrados y una boca que no coincide con lo que dice. Potencial medio: es muy fácil de dibujar e imitar (una mancha y dos ojos) y expresa la esencia del juego (decir una cosa y hacer otra), pero una mancha es menos memorable que una figura con silueta propia. Se puede reforzar dándole una forma fija reconocible (siempre la misma mancha) y un accesorio (una boina de impresor).

## Coste de producción (2 personas con ayuda de IA)

| Partida | Esfuerzo | Cómo |
|---|---|---|
| Sistema visual | 1-2 días | Dos tintas y una trama: el sistema más simple de los cuatro |
| Mascota y 6 poses | 1-2 días | Formas vectoriales; el desplazamiento es un efecto de código |
| Banco de 40-60 signos (icono + forma) | 3-4 días | Pictogramas vectoriales; la IA ayuda a explorar y después se unifican a mano |
| Pantallas de cartel (objetivo, fallo, culpable) | 2 días | Son tipografía y bloques; lo caro es que la composición automática quede bien con textos de longitud variable |
| Animación | 1 día | Casi nada: aparecer, desplazar tintas, temblar |
| Sala, QR, menús | 1-2 días | Componentes de interfaz |

Total orientativo: 1,5-2 semanas de una persona a tiempo parcial. Es la más barata en ilustración y la más exigente en tipografía y maquetación automática (los textos cambian de longitud y de idioma).

## Accesibilidad

- La restricción de dos tintas obliga a codificar todo por forma: cada signo tiene una forma geométrica (círculo, cuadrado, triángulo, trama de rayas) además de un color y un icono.
- Tú = azul y borde continuo; el otro = rosa y borde discontinuo; objetivo = amarillo y marco grueso; culpable = fondo rojo más texto.
- Daltonismo: azul y rosa se distinguen por luminancia y por el patrón de borde; amarillo y rojo se distinguen porque el rojo es siempre fondo completo y el amarillo un bloque.
- Texto: tamaños grandes por diseño; sin grano en cuerpos pequeños.

## Implicaciones técnicas

- **2D plano**: es la dirección más ligera. Vale para web + Capacitor (incluso con DOM y SVG, sin motor de juego) y para Godot 4.
- El desplazamiento de tintas es un segundo dibujo del mismo vector con offset; el grano es una textura tileable con mezcla de multiplicación. Ambos baratos.
- Peso mínimo: vectores y una textura; es la que más fácil cumple el objetivo de < 20 MB.
- Localización: los carteles con texto grande exigen que la maquetación se adapte a palabras largas (alemán, portugués); conviene diseñar con el idioma más largo desde el principio.
- Limitación: no tiene profundidad ni "juice" físico; si el concepto final es A o B, habrá que añadir movimiento de cámara y partículas con cuidado para no romper el estilo.

## Tres prompts para concept art con IA

1. "Cartel impreso en risografía a dos tintas (azul cobalto y rosa fluorescente) sobre papel crema con grano visible: una mancha de tinta con dos ojos que no coinciden y una boca torcida, las tintas ligeramente desplazadas; tipografía negra muy gruesa en mayúsculas que dice 'QUERÍA DECIR SALTA'; sin degradados, sin sombras, estilo fanzine."
2. "Pantalla de juego para móvil en vertical con estética de impresión risográfica: un bloque amarillo con el texto 'LEVANTA EL MÓVIL ×2', debajo cuatro filas de un diccionario con pictogramas grandes (nariz, explosión, alas, silbido) cada uno dentro de una forma distinta (círculo azul, cuadrado rosa, triángulo amarillo, círculo con rayas); papel crema con grano, tinta desplazada en los títulos, sin degradados."
3. "Ilustración a tres tintas de un grupo de seis personas alrededor de una mesa de bar, cada una haciendo un gesto exagerado distinto (tocarse la nariz, aletear, señalar) con el móvil en la otra mano; figuras como manchas de tinta con brazos de línea gruesa, registro imperfecto, papel visible, humor, sin caras detalladas, estilo cartel de fiesta de barrio."
