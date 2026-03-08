# Custom Agents Config

## Agente Orquestador para proyectos backend (Node.js/ts)

Este repositorio contiene la configuración personalizada para los agentes de [OpenCode](https://opencode.ai) y sus respectivos prompts, organizados para proveer subagentes especializados (`backend`, `write-code`, `write-test`, `write-doc`, `extend-project`).

El objetivo es compartir un entorno de inteligencia artificial estandarizado y reproducible para cualquier usuario de la organización o comunidad.

![Gato lindo](./Diagrama-imagen.png)

## Requisitos Previos

Antes de configurar este proyecto en un entorno nuevo, asegúrate de tener instalado:

1. **OpenCode**: Asegúrate de tener la app u la herramienta principal desde donde interactúas con los agentes base instalada.

## Instalación y Configuración

Sigue estos pasos para duplicar este espacio de trabajo en cualquier equipo:

1. **Clonar este repositorio**:

   ```bash
   git clone https://github.com/Joel-RD/opencode-custom-agents.git
   ```

2. **Copiar carpetas** dentro de la raiz de home/.config/opencode

 - desing
 - prompt-agent
 - custom-agents.json en opencode.json

 ### **Nota**: 
 - Tenga cuidado al copiar el json de custom-agents.json en opencode.json ya que esto puede reescribir los agentes propios

## Configuración de Agentes

### Orquestador (orchestrator)
- **Modo**: primary
- **Temperature**: 0.4
- **Quick-thinker**: Configuración de razonamiento rápido con 8 pasos para respuestas ágiles
- **Seguridad**: Modo solo lectura con herramientas denegadas por defecto

### Backend
- **Modo**: subagent (escondido)
- **Temperature**: 0.7
- **Permisos**: 
  - read, list, grep: allow
  - bash: allow para comandos básicos (ls, cat, pwd, echo, find, tree, grep, wc)
  - task: solo permite write-code, write-test, write-doc, extend-project

### write-code
- **Modo**: subagent (escondido)
- **Temperature**: 0.5
- **Permisos completos** de lectura, edición, listado y grep
- **bash**: allow para npm, git, mkdir, cp, mv, find, tree, wc (rm requiere confirmación)

### write-test
- **Modo**: subagent (escondido)
- **Temperature**: 0.5
- **Permisos completos** de lectura, edición, listado y grep
- **bash**: allow para npm, git, mkdir, cp, mv, find, tree, wc (rm requiere confirmación)

### write-doc
- **Modo**: subagent (escondido)
- **Temperature**: 0.5
- **Permisos** de lectura, edición, listado y grep
- **bash**: allow para comandos de búsqueda y lectura

### extend-project
- **Modo**: subagent (escondido)
- **Temperature**: 0.5
- **Permisos completos** de lectura, edición, listado y grep
- **bash**: allow para npm, git, mkdir, cp, mv, find, tree, wc (rm requiere confirmación)

## Estructura de Sub-Agentes

Este proyecto incluye una estricta especialización de responsabilidades:

1. **orchestrator**: Actúa como el modelo `primary`. Analiza el objetivo, dialoga con el usuario y luego solo transfiere control o solicitudes al subagente `backend`. Carece de permisos excesivos de edición del OS (Modo Seguro). Incluye configuración de quick-thinker para respuestas rápidas.
2. **backend**: Un sub-agente estratega escondido del usuario (`hidden: true`) capaz de usar terminal con bash en modo lectura o lectura de estado. Decide asignar trabajo a expertos específicos.
3. **write-code**: Especialista en escritura o estructuración de código.
4. **write-test**: Dedicado completamente a diseñar, escribir y perfeccionar código de tests para tu aplicación.
5. **write-doc**: Maneja lo correspondiente a mantenimiento de READMEs, docstrings y explicaciones.
6. **extend-project**: Herramienta general de extensión integral del proyecto o de módulos transversales.

