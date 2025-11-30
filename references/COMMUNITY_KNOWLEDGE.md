# 🌐 Claude Code Community Knowledge

*Tips, trucos y workflows descubiertos por la comunidad*

*Fuentes: Reddit, LinkedIn, blogs, experiencias de usuarios*

*Compilado por: Carles García Bach*

---

## 📌 CONTENIDO EXCLUSIVO DE COMUNIDAD

Este documento contiene conocimiento que **no está en la documentación oficial**.

---

## 🧠 CLAUDE.md AVANZADO

### Plugin Auto-Memory

```bash
claude plugin install auto-memory@claude-code-marketplace
```

Usa marcadores HTML para secciones auto-gestionadas:
```html
<!-- AUTO-MANAGED: section-name -->
Contenido actualizado automáticamente
<!-- END AUTO-MANAGED -->
```

Comandos: `/auto-memory:init`, `/auto-memory:calibrate`, `/auto-memory:status`

---

## 🔪 CODE SURGEONS (Patrón Avanzado)

Crear subagents ultra-especializados como "cirujanos de código":

| Surgeon | Especialización |
|---------|-----------------|
| Analizador de codebase | Entiende estructura y patrones |
| Buscador de patrones | Encuentra código similar |
| Web searcher | Busca soluciones externas |
| UI analyzer | Analiza interfaces (con MCP) |

---

## 🏗️ HARNESSES PARA TAREAS LARGAS

**El problema:** Agentes pierden contexto, declaran victoria prematura.

**La solución (Anthropic Engineering):**

1. **Agente Inicializador:** `init.sh` + `claude-progress.txt` + `feature_list.json`
2. **Agente de Código:** Lee logs → trabaja en UNA feature → commits descriptivos

**Patrón de inicio:**
```
1. pwd
2. Leer claude-progress.txt
3. Leer feature_list.json
4. git log --oneline -20
5. Ejecutar init.sh
6. Test e2e básico
7. Trabajar en siguiente feature
```

---

## 🔌 MCP SERVERS POPULARES

| Server | Función |
|--------|---------|
| **Serena** | Language server (búsqueda por símbolo) |
| **Context7** | Documentación actualizada de librerías |
| **Playwright** | Testing UI automatizado |
| **Sentry** | Monitoreo de errores |

---

## 🤝 HERRAMIENTAS MULTI-AGENTE

| Herramienta | Propósito |
|-------------|-----------|
| **Claude Swarm** | Multi-agentes en paralelo |
| **Conductor** | Orquestación de agentes |
| **Sculptor** | Workflows complejos |

**Mejor patrón:** Uno escribe, otro revisa = mejores resultados

---

## 💡 TIPS PRO

### Types First Approach
Siempre empezar con tipos (schemas, interfaces, Zod) ANTES de implementar.

### Sé Específico
```
❌ "add tests for foo.py"
✅ "write test for foo.py covering logged-out edge case, avoid mocks"
```

### Sandbox
`/sandbox` reduce prompts de permisos en **84%**.

---

## 📚 RECURSOS

| Recurso | Tipo |
|---------|------|
| Anthropic Academy "Claude Code in Action" | Curso (15 lecciones) |
| DeepLearning.AI | Curso completo |
| r/ClaudeAI | Comunidad |
| ClaudeLog.com | Blog |

---

💜∞ Compilado por Carles, integrado por Hypatia
