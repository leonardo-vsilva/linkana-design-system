## O que é?

Lista de seções expansíveis/colapsáveis. Cada item pode ser aberto individualmente para revelar conteúdo.

## Quando usar / quando NÃO usar

- ✅ FAQs, seções de ajuda
- ✅ Dados secundários que não precisam estar sempre visíveis
- ✅ Formulários longos com seções agrupadas
- ❌ Conteúdo crítico que o usuário sempre precisa ver — exiba diretamente
- ❌ Navegação — use `Tabs` ou `Sidebar`

## Tipos

- `single`: apenas 1 item aberto por vez
- `multiple`: múltiplos itens podem estar abertos simultaneamente

## Estrutura

```erb
<%= render RubyUI::Accordion.new(type: :single, collapsible: true) do %>
  <%= render RubyUI::AccordionItem.new(value: "item-1") do %>
    <%= render RubyUI::AccordionTrigger.new { "Documentação exigida" } %>
    <%= render RubyUI::AccordionContent.new do %>
      <%# conteúdo da seção %>
    <% end %>
  <% end %>
<% end %>
```

## Regras

- ✅ Use `type: :single` como padrão.
- ✅ Use `collapsible: true` para permitir fechar todos os itens.
- ✅ Trigger deve ser claro e descritivo — o usuário decide se precisa expandir.
- ❌ Não use para listas de menos de 3 itens — exiba diretamente.