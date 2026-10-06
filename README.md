# Party game para móvil (nombre provisional: iguesutgigame)

Party game gratuito para móvil (Google Play y App Store, crossplay) creado desde cero por Iñaki y Otger. Cada jugador juega desde su propio móvil, de 2 a 6 personas, en el mismo espacio (bar, sofá) o a distancia. La idea de partida es la esencia de los cooperativos de información repartida (tensión contra el reloj, malentendidos que dan risa, caos y tonterías físicas), pero con una fantasía y una mecánica principal propias, más dinámicas, sin explicación previa y diseñadas para ser compartidas en TikTok. Fase actual: descubrimiento y concepto, sin código del juego. El brief completo está en `docs/00-brief.md`.

> **Regla de coordinación**
> Cualquier sesión de Claude (Iñaki u Otger) debe escribir en este README cada tarea que termine: qué ha hecho y qué ha cambiado. Así la otra sesión se entera. Esta regla también está en CLAUDE.md.

## Estado actual

- 2026-10-06: repo arrancado por la sesión de Iñaki. Base de coordinación creada (brief, CLAUDE.md, README, DECISIONES, carpetas).
- Fase A (investigación) en curso.
- Fases B (concepto) y C (visual) pendientes.
- Nada decidido todavía sobre concepto, motor ni estilo visual.

## En curso

| Sesión | Tarea | Desde |
|---|---|---|
| Iñaki | Fase A · Investigación (5 documentos en `docs/01-investigacion/`) | 2026-10-06 |

## Registro de cambios

_Lo más reciente arriba. Solo se añaden entradas; nunca se borran ni se reescriben las de la otra sesión._

### 2026-10-06 00:20 · Iñaki · Base de coordinación

- **Hecho:** creada la base del repo. El remoto estaba vacío (sin ramas), así que no había trabajo previo que reutilizar.
- **Archivos:** `docs/00-brief.md` (brief íntegro), `CLAUDE.md`, `README.md`, `docs/DECISIONES.md`, carpetas `docs/01-investigacion/`, `docs/02-concepto/`, `docs/03-visual/`.
- **Pendiente de decidir:** nada todavía. Ver `docs/DECISIONES.md`.

## Estructura de carpetas

```
CLAUDE.md                   Reglas que carga Claude Code al iniciar sesión
README.md                   Este archivo: estado, en curso, registro de cambios
docs/
  00-brief.md               Brief íntegro de Iñaki (referencia, no se edita)
  DECISIONES.md             Registro de decisiones (fecha, decisión, descartes, motivo)
  01-investigacion/         Fase A · esencia-y-competencia, juegos-virales,
                            mercado-y-cliente, viabilidad-tecnica, requisitos-publicacion
  02-concepto/              Fase B · semillas, filtro, finalistas, comparativa
  03-visual/                Fase C · direcciones visuales (HTML autocontenido + markdown)
```
