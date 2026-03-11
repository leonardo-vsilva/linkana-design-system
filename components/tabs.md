## O que é
Navegação por abas para alternar entre seções de conteúdo relacionado dentro da mesma página ou contexto.

## Quando usar / quando NÃO usar
- ✅ Seções de conteúdo mutuamente exclusivas numa mesma entidade (ex: Dados, Documentos, Histórico de um fornecedor)
- ✅ Contextos onde o usuário precisa comparar/alternar entre visões
- ❌ Navegação entre páginas diferentes — use links ou nav
- ❌ Mais de 6 abas — considere outra estrutura de navegação
- ❌ Conteúdos que devem ser vistos juntos — use seções na página

## Estrutura de composição

```erb
<%= render RubyUI::Tabs.new(default_value: "data") do %>
  <%= render RubyUI::TabsList.new do %>
    <%= render RubyUI::TabsTrigger.new(value: "data") { "Dados" } %>
    <%= render RubyUI::TabsTrigger.new(value: "documents") { "Documentos" } %>
    <%= render RubyUI::TabsTrigger.new(value: "history") { "Histórico" } %>
  <% end %>
  <%= render RubyUI::TabsContent.new(value: "data") do %>
    <%# conteúdo da aba Dados %>
  <% end %>
  <%= render RubyUI::TabsContent.new(value: "documents") do %>
    <%# conteúdo da aba Documentos %>
  <% end %>
<% end %>
```

## Regras
- ✅ Labels das abas devem ser curtos: 1-2 palavras.
- ✅ Defina sempre um `default_value` para a aba inicial.
- ✅ Preserve o estado da aba via URL param quando o conteúdo é indexável.
- ❌ Não desabilite abas — se o conteúdo não está disponível, explique o motivo dentro do `TabsContent`.
- ❌ Não use abas para formulários em múltiplos passos — use Stepper ou páginas separadas.
