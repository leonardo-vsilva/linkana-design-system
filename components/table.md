## O que é
Componente de tabela estilizado para exibição de dados estruturados em linhas e colunas.

## Quando usar / quando NÃO usar
- ✅ Listagem de entidades com múltiplos atributos (fornecedores, contratos, usuários)
- ✅ Dados comparativos
- ❌ Menos de 3 colunas com 1-2 itens — use `Card`
- ❌ Dados hierárquicos profundos — use árvore ou acordeon

## Estrutura de composição

```erb
<%= render RubyUI::Table.new do %>
  <%= render RubyUI::TableHeader.new do %>
    <%= render RubyUI::TableRow.new do %>
      <%= render RubyUI::TableHead.new { "Nome" } %>
      <%= render RubyUI::TableHead.new { "Status" } %>
      <%= render RubyUI::TableHead.new { "CNPJ" } %>
    <% end %>
  <% end %>
  <%= render RubyUI::TableBody.new do %>
    <% @suppliers.each do |supplier| %>
      <%= render RubyUI::TableRow.new do %>
        <%= render RubyUI::TableCell.new { supplier.name } %>
        <%= render RubyUI::TableCell.new { supplier.status } %>
        <%= render RubyUI::TableCell.new { supplier.cnpj } %>
      <% end %>
    <% end %>
  <% end %>
<% end %>
```

## Regras
- ✅ `TableHead` com texto descritivo e conciso (1-3 palavras).
- ✅ Coluna de ações (editar, excluir) sempre na última coluna à direita.
- ✅ Dados numéricos alinhados à direita: `class="text-right"`.
- ✅ Tabelas longas: envolva em `ScrollArea` para scroll horizontal.
- ✅ Para tabelas com busca, filtros e paginação: use o padrão `DataTable`.
- ❌ Não use Table para < 5 linhas de conteúdo simples — use lista ou Cards.
- ❌ Não coloque mais de 8-10 colunas visíveis sem mecanismo de ocultar colunas.
