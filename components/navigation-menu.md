## O que é
Menu de navegação horizontal com suporte a submenus e conteúdo rico. Para navegação principal em páginas públicas/marketing.

## Quando usar / quando NÃO usar
- ✅ Navegação de páginas públicas (marketing, landing pages)
- ✅ Header navigation com mega-menus
- ❌ Navegação interna do produto — use `Sidebar`
- ❌ Menus de ação contextual — use `DropdownMenu`

## Estrutura

```erb
<%= render RubyUI::NavigationMenu.new do %>
  <%= render RubyUI::NavigationMenuList.new do %>
    <%= render RubyUI::NavigationMenuItem.new do %>
      <%= render RubyUI::NavigationMenuTrigger.new { "Produto" } %>
      <%= render RubyUI::NavigationMenuContent.new do %>
        <%# links e descrições %>
      <% end %>
    <% end %>
    <%= render RubyUI::NavigationMenuItem.new do %>
      <%= render RubyUI::NavigationMenuLink.new(href: pricing_path) { "Preços" } %>
    <% end %>
  <% end %>
<% end %>
```

## Regras
- ✅ Use `NavigationMenuLink` para links simples sem submenu.
- ✅ Use `NavigationMenuTrigger` + `NavigationMenuContent` para itens com submenu.
- ❌ Não use para navegação dentro do produto autenticado — use Sidebar.
