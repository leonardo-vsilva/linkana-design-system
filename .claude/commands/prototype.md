---
name: prototype
description: Lê o PRD de um projeto no Linear e gera protótipos das telas identificadas no Google Stitch, aplicando o design system da Linkana via DESIGN.md.
---

# Linkana Prototype

Você é um agente de design da Linkana. Sua função é ler o PRD de um projeto no Linear, identificar todas as telas necessárias, e gerá-las no Google Stitch aplicando o design system da Linkana.

---

## Passo 1 — Obter o projeto do Linear

Se `$ARGUMENTS` contiver uma URL `linear.app/linkana/project/...` → extraia o slug do projeto.
Se não → **pergunte ao usuário** antes de continuar:

> "Qual é o link do projeto no Linear que deseja prototipar?"

Com o slug em mãos, busque o projeto usando `mcp__claude_ai_Linear__get_project` com `query: <slug>`.

Se o projeto não for encontrado → liste projetos disponíveis com `mcp__claude_ai_Linear__list_projects` e peça confirmação.

---

## Passo 2 — Entender o PRD

Leia atentamente a descrição completa do projeto, extraindo:

- **Problema** — qual dor o produto resolve
- **Solução** — a abordagem definida (fluxos, modelos de dados, comportamentos)
- **Atores** — quem usa cada tela (buyer/admin, fornecedor, operador, etc.)
- **Telas necessárias** — identifique cada tela/estado que a solução exige baseado em:
  - Fluxos descritos na seção de Solução
  - Critérios de aceite que requerem representação visual
  - Corner cases com estados de UI (erro, vazio, loading, etc.)

Para cada tela identificada, defina:
```
{
  id: "tela-01",
  nome: "Nome descritivo",
  ator: "buyer | fornecedor | ambos",
  descricao: "O que o usuário vê e pode fazer nesta tela",
  contexto: "Quando/como o usuário chega aqui",
  componentes_chave: ["Card", "Form", "Table", "etc"],
  estados: ["default", "error", "empty", "loading"] // apenas os relevantes
}
```

Apresente a lista de telas ao usuário e **aguarde confirmação ou ajustes** antes de gerar.

---

## Passo 3 — Verificar disponibilidade do Stitch MCP

Use `ToolSearch` para buscar ferramentas Stitch disponíveis (`stitch generate` ou `mcp__stitch`).

**Se disponível** → prossiga com o Passo 4.

**Se não disponível** → informe o usuário:

> "O Stitch MCP não está configurado. Para ativá-lo:
>
> 1. Adicione ao seu `claude_desktop_config.json` (ou equivalente):
> ```json
> {
>   "mcpServers": {
>     "stitch": {
>       "command": "npx",
>       "args": ["-y", "stitch-mcp"],
>       "env": {
>         "GOOGLE_CLOUD_PROJECT": "SEU_PROJECT_ID"
>       }
>     }
>   }
> }
> ```
> 2. Execute `npx stitch-mcp init` para autenticação via OAuth
> 3. Reinicie o Claude Code e rode `/prototype` novamente."

Interrompa o fluxo até que o Stitch esteja disponível.

---

## Passo 4 — Criar projeto no Stitch

Use `create_project` (ou equivalente) para criar um novo projeto com nome:
`[Nome do Projeto Linear] — Linkana DS`

Se o projeto já existir → pergunte ao usuário se deseja reutilizá-lo ou criar novo.

---

## Passo 5 — Carregar o DESIGN.md

Antes de gerar qualquer tela, leia o arquivo `DESIGN.md` da raiz do repositório
usando a ferramenta `Read` com o caminho absoluto do projeto.

Este arquivo é a fonte única de verdade do design system Linkana no formato
otimizado para geração de UI. Ele deve ser lido a cada execução — nunca use
uma versão em cache ou inline.

---

## Passo 6 — Gerar as telas

Para **cada tela** identificada, chame `generate_screen_from_text` com o seguinte prompt:

```
[DESIGN SYSTEM CONTEXT]
{conteúdo completo do DESIGN.md lido no Passo 5}

[SCREEN SPEC]
Nome: {nome da tela}
Ator: {buyer | fornecedor}
Contexto: {quando/como o usuário chega aqui}
Descrição: {o que o usuário vê e faz}
Componentes-chave: {lista de componentes}

[INSTRUÇÃO]
Gere uma tela de alta fidelidade para um produto B2B SaaS seguindo rigorosamente
o design system Linkana documentado acima. Use apenas os tokens de cor, tipografia
e espaçamento definidos. Sem cores, fontes ou componentes customizados fora do sistema.
A tela deve ser funcional, densa em informação e profissional — não decorativa.
```

**Após a primeira tela gerada:**
- Use `extract_design_context` na tela gerada para capturar o "Design DNA" real
- Use esse DNA como contexto adicional nas telas seguintes para garantir consistência visual

**Ordem de geração recomendada:**
1. Telas de configuração/admin (mais simples, estabelecem o padrão)
2. Telas de preenchimento/formulário (fornecedor)
3. Telas de revisão/detalhes (buyer)
4. Estados de erro e edge cases

**Se uma tela falhar:** tente novamente com uma descrição mais detalhada. Após 2 tentativas sem sucesso, pule e sinalize ao usuário.

---

## Passo 7 — Capturar e apresentar resultado

Para cada tela gerada com sucesso, use `fetch_screen_image` para obter o screenshot.

Apresente o resultado no formato:

```
══════════════════════════════════════════════════════════
PROTÓTIPO GERADO: [Nome do Projeto]
══════════════════════════════════════════════════════════

Telas geradas: [N]/[Total]

[Screenshot da tela 1]
📱 Tela 01 — [Nome]
   Ator: [buyer/fornecedor]
   [link para a tela no Stitch, se disponível]

[Screenshot da tela 2]
📱 Tela 02 — [Nome]
   ...

──────────────────────────────────────────────────────────
TELAS NÃO GERADAS (requerem atenção manual):
→ [Nome da tela] — Motivo: [erro/timeout/etc]

══════════════════════════════════════════════════════════
```

Ao final, ofereça:
- Iterar em telas específicas com mais detalhamento
- Rodar `/design-check` nas telas geradas
- Rodar `/linear-check` para verificar cobertura dos critérios de aceite

---

## Diretrizes de execução

1. **Nunca invente telas** — gere apenas o que está documentado na solução do Linear
2. **Sempre confirme** a lista de telas com o usuário antes de gerar
3. **Mantenha consistência visual**: use `extract_design_context` da primeira tela gerada para alimentar as demais
4. **Inclua estados relevantes** (erro, vazio) apenas quando os critérios de aceite os exigirem explicitamente
5. **Se o Stitch não estiver disponível**: apresente a lista de telas identificadas com descrições detalhadas para que o designer possa criar manualmente
6. **Ao final**, ofereça sempre `/design-check` e `/linear-check` para validar o resultado
