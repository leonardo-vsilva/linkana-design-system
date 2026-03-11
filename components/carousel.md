## O que é
Container de conteúdo deslizável em série (slides). Para navegar entre múltiplos itens de forma sequencial.

## Quando usar / quando NÃO usar
- ✅ Galeria de imagens ou documentos
- ✅ Onboarding com múltiplos passos ilustrados
- ❌ Dados que o usuário precisa comparar — use Grid ou Table
- ❌ Listas de entidades — use Table ou lista scrollável

## Estrutura

```erb
<%= render RubyUI::Carousel.new do %>
  <%= render RubyUI::CarouselContent.new do %>
    <% items.each do |item| %>
      <%= render RubyUI::CarouselItem.new do %>
        <%# conteúdo do slide %>
      <% end %>
    <% end %>
  <% end %>
  <%= render RubyUI::CarouselPrevious.new %>
  <%= render RubyUI::CarouselNext.new %>
<% end %>
```

## Regras
- ✅ Sempre inclua controles de Previous/Next.
- ✅ Inclua indicadores de posição (dots) para séries com mais de 3 itens.
- ❌ Não use autoplay sem controle de pause — causa desorientação.
- ❌ Não use para conteúdo principal crítico — o usuário pode não avançar os slides.
