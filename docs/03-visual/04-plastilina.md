# Dirección visual 4 · Plastilina

**En una línea.** Todo parece modelado con los dedos: figuras rechonchas con huellas, bordes imperfectos, colores de bote de plastilina y luz suave de mesa de taller; lo que falla se aplasta, lo que gana se hincha. Página de muestra: `04-plastilina.html`.

**Encaja mejor con:** A · La mudanza (muebles con peso que se aplastan al caer) y B · Bichos alrededor (bichos blandos de cuerpo redondo). También con C · Idioma inventado, aunque allí el valor de la plastilina (volumen, aplastar) se aprovecha menos. Es la dirección más universal y la de mayor coste.

## Referencias

- Animación de plastilina (stop-motion de arcilla): figuras bajas y anchas, huellas visibles, luz de estudio cálida.
- Juguetes de modelar y manualidades de colegio: colores de bote, mezclas "sucias", piezas que no encajan del todo.
- Fotografía de producto de objetos blandos: sombra de contacto suave, sin contornos.

Comprobación de parecido: BOMBANANA! es 3D cartoon pulido (plástico, no plastilina); PEAK es low-poly; Among Us es plano; Splash es interfaz plana. No hay plastilina en el mapa competitivo. El riesgo es parecerse al género "casual 3D blandito" de las tiendas (puzles con ojos enormes); se evita con las huellas, las imperfecciones y la prohibición de ojos gigantes.

## Legibilidad en pantalla pequeña

- Figuras bajas y anchas con mucha masa de color: se leen bien a 120 px.
- Sin contornos negros: la separación figura-fondo depende de la luz y la sombra de contacto; en pantallas al sol pierde algo frente a las direcciones con contorno.
- Titulares en Baloo 2 con sombra de "grosor": legibles y en la misma lógica de volumen.
- Riesgo: demasiadas figuras blandas juntas se convierten en una masa; regla de máximo tres figuras por escena.

## Potencial en TikTok

- Aplastar y estirar es el lenguaje visual más "gracioso" de los cuatro; la pantalla de culpable (alguien aplastado) funciona como meme por sí sola.
- La mascota es la más "abrazable" y la más fácil de convertir en pegatinas, filtros y merchandising.
- Riesgo: el aspecto "blandito" puede leerse como infantil; el tono lo tienen que poner el humor y el texto, no la estética.

## Personaje o mascota

**Bola**: una bola de plastilina terracota con dos huellas de pulgar y una cara mínima, que cambia de forma según el estado de la partida (redonda en calma, alargada nerviosa, aplastada culpable). Potencial alto: silueta reconocible, expresividad por forma en vez de por cara, apta para icono de app, pegatina y filtro de TikTok, y neutra en género, especie y cultura. Es la mejor candidata a cara de marca de las cuatro direcciones.

## Coste de producción (2 personas con ayuda de IA)

| Partida | Esfuerzo | Cómo |
|---|---|---|
| Sistema visual | 2-3 días | Luz, sombra de contacto y huella como componentes reutilizables |
| Mascota y 8 formas | 3-4 días | Modelar una vez (Blender o Spline) y renderizar sprites, o ilustración 2D con sombreado; la IA ayuda en exploración, no en coherencia |
| 20-30 muebles, obstáculos o bichos | 5-7 días | Cada objeto necesita volumen y sombreado; es la partida cara |
| Escenario | 2-3 días | Suelo y pared con luz; piezas modulares |
| Animación | 3-5 días | Aplastar y estirar por acción; si es 2.5D con sprites, varias direcciones por objeto |
| Pantallas, sala, QR | 2 días | Componentes de interfaz con el mismo lenguaje de volumen |

Total orientativo: 4-5 semanas de una persona a tiempo parcial. Es la dirección más cara (el doble que Cartón y cinta) porque el volumen hay que fabricarlo para cada objeto.

## Accesibilidad

- Tú = huella de pulgar; compañero = bolita encima; objetivo = borde mantequilla; interferencia = pellizco; culpable = aplastado. Nada depende solo del color.
- Daltonismo: terracota y menta se distinguen por luminancia; además, huella y bolita son formas.
- Contraste: arcilla oscura (#33302E) sobre mantel (#FFF4E3) ≈ 12:1; texto claro sobre terracota ≈ 4,6:1 (solo en tamaños grandes).
- Sin contornos: hay que vigilar que la sombra de contacto siempre exista para separar figuras del fondo.

## Implicaciones técnicas

- **2.5D o 3D ligero.** Dos caminos: (a) sprites pre-renderizados desde Blender o Spline con material de arcilla (cámara ortográfica, 4-8 direcciones por objeto); (b) 3D real en Godot 4 con un material "matcap" de plastilina y luz fija. (a) es más ligero y predecible en Android de gama media; (b) da aplastar y estirar gratis (escalado del modelo) pero añade peso y riesgo de rendimiento.
- Es la única dirección donde Blender tiene sentido como herramienta principal (modelar y exportar sprites o glTF), y donde las herramientas de IA para 3D (Meshy, Tripo) pueden ahorrar tiempo con limpieza posterior.
- Peso: los sprites de volumen pesan más que los vectores; hay que vigilar el objetivo de < 50 MB y cargar escenarios en segundo plano.
- Motor: inclina la balanza hacia Godot 4 (2.5D o 3D ligero); en web + Capacitor es viable con sprites pre-renderizados y PixiJS, no con 3D en tiempo real.

## Tres prompts para concept art con IA

1. "Fotografía de stop-motion de plastilina: una bola de plastilina color terracota con dos huellas de pulgar visibles y una cara mínima (dos puntos y una línea), sobre un mantel crema, luz cálida de estudio desde arriba a la izquierda, sombra de contacto suave; tres versiones: redonda y tranquila, alargada y nerviosa, aplastada contra la mesa; sin contornos, sin brillo de plástico."
2. "Escena de plastilina vista desde arriba en formato vertical para móvil: dos figuras bajas y anchas de plastilina cargan un sofá terracota por un pasillo de plastilina, una lo levanta alto y la otra bajo, el sofá se dobla; un gato lavanda pellizcado se cruza; huellas de dedo en todas las piezas, luz suave, colores de bote de plastilina (terracota, menta, mantequilla, lavanda), sin texto."
3. "Pantalla de resultado de un juego de móvil con estética de plastilina: un piano negro de plastilina aplastando a una figura amarilla que asoma por debajo con cara resignada, fondo terracota liso, titular grande redondeado que dice '¡Aplastado!', un botón amarillo en forma de churro; sombras de contacto suaves, huellas visibles, sin contornos negros."
