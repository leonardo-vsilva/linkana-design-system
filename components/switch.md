## O que é
Toggle visual de estado binário (ativo/inativo). Visualmente representa um interruptor — ação imediata ao clicar, sem necessidade de submit.

## Quando usar / quando NÃO usar
- ✅ Ativar/desativar uma funcionalidade ou configuração com efeito imediato
- ✅ Preferências de notificação, visibilidade, permissões
- ❌ Quando a mudança exige confirmação ou submit — use `Checkbox` dentro de um form
- ❌ Múltipla seleção — use `Checkbox`
- ❌ Escolha entre duas opções nomeadas — use `RadioGroup` ou `Tabs`

## Estrutura

```erb
<div class="flex items-center gap-3">
  <%= render RubyUI::Switch.new(id: "notifications") %>
  <%= render RubyUI::Label.new(for: "notifications") { "Receber notificações por e-mail" } %>
</div>
```

## Regras
- ✅ Sempre acompanhe de label descritivo que indica o estado ativo.
- ✅ A mudança de estado deve ter efeito imediato (via Turbo/JS) sem submit manual.
- ✅ Label deve descrever o que acontece quando ativo: "Receber alertas" (não "Alertas").
- ❌ Não use em contextos onde o usuário precisa salvar para confirmar a mudança.
