## O que é
Container que mantém a proporção de aspecto de seu conteúdo (ex: 16:9, 4:3, 1:1).

## Quando usar / quando NÃO usar
- ✅ Imagens responsivas que precisam manter proporção
- ✅ Thumbnails de vídeo ou documento
- ✅ Avatares quadrados ou circulares em tamanho variável
- ❌ Conteúdo de texto — apenas para mídia

## Estrutura

```erb
<%= render RubyUI::AspectRatio.new(ratio: 16/9.0) do %>
  <img src="..." alt="..." class="object-cover w-full h-full rounded-md" />
<% end %>
```

## Ratios comuns

| Ratio | Uso |
|-------|-----|
| `16/9` | Vídeos, thumbnails wide |
| `4/3` | Imagens de documento |
| `1/1` | Avatares, ícones quadrados |
| `3/4` | Retratos |

## Regras
- ✅ A imagem dentro deve ter `object-cover w-full h-full`.
- ✅ Defina `alt` descritivo na imagem.
- ❌ Não use para layout de página — use CSS Grid/Flex.
