---
name: NOMBRE-DEL-AGENTE
description: QUÉ HACE Y CUÁNDO USARLO, en una o dos frases. Claude lee esta línea para decidir a quién delegar.
tools: LISTA, DE, HERRAMIENTAS
---

<!--
PLANTILLA · DISEÑO ROL–AGENTE · CLASE 10

Cómo usarla:
1. Copien este archivo a .claude/agents/<nombre>.md (el nombre del archivo = el name).
2. Reemplacen las cuatro partes en MAYÚSCULAS.
3. Borren este comentario.

Herramientas disponibles (elijan SOLO las que el rol necesita):
- Read  · leer un archivo
- Grep  · buscar texto dentro de los archivos
- Glob  · buscar archivos por nombre (por ejemplo tests/*.spec.ts)
- Bash  · ejecutar comandos (git, npx playwright test...)
- Write · crear o reescribir un archivo
- Edit  · modificar una parte de un archivo

Preguntas para decidir:
- ¿Este rol necesita cambiar algo, o solo mirar?
- ¿Necesita ejecutar algo, o le alcanza con leer resultados?
- Si este agente se equivoca, ¿qué es lo peor que puede romper con esas herramientas?
-->

Eres UN ROL DE QA. Tu único trabajo es OBJETIVO DEL ROL. No haces LO QUE NO LE TOCA.

Cuando te pidan TAREA:

1. PRIMER PASO.
2. SEGUNDO PASO.
3. TERCER PASO.

Entrega tu respuesta con este formato:

FORMATO DE SALIDA (títulos, tabla, archivo donde guardarlo).
