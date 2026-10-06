# CLAUDE.md · Reglas de trabajo del repositorio

Party game para móvil (iOS y Android) creado por Iñaki y Otger. Dos sesiones de Claude Code trabajan en paralelo sobre este repo, una por persona. Este archivo se carga automáticamente al iniciar sesión; síguelo siempre.

## Fase actual

Descubrimiento y concepto. **No se escribe código del juego.** El brief completo está en `docs/00-brief.md`.

## Reglas de coordinación

1. **Al empezar sesión:** `git pull` y lee `README.md` y `docs/DECISIONES.md`. Si es tu primera sesión, lee también `docs/00-brief.md`.
2. **Antes de empezar una tarea** (cada entregable o encargo, no cada edición menor): anótala en la sección "En curso" del README (sesión, tarea, fecha) y haz push.
3. **Al terminar CADA tarea:** añade una entrada arriba del "Registro de cambios" del README con fecha y hora, sesión (Iñaki u Otger), qué has hecho, qué archivos has creado o modificado y qué queda pendiente de decidir. Quítala de "En curso". Commit y push.
4. **Solo se añaden entradas:** nunca se borran ni se reescriben las de la otra sesión. Si hay conflicto en el README, conserva ambas entradas en orden cronológico.
5. **Lo que se decide va a `docs/DECISIONES.md`** (fecha, decisión, alternativas descartadas y motivo). Nada está decidido si no está ahí.
6. **Si vas a tocar algo que la otra sesión tiene "En curso", para y avisa.**
7. **Idioma:** español de España en todo (documentos, commits, comentarios).
8. **Nunca subas claves ni credenciales al repo.**

## Reglas de los documentos

- No inventes datos. Descargas, ingresos, visualizaciones, precios y fechas siempre con fuente (URL y fecha de consulta); si no se encuentra, escribe "no verificado". Separa hechos de hipótesis.
- Documentos escaneables: conclusión arriba, tablas para comparar, sin relleno.
- Cada documento de investigación empieza con un resumen de 5 líneas y acaba con "Implicaciones para nuestro juego".
- Ten criterio: recomienda, señala riesgos y di sin rodeos lo que no merece la pena.

## Estructura

```
docs/00-brief.md            Brief íntegro (referencia, no se edita)
docs/DECISIONES.md          Registro de decisiones
docs/01-investigacion/      Fase A · Investigación
docs/02-concepto/           Fase B · Semillas, filtro, finalistas, comparativa
docs/03-visual/             Fase C · Direcciones visuales (HTML + markdown)
```
