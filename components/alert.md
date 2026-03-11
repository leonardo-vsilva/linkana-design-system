## O que é
Componente inline de feedback contextual. Exibe mensagens de status, avisos ou erros diretamente no conteúdo da página.

## Quando usar / quando NÃO usar
- ✅ Mensagens de erro de formulário ou validação no nível de seção
- ✅ Avisos informativos persistentes (ex: "Seu plano expira em 3 dias")
- ✅ Confirmações de ação concluída dentro do contexto (não toast)
- ❌ Feedback temporário de ação — use `Sonner` (toast)
- ❌ Confirmação de ação destrutiva — use `AlertDialog`

## Variantes

| Variante | Token | Uso |
|----------|-------|-----|
| `default` | `--foreground` | Informativo neutro |
| `destructive` | `--destructive` | Erro ou falha crítica |

## Regras
- ✅ Sempre inclua um ícone descritivo no Alert.
- ✅ `AlertTitle` é opcional mas recomendado para mensagens complexas.
- ✅ `AlertDescription` deve ser concisa — máximo 2 frases.
- ❌ Não empilhe mais de 2 Alerts na mesma tela.

## Exemplos

✅ Correto — erro de validação:
```erb
<%= render RubyUI::Alert.new(variant: :destructive) do %>
  <%= render RubyUI::AlertTitle.new { "Erro ao salvar" } %>
  <%= render RubyUI::AlertDescription.new { "Verifique os campos obrigatórios." } %>
<% end %>
```

✅ Correto — aviso informativo:
```erb
<%= render RubyUI::Alert.new do %>
  <%= render RubyUI::AlertDescription.new { "Seu cadastro está em análise. Prazo: 2 dias úteis." } %>
<% end %>
```
