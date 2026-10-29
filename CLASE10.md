# Clase 10 · Agentes de QA con Claude Code

Desde la Clase 10 el repo trae su propia "plataforma" de agentes:

- `CLAUDE.md` — la memoria del proyecto: reglas que todo agente lee al empezar.
- `.claude/agents/` — cuatro agentes, cada uno con un rol y solo las herramientas de ese rol:

| Agente | Rol | Herramientas |
|---|---|---|
| `analista-requisitos` | Lee el bloque RF-... y lista reglas y fronteras | Read, Grep, Glob |
| `preparador-datos` | Convierte las fronteras en `datos/*.json` con su esperado | Read, Grep, Glob, Write |
| `disenador-casos` | Escribe pruebas de Playwright desde esos datos | Read, Grep, Glob, Write |
| `analista-resultados` | Corre las pruebas y explica cada falla | Read, Grep, Glob, Bash |

- `plantillas/agente.md` — plantilla para diseñar el quinto agente (`reportero-calidad`) en el taller.
- `datos/` y `reportes/` — carpetas donde los agentes guardan lo que generan.

## Rama del taller

`pr-9-envio-simplificado` · "Ordenamos envio.ts: los montos pasan a constantes con nombre, sin cambiar reglas". Las 14 pruebas pasan. ¿Lo aprobarían? Esa es la pregunta del taller.

## Uso con Claude Code (plan Pro o superior)

```bash
claude
> @agent-analista-requisitos Analiza el requisito RF-ENV de src/envio.ts
```

## Sin Claude Code (plan gratuito de claude.ai)

Abran un chat nuevo, peguen como primer mensaje el contenido del archivo del agente (sin las líneas entre `---`) y adjunten el archivo que el agente necesita leer.
