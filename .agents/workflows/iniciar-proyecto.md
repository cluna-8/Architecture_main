---
description: Flujo para instanciar un nuevo proyecto a partir de los requerimientos y entregarlo a los programadores
---
# Iniciar Proyecto y Andamiaje (Project Factory)

Este flujo de trabajo orquesta el inicio de un nuevo proyecto, desde la recepción de requerimientos hasta el traspaso (handoff) al equipo de programación.

1. **Recopilación Inicial:** Pregunta inmediatamente al usuario por la siguiente información:
   - Nombre del proyecto.
   - Nombre del repositorio Git.
   - Fuente de los requerimientos: ¿Existe un notebook en NotebookLM (pide el nombre), o prefiere pegar/adjuntar los archivos directamente?
   - Tecnología y estructura para la arquitectura: Pregunta cómo estructurar el documento `arquitectura.md`. **No asumas ninguna arquitectura por defecto (ni siquiera microservicios).** En su lugar, sugiere evaluar juntos la mejor tecnología y estructura (ej. monolito, serverless, microservicios) según los requerimientos antes de redactar el documento final.
   *Detente aquí (por ejemplo, usando `notify_user` si estás en modo tarea) y NO avances al siguiente paso hasta que el usuario te proporcione estos datos.*
2. **Generación de PRD, Plan y Arquitectura:** Una vez que el usuario proporciona los datos y requerimientos, procésalos aplicando las reglas de `arquitecto-master.md`. Genera:
   - Un PRD (Product Requirements Document).
   - Un archivo `arquitectura.md` detallando las decisiones tecnológicas (ej. microservicios, Docker).
   - Un Plan de Implementación.
3. **Revisión del Arquitecto:** Presenta el PRD y la Arquitectura al arquitecto humano y espera aprobación.
// turbo
4. **Scaffolding Inicial:** Una vez aprobado, el agente creará la carpeta para el nuevo proyecto estrictamente dentro de `/home/drexgen/Documents/arquitectura_projects/` (creando `arquitectura_projects` si no existe). Toda la documentación generada (PRD, `arquitectura.md`) se moverá aquí.
// turbo
5. **Configuración de .agents/ local:** Genera la carpeta `.agents/rules/` específica dentro del andamiaje del nuevo proyecto. Estas reglas deben instruir al próximo agente (el programador) sobre cómo trabajar bajo los estándares de arquitectura definidos en el PRD. Además, **debes incluir obligatoriamente una regla de inicialización interactiva**: el agente debe iniciar preguntando al programador en qué módulo trabajará y con qué tecnología, asistiéndolo en la investigación y análisis profundo antes de codificar.
// turbo
6. **Notebook del Desarrollador:** Genera un archivo `README.md` detallado en la raíz del nuevo proyecto. Este archivo debe incluir:
   - Las instrucciones de instalación y despliegue (ej. comandos de Docker).
   - La arquitectura definida (o referenciar a `arquitectura.md`).
   - La lista de tareas de desarrollo pendientes (incluyendo la sección de "Investigación Pendiente" si hay indefiniciones tecnológicas).
7. **Flujo de Trabajo Git y Creación del Repositorio:** Define las reglas de Git para los programadores en el proyecto:
   - **Ramas Dev:** Todo el desarrollo debe hacerse en ramas `dev` o características (features).
   - **Rama Main:** La rama `main` estará protegida.
   - **Aprobación:** Solo se harán merges a la rama `main` cuando la versión esté aprobada y revisada por el Arquitecto.
   - Si se dispone del MCP de GitHub, solicita inicializar el repositorio GitHub remoto, realiza el commit inicial de esta estructura en la rama correspondiente y sube el código.
8. **Entrega Final:** Presenta al usuario el enlace de Git del nuevo repositorio. Ahora está listo para ser asignado al equipo de programadores.
