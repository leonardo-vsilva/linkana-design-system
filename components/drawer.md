## O que é
Painel deslizante otimizado para mobile. Abre a partir da borda inferior da tela (padrão) com gesto de arrastar para fechar.

## Quando usar / quando NÃO usar
- ✅ Painéis de ação em mobile (filtragem, seleção, confirmação)
- ✅ Substituição de Sheet em viewports móveis
- ❌ Em desktop — use `Sheet` ou `Dialog`
- ❌ Formulários longos em mobile — prefira página dedicada

## Estrutura

```erb
<%= render RubyUI::Drawer.new do %>
  <%= render RubyUI::DrawerTrigger.new do %>
    <%= render RubyUI::Button.new { "Filtros" } %>
  <% end %>
  <%= render RubyUI::DrawerContent.new do %>
    <%= render RubyUI::DrawerHeader.new do %>
      <%= render RubyUI::DrawerTitle.new { "Filtros" } %>
    <% end %>
    <%# conteúdo %>
    <%= render RubyUI::DrawerFooter.new do %>
      <%= render RubyUI::Button.new { "Aplicar" } %>
      <%= render RubyUI::DrawerClose.new do %>
        <%= render RubyUI::Button.new(variant: :outline) { "Cancelar" } %>
      <% end %>
    <% end %>
  <% end %>
<% end %>
```

## Regras
- ✅ Sempre inclua `DrawerTitle` para acessibilidade.
- ✅ Inclua `DrawerClose` no footer como alternativa ao gesto de arrastar.
- ❌ Não use Drawer em desktop — use Sheet.
