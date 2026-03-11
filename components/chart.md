## O que é
Componentes de visualização de dados baseados em Recharts. Inclui Line Chart, Bar Chart, Area Chart, Pie Chart, Radar Chart.

## Quando usar / quando NÃO usar
- ✅ Métricas e KPIs em dashboards
- ✅ Evolução temporal de dados
- ✅ Comparação entre categorias
- ❌ Dados que podem ser expressos em tabela simples — use `Table`
- ❌ Valor único — use número grande com label

## Tokens de cor para charts

Use os tokens específicos de chart — nunca cores hardcoded:

| Token | Classe |
|-------|--------|
| `--chart-1` | `text-chart-1` / via config |
| `--chart-2` | `text-chart-2` |
| `--chart-3` | `text-chart-3` |
| `--chart-4` | `text-chart-4` |
| `--chart-5` | `text-chart-5` |

## Estrutura básica (Bar Chart)

```erb
<%= render RubyUI::ChartContainer.new(config: @chart_config) do %>
  <%# Recharts components via ruby_ui %>
<% end %>
```

## Regras
- ✅ Sempre inclua legenda quando há mais de 1 série de dados.
- ✅ Sempre inclua tooltip ao passar o mouse.
- ✅ Use no máximo 5 séries/categorias por chart (1 por token de cor).
- ✅ Eixos devem ter label descritivo.
- ❌ Não use mais de 5 cores — fica ilegível.
- ❌ Não use Pie Chart para mais de 5 fatias.
- ❌ Não remova o tooltip — é essencial para leitura dos dados.
