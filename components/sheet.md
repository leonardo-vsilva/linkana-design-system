## O que é
Painel lateral deslizante (drawer lateral) que aparece sobre o conteúdo sem substituir a página. Variante do Dialog que vem de uma das bordas da tela.

## Quando usar / quando NÃO usar
- ✅ Formulários de edição que precisam de mais espaço que um Dialog
- ✅ Painéis de detalhes de um item mantendo a lista visível ao fundo
- ✅ Filtros avançados de uma listagem
- ❌ Ações simples de confirmação — use `Dialog` ou `AlertDialog`
- ❌ Conteúdo principal da página — use página dedicada
- ❌ Em mobile com conteúdo scrollável complexo — prefira `Drawer`

## Lados disponíveis
`right` (padrão), `left`, `top`, `bottom`

## Estrutura de composição

```erb
<%= render RubyUI::Sheet.new do %>
  <%= render RubyUI::SheetTrigger.new do %>
    <%= render RubyUI::Button.new { "Editar fornecedor" } %>
  <% end %>
  <%= render RubyUI::SheetContent.new(side: :right) do %>
    <%= render RubyUI::SheetHeader.new do %>
      <%= render RubyUI::SheetTitle.new { "Editar fornecedor" } %>
      <%= render RubyUI::SheetDescription.new { "Atualize os dados do fornecedor." } %>
    <% end %>
    <%# formulário ou conteúdo %>
    <%= render RubyUI::SheetFooter.new do %>
      <%= render RubyUI::Button.new { "Salvar" } %>
    <% end %>
  <% end %>
<% end %>
```

## Regras
- ✅ Use `side: :right` como padrão.
- ✅ Sempre inclua `SheetTitle` para acessibilidade.
- ✅ Ações no `SheetFooter` — não dentro do conteúdo.
- ❌ Não abra Sheet dentro de Sheet.
- ❌ Não use para fluxos com mais de 2 etapas.
