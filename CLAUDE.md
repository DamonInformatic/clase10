# CLAUDE.md · Memoria del proyecto qa-dmc-curso

Este archivo lo lee Claude Code al empezar cada sesión en esta carpeta. Es la **memoria** de los agentes: las reglas del proyecto que no hace falta repetir en cada prompt.

## Qué es este proyecto

Kit de clases de la Especialización en QA & Testing Engineering con IA (DMC Institute). Dos módulos de negocio, con sus pruebas en Playwright Test:

| Módulo | Requisito | Pruebas | Tag |
|---|---|---|---|
| `src/descuentos.ts` | RF-DESC | `tests/descuentos.spec.ts` | `@descuentos` |
| `src/envio.ts` | RF-ENV | `tests/envio.spec.ts` | `@envio` |

## Reglas para cualquier agente de QA en este repo

1. **El requisito es la fuente de verdad, no el código.** Cada archivo de `src/` empieza con un bloque de comentario `RF-...` que describe las reglas de negocio. El resultado esperado de una prueba se calcula SIEMPRE desde ese bloque, nunca leyendo el cuerpo de la función. Si se calcula desde el código, la prueba confirma el defecto en vez de encontrarlo.
2. **Los agentes de QA no corrigen `src/`.** Encuentran, prueban y reportan. Quien corrige es la persona que abrió el Pull Request.
3. **Fronteras primero.** Para cada regla con un monto o una cantidad, prueba el valor exacto del límite y el valor justo debajo (por ejemplo, en RF-DESC: 25 y 24 unidades; 10 y 9 unidades).
4. **Montos en soles (S/)**, con dos decimales cuando hace falta.
5. **Escribe en español**, en frases cortas.

## Comandos

```bash
npm install                       # una sola vez
npx playwright test               # toda la suite (14 pruebas en main)
npx playwright test --grep @envio # solo un tag
git diff main...HEAD              # qué cambió en la rama actual
```

## Dónde guardar lo que generen los agentes

- Datos de prueba: `datos/` (JSON).
- Pruebas nuevas: `tests/` (`*.spec.ts`, con el tag del módulo en el `describe`).
- Reportes de calidad: `reportes/` (Markdown).

## Agentes del proyecto

Están en `.claude/agents/`. Cada uno tiene un solo rol y solo las herramientas que ese rol necesita:

- `analista-requisitos` · lee el requisito y lista reglas y fronteras. Solo lectura.
- `preparador-datos` · convierte las fronteras en una tabla de datos de prueba (JSON).
- `disenador-casos` · escribe las pruebas de Playwright a partir de los datos.
- `analista-resultados` · corre las pruebas y explica cada falla.

El quinto rol, `reportero-calidad`, lo diseñan los alumnos en el taller de la Clase 10 (plantilla en `plantillas/agente.md`).
