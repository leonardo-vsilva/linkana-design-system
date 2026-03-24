## O que é
Navegação por abas para alternar entre seções de conteúdo relacionado dentro da mesma página ou contexto.

## Quando usar / quando NÃO usar
- ✅ Seções de conteúdo mutuamente exclusivas numa mesma entidade (ex: Dados, Documentos, Histórico de um fornecedor)
- ✅ Contextos onde o usuário precisa comparar/alternar entre visões
- ❌ Navegação entre páginas diferentes — use links ou nav
- ❌ Mais de 6 abas — considere outra estrutura de navegação
- ❌ Conteúdos que devem ser vistos juntos — use seções na página
- ❌ Formulários com campos dependentes de seleção — use exibição condicional inline (ver abaixo)

### Tabs em formulários (não usar)

Evite usar abas como mecanismo de seleção dentro de formulários para expor campos dependentes de uma escolha do usuário (ex: tipo de fornecedor determinando quais campos aparecem).

Essa abordagem apresenta dois problemas:

1. **Usuários ignoram abas em formulários.** O fluxo natural de preenchimento é de cima para baixo. Abas horizontais saem desse caminho e costumam passar despercebidas.
2. **Comportamento ambíguo.** Não fica claro se as abas são mutuamente exclusivas. O usuário não sabe se o formulário vai enviar apenas os campos da aba ativa ou os de todas as abas preenchidas.

**Alternativa recomendada:** exibição condicional inline — mostre e oculte os campos diretamente na página conforme a seleção do usuário, sem mudar de aba ou de página.

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
