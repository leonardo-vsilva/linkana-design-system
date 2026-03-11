## O que é
Card flutuante com informações detalhadas que aparece ao passar o mouse sobre um elemento. Para conteúdo mais rico que um Tooltip.

## Quando usar / quando NÃO usar
- ✅ Preview de entidade ao passar o mouse (fornecedor, usuário, contrato)
- ✅ Informações complementares sem sair do contexto atual
- ❌ Conteúdo simples de 1 linha — use `Tooltip`
- ❌ Conteúdo interativo — use `Popover`
- ❌ Em mobile — hover não existe em touch

## Estrutura

```erb
<%= render RubyUI::HoverCard.new do %>
  <%= render RubyUI::HoverCardTrigger.new do %>
    <a href="#" class="text-sm font-medium underline">Acme Corp</a>
  <% end %>
  <%= render RubyUI::HoverCardContent.new do %>
    <div class="flex flex-col gap-2">
      <p class="text-sm font-semibold">Acme Corp</p>
      <p class="text-xs text-muted-foreground">CNPJ: 12.345.678/0001-99</p>
      <p class="text-xs text-muted-foreground">Status: Ativo</p>
    </div>
  <% end %>
<% end %>
```

## Regras
- ✅ Conteúdo máximo: 4-5 linhas de informação.
- ✅ Delay padrão de abertura: 300ms (não remova).
- ❌ Não coloque botões ou links clicáveis dentro do HoverCard.
- ❌ Não use para informação crítica — o usuário pode não passar o mouse.
