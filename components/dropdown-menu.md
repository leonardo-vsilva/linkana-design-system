## O que é
Menu flutuante de ações contextuais que abre a partir de um trigger (geralmente um botão). Agrupa múltiplas ações secundárias sem ocupar espaço permanente na interface.

## Quando usar / quando NÃO usar
- ✅ Menu de ações de um item de tabela ("Editar", "Duplicar", "Excluir")
- ✅ Menu de opções de usuário (perfil, configurações, logout)
- ✅ Quando há 3+ ações secundárias num mesmo contexto
- ❌ Menos de 2 ações — exiba os botões diretamente
- ❌ Ações primárias — use Button visível
- ❌ Navegação principal — use `NavigationMenu` ou `Sidebar`

## Estrutura de composição

```erb
<%= render RubyUI::DropdownMenu.new do %>
  <%= render RubyUI::DropdownMenuTrigger.new do %>
    <%= render RubyUI::Button.new(variant: :ghost, size: :icon) do %>
      <%# ícone de três pontos %>
    <% end %>
  <% end %>
  <%= render RubyUI::DropdownMenuContent.new do %>
    <%= render RubyUI::DropdownMenuItem.new { "Editar" } %>
    <%= render RubyUI::DropdownMenuItem.new { "Duplicar" } %>
    <%= render RubyUI::DropdownMenuSeparator.new %>
    <%= render RubyUI::DropdownMenuItem.new(class: "text-destructive") { "Excluir" } %>
  <% end %>
<% end %>
```

## Partes disponíveis
`DropdownMenuLabel`, `DropdownMenuSeparator`, `DropdownMenuGroup`, `DropdownMenuCheckboxItem`, `DropdownMenuRadioGroup`, `DropdownMenuRadioItem`, `DropdownMenuSub`

## Regras
- ✅ Ações destrutivas no final do menu, separadas por `DropdownMenuSeparator`.
- ✅ Ações destrutivas em `text-destructive`.
- ✅ Use `DropdownMenuLabel` para nomear grupos de ações.
- ✅ Trigger padrão para menus de linha de tabela: `Button ghost size="icon"` com ícone `...`.
- ❌ Não coloque mais de 8 itens sem agrupamento.
- ❌ Não use como alternativa a `Select` para escolha de valores.
