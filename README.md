# Loopwise

**Un sistema operativo de IA para tu negocio, sobre Claude Code, que aprende del resultado de cada proceso.** Gratis y de código abierto (MIT).

Loopwise es una versión de [AIS-OS](https://github.com/nateherkai/AIS-OS), el kit de Nate Herk, con mejoras de [David Torras Mellado](https://www.linkedin.com/in/davidtorrasmellado), de [DamaizLabs](https://www.damaizlabs.com/). Las mejoras siguen el AI OS que describe McKinsey en [«The AI operating system: A new way for CEOs to run the enterprise»](https://www.mckinsey.com/capabilities/quantumblack/our-insights/the-ai-operating-system-a-new-way-for-ceos-to-run-the-enterprise). Ni Nate Herk ni McKinsey participan en Loopwise ni lo respaldan.

## Qué es

Un sistema operativo de IA (AI OS) es una carpeta que Claude Code lee en cada sesión. Dentro están tu contexto, tus conexiones y tus comandos. Nate Herk lo resume en cuatro capas, las Four Cs:

| Capa | Qué hace |
|---|---|
| **Context** | Conoce tu negocio: quién eres, qué vendes y qué importa este trimestre |
| **Connections** | Llega a tus herramientas: correo, calendario, facturación |
| **Capabilities** | Sabe hacer el trabajo: un comando lanza un proceso de varios pasos |
| **Cadence** | Trabaja sin que se lo pidas: tareas programadas que te avisan |

El nombre viene del ciclo (*loop*) que Loopwise cierra en cada proceso: decide, mide el resultado y aprende de él.

## Qué añade Loopwise a AIS-OS

AIS-OS te ayuda a encontrar y lanzar una automatización por semana. Le faltan tres cosas: no comprueba si lo que lanzaste funcionó, no guarda las reglas de cada proceso y da un solo nivel de autonomía a todo un proceso. Loopwise las añade con cuatro reglas sacadas del AI OS de McKinsey:

| Regla | Qué cambia | Dónde |
|---|---|---|
| **1. Aprende de los resultados** | `/level-up` empieza por una fase 0. Antes de buscar algo nuevo, pregunta si lo último que lanzaste movió su número y apunta el resultado. Si una persona resolvió un caso que las reglas no preveían, y confirmas que siempre se hará así, pasa a ser una regla. | [`level-up/SKILL.md`](.claude/skills/level-up/SKILL.md) |
| **2. Los datos se quedan donde están** | La ficha de cada proceso dice en qué sistema vive cada dato y qué conexión lo lee. No copia nada. | [`ficha-proceso.md`](.claude/skills/level-up/references/ficha-proceso.md) |
| **3. El contexto de cada proceso se escribe en reglas** | Cada proceso tiene su ficha en `context/proceso-<nombre>.md`: su responsable, sus definiciones, sus reglas de negocio y sus criterios de decisión. Un índice, `context/procesos.md`, las ordena por el valor que mueven. | [`ficha-proceso.md`](.claude/skills/level-up/references/ficha-proceso.md) y [`CLAUDE.md`](CLAUDE.md) |
| **4. Se decide una por una qué decisiones toma la IA** | Cada decisión del proceso tiene quien la toma (la IA, una persona, o la IA avisando a una persona), su nivel de autonomía y su umbral de aviso. Lo que corre solo avisa únicamente cuando algo pasa ese umbral. | [`level-up/SKILL.md`](.claude/skills/level-up/SKILL.md) |

Además, está en español: el manual (`CLAUDE.md`), el cuestionario de `/onboard` (`aios-intake.md`), el registro de conexiones (`connections.md`) y este README. Los comandos siguen en inglés, como los escribió Nate. Claude te responde en español.

## Los comandos

| Comando | Cuándo |
|---|---|
| `/onboard` | El primer día. Siete preguntas, unos 15 minutos. Rellena tu contexto, tu voz y tus conexiones. |
| `/grill-me` | Cuando quieras pensar un plan o darle más contexto. Pregunta de una en una y guarda cada respuesta en `brainstorms/`. |
| `/link` | Cuando añadas un proyecto, archivo o fuente. Lo enlaza en el manual para que el sistema lo encuentre. |
| `/audit` | Después de montarlo y cada semana. Puntúa las Four Cs con evidencias y guarda un informe con fecha en `audits/`. |
| `/level-up` | Cada semana. Revisa lo último que lanzaste y encuentra, acota y lanza la siguiente automatización, con su ficha de proceso. |

## Cómo empezar

Necesitas [Claude Code](https://claude.com/claude-code). Usarlo puede tener coste según tu plan.

1. **Clona el repositorio** en una carpeta de tu equipo.
2. **Ábrela en Claude Code y ejecuta `/onboard`.** Responde las siete preguntas. Las muestras de tu forma de escribir se pegan tal cual, sin retocarlas.
3. **Úsalo una semana** con preguntas y decisiones reales. Pide que anote cada decisión en `decisions/log.md`. Si ves que le falta contexto de tu negocio, ejecuta `/grill-me` y dile que quieres ampliarlo: te pregunta de una en una, guarda cada respuesta en `brainstorms/` y pasa a `context/` lo que le confirmes. Si añades un proyecto, un archivo o una carpeta que deba conocer, ejecuta `/link` con su ruta: lo enlaza desde `CLAUDE.md` para que lo encuentre, sin copiarlo.
4. **Día 7: ejecuta `/audit`** y elige un hueco que cerrar.
5. **Día 14: ejecuta `/level-up`.** Sale una automatización y la ficha de su proceso.
6. **Cada semana, `/level-up` otra vez.** Primero revisa cómo fue lo último que lanzaste; después busca lo siguiente.

## ¿Te ayudo a implantarlo?

Loopwise es gratis y tiene licencia MIT: cualquier empresa o profesional independiente puede usarlo, adaptarlo y montarlo por su cuenta. Si te atascas al implantarlo en tu negocio, lo hacemos juntos: reserva una llamada de 30 minutos en [damaizlabs.com/contacto](https://www.damaizlabs.com/contacto/).

## Qué sale de tu equipo

Lo que escribes en Claude Code va a Anthropic, como en cualquier sesión. Tus archivos se quedan en tu carpeta. `audits/` y `brainstorms/` ya están en `.gitignore`, pero `context/`, `references/voice.md` y `connections.md` no: si guardas tu copia en GitHub, hazlo en un repositorio privado.

## Estructura

```
loopwise/
├── README.md
├── CLAUDE.md               ← el manual que Claude Code lee en cada sesión
├── EXPANSIONS.md           ← qué añadir a medida que crezcas
├── LICENSE
├── aios-intake.md          ← las respuestas de /onboard; edítalas y vuelve a lanzarlo
├── connections.md          ← cada sistema al que llega tu AI OS
├── context/                ← tú, tu negocio, tus prioridades y una ficha por proceso
├── references/
│   └── 3ms-framework.md    ← el marco de las Three Ms de Nate Herk
├── decisions/log.md        ← qué se decidió y por qué
├── archives/               ← lo antiguo; no se borra, se mueve aquí
├── brainstorms/            ← lo crea /grill-me (fuera de git)
├── audits/                 ← lo crea /audit (fuera de git)
└── .claude/skills/         ← onboard, audit, grill-me, link y level-up
```

## Créditos y licencia

- **Loopwise es MIT**: ver [LICENSE](LICENSE). La base es [AIS-OS](https://github.com/nateherkai/AIS-OS) de Nate Herk, commit `ce9cb93` (07-09-2026), también MIT. El copyright de la base es de Nate Herk, y el de las mejoras, de DamaizLabs.
- **The Three Ms of AI™** y **The Four Cs of an AI OS™** son marcas de Nate Herk. Loopwise usa los dos marcos con su atribución y no los presenta como propios.
- **Las cuatro reglas de procesos** se basan en el artículo de McKinsey citado arriba. Es una lectura propia de DamaizLabs, no un producto de McKinsey.
