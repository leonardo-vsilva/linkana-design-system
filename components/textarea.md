## O que é
Campo de entrada de texto multi-linha para conteúdo textual longo.

## Quando usar / quando NÃO usar
- ✅ Descrições, observações, justificativas
- ✅ Qualquer texto com potencial de > 1 linha
- ❌ Texto curto (nome, email, código) — use `Input`
- ❌ Conteúdo rico (com formatação) — use editor de rich text

## Estrutura

```erb
<%= render RubyUI::Label.new(for: "notes") { "Observações" } %>
<%= render RubyUI::Textarea.new(id: "notes", name: "supplier[notes]", placeholder: "Adicione observações relevantes...") %>
```

## Regras
- ✅ Sempre acompanhe de `Label`.
- ✅ Defina `rows` baseado no volume esperado de texto (padrão: 4 linhas).
- ✅ Defina `maxlength` quando houver limite de caracteres — exiba contador visível.
- ❌ Não use `resize-none` sem motivo — o usuário deve poder redimensionar.
