## O que é
Controle de seleção binária (marcado/desmarcado). Usado para opções independentes ou múltipla seleção de uma lista.

## Quando usar / quando NÃO usar
- ✅ Aceite de termos e condições
- ✅ Múltipla seleção de uma lista de opções
- ✅ Toggle de uma opção individual independente
- ❌ Escolha mutuamente exclusiva (apenas uma opção) — use `RadioGroup`
- ❌ Toggle de estado on/off visível — use `Switch`

## Estrutura

```erb
<div class="flex items-center gap-2">
  <%= render RubyUI::Checkbox.new(id: "terms") %>
  <%= render RubyUI::Label.new(for: "terms") { "Aceito os termos de uso" } %>
</div>
```

## Regras
- ✅ Sempre associe a um `Label` via `for/id`.
- ✅ Label deve estar à direita do checkbox.
- ✅ Em listas de checkboxes, use `gap-3` entre cada item.
- ❌ Não use checkbox sem label visível.
