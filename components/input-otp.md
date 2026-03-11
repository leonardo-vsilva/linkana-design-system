## O que é
Campo de entrada para código OTP (One-Time Password) de múltiplos dígitos separados visualmente.

## Quando usar / quando NÃO usar
- ✅ Verificação de código enviado por e-mail ou SMS
- ✅ Autenticação de dois fatores (2FA)
- ❌ Outros tipos de código/token — use `Input` comum

## Estrutura

```erb
<%= render RubyUI::InputOTP.new(max_length: 6) do %>
  <%= render RubyUI::InputOTPGroup.new do %>
    <%= render RubyUI::InputOTPSlot.new(index: 0) %>
    <%= render RubyUI::InputOTPSlot.new(index: 1) %>
    <%= render RubyUI::InputOTPSlot.new(index: 2) %>
  <% end %>
  <%= render RubyUI::InputOTPSeparator.new %>
  <%= render RubyUI::InputOTPGroup.new do %>
    <%= render RubyUI::InputOTPSlot.new(index: 3) %>
    <%= render RubyUI::InputOTPSlot.new(index: 4) %>
    <%= render RubyUI::InputOTPSlot.new(index: 5) %>
  <% end %>
<% end %>
```

## Regras
- ✅ Padrão: 6 dígitos separados em 2 grupos de 3.
- ✅ Auto-foco no primeiro slot ao renderizar.
- ✅ Auto-submit ao completar todos os slots (quando possível).
- ❌ Não use para códigos alfanuméricos longos.
