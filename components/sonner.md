## O que é
Notificações temporárias flutuantes de feedback de ação. Aparecem automaticamente e somem após alguns segundos.

## Quando usar / quando NÃO usar
- ✅ Confirmação de ação concluída ("Fornecedor salvo com sucesso")
- ✅ Erros de requisição não relacionados a campos específicos
- ✅ Feedback de ações assíncronas (upload, processamento)
- ❌ Erros de validação de formulário — use mensagens inline no campo
- ❌ Alertas críticos que exigem leitura garantida — use `Alert` inline
- ❌ Confirmação de ação destrutiva — use `AlertDialog` antes da ação

## Tipos

| Tipo | Uso |
|------|-----|
| `success` | Ação concluída com sucesso |
| `error` | Falha em operação |
| `warning` | Aviso não-bloqueante |
| `info` | Informação contextual |
| `loading` | Operação em andamento (atualiza para success/error) |

## Regras
- ✅ Mensagem concisa: "Fornecedor salvo." — não precisa de sujeito explícito.
- ✅ Máximo 1 toast visível por vez (Sonner gerencia a fila automaticamente).
- ✅ Toasts de erro devem ter botão de ação quando há algo que o usuário pode fazer.
- ❌ Não use toast para informações que o usuário precisa reler (use Alert).
- ❌ Não duplique o toast com Alert inline para a mesma ação.

## Setup necessário
O componente `<%= render RubyUI::Sonner.new %>` deve estar no layout da aplicação, fora do conteúdo principal.
