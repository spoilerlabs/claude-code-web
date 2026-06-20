# MCP de n8n para Claude Code Web

Este repo declara en [`.mcp.json`](.mcp.json) dos servidores MCP remotos (HTTP)
para que el agente de **Claude Code Web** (app de Claude → sección Código) pueda
crear y arreglar flujos en n8n desde el iPhone.

| Servidor MCP | Instancia | Endpoint |
|---|---|---|
| `n8n-dev` | desarrollo | `https://n8n-dev.raddo.cl/mcp-server/http` |
| `n8n-prod` | producción | `https://n8n.raddo.cl/mcp-server/http` |

## Variables de entorno requeridas (NO van en el repo)

El repo es **público**: los tokens nunca se escriben aquí. El `.mcp.json` los
referencia con `${...}` y el entorno cloud los inyecta en el header `Authorization`.

Hay que definir, en la **configuración de variables de entorno del entorno de
Claude Code Web**, estas dos:

| Variable | Valor |
|---|---|
| `N8N_DEV_TOKEN` | API key del MCP de n8n **dev** |
| `N8N_PROD_TOKEN` | API key del MCP de n8n **prod** |

Son los mismos tokens que ya se usan en la config MCP local de Claude Code
(header `Authorization: Bearer <token>` de cada instancia).

## Verificación

1. App de Claude → sección **Código** → repo `spoilerlabs/claude-code-web`.
2. Los servidores `n8n-dev` y `n8n-prod` deben aparecer disponibles.
3. Probar: "lista los workflows de n8n-dev" antes de tocar prod.

> Recomendación: probar siempre en `n8n-dev` antes de aplicar cambios en `n8n-prod`.
