---
name: process-mapper
description: Use when necesitas diagnosticar un proceso de negocio para encontrar dónde se pierde tiempo y qué rediseñar. Le describes el proceso paso a paso (como lo vives hoy, no como debería ser) y te devuelve el proceso mapeado con esperas, reprocesos y traspasos marcados, cada paso clasificado, y una propuesta de rediseño con lo que conviene automatizar primero.
---

# Process Mapper

## Qué hace

Toma la descripción de un proceso de negocio, tal como ocurre hoy — no la
versión idealizada del manual — y devuelve un diagnóstico: dónde se pierde el
tiempo, por qué, y qué parte del proceso conviene rediseñar o automatizar
primero.

## Cómo usarla

Pégame la descripción del proceso como si se la contaras a un compañero
nuevo: quién hace qué, en qué orden, con qué herramienta, y cuánto se demora
cada parte (aunque sea un estimado). Entre más real y menos "así debería
ser", mejor el diagnóstico.

## Método

### 1. Levanta el proceso tal como es hoy

Reconstruye la secuencia completa de pasos, en el orden real en que
ocurren — incluyendo los rodeos, las excepciones y los "eso en realidad lo
hace alguien por WhatsApp aunque el manual diga otra cosa". Si faltan datos
de tiempo o de quién hace qué, pregunta antes de inventar un número.

### 2. Marca esperas, reprocesos y traspasos

Sobre esa secuencia, señala tres tipos de fricción:

- **Espera**: el trabajo está detenido porque depende de que alguien más lo
  revise, apruebe o retome (una aprobación que duerme en un correo, una
  cola).
- **Reproceso**: el mismo trabajo se hace más de una vez porque la primera
  vez salió mal, faltó un dato o cambió de manos sin contexto.
- **Traspaso**: el trabajo cambia de persona o de sistema, y ese cambio de
  manos cuesta tiempo aunque nadie lo esté trabajando en ese momento (copiar
  de un Excel a otro, reescribir lo mismo en dos sistemas).

Para cada uno, anota dónde ocurre y — si el dato existe — cuánto tiempo se
come.

### 3. Clasifica cada paso

Etiqueta cada paso del proceso en una de tres categorías:

- **Decide**: alguien evalúa información y elige un camino (aprobar,
  rechazar, priorizar).
- **Ejecuta**: se produce o transforma algo (redactar, calcular, construir,
  editar).
- **Transporta**: la información o el trabajo se mueve de un lugar a otro
  sin transformarse (copiar, reenviar, subir un archivo).

Los pasos de "transporta" son casi siempre candidatos a desaparecer. Los de
"decide" casi nunca se automatizan del todo — se apoyan, no se reemplazan.

### 4. Propón el rediseño

Con el mapa completo, entrega:

- Qué pasos se eliminan (casi siempre traspasos que no aportan nada).
- Qué pasos se fusionan o se reordenan.
- Qué parte del proceso es candidata a automatizarse — y cuál no, porque
  necesita criterio humano.
- Un orden de prioridad: empieza por el punto de mayor fricción con menor
  esfuerzo de cambio, no por el más vistoso.

Sé específico al proceso descrito. No repitas el mismo diagnóstico genérico
para procesos distintos.

## Ejemplo

**Entrada:**

"Cuando llega una cotización, ventas la anota en un Excel. Luego se la manda
por correo a finanzas para que revise el margen. Finanzas a veces se demora
dos o tres días en contestar porque tiene otras cosas. Si el margen no da,
ventas tiene que volver a armar la cotización desde cero y mandarla otra
vez. Cuando finanzas aprueba, alguien de ventas la pasa manualmente al
sistema de facturación, que es un programa distinto al Excel."

**Salida:**

| Paso | Tipo | Fricción |
|---|---|---|
| Anotar cotización en Excel | Ejecuta | — |
| Enviar por correo a finanzas | Transporta | Traspaso |
| Esperar revisión de finanzas (2-3 días) | — | Espera |
| Finanzas revisa margen | Decide | — |
| Si no da: rearmar cotización desde cero | Ejecuta | Reproceso |
| Pasar la cotización aprobada al sistema de facturación a mano | Transporta | Traspaso |

Rediseño propuesto:

1. El mayor punto de fricción es la espera de 2-3 días en finanzas: no es un
   problema de herramienta, es que la revisión no tiene prioridad ni dueño
   claro. Antes de automatizar algo, vale la pena fijar un tiempo de
   respuesta acordado.
2. El traspaso Excel → correo → sistema de facturación se puede eliminar
   del todo: si la cotización se arma directamente en el sistema (o en una
   plantilla que lo alimenta), desaparecen dos traspasos y el reproceso baja,
   porque el margen se puede calcular antes de que finanzas la vea.
3. El paso de "decide" (revisar margen) no se automatiza — se le puede dar
   un umbral automático (si el margen está sobre X%, pasa directo; si no, va
   a revisión), para que finanzas solo mire las excepciones.
