## O que é
Tabela avançada com suporte a ordenação, filtro, paginação e seleção de linhas. Construída sobre o componente `Table`.

## Quando usar / quando NÃO usar
- ✅ Listagens principais de entidades (fornecedores, contratos, usuários)
- ✅ Quando o usuário precisa ordenar, filtrar ou paginar
- ❌ Listas simples sem interação — use `Table`
- ❌ Menos de 10 itens sem necessidade de filtro — use `Table`

## Anatomia

1. **Toolbar** — busca, filtros, botão de criar
2. **Table** — cabeçalho com ordenação + linhas de dados
3. **Pagination** — paginação inferior com contador

## Estrutura padrão de toolbar

```erb
<div class="flex items-center justify-between gap-4 mb-4">
  <div class="flex items-center gap-2">
    <%= render RubyUI::Input.new(placeholder: "Buscar...", class: "max-w-sm") %>
    <%# filtros adicionais via Select ou Combobox %>
  </div>
  <%= render RubyUI::Button.new { "Novo fornecedor" } %>
</div>
```

## Coluna de ações

A última coluna deve ter largura fixa e conter `DropdownMenu` com as ações da linha:

```erb
<%= render RubyUI::TableHead.new(class: "w-[50px]") { "" } %>
<%# célula: %>
<%= render RubyUI::TableCell.new do %>
  <%# DropdownMenu com: Editar, Visualizar, Excluir %>
<% end %>
```

## Regras
- ✅ Paginação padrão: 25 itens por página.
- ✅ Ordenação padrão: campo mais relevante (geralmente nome ou data de criação).
- ✅ Estado vazio: exiba mensagem "Nenhum [entidade] encontrado." com CTA de criar.
- ✅ Estado de loading: use `Skeleton` nas linhas da tabela.
- ❌ Não coloque mais de 2 ações diretas visíveis por linha — agrupe no DropdownMenu.
- ❌ Não use seleção de linha sem ação em lote disponível.

Veja também: `components/table.md`, `components/pagination.md`
