## O que é
Botão com dois estados (pressionado/não pressionado). Visualmente indica seleção ativa.

## Quando usar / quando NÃO usar
- ✅ Ativar/desativar um modo ou filtro (ex: "Negrito" em editor de texto)
- ✅ Filtros de visualização (ex: "Mostrar apenas ativos")
- ❌ Toggle de configurações que persistem — use `Switch`
- ❌ Ações únicas — use `Button`

## Variantes

| Variante | Uso |
|----------|-----|
| `default` | Uso geral |
| `outline` | Em toolbars com borda |

## Estrutura

```erb
<%= render RubyUI::Toggle.new(aria_label: "Ativar modo compacto") do %>
  <%# ícone ou texto %>
<% end %>
```

## Regras
- ✅ Sempre defina `aria-label` quando o conteúdo for apenas ícone.
- ✅ Estado ativo deve ser visualmente claro (fundo preenchido).
- ❌ Não use Toggle isolado para on/off persistente — use Switch.
