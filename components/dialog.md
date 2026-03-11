## O que é
Modal que aparece sobre o conteúdo principal para capturar atenção em ações que requerem foco ou confirmação.

## Quando usar / quando NÃO usar
- ✅ Formulários de criação/edição rápida
- ✅ Confirmações de ação (não destrutiva — para destrutiva use `AlertDialog`)
- ✅ Detalhes de um item sem sair da página atual
- ❌ Fluxos complexos com múltiplos passos — use página dedicada
- ❌ Confirmação de exclusão — use `AlertDialog`
- ❌ Conteúdo que precisa de contexto lateral — use `Sheet`

## Estrutura de composição

```erb
<%= render RubyUI::Dialog.new do %>
  <%= render RubyUI::DialogTrigger.new do %>
    <%= render RubyUI::Button.new { "Abrir" } %>
  <% end %>
  <%= render RubyUI::DialogContent.new do %>
    <%= render RubyUI::DialogHeader.new do %>
      <%= render RubyUI::DialogTitle.new { "Título" } %>
      <%= render RubyUI::DialogDescription.new { "Descrição opcional do contexto." } %>
    <% end %>
    <%# conteúdo %>
    <%= render RubyUI::DialogFooter.new do %>
      <%= render RubyUI::Button.new(variant: :outline) { "Cancelar" } %>
      <%= render RubyUI::Button.new { "Confirmar" } %>
    <% end %>
  <% end %>
<% end %>
```

## Regras
- ✅ Sempre inclua `DialogTitle` — obrigatório para acessibilidade.
- ✅ `DialogDescription` é opcional mas recomendado quando o contexto não é óbvio.
- ✅ Footer: botão de confirmação à direita, cancelar à esquerda.
- ✅ Largura padrão é suficiente para a maioria dos casos. Use `sm:max-w-lg` para formulários maiores.
- ❌ Não abra Dialog dentro de Dialog — reestruture o fluxo.
- ❌ Não use Dialog sem botão de fechar ou ação de cancelar.
