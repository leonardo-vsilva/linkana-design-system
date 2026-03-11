## O que é
Componente de formulário com validação integrada via biblioteca de formulários (ex: Stimulus + validação server-side ou client-side). Composto por `FormField`, `FormItem`, `FormLabel`, `FormControl`, `FormDescription`, e `FormMessage`.

## Quando usar / quando NÃO usar
- ✅ Qualquer formulário que exige validação e mensagens de erro
- ✅ Formulários com múltiplos campos
- ❌ Campo único sem validação — use `Input` + `Label` diretamente

## Estrutura de composição

```erb
<%# Exemplo de campo de formulário completo %>
<div class="flex flex-col gap-2">
  <%= render RubyUI::Label.new(for: "name") { "Nome *" } %>
  <%= render RubyUI::Input.new(id: "name", name: "supplier[name]", placeholder: "ex: Empresa Ltda") %>
  <p class="text-sm text-muted-foreground">Razão social completa conforme CNPJ.</p>
  <%# Mensagem de erro (quando presente): %>
  <p class="text-sm text-destructive">Campo obrigatório.</p>
</div>
```

## Anatomia de um campo

1. **Label** — sempre visível, nunca substitua pelo placeholder
2. **Control** — o input, select, checkbox, etc.
3. **Description** — texto auxiliar opcional abaixo do controle (cinza)
4. **Message** — mensagem de erro (vermelho), aparece apenas em estado inválido

## Regras
- ✅ Campos obrigatórios marcados com `*` no label.
- ✅ Mensagem de erro sempre abaixo do campo, em `text-sm text-destructive`.
- ✅ Description (hint) sempre abaixo do campo, antes da mensagem de erro.
- ✅ Agrupe campos relacionados com espaçamento `gap-4`.
- ✅ Botão de submit sempre no final do formulário.
- ❌ Não valide apenas no client-side — valide também no servidor.
- ❌ Não use `placeholder` como substituto do `Label`.
- ❌ Não misture estilos de layout de formulário na mesma página (sempre grid ou sempre stack vertical).

Veja também: `patterns/forms.md` para padrões de composição de formulários completos.
