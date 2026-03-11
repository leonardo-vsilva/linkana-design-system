## O que é
Texto de rótulo associado a um campo de formulário. Essencial para acessibilidade e usabilidade.

## Quando usar / quando NÃO usar
- ✅ Sempre que houver um campo de formulário (Input, Select, Checkbox, etc.)
- ❌ Títulos de seções — use `h2`, `h3` com classes Tailwind
- ❌ Texto descritivo — use `p` com `text-muted-foreground`

## Estrutura

```erb
<%= render RubyUI::Label.new(for: "field_id") { "Nome do campo" } %>
```

## Regras
- ✅ Sempre use `for` apontando para o `id` do campo associado.
- ✅ Campos obrigatórios: adicione `*` ao final do texto do label.
- ✅ Label deve ser conciso: 1-4 palavras.
- ❌ Não use Label sem `for` — perde o vínculo de acessibilidade.
- ❌ Não use Label como substituto de `placeholder`.
