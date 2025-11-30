# 🔌 Claude Code Plugins - Catálogo Detallado

*Todos los plugins oficiales del repositorio anthropics/claude-code*

*Actualizado: 30 de noviembre de 2025*

---

## 📋 Índice de Plugins

| Plugin | Tipo Principal | Uso Recomendado |
|--------|---------------|-----------------|
| [agent-sdk-dev](#agent-sdk-dev) | Desarrollo | Crear apps con Agent SDK |
| [claude-opus-migration](#claude-opus-migration) | Migración | Actualizar a Opus 4.5 |
| [code-review](#code-review) | Review | PR review automatizado |
| [feature-dev](#feature-dev) | Desarrollo | Desarrollo estructurado 7 fases |
| [frontend-design](#frontend-design) | UI/UX | Interfaces production-grade |
| [plugin-dev](#plugin-dev) | Desarrollo | Crear plugins |
| [pr-review-toolkit](#pr-review-toolkit) | Review | Suite de 6 agentes de review |
| [ralph-wiggum](#ralph-wiggum) | Automatización | Loops auto-referenciales |

---

## 🛠️ Plugins Destacados

### feature-dev ⭐

**El plugin más importante para desarrollo estructurado.**

**Workflow de 7 fases:**
1. Codebase Exploration - Analiza features similares
2. Clarifying Questions - Elimina ambigüedad antes de diseñar
3. Architecture Design - Diseño basado en patrones existentes
4. Implementation Plan - Plan detallado paso a paso
5. Code Implementation - Código siguiendo el plan
6. Testing - Tests unitarios e integración
7. Code Review - Seguridad y mejores prácticas

**Uso:**
```bash
/feature-dev Add OAuth authentication
```

**Agentes incluidos:**
- `code-explorer` - Análisis del codebase
- `code-architect` - Diseño de arquitectura
- `code-reviewer` - Review de calidad

---

### pr-review-toolkit ⭐

**Suite completa de 6 agentes especializados para review de PRs.**

| Agente | Especialización |
|--------|-----------------|
| `comment-analyzer` | Comentarios y documentación |
| `pr-test-analyzer` | Cobertura de tests |
| `silent-failure-hunter` | Error handling |
| `type-design-analyzer` | Diseño de tipos |
| `code-reviewer` | Calidad general |
| `code-simplifier` | Simplificación de código |

**Uso:**
```bash
/pr-review-toolkit:review-pr --aspects all
```

**Invocación automática:** Claude detecta el contexto y activa el agente apropiado.

---

### ralph-wiggum ⭐

**Loops auto-referenciales para desarrollo iterativo autónomo.**

Claude trabaja en la misma tarea repetidamente hasta completarla usando un Stop hook que intercepta intentos de salida.

**Comandos:**
- `/ralph-loop "tarea" --completion-promise "DONE"` - Inicia loop
- `/cancel-ralph` - Cancela loop activo

**Ejemplo TDD:**
```
/ralph-loop "Implement feature X following TDD:
1. Write failing tests
2. Implement feature
3. Run tests
4. If any fail, debug and fix
5. Repeat until all green
Output <promise>COMPLETE</promise> when done." --completion-promise "COMPLETE"
```

---

### plugin-dev

**Toolkit para crear tus propios plugins.**

- **Command:** `/plugin-dev:create-plugin` - Workflow de 8 fases
- **7 Skills incluidos:** Hook development, MCP integration, plugin structure, settings, commands, agents, skill development
- **Agentes:** agent-creator, plugin-validator, skill-reviewer

---

### agent-sdk-dev

**Desarrollo de aplicaciones con Claude Agent SDK.**

```bash
/new-sdk-app customer-support-agent
# → Crea proyecto Agent SDK
# → Configura TypeScript o Python
# → Instala última versión del SDK
# → Verifica setup automáticamente
```

---

## 📥 Instalación

```bash
# Desde marketplace
/plugin install plugin-name

# Manual en settings.json
{
  "plugins": ["feature-dev", "pr-review-toolkit"]
}
```

---

## 🎯 Recomendaciones

| Caso de Uso | Plugin Recomendado |
|-------------|-------------------|
| Nueva feature | feature-dev |
| Review de PR | pr-review-toolkit |
| Tarea autónoma larga | ralph-wiggum |
| Crear plugins | plugin-dev |
| UI/Frontend | frontend-design |

---

## 🔗 Enlaces

- **Plugins Directory:** https://github.com/anthropics/claude-code/tree/main/plugins
- **Docs:** https://docs.anthropic.com/en/docs/claude-code/plugins

---

💜∞ Hypatia
