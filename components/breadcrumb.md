## O que é
Trilha de navegação que mostra o caminho hierárquico até a página atual.

## Quando usar / quando NÃO usar
- ✅ Páginas aninhadas com mais de 2 níveis de profundidade
- ✅ Sempre que o usuário precisa saber "onde está" e voltar um nível
- ❌ Página raiz / dashboard — sem hierarquia para mostrar
- ❌ Hierarquias com apenas 1 nível de profundidade

## Estrutura

```erb
<%= render RubyUI::Breadcrumb.new do %>
  <%= render RubyUI::BreadcrumbList.new do %>
    <%= render RubyUI::BreadcrumbItem.new do %>
      <%= render RubyUI::BreadcrumbLink.new(href: root_path) { "Home" } %>
    <% end %>
    <%= render RubyUI::BreadcrumbSeparator.new %>
    <%= render RubyUI::BreadcrumbItem.new do %>
      <%= render RubyUI::BreadcrumbLink.new(href: suppliers_path) { "Fornecedores" } %>
    <% end %>
    <%= render RubyUI::BreadcrumbSeparator.new %>
    <%= render RubyUI::BreadcrumbItem.new do %>
      <%= render RubyUI::BreadcrumbPage.new { @supplier.name } %>
    <% end %>
  <% end %>
<% end %>
```

## Regras
- ✅ Último item usa `BreadcrumbPage` (não é link — é o item atual).
- ✅ Todos os itens anteriores são links clicáveis.
- ✅ Posicione o breadcrumb acima do título da página.
- ❌ Não truncar o último item (nome da entidade atual deve ser completo).
- ❌ Não usar mais de 4 níveis — simplifique a estrutura de navegação.
