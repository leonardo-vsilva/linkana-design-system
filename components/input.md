## O que é
Campo de entrada de texto de linha única. Usado em formulários para dados como nome, email, busca, etc.

## Quando usar / quando NÃO usar
- ✅ Campos de texto curto: nome, email, CPF, CNPJ, código
- ✅ Campos de busca (com ícone de lupa)
- ❌ Texto longo (mais de 1 linha) — use `Textarea`
- ❌ Seleção de opções — use `Select` ou `Combobox`
- ❌ Data — use `DatePicker`

## Props principais

| Prop | Tipo | Uso |
|------|------|-----|
| `type` | string | `text`, `email`, `password`, `number`, `search`, `tel` |
| `placeholder` | string | Texto de exemplo — não substitui o label |
| `disabled` | boolean | Desabilita o campo |
| `readonly` | boolean | Campo apenas leitura |

## Regras
- ✅ Sempre acompanhe o Input de um `Label` associado via `for/id`.
- ✅ Mensagens de erro ficam abaixo do input em `text-destructive text-sm`.
- ✅ Placeholder deve ser um exemplo do valor esperado, não o label (ex: "ex: 12.345.678/0001-99").
- ✅ Campos obrigatórios: marque com `*` no label, não no placeholder.
- ❌ Não use input sem label (exceto campos de busca com `aria-label`).
- ❌ Não esconda a label usando o placeholder como substituto.

## Estados

| Estado | Classe |
|--------|--------|
| Default | — |
| Focus | `ring-ring` automático via `:focus-visible` |
| Error | `border-destructive` + mensagem de erro abaixo |
| Disabled | `disabled:opacity-50 disabled:cursor-not-allowed` |

## Exemplos

✅ Correto:
```erb
<%= render RubyUI::Label.new(for: "email") { "E-mail" } %>
<%= render RubyUI::Input.new(type: "email", id: "email", placeholder: "ex: joao@empresa.com") %>
```

❌ Errado — label ausente:
```erb
<%= render RubyUI::Input.new(type: "email", placeholder: "E-mail") %>
```
