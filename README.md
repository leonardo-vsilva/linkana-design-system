# Linkana Design System

Documentação oficial do design system da Linkana e ferramentas de AI para design e revisão.

**Stack:** Ruby on Rails · Tailwind CSS v4 · ruby_ui · tw-animate-css

---

## Princípios

- **Consistência acima de criatividade** — prefira componentes existentes a soluções ad-hoc
- **Sem cores hardcoded** — use apenas os tokens semânticos definidos
- **Dark mode sempre** — todos os componentes funcionam com a classe `.dark`
- **Semântica primeiro** — use o componente correto para o contexto (Button ≠ Link)

---

## Estrutura

```
DESIGN.md                 — design system em formato machine-readable (usado pelas AI skills)

tokens/
  colors.md               — tokens de cor (CSS custom properties)
  typography.md           — fonte, tamanhos, pesos
  radius.md               — escala de border-radius
  spacing.md              — espaçamento e containers

components/
  button.mdx              — Button: variantes, tamanhos, hierarquia
  [nome].mdx              — demais componentes

patterns/
  forms.md                — padrões de composição de formulários

.claude/
  commands/
    design-check.md       — skill /design-check
    linear-check.md       — skill /linear-check
    prototype.md          — skill /prototype
```

---

## AI Skills

Este repositório inclui slash commands para uso no **Claude Code** que automatizam fluxos de design system.

### `/design-check`

Audita código (Rails/ERB/HTML) ou um frame do Figma contra as regras do design system.

```
/design-check                          # analisa frame selecionado no Figma
/design-check app/views/supplier/...   # audita arquivo de código
```

Verifica: tokens de cor, espaçamento 8pt grid, tipografia, border radius, uso de componentes, padrões de formulário, dark mode, acessibilidade WCAG 2.1 e hierarquia de botões.

---

### `/linear-check`

Cruza as telas prototipadas no Figma com o projeto do Linear para verificar se o design resolve o problema, está alinhado à solução e cobre todos os critérios de aceite.

```
/linear-check https://linear.app/linkana/project/...
```

---

### `/prototype`

Lê o PRD de um projeto no Linear, identifica as telas necessárias e as gera no **Google Stitch** aplicando o design system Linkana via `DESIGN.md`.

```
/prototype                                          # pergunta a URL do Linear
/prototype https://linear.app/linkana/project/...  # usa o projeto informado
```

Requer o [Stitch MCP](https://stitch.withgoogle.com/docs/mcp/setup) configurado. Veja a seção de setup abaixo.

---

## DESIGN.md

O arquivo `DESIGN.md` na raiz é a representação machine-readable do design system — otimizado para geração de UI com o Google Stitch. Ele é a fonte única de verdade consumida pela skill `/prototype` em runtime.

A documentação humana (Mintlify) e o `DESIGN.md` devem ser atualizados juntos no mesmo PR sempre que o design system mudar.

---

## Setup do Stitch MCP

Para usar a skill `/prototype`, configure o Stitch MCP no Claude Code:

1. Adicione ao seu `claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "stitch": {
      "command": "npx",
      "args": ["-y", "stitch-mcp"],
      "env": {
        "GOOGLE_CLOUD_PROJECT": "SEU_PROJECT_ID"
      }
    }
  }
}
```

2. Execute a autenticação:

```bash
npx stitch-mcp init
```

3. Reinicie o Claude Code.

---

## Contribuindo

- PRs de mudança estrutural no design system passam por **Leo e Cidão**
- Ao alterar regras do DS: atualize `DESIGN.md` + o(s) arquivo(s) MDX relevante(s) no mesmo PR
- Branch protection ativa em `main` — todo merge via PR com squash

---

## Referências

- [shadcn/ui](https://ui.shadcn.com/docs/components)
- [ruby_ui](https://ruby-ui.com)
- [Tailwind CSS v4](https://tailwindcss.com/docs)
- [Google Stitch MCP](https://stitch.withgoogle.com/docs/mcp/setup)
