## O que é
Controle de navegação entre páginas de um conjunto de dados paginado.

## Quando usar / quando NÃO usar
- ✅ Sempre que uma listagem tem mais itens que o limite por página
- ❌ Scroll infinito — use implementação customizada de infinite scroll
- ❌ Listas com < 25 itens — não pagine

## Estrutura

```erb
<%= render RubyUI::Pagination.new do %>
  <%= render RubyUI::PaginationContent.new do %>
    <%= render RubyUI::PaginationPrevious.new(href: path(page: @page - 1)) %>
    <%= render RubyUI::PaginationItem.new do %>
      <%= render RubyUI::PaginationLink.new(href: path(page: 1)) { "1" } %>
    <% end %>
    <%= render RubyUI::PaginationEllipsis.new %>
    <%= render RubyUI::PaginationNext.new(href: path(page: @page + 1)) %>
  <% end %>
<% end %>
```

## Regras
- ✅ Padrão: 25 itens por página. Máximo: 100.
- ✅ Exiba sempre o total de itens: "X-Y de Z resultados".
- ✅ Desabilite Previous na página 1 e Next na última página.
- ✅ Use `PaginationEllipsis` para reticências quando há muitas páginas.
- ❌ Não mostre a paginação quando há apenas 1 página.
