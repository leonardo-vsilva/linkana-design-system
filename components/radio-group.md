## O que é
Grupo de opções mutuamente exclusivas. O usuário pode selecionar apenas uma.

## Quando usar / quando NÃO usar
- ✅ Escolha entre 2-5 opções mutuamente exclusivas bem definidas
- ✅ Quando todas as opções devem ser visíveis simultaneamente para comparação
- ❌ Mais de 5 opções — use `Select`
- ❌ Múltipla seleção — use `Checkbox`
- ❌ Toggle simples on/off — use `Switch`

## Estrutura

```erb
<%= render RubyUI::RadioGroup.new(default_value: "active") do %>
  <div class="flex items-center gap-2">
    <%= render RubyUI::RadioGroupItem.new(value: "active", id: "active") %>
    <%= render RubyUI::Label.new(for: "active") { "Ativo" } %>
  </div>
  <div class="flex items-center gap-2">
    <%= render RubyUI::RadioGroupItem.new(value: "inactive", id: "inactive") %>
    <%= render RubyUI::Label.new(for: "inactive") { "Inativo" } %>
  </div>
<% end %>
```

## Regras
- ✅ Sempre defina um `default_value`.
- ✅ Cada item deve ter um `Label` associado via `for/id`.
- ✅ Apresente as opções em ordem lógica (mais provável primeiro, ou ordem alfabética).
- ❌ Não use para listas longas — use `Select`.
