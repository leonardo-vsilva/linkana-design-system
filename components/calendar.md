## O que é
Componente de calendário visual para seleção de datas. Geralmente usado como parte do `DatePicker`.

## Quando usar / quando NÃO usar
- ✅ Exibição e seleção de datas em contextos de planejamento
- ✅ Seleção de range de datas (período)
- ❌ Input direto de data conhecida (ex: data de nascimento) — use `Input type="date"`
- ❌ Seleção de data em formulários simples sem contexto visual — use `DatePicker`

## Regras
- ✅ Sempre use dentro de `Popover` ou `Sheet` — não inline na página.
- ✅ Para range de datas, use `mode: :range`.
- ✅ Defina `disabled_days` para bloquear datas inválidas (ex: datas no passado quando não permitido).
- ❌ Não exiba o Calendar fora de um container posicionado.

Veja também: `components/date-picker.md`
