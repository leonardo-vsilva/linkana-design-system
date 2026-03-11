## O que é
Modal de confirmação bloqueante para ações irreversíveis ou de alto impacto. Diferente do `Dialog`, ele não pode ser fechado clicando fora.

## Quando usar / quando NÃO usar
- ✅ Confirmação de exclusão (fornecedor, contrato, usuário)
- ✅ Ações que não podem ser desfeitas
- ✅ Ações com consequências financeiras ou legais
- ❌ Confirmações de ações reversíveis — use `Dialog`
- ❌ Formulários — use `Dialog`

## Estrutura de composição

```erb
<%= render RubyUI::AlertDialog.new do %>
  <%= render RubyUI::AlertDialogTrigger.new do %>
    <%= render RubyUI::Button.new(variant: :destructive) { "Excluir" } %>
  <% end %>
  <%= render RubyUI::AlertDialogContent.new do %>
    <%= render RubyUI::AlertDialogHeader.new do %>
      <%= render RubyUI::AlertDialogTitle.new { "Tem certeza?" } %>
      <%= render RubyUI::AlertDialogDescription.new do %>
        Essa ação não pode ser desfeita. O fornecedor será removido permanentemente.
      <% end %>
    <% end %>
    <%= render RubyUI::AlertDialogFooter.new do %>
      <%= render RubyUI::AlertDialogCancel.new { "Cancelar" } %>
      <%= render RubyUI::AlertDialogAction.new { "Sim, excluir" } %>
    <% end %>
  <% end %>
<% end %>
```

## Regras
- ✅ Título deve ser uma pergunta direta: "Tem certeza?", "Deseja excluir?"
- ✅ Descrição deve explicar a consequência da ação.
- ✅ Botão de ação deve descrever o que acontece: "Sim, excluir" — não apenas "Confirmar".
- ✅ Botão de cancelar sempre à esquerda, ação à direita.
- ❌ Não feche o AlertDialog programaticamente sem ação do usuário.
- ❌ Não use para ações reversíveis.
