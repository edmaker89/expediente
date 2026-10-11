# Workspace do agente

A pasta `.agents/` é o workspace para arquivos produzidos pelo agente que não fazem parte do funcionamento do projeto.

- Salvar aqui documentos de análise, As Is, brainstorms, planos, relatórios, scripts auxiliares e arquivos temporários do agente.
- Organizar o conteúdo por finalidade em subdiretórios; criar outros conforme necessário.
- Usar `docs/` para documentação e análises e `work/` para materiais temporários e intermediários.
- Manter código, configurações e recursos necessários ao funcionamento do sistema nas pastas próprias do projeto.
- A antiga pasta `tasks/` foi removida a pedido do usuário; não recuperar seu conteúdo sem solicitação.

## Fluxo de entrega da versão 2

- Usar `v2` como branch de integração da nova versão.
- Trabalhar cada etapa em branch própria criada a partir de `v2`.
- Depois de validar a etapa com o usuário, fazer commit, abrir PR para `v2`, executar squash merge e excluir a branch da etapa.
- Manter materiais temporários de `work/` locais, fora dos commits.
