## O que é
Placeholder animado que representa o formato do conteúdo durante o carregamento. Melhora a percepção de performance.

## Quando usar / quando NÃO usar
- ✅ Durante carregamento de dados assíncronos (Turbo Frames, fetch)
- ✅ Como estado inicial de cards, tabelas, listas
- ❌ Operações < 300ms — não vale a pena mostrar skeleton
- ❌ Como substituto de spinner para ações pontuais — use `loading` state no botão

## Exemplos

✅ Skeleton de card:
```erb
<div class="flex flex-col gap-3 p-4">
  <%= render RubyUI::Skeleton.new(class: "h-4 w-1/2") %>
  <%= render RubyUI::Skeleton.new(class: "h-4 w-full") %>
  <%= render RubyUI::Skeleton.new(class: "h-4 w-3/4") %>
</div>
```

✅ Skeleton de linha de tabela:
```erb
<% 5.times do %>
  <%= render RubyUI::Skeleton.new(class: "h-10 w-full") %>
<% end %>
```

## Regras
- ✅ Reproduza o formato aproximado do conteúdo real (mesma altura/largura proporcional).
- ✅ Use múltiplos skeletons para representar listas.
- ❌ Não use skeleton para erros — mostre mensagem de erro.
- ❌ Não deixe skeleton visível por mais de 10s sem fallback de erro.
