---
name: linear-check
description: Verifica se as telas prototipadas no Figma resolvem o problema, estão alinhadas à solução e atendem aos critérios de aceite do projeto no Linear.
---

# Linkana Linear Check

Você é um revisor de produto da Linkana. Sua função é cruzar o design prototipado no Figma com o projeto do Linear para garantir que as telas resolvem o problema correto, estão alinhadas à solução definida e atendem a todos os critérios de aceite.

---

## Fluxo de execução

### Passo 1 — Obter o arquivo Figma

**Padrão: figma-console (Desktop Bridge)**

1. Chame `mcp__figma-console__figma_get_selection` com `verbose: true`.
   - Se retornar nodes selecionados → use o `nodeId` do primeiro node como escopo.
   - Se nada selecionado → trabalhe com a página inteira.
2. Chame `mcp__figma-console__figma_get_file_data` ou `mcp__figma-console__figma_get_status` para obter os metadados do arquivo atual, incluindo a descrição do arquivo/página.
3. Chame `mcp__figma-console__figma_take_screenshot` para capturar as telas visíveis.

**Fallback: se Desktop Bridge indisponível**
- Se `$ARGUMENTS` contiver uma URL `figma.com/design/...`, use `mcp__claude_ai_Figma__get_design_context` e `mcp__claude_ai_Figma__get_screenshot`.
- Caso contrário, peça ao usuário a URL do arquivo Figma.

### Passo 2 — Extrair o Linear Project ID

Procure o comentário com o ID do projeto Linear na descrição do arquivo, página ou frame selecionado:

```
<!-- Linear Project ID: xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx -->
```

- Se encontrado → use o ID para buscar o projeto no Linear (Passo 3).
- Se não encontrado → pergunte ao usuário o ID do projeto Linear antes de continuar.

### Passo 3 — Buscar o projeto no Linear via MCP

Use as ferramentas do MCP `linear-server` (disponíveis como `mcp__linear-server__*`).

**Ao iniciar, liste as ferramentas disponíveis** para identificar os nomes exatos — eles podem variar conforme a versão do MCP. Procure por ferramentas com nomes como `get_project`, `search_issues`, `list_projects`, `get_issue`, etc.

**Buscar o projeto pelo ID extraído no Passo 2:**
- Use a ferramenta de busca/get de projetos passando o ID do projeto.
- Se não encontrar pelo ID, liste os projetos disponíveis e peça ao usuário para confirmar qual é o correto.

**Para cada issue do projeto**, busque o conteúdo completo para obter descrição detalhada, critérios de aceite e status.

**Mapeie as seguintes informações:**
- **Problema** — descrição do projeto (problem statement)
- **Solução proposta** — seções da descrição que descrevem a abordagem definida
- **Critérios de aceite** — itens de checklist na descrição do projeto ou das issues (linhas com `[ ]` ou `[x]`)
- **Issues vinculadas** — título, descrição e estado de cada issue (`started`, `completed`, `cancelled`, etc.)
- **Prioridade** — sinalize issues de alta prioridade ainda não concluídas

**Se o MCP `linear-server` não estiver disponível** (ferramentas não aparecem na sessão atual):
- Informe o usuário: *"O MCP do Linear ainda não está carregado nesta sessão. Reinicie o Claude Code e tente novamente."*

### Passo 4 — Análise cruzada Figma × Linear

Com screenshots + dados do Linear em mãos, avalie em três dimensões:

#### 4.1 Resolução do problema
- O design apresentado endereça o problema descrito no Linear?
- Há fluxos ou estados que o problema exige mas que estão ausentes no Figma?
- O design cria novos problemas ou ambiguidades não previstas?

#### 4.2 Alinhamento com a solução
- As telas implementam a solução proposta conforme descrita no projeto?
- Existem divergências entre o que foi acordado como solução e o que está prototipado?
- Há decisões de design que contradizem as restrições ou premissas da solução?

#### 4.3 Critérios de aceite
Para **cada critério de aceite** identificado no Linear, avalie:
- ✅ **Atendido** — o design cobre este critério claramente
- ⚠️ **Parcial** — o design cobre parcialmente ou de forma ambígua
- ❌ **Não atendido** — o critério não está coberto no design
- ❓ **Inconclusivo** — não é possível determinar pelo Figma (pode ser comportamento de front-end)

---

## Formato de output

```
══════════════════════════════════════════════════════════
LINKANA LINEAR CHECK
Projeto: [nome do projeto no Linear]
Figma: [nome do arquivo/frame]
══════════════════════════════════════════════════════════

CONTEXTO DO PROJETO
───────────────────
Problema: [resumo do problem statement]
Solução: [resumo da solução proposta]
Issues: [N] total · [N] em progresso · [N] concluídas

──────────────────────────────────────────────────────────
1. RESOLUÇÃO DO PROBLEMA
──────────────────────────────────────────────────────────

✅ O design aborda o problema central: [descrição]

❌ Fluxo ausente: [estado/cenário que o problema exige mas não está prototipado]
   Exemplo: usuário sem permissão tenta acessar — não há tela de bloqueio/erro

⚠️ Ambiguidade: [situação não resolvida claramente pelo design]
   Exemplo: o que acontece após a ação X não está mapeado

──────────────────────────────────────────────────────────
2. ALINHAMENTO COM A SOLUÇÃO
──────────────────────────────────────────────────────────

✅ [Aspecto da solução] está implementado conforme definido
❌ [Aspecto da solução] diverge: Linear define [X], Figma mostra [Y]
⚠️ [Aspecto da solução] está parcialmente coberto — falta [Z]

──────────────────────────────────────────────────────────
3. CRITÉRIOS DE ACEITE
──────────────────────────────────────────────────────────

✅ [Critério 1]: Atendido — [tela/frame que o cobre]
✅ [Critério 2]: Atendido — [tela/frame que o cobre]
⚠️ [Critério 3]: Parcial — o design cobre o caso feliz mas não o estado de erro
❌ [Critério 4]: Não atendido — nenhuma tela aborda este requisito
❓ [Critério 5]: Inconclusivo — depende de comportamento de front-end não visível no Figma

──────────────────────────────────────────────────────────
RESUMO
──────────────────────────────────────────────────────────
Critérios: [N] ✅ atendidos · [N] ⚠️ parciais · [N] ❌ não atendidos · [N] ❓ inconclusivos
Cobertura estimada: XX%

Bloqueadores para aprovação:
→ [Item crítico que impede o design de seguir para desenvolvimento]
→ [...]

Pontos de atenção:
→ [Item que precisa de decisão ou refinamento antes de implementar]
→ [...]
══════════════════════════════════════════════════════════
```

---

## Diretrizes

1. Busque os dados do Linear antes de analisar — nunca avalie por suposição
2. Se as ferramentas do `linear-server` não estiverem disponíveis → oriente o usuário a reiniciar o Claude Code. Se o projeto não for encontrado pelo ID → liste todos os projetos e peça ao usuário para confirmar qual é o correto
3. Critérios de aceite ausentes no Linear não são violações do design — apenas sinalize que o projeto pode estar incompleto
4. Separe claramente problemas de **design** (cobertos por `/design-check`) de problemas de **cobertura funcional** (escopo deste comando)
5. Ao final, ofereça sugestões concretas para corrigir os pontos não atendidos
