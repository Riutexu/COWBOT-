# AGENTS.md — COW-BOT

Contrato de trabajo para agentes de IA (opencode, Claude Code, Cursor, Gemini CLI, Copilot...).

Este repositorio sigue la metodología [superpowers](https://github.com/obra/superpowers) con el ciclo obligatorio:

**Brainstorm → Plan → Build → Test → Review**

Todo agente que toque este repo DEBE completar las 5 fases en orden. Ninguna se salta.

## Fase 1 · Brainstorm
- Carga la skill `brainstorming` antes de escribir código.
- Refina la idea con preguntas: ¿qué parte del pipeline de voz se mejora (grabación, Whisper, respuesta, webhook, TTS)?
- Valida el diseño con el humano en secciones.

## Fase 2 · Plan
- Carga la skill `writing-plans`.
- Descompón el trabajo en tareas de 2–5 minutos, cada una con ruta de archivo exacta, cambio concreto y verificación.

## Fase 3 · Build
- Carga la skill `test-driven-development` (RED-GREEN-REFACTOR: primero el test que falla, luego el código mínimo, luego refactoriza).
- Trabaja en ramas. Commits atómicos y descriptivos.
- Respeta el flujo: micrófono → Whisper STT → OpenRouter AI → webhook (como usuario humano) → TTS en canal de voz.

## Fase 4 · Test
- Carga la skill `verification-before-completion`: evidencia sobre afirmaciones.
- Verifica los módulos del bot: transcripción, generación de respuesta, envío por webhook, lectura TTS y detección de actividad de voz (VAD).
- No expongas tokens ni secretos del bot en el repo (`.env`, config).

## Fase 5 · Review
- Carga la skill `requesting-code-review` y `finishing-a-development-branch`.
- Revisa contra el plan: ¿todo implementado? ¿código sobrante? Clasifica hallazgos por severidad.
- Los hallazgos críticos bloquean el merge. Nada de "ya está" sin verificación.

## Contexto del repositorio

- **Bot**: Discord con procesamiento de voz → respuesta IA → respuesta como usuario humano vía webhook → lectura en voz alta.
- **Stack**: Python, Whisper (STT), OpenRouter (LLM), Discord API, TTS, VAD.
- **Estado**: en desarrollo (ver SKILL TREE en el README).
