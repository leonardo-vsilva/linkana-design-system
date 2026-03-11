# Tokens de Espaçamento

Sistema baseado em **8pt grid**. Todos os valores de espaçamento são múltiplos de 4px (base Tailwind), privilegiando os múltiplos de 8px como escala principal.

## Por que 8pt grid?

O número 8 é divisível por 2 e 4, criando uma escala harmoniosa (8, 16, 24, 32…). A maioria das telas modernas tem resoluções múltiplas de 8, garantindo renderização sem problemas de sub-pixel em densidades 1x, 1.5x, 2x e 3x.

## Escala de espaçamento

| Valor | Tailwind | Uso |
|-------|----------|-----|
| **4px** | `gap-1` / `p-1` | Espaçamento mínimo entre elementos muito próximos (ícones inline, badges) |
| **8px** | `gap-2` / `p-2` | Espaçamento mínimo entre elementos relacionados (itens de lista, nav) |
| **16px** | `gap-4` / `p-4` | Espaçamento entre elementos relacionados (campos de form, itens de card) |
| **24px** | `gap-6` / `p-6` | Espaçamento entre seções relacionadas (grupos de campos, modais) |
| **32px** | `gap-8` / `p-8` | Espaçamento entre seções distintas (separadores de página) |
| **40px** | `gap-10` / `p-10` | Espaçamento largo entre áreas principais |
| **48px** | `gap-12` / `p-12` | Espaçamento extra largo |
| **64px+** | `gap-16` / `p-16` | Separações maiores e margens externas |

## Layout de containers

Resolução de referência principal: **1920×1080** (desktop-first).

| Contexto | `max-width` | Tailwind | Padding | Posicionamento |
|----------|------------|----------|---------|----------------|
| Preview / Documentos / Performance | 1152px | `max-w-6xl` | `p-6 pb-10` | Centralizado |
| Formulários / CRUD | 768px | `max-w-3xl` | `p-6 pb-10` | Centralizado |
| Tabelas / Listas / Dashboards | 100% | `max-w-full` | `p-6 pb-10` | Full |

## Grid responsivo

| Breakpoint | Container `max-width` | Colunas | Margin | Gutter |
|------------|----------------------|---------|--------|--------|
| ≥ 1366px | 1148px | 12 | 16pt | 24pt |
| ≥ 1024px | 863px | 12 | 16pt | 24pt |
| < 768px | 713px | 4 | 16pt | 16pt |

## Regras

- ✅ Use apenas múltiplos de 4 (escala Tailwind padrão). Prefira múltiplos de 8.
- ✅ `gap-4` (16px) entre campos de formulário.
- ✅ `gap-6` (24px) entre seções de formulário.
- ✅ `p-6 pb-10` como padding padrão de página.
- ✅ Containers centralizados para Preview e Form; full-width para tabelas e dashboards.
- ❌ Não use valores arbitrários (ex: `p-[13px]`) — ajuste para o múltiplo mais próximo.
- ❌ Não alinhe conteúdo à esquerda em páginas de Preview/Form — use container centralizado.
- ❌ Não use mais de `max-w-6xl` para conteúdo editorial — evita linhas excessivamente longas.
