## O que é
Representação visual de um usuário ou entidade, geralmente com foto ou iniciais como fallback.

## Quando usar / quando NÃO usar
- ✅ Identificação de usuário em headers, comentários, listas de membros
- ✅ Representação de fornecedor/empresa com logo
- ❌ Ícones decorativos — use ícone SVG diretamente
- ❌ Imagens de conteúdo — use `<img>` ou `AspectRatio`

## Estrutura

```erb
<%= render RubyUI::Avatar.new do %>
  <%= render RubyUI::AvatarImage.new(src: user.avatar_url, alt: user.name) %>
  <%= render RubyUI::AvatarFallback.new { user.initials } %>
<% end %>
```

## Tamanhos (customizados via classe)

| Tamanho | Classe | Uso |
|---------|--------|-----|
| Pequeno | `size-6` | Avatares em listas compactas |
| Médio (padrão) | `size-8` | Uso geral |
| Grande | `size-10` | Headers de perfil |
| Extra grande | `size-12` | Página de perfil |

## Regras
- ✅ Sempre defina `AvatarFallback` com as iniciais do nome (2 letras).
- ✅ Defina `alt` descritivo na `AvatarImage`.
- ❌ Não use avatares sem fallback — a imagem pode falhar.
