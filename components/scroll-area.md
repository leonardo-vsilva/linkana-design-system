## O que é
Container com scroll customizado e estilizado, substituindo o scroll nativo do browser.

## Quando usar / quando NÃO usar
- ✅ Listas longas dentro de containers com altura fixa (Popover, Sheet, Sidebar)
- ✅ Tabelas com scroll horizontal em viewports pequenos
- ✅ Painéis de conteúdo com altura máxima definida
- ❌ Página inteira — use scroll nativo do body
- ❌ Containers sem altura fixa

## Estrutura

```erb
<%= render RubyUI::ScrollArea.new(class: "h-72") do %>
  <%# conteúdo longo %>
<% end %>
```

## Regras
- ✅ Defina sempre uma altura fixa no ScrollArea (`h-72`, `h-96`, `max-h-[400px]`).
- ✅ Use `orientation: :horizontal` para scroll horizontal.
- ❌ Não use sem altura definida — o componente não terá efeito.
