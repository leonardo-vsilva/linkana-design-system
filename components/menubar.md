## O que é
Barra de menus horizontal estilo desktop (File, Edit, View...). Navegação por menus em cascata.

## Quando usar / quando NÃO usar
- ✅ Aplicações desktop-like com múltiplos menus contextuais
- ✅ Edição de documentos, configurações avançadas
- ❌ Navegação principal de produto SaaS — use `Sidebar`
- ❌ Ações simples — use `Button` ou `DropdownMenu`

## Estrutura

```erb
<%= render RubyUI::Menubar.new do %>
  <%= render RubyUI::MenubarMenu.new do %>
    <%= render RubyUI::MenubarTrigger.new { "Arquivo" } %>
    <%= render RubyUI::MenubarContent.new do %>
      <%= render RubyUI::MenubarItem.new { "Novo" } %>
      <%= render RubyUI::MenubarSeparator.new %>
      <%= render RubyUI::MenubarItem.new { "Exportar" } %>
    <% end %>
  <% end %>
<% end %>
```

## Regras
- ✅ Máximo 5 menus na menubar.
- ✅ Agrupe itens relacionados com `MenubarSeparator`.
- ❌ Não use em contextos mobile.
