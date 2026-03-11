## O que é
Barra de progresso que indica o avanço de uma operação ou preenchimento de um processo.

## Quando usar / quando NÃO usar
- ✅ Progresso de upload de arquivo
- ✅ Progresso de onboarding (etapas concluídas de X)
- ✅ Preenchimento de formulário multi-etapas
- ❌ Status de loading indeterminado — use Spinner ou Skeleton
- ❌ Métricas de performance — use Chart

## Estrutura

```erb
<%= render RubyUI::Progress.new(value: 60) %>
```

## Regras
- ✅ Sempre exiba o valor percentual próximo à barra (ex: "60%").
- ✅ Para progresso indeterminado, use animação de pulse — não `value: nil`.
- ✅ Acompanhe com texto descritivo: "3 de 5 etapas concluídas".
- ❌ Não use para valores que não são literalmente progresso (ex: avaliação, nota).
