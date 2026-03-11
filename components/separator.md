## O que é
Divisor visual horizontal ou vertical para separar grupos de conteúdo relacionado.

## Quando usar / quando NÃO usar
- ✅ Separar grupos de itens em menus ou listas
- ✅ Dividir seções dentro de um Card ou formulário
- ❌ Separar seções de página — use espaçamento (`mt-8`, `pt-8`) ou heading
- ❌ Tabelas — use bordas de célula

## Estrutura

```erb
<%= render RubyUI::Separator.new %>                    <%# horizontal (padrão) %>
<%= render RubyUI::Separator.new(orientation: :vertical) %>  <%# vertical %>
```

## Regras
- ✅ Use com `my-4` para espaçamento adequado ao redor.
- ✅ Separador vertical: use dentro de `flex` com `h-full` ou altura explícita.
- ❌ Não use mais de 2 separadores em sequência — reestruture o layout.
