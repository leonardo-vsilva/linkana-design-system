## O que é
Painel flutuante ancorado a um trigger. Similar ao Tooltip mas pode conter conteúdo interativo.

## Quando usar / quando NÃO usar
- ✅ Filtros rápidos (date range picker, multi-select)
- ✅ Informações detalhadas com interação (ex: preview de entidade)
- ✅ Formulários pequenos ancorados a um campo
- ❌ Conteúdo simples sem interação — use `Tooltip`
- ❌ Conteúdo grande ou formulário complexo — use `Sheet` ou `Dialog`
- ❌ Menu de ações — use `DropdownMenu`

## Estrutura

```erb
<%= render RubyUI::Popover.new do %>
  <%= render RubyUI::PopoverTrigger.new do %>
    <%= render RubyUI::Button.new(variant: :outline) { "Filtrar" } %>
  <% end %>
  <%= render RubyUI::PopoverContent.new do %>
    <%# conteúdo interativo %>
  <% end %>
<% end %>
```

## Regras
- ✅ Popover fecha ao clicar fora (comportamento padrão — não sobrescreva).
- ✅ Defina `align` (start, center, end) conforme posição do trigger na tela.
- ❌ Não coloque scrollable content longo em Popover.
