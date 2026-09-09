# Revisión de tesis UTM

Agente de VS Code para revisar avances de tesis en PDF de la **Maestría en Electrónica, opción Sistemas Inteligentes Aplicados (MEOSIA)** de la Universidad Tecnológica de la Mixteca, Oaxaca.

## Organización del proyecto

La configuración está separada en agentes, instrucciones y habilidades dentro de `.github`, con la siguiente estructura:

```text
utm_thesis_review/
├── .github/
│   ├── instructions/
│   │   ├── academic-review.instructions.md
│   │   └── reference-authority.instructions.md
│   ├── skills/
│   │   ├── thesis-progress-review/
│   │   │   └── SKILL.md
│   │   └── reviewed-pdf/
│   │       └── SKILL.md
│   └── agents/
│       └── utm-thesis-review.agent.md
└── README.md
```

- [Agente](.github/agents/utm-thesis-review.agent.md): define el rol y coordina la revisión; carga explícitamente las instrucciones y habilidades locales.
- [Principios de revisión](.github/instructions/academic-review.instructions.md): prioridad de redacción y estructura, evidencia, privacidad y límites académicos.
- [Autoridad de referencias](.github/instructions/reference-authority.instructions.md): ubicación de las guías, contexto UTM y distinción entre recomendaciones y requisitos verificados.
- [Revisión del avance](.github/skills/thesis-progress-review/SKILL.md): evaluación académica y técnica, cobertura y registro de hallazgos.
- [Producción del PDF revisado](.github/skills/reviewed-pdf/SKILL.md): inspección, anotaciones, resumen anexo y validación sin modificar originales.

Las instrucciones se cargan por pertinencia o por lectura explícita del agente; no usan un patrón global que afecte tareas ajenas a la revisión. Las habilidades se cargan cuando corresponden y no se muestran como comandos independientes. No se requiere el plugin IPS utilizado durante la creación de estos archivos. Las bibliotecas PDF/OCR siguen siendo dependencias del entorno, no código incluido en las habilidades.

## Uso

1. Abre esta carpeta, `utm_thesis_review`, en VS Code como carpeta de trabajo.
2. Selecciona **UTM Thesis Reviewer** en el selector de agentes del chat. Si no aparece, recarga la ventana y comprueba que los agentes locales estén habilitados.
3. Indica la ruta del PDF del estudiante. Puedes añadir la etapa del avance, capítulos prioritarios e instrucciones del asesor.
4. El agente revisará el contenido y generará una copia con sufijo `_reviewed.pdf` junto al original. El PDF incluirá anotaciones en las páginas de la tesis y un resumen de revisión al final, con todos los comentarios también disponibles como texto legible.

Ejemplo de solicitud:

> Revisa el PDF de avance que adjunto. Corresponde al primer seminario de tesis. Prioriza la coherencia entre objetivos y metodología, y comenta en español de México.

## Alcance

- Prioridad predeterminada: redacción académica y estructura de la tesis, incluyendo coherencia entre capítulos, cohesión de párrafos y precisión del lenguaje.
- Revisión técnica y metodológica, coherencia de la investigación, redacción, referencias y presentación.
- Evaluación proporcional a la etapa del avance, sin exigir resultados finales prematuramente.
- Comentarios en español de México, priorizados y vinculados a páginas concretas.
- Originales sin modificaciones; si ya existe una revisión, la nueva salida usa una marca de tiempo antes del sufijo `_reviewed.pdf`.
- Procesamiento local de los documentos, sin subir tesis a servicios externos.

## Referencias y autoridad

Las guías permanecen en `C:/Users/marti343/Documents/mbd-model-review/docs`. Son **referencias orientativas de otras universidades mexicanas**, no requisitos oficiales de UTM. El agente distingue recomendaciones externas, criterios académicos y requisitos UTM verificados; no combina reglas incompatibles ni aplica marcas o plantillas de otra institución a la tesis.

El contexto del programa proviene de <https://www.utm.mx/postgrado/m_electronica_sia.html>. Para una revisión de cumplimiento institucional, proporciona además los requisitos UTM vigentes que correspondan.

## Requisitos operativos

El agente necesita permisos para leer los documentos, ejecutar herramientas locales y escribir la copia revisada. Puede utilizar Python y PyMuPDF para extraer texto, anotar y generar el PDF; un documento escaneado puede requerir OCR local adicional. La instalación de dependencias y el acceso a herramientas siguen los permisos de VS Code y del entorno seleccionado.

La definición del agente guía la revisión; no es un servicio automático de vigilancia de carpetas. Debe iniciarse desde el chat con un PDF de entrada. Aún no se ha ejecutado una revisión de un estudiante ni probado la generación de PDF en este proyecto.
