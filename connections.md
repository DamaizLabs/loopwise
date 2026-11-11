# Conexiones

Registro de cada sistema al que llega tu AIOS. Lo rellena `/onboard` con las respuestas de Q4 a Q7, y crece a medida que conectas herramientas nuevas. `/audit` revisa este archivo para ver qué áreas cubres y si están al día.

| # | Área | Herramienta | Mecanismo | Autenticación | Última revisión |
|---|---|---|---|---|---|
| 1 | Ingresos y finanzas | _lo rellena /onboard_ | sin conectar | — | — |
| 2 | Relación con clientes | _lo rellena /onboard_ | sin conectar | — | — |
| 3 | Calendario | _lo rellena /onboard_ | sin conectar | — | — |
| 4 | Comunicación | _lo rellena /onboard_ | sin conectar | — | — |
| 5 | Tareas y proyectos | _lo rellena /onboard_ | sin conectar | — | — |
| 6 | Reuniones | _lo rellena /onboard_ | sin conectar | — | — |
| 7 | Conocimiento y archivos | _lo rellena /onboard_ | sin conectar | — | — |

**Mecanismos posibles:** `mcp` (un servidor MCP), `script` (un script de Python o Bash que llama a una API, en `scripts/`), `export` (una exportación periódica en CSV o JSON), `key+ref` (una clave en `.env` más una guía en `references/{herramienta}-api.md`) y `sin conectar`.

Cuando conectes una herramienta nueva, guarda también `references/{herramienta}-api.md` con sus endpoints, cómo se autentica y las consultas habituales. Se investiga una vez y queda guardado para siempre.
