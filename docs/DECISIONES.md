# Registro de decisiones

Nada está decidido si no está aquí. Cada entrada: fecha, decisión, alternativas descartadas y motivo. Las decisiones de producto las toman Iñaki y Otger; las sesiones de Claude proponen y anotan. Lo más reciente arriba.

---

## 2026-10-06 · Rediseño del finalista C: C2 · Expedición Glifo (propuesta de la sesión `claude/gifted-brown-0ge63s`, pendiente de confirmar)

No es decisión hasta que Iñaki y Otger la confirmen. Ficha: `02-concepto/finalista-C2-expedicion-glifo.md`; explicador: `finalista-C2-expedicion-glifo.html`.

- **Propuesta:** el idioma inventado deja de jugarse con gestos y pasa a jugarse desde el móvil: escapar de una ruina alienígena sala a sala, con órdenes en glifos, diccionario repartido entre los móviles y voz libre como canal. De 2 a 6 jugadores; capa opcional "traductor averiado"; estilo 2.5D (capas 2D con parallax) en tinta risográfica, dos tintas por sala; banco de 8 salas, MVP con 3.
- **Alternativas descartadas:** desactivar una bomba como finalidad (el brief la veta salvo reinvención evidente y es el módulo de teclado de Keep Talking; queda solo como sala final "El Núcleo", de la que se escapa); impostor como finalidad (deducción social saturada); atraco, embajada, cocina, criatura y aterrizaje como marco (detalle en la ficha, §1); 3D (coste y rendimiento sin aportar risa).
- **Motivo:** petición expresa de que el móvil forme parte del juego, que haya finalidad y más riqueza visual. Además mejora el modo a distancia del C original.

## 2026-10-06 · Brief v2 y arranque del repo

- **Decisión:** el brief vigente es el guardado en `docs/00-brief.md` (versión de 2026-10-06). No existía versión anterior en el repo (el remoto estaba vacío), así que no hay `00-brief-v1.md`.
- **Alternativas descartadas:** ninguna.
- **Motivo:** punto de partida de la fase de descubrimiento y concepto.

## 2026-10-06 · Fase actual: descubrimiento y concepto, sin código

- **Decisión:** en esta fase no se escribe código del juego. Entregables: investigación (`docs/01-investigacion/`), concepto (`docs/02-concepto/`) y direcciones visuales (`docs/03-visual/`). Al terminar la Fase C se para y se piden decisiones a Iñaki y Otger.
- **Alternativas descartadas:** empezar por un prototipo digital directamente.
- **Motivo:** el brief prioriza validar la diversión pronto, pero antes hay que elegir concepto; el prototipo digital es la fase siguiente.

## 2026-10-06 · Hipótesis del brief evaluadas (propuesta de la sesión de Iñaki, pendiente de confirmar)

No son decisiones hasta que Iñaki y Otger las confirmen; se anotan aquí para que la otra sesión sepa de dónde vienen los finalistas.

- **Saboteador oculto fijo desde 4 jugadores:** se propone descartarlo como mecánica (suspende originalidad: es "cooperativo + impostor" tal cual) y sustituirlo por **La tentación** (ofertas privadas y breves de traición, sin rol fijo, desde 3 jugadores) como capa opcional. Fuente: `02-concepto/filtro.md`.
- **Restricciones de comunicación sin atrezo:** se mantienen; el finalista C las convierte en el centro (idioma generado) y A y B las usan como interferencias cortas.
- **Rol de entrada:** se mantiene en A (asa de atrás) y B (mano); C lo sustituye por "idioma de dos signos" para el recién llegado.
- **Soluciones generadas por partida:** se mantiene en los tres finalistas.
- **Asientos izquierda/derecha en presencial:** opcional en A (parejas con vecinos reales); innecesario en B y C.
- **Pantalla de culpable y clip automático:** se mantiene en los tres; el clip se genera desde el estado del juego, sin grabar pantalla ni cámara (recomendación de `01-investigacion/viabilidad-tecnica.md`).
- **Paga el anfitrión, sin anuncios en partida:** se mantiene como hipótesis de monetización para después de validar; MVP sin monetización (`01-investigacion/mercado-y-cliente.md`).

## Pendientes de decisión (Iñaki y Otger) · con la recomendación de la sesión de Iñaki

| Decisión | Recomendación | Dónde está el razonamiento |
|---|---|---|
| Qué finalistas se prueban en papel y cuándo | Los tres, en una misma sesión de una hora con 4-6 amigos, en el orden A → B → C; repetir con un segundo grupo; grabar 15 s de cada uno | `02-concepto/comparativa.md` §5 y las fichas `finalista-*.md` |
| Qué concepto va a prototipo digital | **A · La mudanza**; B si A no produce risas en dos grupos; C como plan B barato o como tipo de ronda dentro de A o B | `02-concepto/comparativa.md` |
| Qué dirección visual | **Cartón y cinta** si el concepto es A; Neón de bar si es B; Risografía si es C. Plastilina solo si se prioriza la mascota y se asume el doble de coste | `03-visual/README.md` |
| Finalista C: ¿se sustituye por C2 · Expedición Glifo? | **Sí**, y probarlo en papel junto a A (20 min, ficha §12). Si el pitch suena a "Keep Talking" para 3 de 5 personas, repensar | `02-concepto/finalista-C2-expedicion-glifo.md` |
| Capa social por defecto | **La tentación** desde 3 jugadores, activable; nunca saboteador fijo | `02-concepto/filtro.md` |
| Motor y arquitectura | **No decidir todavía**: Godot 4 o web + Capacitor según concepto y estilo; antes, una tarde de medición en un Android de gama media. El prototipo desechable, en PWA con lo que ya sabéis (Next.js) y una sala autoritativa ligera (PartyKit/Durable Objects o Colyseus), no Supabase Realtime para el estado de ronda | `01-investigacion/viabilidad-tecnica.md` §2 y §4 |
| Cuenta de desarrollador y titular | Cuenta personal de Google Play y cuenta individual de Apple a nombre de uno de los dos, con pacto escrito; sin SL hasta que haya ingresos. Validar con una gestoría | `01-investigacion/requisitos-publicacion.md` |
