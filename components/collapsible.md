## O que é
Seção expansível/colapsável simples. Versão primitiva e sem estilo do Accordion — para um único item.

## Quando usar / quando NÃO usar
- ✅ Uma seção opcional que o usuário pode expandir para ver mais detalhes
- ✅ "Ver mais" de conteúdo longo
- ❌ Múltiplas seções — use `Accordion`
- ❌ Quando o conteúdo é sempre importante — exiba diretamente

## Estrutura

```erb
<%= render RubyUI::Collapsible.new do %>
  <%= render RubyUI::CollapsibleTrigger.new do %>
    <%= render RubyUI::Button.new(variant: :ghost, size: :sm) { "Ver detalhes" } %>
  <% end %>
  <%= render RubyUI::CollapsibleContent.new do %>
    <%# conteúdo expansível %>
  <% end %>
<% end %>
```

## Regras
- ✅ O trigger deve indicar claramente que há conteúdo a ser expandido.
- ✅ Use ícone de chevron que rotaciona para indicar estado.
- ❌ Não use para conteúdo crítico ao uso.
