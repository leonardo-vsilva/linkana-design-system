## O que é
Controle deslizante para seleção de valor numérico dentro de um range.

## Quando usar / quando NÃO usar
- ✅ Seleção de range numérico onde o valor exato é menos importante (ex: nível de risco 1-10)
- ✅ Filtro de range de valores (preço mínimo/máximo)
- ❌ Quando o usuário precisa inserir um valor exato — use `Input type="number"`
- ❌ Seleção de itens de lista — use `Select`

## Estrutura

```erb
<%= render RubyUI::Slider.new(default_value: [50], max: 100, step: 1) %>
```

## Regras
- ✅ Sempre exiba o valor atual do slider próximo ao controle.
- ✅ Defina `min`, `max` e `step` explicitamente.
- ✅ Use label descritivo.
- ❌ Não use para valores binários — use `Switch`.
