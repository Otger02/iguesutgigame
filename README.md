# Party game para móvil (nombre provisional: iguesutgigame)

Party game gratuito para móvil (Google Play y App Store, crossplay) creado desde cero por Iñaki y Otger. Cada jugador juega desde su propio móvil, de 2 a 6 personas, en el mismo espacio (bar, sofá) o a distancia. La idea de partida es la esencia de los cooperativos de información repartida (tensión contra el reloj, malentendidos que dan risa, caos y tonterías físicas), pero con una fantasía y una mecánica principal propias, más dinámicas, sin explicación previa y diseñadas para ser compartidas en TikTok. Fase actual: descubrimiento y concepto, sin código del juego. El brief completo está en `docs/00-brief.md`.

> **Regla de coordinación**
> Cualquier sesión de Claude (Iñaki u Otger) debe escribir en este README cada tarea que termine: qué ha hecho y qué ha cambiado. Así la otra sesión se entera. Esta regla también está en CLAUDE.md.

## Estado actual

- 2026-10-06: repo arrancado por la sesión de Iñaki. Fase A (investigación, 5 documentos) y Fase B (12 semillas, filtro, 3 finalistas, comparativa) terminadas.
- Finalistas: A · La mudanza, B · Bichos alrededor, C · Idioma inventado. Recomendación: probar los tres en papel esta semana y llevar A a prototipo.
- Fase C (direcciones visuales) en curso.
- Nada decidido todavía: concepto, dirección visual y motor esperan a Iñaki y Otger (ver `docs/DECISIONES.md`).
- Limitación de la investigación: el proxy de red bloqueó la lectura directa de muchas webs (Steam, tiendas, prensa); las cifras vienen de extractos de buscador y están marcadas para comprobar a mano.

## En curso

| Sesión | Tarea | Desde |
|---|---|---|
| Iñaki | Fase C · Direcciones visuales (3-4 HTML + markdown en `docs/03-visual/`) | 2026-10-06 |

## Registro de cambios

_Lo más reciente arriba. Solo se añaden entradas; nunca se borran ni se reescriben las de la otra sesión._

### 2026-10-06 01:05 · Iñaki · Fase B terminada (concepto)

- **Hecho:** 12 semillas, filtro contra innegociables y criterios de éxito, fichas de una página de los 3 finalistas con prueba en papel de 15 minutos, y comparativa con recomendación y objetivos de dinamismo y de tiempo hasta jugar.
- **Archivos:** `docs/02-concepto/semillas.md`, `filtro.md`, `finalista-A-la-mudanza.md`, `finalista-B-bichos-alrededor.md`, `finalista-C-idioma-inventado.md`, `comparativa.md`.
- **Pendiente de decidir:** qué finalistas se prueban en papel (recomendación: los tres, en ese orden), qué concepto va a prototipo (recomendación: A · La mudanza), si La tentación es la capa social por defecto, y si C se convierte en tipo de ronda dentro de A o B.

### 2026-10-06 00:55 · Iñaki · Fase A terminada (investigación)

- **Hecho:** cinco documentos de investigación con resumen de 5 líneas, fuentes con URL y fecha, y "Implicaciones para nuestro juego". Hecho con cinco subagentes en paralelo.
- **Archivos:** `docs/01-investigacion/esencia-y-competencia.md`, `juegos-virales.md`, `mercado-y-cliente.md`, `viabilidad-tecnica.md`, `requisitos-publicacion.md`.
- **Hallazgos clave:** BOMBANANA! sale en iOS/Android el 9-10-2026 (precio y modelo no verificados); el hueco "cooperativo gratuito, cada uno con su móvil, mismo espacio, cuerpo y voz, 2-6" solo lo ocupa Spaceteam (2012); Google Play exige prueba cerrada con 12 testers 14 días para cuentas personales nuevas (6-8 semanas de calendario); soplar no es fiable en un bar y choca con el chat de voz; motor provisional Godot 4 o web + Capacitor; Supabase Realtime se queda corto por volumen de mensajes para el producto (vale para el prototipo).
- **No verificado (resumen):** precios en euros de varias apps, reseñas literales de Steam, visualizaciones de hashtags, estado de Nearby Connections, precios de voz por minuto. Cada documento lista lo suyo al final.
- **Pendiente de decidir:** nada de la Fase A es decisión; alimenta las fases B y C.

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
