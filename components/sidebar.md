## O que é
Painel de navegação lateral principal da aplicação. Contém links de navegação, logo e ações de usuário.

## Quando usar / quando NÃO usar
- ✅ Navegação principal do produto (sempre presente)
- ❌ Navegação secundária dentro de uma página — use `Tabs` ou `NavigationMenu`
- ❌ Painéis de conteúdo lateral — use `Sheet`

## Estrutura (composição completa)

```erb
<%= render RubyUI::SidebarProvider.new do %>
  <%= render RubyUI::Sidebar.new do %>
    <%= render RubyUI::SidebarHeader.new do %>
      <%# logo + nome do produto %>
    <% end %>
    <%= render RubyUI::SidebarContent.new do %>
      <%= render RubyUI::SidebarGroup.new do %>
        <%= render RubyUI::SidebarGroupLabel.new { "Principal" } %>
        <%= render RubyUI::SidebarMenu.new do %>
          <%= render RubyUI::SidebarMenuItem.new do %>
            <%= render RubyUI::SidebarMenuButton.new(href: suppliers_path) { "Fornecedores" } %>
          <% end %>
        <% end %>
      <% end %>
    <% end %>
    <%= render RubyUI::SidebarFooter.new do %>
      <%# menu de usuário %>
    <% end %>
  <% end %>
  <%= render RubyUI::SidebarInset.new do %>
    <%# conteúdo principal da página %>
  <% end %>
<% end %>
```

## Tokens de cor específicos
A sidebar usa seus próprios tokens: `--sidebar`, `--sidebar-foreground`, `--sidebar-primary`, `--sidebar-accent`, etc. Não use tokens genéricos dentro da sidebar.

## Regras
- ✅ Agrupe links com `SidebarGroup` + `SidebarGroupLabel`.
- ✅ Item ativo deve ter estado visual claro (geralmente `isActive` prop).
- ✅ Use `SidebarInset` para o conteúdo principal — garante o layout correto.
- ❌ Não coloque ações de página na sidebar — use o header ou toolbar da página.
