## O que é
Palette de comando com busca integrada. Interface de busca/navegação rápida por teclado.

## Quando usar / quando NÃO usar
- ✅ Busca global na aplicação (cmd+k)
- ✅ Seleção de itens com busca em listas longas (base do `Combobox`)
- ❌ Selects simples com < 10 opções — use `Select`
- ❌ Navegação principal — use `Sidebar` ou `NavigationMenu`

## Estrutura

```erb
<%= render RubyUI::Command.new do %>
  <%= render RubyUI::CommandInput.new(placeholder: "Buscar...") %>
  <%= render RubyUI::CommandList.new do %>
    <%= render RubyUI::CommandEmpty.new { "Nenhum resultado." } %>
    <%= render RubyUI::CommandGroup.new(heading: "Fornecedores") do %>
      <%= render RubyUI::CommandItem.new(value: "acme") { "Acme Corp" } %>
    <% end %>
  <% end %>
<% end %>
```

## Regras
- ✅ Sempre defina `CommandEmpty` com mensagem de estado vazio.
- ✅ Agrupe itens com `CommandGroup` e `heading` descritivo.
- ✅ Geralmente usado dentro de `Popover` ou `Dialog` para o cmd+k global.
