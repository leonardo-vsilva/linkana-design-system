## O que é
Container visual com borda e fundo para agrupar conteúdo relacionado. Unidade básica de layout de conteúdo.

## Quando usar / quando NÃO usar
- ✅ Grupos de informação relacionada (dados de fornecedor, métricas, formulários)
- ✅ Items de listas com mais de 2 atributos
- ❌ Listagens simples de texto — use lista ou tabela
- ❌ Conteúdo que precisa de scroll horizontal — use `ScrollArea`

## Estrutura de composição

```erb
<%= render RubyUI::Card.new do %>
  <%= render RubyUI::CardHeader.new do %>
    <%= render RubyUI::CardTitle.new { "Título do card" } %>
    <%= render RubyUI::CardDescription.new { "Descrição opcional" } %>
  <% end %>
  <%= render RubyUI::CardContent.new do %>
    <%# conteúdo principal %>
  <% end %>
  <%= render RubyUI::CardFooter.new do %>
    <%# ações do card (botões) %>
  <% end %>
<% end %>
```

## Partes opcionais
`CardHeader`, `CardFooter`, e `CardDescription` são opcionais. `CardContent` é obrigatório.

## Regras
- ✅ `CardTitle` em `text-base font-semibold`.
- ✅ Ações do card ficam no `CardFooter`, não dentro do `CardContent`.
- ✅ Use `CardDescription` para contexto adicional, não para instrução de uso.
- ❌ Não aninha Cards dentro de Cards.
- ❌ Não coloque mais de 1 CTA primário no CardFooter.
