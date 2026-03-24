---
title: "Tipografia"
---

# Tipografia

Inter é a fonte primária do sistema, declarada explicitamente antes dos fallbacks do sistema operacional:

```text
Inter, -apple-system, BlinkMacSystemFont, "Segoe UI", "Helvetica Neue", Roboto, Arial, sans-serif,
"Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol"
```

Inter garante consistência visual entre plataformas — em Windows, o fallback nativo (Segoe UI) tem aparência visivelmente diferente. Nenhuma outra fonte customizada (Google Fonts, display fonts, etc.) está em uso.

## Sizes

Escala reduzida a 4 tamanhos. A hierarquia dentro de uma tela é criada por peso e cor, não por variações granulares de tamanho.

| Classe      | Tamanho | Uso típico                                               |
| ----------- | ------- | -------------------------------------------------------- |
| `text-xs`   | 12px    | Metadados, timestamps, contadores, badges, atalhos       |
| `text-sm`   | 14px    | Padrão universal: corpo, labels, descrições, células, botões |
| `text-xl`   | 20px    | Títulos de seção, card titles, panel headings            |
| `text-2xl`  | 24px    | Título de página — único por tela                        |

`text-base` (16px), `text-lg` (18px) e `text-3xl` (30px) estão fora da escala do sistema.

## Weights

| Classe          | Peso | Uso típico                                                   |
| --------------- | ---- | ------------------------------------------------------------ |
| `font-normal`   | 400  | Default para todo conteúdo não-acionável: corpo, descrições, valores em exibição, helper text, dados de tabela |
| `font-medium`   | 500  | Elementos interativos e de navegação: labels de form, botões, nav items, headers de coluna, estados ativos |
| `font-semibold` | 600  | Todos os headings: card titles, títulos de seção, título de página |

`font-bold` (700) está fora da escala do sistema.

## Letter Spacing

| Contexto              | Valor          | Classe Tailwind   |
| --------------------- | -------------- | ----------------- |
| Corpo (≤ 14px)        | 0 (padrão)     | —                 |
| Headings (20px, 24px) | `-0.01em`      | `tracking-tight`  |

## Line Height

| Contexto                       | Valor | Resultado para 14px |
| ------------------------------ | ----- | ------------------- |
| Corpo e labels (≤ 14px)        | 1.5   | 21px                |
| Headings de linha única (20px+) | 1.25  | 25px / 30px         |

## Text Colors

Três níveis de hierarquia. `text-muted-foreground` é o **default** para conteúdo de suporte — `text-foreground` é reservado para o que demanda atenção ou ação.

| Classe                       | Token                | Uso                                                          |
| ---------------------------- | -------------------- | ------------------------------------------------------------ |
| `text-foreground`            | `--foreground`       | **Ativo / primário:** títulos, valores principais, itens selecionados, CTAs inline |
| `text-muted-foreground`      | `--muted-foreground` | **Suporte:** corpo de texto, labels de apoio, descrições, helper text, valores em exibição |
| `text-muted-foreground/60`   | —                    | **Terciário:** timestamps, contadores, metadados, atalhos de teclado |
| `text-primary`               | `--primary`          | Destaque com cor primária                                    |
| `text-destructive`           | `--destructive`      | Erros e ações destrutivas                                    |
| `text-warning`               | `--warning`          | Alertas                                                      |
| `text-success`               | `--success`          | Confirmações                                                 |

---

## Combinações padrão

| Contexto                  | Classes                                              |
| ------------------------- | ---------------------------------------------------- |
| Corpo / UI padrão         | `text-sm font-normal text-muted-foreground`          |
| Labels interativos        | `text-sm font-medium text-foreground`                |
| Helper / descrição        | `text-sm font-normal text-muted-foreground`          |
| Metadados / timestamps    | `text-xs text-muted-foreground/60`                   |
| Título de card / seção    | `text-xl font-semibold tracking-tight text-foreground` |
| Título de página          | `text-2xl font-semibold tracking-tight text-foreground` |

---

## Regras

- ✅ Hierarquia visual é criada por **peso e cor** — não por variações de tamanho dentro do corpo de texto.
- ✅ `text-muted-foreground` é o default. `text-foreground` é a exceção — use onde o usuário precisa agir ou ler com atenção.
- ✅ Máximo de **2 tamanhos de fonte simultâneos** em telas utilitárias (sidebar, tabela, formulário): `text-xs` e `text-sm`. Os tamanhos `text-xl` e `text-2xl` são exclusivos de headings.
- ✅ `tracking-tight` em todo heading `text-xl` ou maior.
- ❌ Não use `text-base` (16px), `text-lg` (18px) ou `text-3xl` (30px) — fora da escala.
- ❌ Não use `font-bold` (700) — fora da escala do sistema.
- ❌ Não use cores hardcoded — apenas tokens semânticos.
- ❌ Sem itálico em elementos de UI.
