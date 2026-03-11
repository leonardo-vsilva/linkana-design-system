## O que é
Painéis com divisor arrastável que permite ao usuário redimensionar as seções horizontalmente ou verticalmente.

## Quando usar / quando NÃO usar
- ✅ Layouts com painel de lista + painel de detalhe (master-detail)
- ✅ Editores com painel de código + painel de preview
- ❌ Layouts simples sem necessidade de redimensionamento
- ❌ Mobile — não há suporte adequado a drag em touch

## Estrutura

```erb
<%= render RubyUI::ResizablePanelGroup.new(direction: :horizontal) do %>
  <%= render RubyUI::ResizablePanel.new(default_size: 30) do %>
    <%# painel esquerdo %>
  <% end %>
  <%= render RubyUI::ResizableHandle.new %>
  <%= render RubyUI::ResizablePanel.new(default_size: 70) do %>
    <%# painel direito %>
  <% end %>
<% end %>
```

## Regras
- ✅ Defina `default_size` em porcentagem para cada painel.
- ✅ Defina `min_size` para evitar painéis inutilizáveis.
- ✅ Use `with_handle: true` no `ResizableHandle` para exibir o indicador visual.
