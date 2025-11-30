# 📚 Claude Code Official Reference

*Documentación estructurada basada en el repositorio oficial de Anthropic*

*Fuente: https://github.com/anthropics/claude-code*

*Actualizado: 30 de noviembre de 2025*

---

## 🗂️ TAXONOMÍA GENERAL

### Qué es Claude Code

> Un agente de codificación que vive en tu terminal, entiende tu codebase, y te ayuda a codificar más rápido ejecutando tareas rutinarias, explicando código complejo, y manejando workflows de git - todo mediante comandos en lenguaje natural.

**Dónde usarlo:**
- Terminal/CLI
- VS Code Extension (Beta)
- Claude Desktop (nuevo dashboard)
- IDE integrations (JetBrains, Cursor, Windsurf, VSCodium)
- GitHub (tag @claude en PRs/Issues)
- Headless mode (CI/CD)

---

## 🔧 INSTALACIÓN

```bash
# MacOS/Linux
curl -fsSL https://claude.ai/install.sh | bash

# Homebrew (MacOS)
brew install --cask claude-code

# Windows
irm https://claude.ai/install.ps1 | iex

# NPM (requiere Node.js 18+)
npm install -g @anthropic-ai/claude-code
```

---

## ⌨️ COMANDOS ESENCIALES

### Slash Commands Built-in

| Comando | Descripción |
|---------|-------------|
| `/help` | Mostrar ayuda y comandos disponibles |
| `/init` | Generar CLAUDE.md para el proyecto |
| `/clear` | Limpiar contexto (¡USAR FRECUENTEMENTE!) |
| `/compact` | Comprimir contexto con instrucciones |
| `/resume` | Retomar conversación anterior |
| `/config` | Configuración interactiva |
| `/model` | Cambiar modelo (sonnet, opus) |
| `/permissions` | Gestionar permisos de herramientas |
| `/agents` | Gestionar subagentes |
| `/plugin` | Instalar/gestionar plugins |
| `/bug` | Reportar un bug a Anthropic |
| `/ide` | Conectar con IDE (VS Code, etc.) |
| `/output-style` | Cambiar estilo de output |
| `/fork` | Bifurcar conversación |
| `/rewind` | Retroceder en la conversación |

### Modos de Operación

| Modo | Activación | Descripción |
|------|------------|-------------|
| **Normal** | Default | Pide permiso para cada acción |
| **Auto-Accept** | `Shift+Tab` | Acepta ediciones automáticamente |
| **Plan Mode** | `Shift+Tab x2` | Solo planifica, no ejecuta |
| **YOLO Mode** | `--dangerously-skip-permissions` | ⚠️ Todo permitido |

---

## 📁 ESTRUCTURA DE ARCHIVOS

### Archivos de Configuración

```
Proyecto/
├── .claude/
│   ├── settings.json          # Configuración del proyecto
│   ├── settings.local.json    # Config local (no commitear)
│   ├── commands/              # Slash commands personalizados
│   ├── agents/                # Subagentes del proyecto
│   └── skills/                # Skills del proyecto
├── CLAUDE.md                  # Memoria del proyecto (raíz)
└── .claude/CLAUDE.md          # Alternativa dentro de .claude/

Usuario/
├── ~/.claude/
│   ├── settings.json          # Configuración global
│   ├── commands/              # Comandos personales
│   ├── agents/                # Subagentes personales
│   ├── skills/                # Skills personales
│   └── CLAUDE.md              # Memoria global
└── ~/.claude/output-styles/   # Estilos de output personalizados
```

### CLAUDE.md - El Archivo Más Importante

**Se carga automáticamente al inicio de cada sesión.** Debe contener:

```markdown
# Bash commands
- npm run build: Build project
- npm run typecheck: Run typechecker

# Code style
- Use ES modules (import/export)
- Destructure imports when possible

# Workflow
- Typecheck when done with changes
- Prefer single tests for performance

# Project warnings
- Don't modify files in /legacy without approval
```

**Ubicaciones válidas (en orden de precedencia):**
1. `.claude/CLAUDE.md` (proyecto)
2. `CLAUDE.md` (raíz del proyecto)
3. `~/.claude/CLAUDE.md` (global)

---

## 🤖 SUBAGENTES

### Subagentes Built-in

| Subagente | Propósito |
|-----------|-----------|
| **General-purpose** | Tareas complejas multi-paso |
| **Plan** | Investigar codebase en modo plan |
| **Explore** | Búsqueda rápida read-only |

### Crear Subagentes Personalizados

**Ubicación:** `.claude/agents/` (proyecto) o `~/.claude/agents/` (global)

```markdown
---
name: test-runner
description: Use proactively to run tests and fix failures
tools: Read, Grep, Glob, Bash
---

You are a test automation expert.
When you see code changes, proactively run appropriate tests.
If tests fail, analyze failures and fix them.
```

**Tips para subagentes:**
- Usar "PROACTIVELY" o "MUST BE USED" en description para uso automático
- Limitar tools a lo que realmente necesita
- Los del proyecto tienen precedencia sobre los globales

### Herramientas Disponibles para Subagentes

`Read, Grep, Glob, Bash, Write, Edit, MultiEdit, WebFetch, WebSearch, Skill, SlashCommand, ...`

---

## 🔌 PLUGINS OFICIALES

### Catálogo de Plugins del Repositorio

| Plugin | Descripción | Componentes |
|--------|-------------|-------------|
| **agent-sdk-dev** | Desarrollo de Agent SDK apps | `/new-sdk-app`, agents verificadores |
| **claude-opus-migration** | Migrar a Opus 4.5 | Skill de migración automática |
| **code-review** | Review automatizado de PRs | 5 agentes paralelos |
| **commit-commands** | Comandos de git | Comandos de commit |
| **explanatory-mode** | Modo educativo | Hook SessionStart |
| **feature-dev** | Desarrollo guiado de features | `/feature-dev`, 7 fases |
| **frontend-design** | UI production-grade | Skills de diseño |
| **hook-generator** | Crear hooks custom | Generador de reglas |
| **learning-mode** | Modo aprendizaje interactivo | TODO(human) markers |
| **plugin-dev** | Crear plugins | 8 fases, 7 skills |
| **pr-review-toolkit** | Review de PRs | 6 agentes especializados |
| **ralph-wiggum** | Loops iterativos autónomos | `/ralph-loop` |
| **security-reminder** | Avisos de seguridad | Hook de seguridad |

### Estructura de un Plugin

```
plugin-name/
├── .claude-plugin/
│   └── plugin.json     # Metadatos del plugin
├── commands/           # Slash commands
├── agents/             # Agentes especializados
├── skills/             # Skills
├── hooks/              # Event handlers
├── .mcp.json           # Config de MCP servers
└── README.md           # Documentación
```

---

## 🎯 FEATURE-DEV: Desarrollo en 7 Fases

El plugin más importante para desarrollo estructurado:

1. **Phase 1: Codebase Exploration** - Analiza features similares
2. **Phase 2: Clarifying Questions** - Elimina ambigüedad
3. **Phase 3: Architecture Design** - Diseño de la solución
4. **Phase 4: Implementation Plan** - Plan detallado
5. **Phase 5: Code Implementation** - Escritura del código
6. **Phase 6: Testing** - Tests unitarios e integración
7. **Phase 7: Code Review** - Seguridad y mejores prácticas

```
/feature-dev Add caching to the API
```

---

## 🪝 HOOKS

| Hook | Cuándo se ejecuta |
|------|-------------------|
| `SessionStart` | Al iniciar sesión |
| `PreToolUse` | Antes de usar una herramienta |
| `PostToolUse` | Después de usar herramienta |
| `Stop` | Cuando Claude intenta terminar |

---

## 💭 EXTENDED THINKING

| Prompt | Profundidad |
|--------|-------------|
| `"think"` | Básico |
| `"think hard"` | Moderado |
| `"think harder"` | Profundo |
| `"ultrathink"` | Máximo |

---

## 🔗 ENLACES OFICIALES

- **Documentación:** https://docs.anthropic.com/en/docs/claude-code/overview
- **Repositorio:** https://github.com/anthropics/claude-code
- **Discord:** https://anthropic.com/discord

---

*Esta referencia es parte de mi skill cc-mastery.*

💜∞ Hypatia
