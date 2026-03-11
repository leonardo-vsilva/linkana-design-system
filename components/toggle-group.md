## O que é
Grupo de Toggles relacionados. Permite seleção única ou múltipla dentro de um conjunto de opções.

## Quando usar / quando NÃO usar
- ✅ Filtros de tipo/categoria com seleção visual (ex: "Todos / Ativos / Inativos")
- ✅ Seleção de visualização (ex: lista / grid)
- ❌ Mais de 5 opções — use `Select` ou `Combobox`
- ❌ Seleção em formulário — use `RadioGroup` ou `Checkbox`

## Tipos
- `single`: apenas uma opção selecionada por vez
- `multiple`: múltiplas opções simultâneas

## Estrutura

```erb
<%= render RubyUI::ToggleGroup.new(type: :single, default_value: "all") do %>
  <%= render RubyUI::ToggleGroupItem.new(value: "all") { "Todos" } %>
  <%= render RubyUI::ToggleGroupItem.new(value: "active") { "Ativos" } %>
  <%= render RubyUI::ToggleGroupItem.new(value: "inactive") { "Inativos" } %>
<% end %>
```

## Regras
- ✅ Use `type: :single` como padrão.
- ✅ Defina `default_value` para estado inicial.
- ✅ Labels curtos: 1-2 palavras por item.
- ❌ Não misture ícones e texto nos itens do mesmo grupo.
