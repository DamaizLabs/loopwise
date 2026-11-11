# Ficha de proceso — plantilla

`/level-up` copia esta plantilla a `context/proceso-<slug>.md` al definir un proceso, y añade su fila a `context/procesos.md`. Se rellena con lo que el usuario confirma; lo que falte se deja como «pendiente: <quién lo sabe>», nunca inventado.

El índice `context/procesos.md` tiene esta forma y se crea con la primera ficha:

```markdown
# Procesos

Ordenados por valor: el 1 es el que más mueve. Cada uno tiene su ficha.

| Prioridad | Proceso | Responsable | Estado | Ficha |
|---|---|---|---|---|
| 1 | <nombre> | <persona> | <estado> | [proceso-<slug>.md](proceso-<slug>.md) |
```

---

```markdown
# Proceso: <nombre>

- **Responsable:** <persona que responde de las reglas de este proceso>
- **Prioridad:** <1 = el que más valor mueve>
- **Número que mueve:** <más clientes / más valor por cliente / menos coste> · <métrica> · hoy: <valor> (<fecha>)
- **Estado:** <en diseño / a mano / fase N del método de la bicicleta / programado>
- **Decisión de origen:** <fecha y título de la entrada en decisions/log.md>

## Cómo funciona

<Qué lo pone en marcha → de dónde salen los datos → cómo cambian → dónde se decide algo → dónde acaba. De tres a cinco líneas.>

## Reglas

Definiciones, reglas de negocio y criterios de decisión de los que depende el proceso. Una por línea, con su fuente y su fecha. Si una definición la usa otra ficha, vive en `context/definiciones.md` y aquí solo se enlaza.

- <regla> — fuente: <persona o documento>, <fecha>

## Datos

Dónde viven y qué conexión los lee. Aquí no se copian datos: solo se dice dónde están.

| Dato | Sistema donde vive | Conexión (fila de connections.md) |
|---|---|---|
| <dato> | <sistema> | <fila o «sin conectar»> |

## Quién decide qué

Una fila por cada decisión del proceso. La toma la IA, una persona, o la IA y avisa a una persona. Lo que funciona solo avisa únicamente cuando se cumple la última columna.

| Decisión | La toma | Nivel (L0-L4) | Avisa a una persona cuando |
|---|---|---|---|
| <decisión> | <IA / persona / IA y avisa> | <L1> | <umbral o caso no previsto> |

## Resultados

Una fila por revisión (la fase 0 de `/level-up`). Si una persona resolvió un caso que las reglas no preveían y se confirma que siempre se hará así, la decisión pasa a Reglas.

| Fecha | Valor del número | Qué falló | Qué regla cambió |
|---|---|---|---|
```
