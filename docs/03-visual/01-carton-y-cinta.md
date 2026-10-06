# Dirección visual 1 · Cartón y cinta

**En una línea.** Todo está recortado de una caja de mudanza y pegado con cinta de embalar: figuras planas con sombra dura, textura de cartón, rotulador grueso y movimiento de stop-motion. Página de muestra: `01-carton-y-cinta.html`.

**Encaja mejor con:** A · La mudanza (es literalmente su mundo). Funciona también con B · Bichos alrededor (bichos de cartón con alas de papel) y con C · Idioma inventado (signos como pegatinas de embalaje), pero en A es donde la fantasía y el estilo son la misma cosa.

## Referencias

- Animación en recorte de papel y stop-motion con cartón (el imaginario de los cortos de papel y de los anuncios hechos con cajas): planos, imperfecciones de corte, sombra de papel sobre papel.
- Rotulación de cajas de mudanza y de mercado: rotulador negro grueso, cinta amarilla, pegatinas "frágil" con rayas.
- Juegos de mesa de cartón troquelado: la estética de las fichas con borde de cartón visible.

Comprobación de parecido: BOMBANANA! es 3D cartoon con monos y amarillo plátano; Among Us es vectorial plano con personajes cápsula; PEAK es low-poly 3D; Splash es interfaz plana pastel; Spaceteam es panel retro. Ninguno usa cartón, cinta ni stop-motion. El riesgo de parecido es con juegos de puzle "de papel" genéricos (tipo recortables), bajo.

## Legibilidad en pantalla pequeña

- Formas grandes, sin degradados, contornos de 4 px: se lee a 120 px de ancho (miniatura de TikTok).
- Máximo tres colores por pantalla sobre fondo cartón uniforme.
- Titulares en Bungee (mayúsculas, sin descendentes problemáticas) y números tabulares a 30 px o más.
- Riesgo: la textura de cartón puede ensuciar el contraste; se aplica solo a planos grandes y nunca detrás de texto.

## Potencial en TikTok

- La estética "cosa hecha a mano" transmite "esto lo ha hecho gente, no una fábrica": encaja con el tono de los virales de 2025 (friendslop, Impostor) donde el producto es la reacción del grupo.
- El fondo cartón uniforme hace que cualquier texto sobreimpreso (el "él tenía que…" de los dos primeros segundos) se lea sin caja.
- Gesto propio visual: la cinta amarilla inclinada como sello de "lo tuyo" se puede usar en los clips, en las pegatinas de la app y en merchandising barato (cinta de embalar real).

## Personaje o mascota

**La Caja**: una caja de mudanza con patas, dos ojos de rotulador y una tira de cinta por boca. Potencial alto: es una silueta reconocible a cualquier tamaño, se dibuja en diez segundos (la puede imitar cualquiera en un comentario), expresa emociones con la cinta (recta, torcida, arrancada) y cuando algo se rompe aparece mareada. Es neutra en género, especie y cultura, y no se parece a ninguna mascota del mapa competitivo. Variante: cajas de tamaños distintos para avatares (cada jugador es una caja con su etiqueta).

## Coste de producción (2 personas con ayuda de IA)

| Partida | Esfuerzo | Cómo |
|---|---|---|
| Sistema visual (paleta, tipos, componentes) | 2-3 días | Figma con el token set de la página HTML |
| Mascota y 6 poses | 2-3 días | Boceto propio + IA para explorar + limpieza vectorial |
| 20-30 muebles y obstáculos | 3-4 días | Formas vectoriales simples; la textura de cartón es una sola imagen tileable |
| Escenario generado (piezas de casa) | 2 días | 10-12 piezas modulares (pasillo, escalera, puerta, balcón) |
| Animación | 2-3 días | Stop-motion a 12 fps con 2-4 fotogramas por acción; sin rigs |
| Pantallas de culpable, sala y QR | 1-2 días | Componentes de la propia interfaz |

Total orientativo: 2-3 semanas de una persona a tiempo parcial. Es la dirección más barata de las cuatro porque todo es plano, con pocos fotogramas y sin iluminación.

## Accesibilidad

- Ninguna mecánica depende solo del color: tuyo = cinta, compañero = pinza, peligro = rayas, acierto = tick, culpable = fondo rojo más texto y mascota mareada.
- Contraste: rotulador sobre cartón (#2B2118 sobre #C9A46A) ≈ 7:1; rotulador sobre cinta ≈ 10:1. El rojo de cartel solo lleva texto claro (#F3EBDC) y grande.
- Daltonismo: rojo y azul se distinguen por forma (cinta frente a pinza; línea continua frente a discontinua en la gráfica de culpable).
- Movimiento: la animación en pasos no marea; se respeta `prefers-reduced-motion` para quitar el balanceo.

## Implicaciones técnicas

- **2D puro**, sprites planos con una textura multiplicada. Vale para Godot 4 (nodos 2D, CanvasItem con material de multiplicación) y para web + Capacitor (PixiJS o incluso DOM/SVG para la interfaz).
- Peso muy bajo: formas vectoriales (SVG) y una textura de 512 px; cabe en el objetivo de < 20 MB del invitado.
- La "sombra dura desplazada" es un offset, no un filtro: barata en WebView.
- El stop-motion a 12 fps se hace con spritesheets pequeños; no hace falta esqueleto ni física visual (la física del mueble es lógica del juego, no del render).

## Tres prompts para concept art con IA

1. "Ilustración de recorte de papel y cartón: dos personas de cartón cargan un sofá rojo por una escalera estrecha, una lo lleva alto y la otra bajo, el sofá se inclina peligrosamente; cinta de embalar amarilla, rotulador negro grueso, sombras duras de papel, fondo de cartón liso, estilo stop-motion, sin texto."
2. "Mascota para una app de juegos: una caja de mudanza de cartón con patas cortas, dos ojos de rotulador y una tira de cinta de embalar amarilla torcida como boca, expresión de pánico porque se tambalea; estilo recortable plano, contorno negro grueso, fondo de un solo color, vista frontal, apto para icono de app."
3. "Pantalla de juego para móvil en vertical, estilo recortable de cartón: un pasillo de casa con un escalón marcado con rayas amarillas y negras, un piano de cartón sostenido por tres asas con pinzas de colores, un nivel de carpintero en la parte baja; interfaz con cinta de embalar como botones, tipografía gruesa de rotulación, sin degradados."
