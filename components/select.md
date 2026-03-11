## O que é
Dropdown de seleção nativo estilizado. Permite escolher uma opção de uma lista fechada e conhecida.

## Quando usar / quando NÃO usar
- ✅ Listas fixas com 5+ opções (status, tipo, categoria)
- ✅ Quando o usuário não pode digitar — apenas selecionar
- ❌ Menos de 4 opções — use `RadioGroup`
- ❌ Busca dentro das opções necessária — use `Combobox`
- ❌ Múltipla seleção — use `Combobox` com multi-select

## Estrutura de composição

```erb
<%= render RubyUI::Select.new do %>
  <%= render RubyUI::SelectTrigger.new do %>
    <%= render RubyUI::SelectValue.new(placeholder: "Selecione...") %>
  <% end %>
  <%= render RubyUI::SelectContent.new do %>
    <%= render RubyUI::SelectItem.new(value: "active") { "Ativo" } %>
    <%= render RubyUI::SelectItem.new(value: "inactive") { "Inativo" } %>
  <% end %>
<% end %>
```

## Regras
- ✅ Sempre inclua um `placeholder` no `SelectValue`.
- ✅ Agrupe opções relacionadas com `SelectGroup` + `SelectLabel`.
- ✅ Sempre associe ao `Label` externo.
- ❌ Não use para listas com mais de ~50 itens sem busca — use `Combobox`.
