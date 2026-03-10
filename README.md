# Custom Agents Config

## Agente Orquestador para proyectos backend (Node.js/ts)

Este repositorio contiene la configuración personalizada para los agentes de [OpenCode](https://opencode.ai) y sus respectivos prompts, organizados para proveer subagentes especializados (`orchestrator`, `core`, `code-creator`, `code-modifier`, `documenter`, `tester`).

El objetivo es compartir un entorno de inteligencia artificial estandarizado y reproducible para cualquier usuario de la organización o comunidad.

## Requisitos Previos

Antes de configurar este proyecto en un entorno nuevo, asegúrate de tener instalado:

1. **OpenCode**: Asegúrate de tener la app u la herramienta principal desde donde interactúas con los agentes base instalada.

## Instalación y Configuración

Sigue estos pasos para duplicar este espacio de trabajo en cualquier equipo:

1. **Clonar este repositorio**:

   ```bash
   git clone https://github.com/Joel-RD/opencode-custom-agents.git
   ```

2. **Copiar carpetas** dentro de la raíz de home/.config/opencode

 - prompt-agent
 - custom-agents.json en opencode.json

### **Nota**: 
 - Tenga cuidado al copiar el json de custom-agents.json en opencode.json ya que esto puede reescribir los agentes propios

## Configuración de Agentes

### Orchestrator (orchestrator)
- **Modo**: primary
- **Temperature**: 0.1
- **Seguridad**: Modo solo lectura con herramientas denegadas por defecto
- **Permisos**: Solo permite tareas tipo "core"

### Core
- **Modo**: subagent (escondido)
- **Temperature**: 0.3
- **Permisos**: 
  - read, list, grep: allow
  - bash: allow para comandos básicos (ls, cat, pwd, echo, find, tree, grep, wc)
  - task: permite code-creator, code-modifier, documenter, tester

### Code Creator
- **Modo**: subagent (escondido)
- **Temperature**: 0.5
- **Permisos completos** de lectura, edición, listado y grep
- **bash**: allow para npm, git, mkdir, cp, mv, find, tree, wc (rm requiere confirmación)
- **task**: permite tester, documenter

### Code Modifier
- **Modo**: subagent (escondido)
- **Temperature**: 0.5
- **Permisos completos** de lectura, edición, listado y grep
- **bash**: allow para npm, git, mkdir, cp, mv, find, tree, wc (rm requiere confirmación)
- **task**: permite tester, documenter

### Documenter
- **Modo**: subagent (escondido)
- **Temperature**: 0.5
- **Permisos** de lectura, edición, listado y grep
- **bash**: allow para comandos de búsqueda y lectura

### Tester
- **Modo**: subagent (escondido)
- **Temperature**: 0.5
- **Permisos completos** de lectura, edición, listado y grep
- **bash**: allow para npm, git, mkdir, cp, mv, find, tree, wc (rm requiere confirmación)

## Estructura de Sub-Agentes

Este proyecto incluye una estricta especialización de responsabilidades:

1. **orchestrator**: Actúa como el modelo `primary`. Analiza el objetivo, dialoga con el usuario y luego solo transfiere control o solicitudes al subagente `core`. Carece de permisos excesivos de edición del OS (Modo Seguro).

2. **core**: Un sub-agente estratega escondido del usuario (`hidden: true`) capaz de usar terminal con bash en modo lectura o lectura de estado. Decide asignar trabajo a expertos específicos.

3. **code-creator**: Especialista en escritura o estructuración de código nuevo.

4. **code-modifier**: Especialista en modificar, extender y refactorizar código existente.

5. **documenter**: Dedicado completamente a crear documentación técnica clara, visual y profesional.

6. **tester**: Dedicado completamente a diseñar, escribir y perfeccionar código de tests para tu aplicación.

## Sistema de Contexto Compartido

El sistema usa un enfoque de contexto compartido en lugar de briefs rígidos:

- **Stack tecnológico** - Lenguajes, frameworks, libs
- **Patrones usados** - Arquitectura, convenciones
- **Decisiones tomadas** - Por qué se eligió X o Y
- **Estado del proyecto** - Fase actual, qué falta
- **Preferencias** - Estilo del usuario, patrones favoritos
