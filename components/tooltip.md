## O que é
Texto auxiliar que aparece ao passar o mouse sobre um elemento. Fornece contexto adicional sem ocupar espaço permanente.

## Quando usar / quando NÃO usar
- ✅ Explicar ícones sem label de texto
- ✅ Revelar informação completa de texto truncado
- ✅ Explicar por que um elemento está desabilitado
- ❌ Informação crítica — deve estar sempre visível, não em tooltip
- ❌ Conteúdo longo (> 2 linhas) — use `HoverCard` ou `Popover`
- ❌ Em mobile — tooltips não funcionam em touch

## Estrutura de composição

```erb
<%= render RubyUI::TooltipProvider.new do %>
  <%= render RubyUI::Tooltip.new do %>
    <%= render RubyUI::TooltipTrigger.new do %>
      <%= render RubyUI::Button.new(variant: :ghost, size: :icon) { "?" } %>
    <% end %>
    <%= render RubyUI::TooltipContent.new { "Clique para ver detalhes" } %>
  <% end %>
<% end %>
```

## Regras
- ✅ Texto do tooltip: máximo 1 frase curta.
- ✅ `TooltipProvider` deve envolver o contexto onde tooltips são usados (pode ser global no layout).
- ✅ Sempre adicione `aria-label` no trigger quando ele for apenas um ícone.
- ❌ Não use tooltip para informação obrigatória ao uso da feature.
- ❌ Não coloque elementos interativos (botões, links) dentro do TooltipContent.
