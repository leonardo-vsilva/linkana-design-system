## O que é
Menu que aparece ao clicar com o botão direito sobre um elemento. Ações contextuais para o item clicado.

## Quando usar / quando NÃO usar
- ✅ Ações em elementos de tabela ou lista com suporte a right-click
- ✅ Interface com paradigma de workspace (visual, drag-and-drop)
- ❌ Como único meio de acessar ações — sempre ofereça alternativa visível (DropdownMenu)
- ❌ Em mobile — right-click não existe em touch

## Estrutura

```erb
<%= render RubyUI::ContextMenu.new do %>
  <%= render RubyUI::ContextMenuTrigger.new do %>
    <%# elemento que recebe right-click %>
  <% end %>
  <%= render RubyUI::ContextMenuContent.new do %>
    <%= render RubyUI::ContextMenuItem.new { "Editar" } %>
    <%= render RubyUI::ContextMenuSeparator.new %>
    <%= render RubyUI::ContextMenuItem.new(class: "text-destructive") { "Excluir" } %>
  <% end %>
<% end %>
```

## Regras
- ✅ As ações do ContextMenu devem estar também disponíveis via DropdownMenu ou botões visíveis.
- ✅ Ações destrutivas no final, separadas.
- ❌ Não use como única forma de acessar funcionalidades críticas.
