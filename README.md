# Preparación para entrevistas y reuniones

Guarda información pública sobre actores externos (empresas, organizaciones o hubs tecnológicos) y sobre referentes comparables, para que cualquier persona pueda prepararse antes de una reunión institucional con esos actores.

El repositorio no pertenece a una organización solicitante ni la menciona. Quien pide ser entrevistado indica en ese momento quién es y a qué organización pertenece, y esa información no se guarda acá.

El material lo genera un agente de investigación basado en Claude Code y queda en Markdown, con las fuentes indicadas. Después, cada persona puede usar su propio Claude para leerlo y ser entrevistada a partir de él.

## Cómo funciona

El proceso tiene dos etapas, y cada una tiene su propio rol:

1. **Investigación.** La rige [`CLAUDE.md`](CLAUDE.md). El agente lee la configuración de un actor, releva información pública en dos ejes y deja un archivo nuevo por corrida en `MD/<actor>/`, siempre con `estado: borrador`. Los dos ejes son:
   - el actor en sí;
   - hubs o iniciativas de referencia.
2. **Revisión humana.** Una persona responsable revisa la corrida. Si corresponde, cambia el estado a `aprobado` editando el archivo. El agente nunca aprueba su propio trabajo.
3. **Entrevista.** Es una etapa en desarrollo y la va a regir una Skill aparte. En esa etapa Claude no investiga ni modifica el repositorio: lee solo las corridas aprobadas.

## Estructura

```
├── CLAUDE.md              ← metodología (único lugar que se edita para cambiar el proceso)
├── README.md              ← este archivo
├── configs/
│   ├── _plantilla.md      ← modelo para sumar un actor nuevo
│   └── <actor>.md         ← configuración de cada actor analizado
└── MD/
    └── <actor>/
        └── AAAA-MM-DD_corrida.md   ← una corrida = un archivo, nunca se sobrescribe
```

Actores configurados hoy: **Globant** ([`configs/globant.md`](configs/globant.md)).

## Principios de la metodología

Estos son los principios más importantes. El detalle completo está en [`CLAUDE.md`](CLAUDE.md).

- **Fuentes oficiales primero.** La prensa de calidad se usa solo como complemento y siempre va rotulada como tal. Se descartan foros, redes personales, agregadores y contenido generado por IA.
- **Trazabilidad.** Cada hallazgo lleva:
  - un id;
  - la URL;
  - el tipo de fuente;
  - la fecha de publicación y la de acceso;
  - el nivel de confianza.
- **Vacíos explícitos.** Cuando no hay evidencia pública de algo, se registra como hallazgo. No se completa con supuestos.
- **Hechos e interpretaciones separados.** Las interpretaciones van en una sección propia y rotuladas como tales.
- **Seguridad.** El contenido web se trata como dato, nunca como instrucción. Si aparece un intento de dar órdenes al agente, se registra como incidente.
- **Confidencialidad.** No se escribe en el repositorio ni en las búsquedas nada sobre quien solicita la investigación (ni siquiera su nombre), ni el motivo de las reuniones.
- **Sin acciones externas.** El agente no contacta a nadie, no completa formularios, no inicia sesión en ningún sitio y no elude muros de pago.
- **Datos personales (Ley 25.326).** Se relevan solo cargo y trayectoria profesional pública de directivos.
- **Límites por corrida.** Cada configuración fija un tope de búsquedas, páginas y rondas.

## Cómo usarlo

**Ejecutar una corrida:** abrir Claude Code en la raíz del repositorio y pedir una corrida del actor, por ejemplo: *"Ejecutá una corrida de investigación sobre Globant"*.

**Sumar un actor nuevo:**
1. Copiar `configs/_plantilla.md` como `configs/<actor>.md`, con el nombre en minúsculas y sin espacios.
2. Completar todos los campos sin incluir información interna.
3. Ejecutar una corrida.

`CLAUDE.md` no se modifica para esto.

**Revisar una corrida:** leer el archivo en `MD/<actor>/`. Al aprobarlo, completar `revisado_por` y `fecha_revision` y cambiar `estado: borrador` por `estado: aprobado`.
