## O que é
Campo de seleção de data que combina `Button` + `Popover` + `Calendar`. Padrão de seleção de data na Linkana.

## Quando usar / quando NÃO usar
- ✅ Qualquer seleção de data em formulário onde o contexto visual ajuda
- ✅ Seleção de range de datas (vigência de contrato, período de relatório)
- ❌ Data de nascimento ou datas muito específicas conhecidas — use `Input type="date"`

## Estrutura (composição)

```erb
<%= render RubyUI::Popover.new do %>
  <%= render RubyUI::PopoverTrigger.new do %>
    <%= render RubyUI::Button.new(variant: :outline) do %>
      <%= @date ? l(@date, format: :short) : "Selecione uma data" %>
    <% end %>
  <% end %>
  <%= render RubyUI::PopoverContent.new(class: "w-auto p-0") do %>
    <%= render RubyUI::Calendar.new(mode: :single, selected: @date) %>
  <% end %>
<% end %>
```

## Regras
- ✅ O trigger exibe a data formatada quando selecionada, ou placeholder quando vazio.
- ✅ Use locale brasileiro no formato da data: `dd/mm/aaaa`.
- ✅ Para range: exiba "01/01/2025 → 31/01/2025" no trigger.
- ❌ Não use input de texto livre para data — sempre use DatePicker ou `Input type="date"`.
