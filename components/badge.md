## O que é
Etiqueta visual compacta para indicar status, categoria ou contagem. Não é interativa.

## Quando usar / quando NÃO usar
- ✅ Status de entidade (Ativo, Inativo, Pendente, Em análise)
- ✅ Contagem de itens (ex: "3 pendentes")
- ✅ Categorias ou tags
- ❌ Ações clicáveis — use `Button` com `size="sm"`
- ❌ Notificações numéricas sobre ícones — use overlay customizado

## Variantes

| Variante | Uso |
|----------|-----|
| `default` | Status neutro ou positivo (preto) |
| `secondary` | Status informativo discreto (cinza) |
| `destructive` | Status de erro ou bloqueio (vermelho) |
| `outline` | Status com borda, sem fundo preenchido |

## Convenção de status na Linkana

| Status | Variante sugerida |
|--------|------------------|
| Ativo | `default` |
| Inativo | `secondary` |
| Pendente | `outline` |
| Bloqueado / Recusado | `destructive` |
| Em análise | `secondary` |

## Regras
- ✅ Texto do Badge deve ser curto: 1-3 palavras.
- ✅ Use `rounded-full` para badges de contagem numérica.
- ❌ Não use mais de 3 badges diferentes por linha de tabela.
- ❌ Não use Badge para texto longo — use `Alert` ou texto inline.
