# Casos de teste — PIM e funcionários

Use contas autorizadas para PIM e dados fictícios exclusivos da instância. Para os casos de criação, confirme previamente quais campos são obrigatórios na versão em uso.

## PIM-001 — Abrir a lista de funcionários

**Prioridade:** Alta  
**Pré-condições:** usuário com permissão para consultar funcionários.

1. Acesse o módulo PIM e abra a lista de funcionários.
2. Aguarde o carregamento dos resultados.

**Resultado esperado:** a lista é exibida sem erro; as ações visíveis correspondem às permissões da conta.

## PIM-002 — Cadastrar funcionário com dados válidos

**Prioridade:** Alta  
**Pré-condições:** usuário com permissão de criação; nome e ID exclusivos; campos obrigatórios conhecidos.

1. Inicie a inclusão de um funcionário.
2. Preencha os campos obrigatórios com dados fictícios válidos e um ID ainda não utilizado.
3. Salve o cadastro.
4. Pesquise o funcionário pelo ID criado.

**Resultado esperado:** o cadastro é salvo uma única vez e o funcionário pode ser localizado com os dados informados.

## PIM-003 — Validar campos obrigatórios no cadastro

**Prioridade:** Média  
**Pré-condições:** usuário com permissão de criação.

1. Abra o formulário de inclusão.
2. Deixe sem preencher um campo identificado pela instância como obrigatório.
3. Tente salvar.

**Resultado esperado:** o sistema não cria o cadastro incompleto e indica os campos que precisam ser corrigidos.

## PIM-004 — Impedir ID de funcionário duplicado

**Prioridade:** Alta  
**Pré-condições:** usuário com permissão de criação; existe um funcionário de teste com ID conhecido.

1. Inicie um novo cadastro.
2. Informe outro conjunto de dados, mas reutilize o ID existente.
3. Tente salvar.

**Resultado esperado:** o sistema não cria um segundo funcionário com o mesmo ID e informa que o dado precisa ser corrigido.

## PIM-005 — Editar dados de funcionário

**Prioridade:** Alta  
**Pré-condições:** usuário com permissão de edição; funcionário de teste identificável.

1. Localize o funcionário e abra sua edição.
2. Altere um campo editável para um valor fictício válido.
3. Salve e reabra o registro.

**Resultado esperado:** o valor atualizado é persistido no registro correto; o ID do funcionário permanece associado ao mesmo registro, salvo se a instalação permitir explicitamente sua edição.

## PIM-006 — Buscar funcionário por ID

**Prioridade:** Alta  
**Pré-condições:** existe um funcionário de teste com ID conhecido.

1. Abra a busca/lista de funcionários.
2. Informe o ID completo no campo correspondente e execute a pesquisa.

**Resultado esperado:** o resultado corresponde ao funcionário de teste com aquele ID; nenhum registro diferente é apresentado como correspondência exata.

## PIM-007 — Buscar funcionário por nome

**Prioridade:** Média  
**Pré-condições:** existe funcionário de teste com nome conhecido e não ambíguo.

1. Informe o nome no campo de busca correspondente.
2. Execute a pesquisa.

**Resultado esperado:** o funcionário esperado aparece nos resultados. Se a busca for parcial ou não distinguir maiúsculas/minúsculas, registre o comportamento observado sem tratá-lo como falha, a menos que exista requisito específico.

## PIM-008 — Combinar filtros de pesquisa

**Prioridade:** Média  
**Pré-condições:** dados de teste que permitam distinguir ao menos dois critérios e campos de filtro disponíveis.

1. Informe dois ou mais critérios compatíveis, por exemplo nome e ID ou status e unidade.
2. Execute a pesquisa.
3. Remova um critério e pesquise novamente.

**Resultado esperado:** a primeira pesquisa respeita os critérios combinados; ao remover um critério, os resultados são recalculados de acordo com os filtros restantes.

## PIM-009 — Pesquisar sem correspondências

**Prioridade:** Baixa  
**Pré-condições:** nenhum funcionário de teste usa o valor exclusivo escolhido para a pesquisa.

1. Pesquise por um ID ou nome fictício que não exista.

**Resultado esperado:** nenhum funcionário é listado como correspondência e a tela permanece utilizável para uma nova pesquisa.

## PIM-010 — Cancelar alterações não salvas

**Prioridade:** Baixa  
**Pré-condições:** usuário com permissão de edição; funcionário de teste.

1. Abra a edição do funcionário.
2. Altere um campo, sem salvar.
3. Cancele ou navegue para fora do formulário.
4. Reabra o registro.

**Resultado esperado:** a alteração não salva não aparece no registro, ou o sistema solicita confirmação antes de descartá-la.
