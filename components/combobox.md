## O que é
Campo de seleção com busca integrada. Combina `Popover` + `Command` para permitir filtrar e selecionar itens de uma lista.

## Quando usar / quando NÃO usar
- ✅ Seleção com busca em listas longas (> 10 itens)
- ✅ Múltipla seleção com busca
- ✅ Seleção de entidades dinâmicas (fornecedores, usuários, categorias)
- ❌ Listas curtas (< 10 itens) sem necessidade de busca — use `Select`
- ❌ Seleção binária — use `Switch` ou `Checkbox`

## Estrutura (composição de Popover + Command)

```erb
<%= render RubyUI::Popover.new do %>
  <%= render RubyUI::PopoverTrigger.new do %>
    <%= render RubyUI::Button.new(variant: :outline) do %>
      <%= selected_value.present? ? selected_value : "Selecione um fornecedor..." %>
    <% end %>
  <% end %>
  <%= render RubyUI::PopoverContent.new(class: "p-0") do %>
    <%= render RubyUI::Command.new do %>
      <%= render RubyUI::CommandInput.new(placeholder: "Buscar fornecedor...") %>
      <%= render RubyUI::CommandList.new do %>
        <%= render RubyUI::CommandEmpty.new { "Nenhum fornecedor encontrado." } %>
        <%= render RubyUI::CommandGroup.new do %>
          <% @suppliers.each do |supplier| %>
            <%= render RubyUI::CommandItem.new(value: supplier.id) { supplier.name } %>
          <% end %>
        <% end %>
      <% end %>
    <% end %>
  <% end %>
<% end %>
```

## Regras
- ✅ O trigger do Popover deve exibir o valor selecionado (ou placeholder).
- ✅ `CommandEmpty` obrigatório com mensagem clara de "sem resultados".
- ✅ Para busca server-side, use debounce de 300ms antes de disparar a requisição.
- ❌ Não use para listas com < 10 itens — prefira `Select`.
