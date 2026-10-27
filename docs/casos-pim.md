# Casos de teste — PIM e funcionários

Antes da execução, preencha os campos obrigatórios, limites de texto e critérios de pesquisa em [parâmetros da instância e dados de teste](parametros-instancia.md). Use as fixtures fictícias dessa ficha e bloqueie os casos que dependam de parâmetros não confirmados.

## PIM-001 — Abrir a lista de funcionários

**Prioridade:** Alta  
**Pré-condições:** usuário com permissão para consultar funcionários.

1. Acesse o módulo PIM e abra a lista de funcionários.
2. Aguarde o carregamento dos resultados.

**Resultado esperado:** a lista é exibida sem erro; as ações visíveis correspondem às permissões da conta.

## PIM-002 — Cadastrar funcionário com dados válidos

**Prioridade:** Alta  
**Pré-condições:** usuário com permissão de criação; fixtures PIM válidas preenchidas e exclusivas; campos obrigatórios confirmados.

1. Inicie a inclusão de um funcionário.
2. Preencha os campos obrigatórios usando a fixture válida da ficha de parâmetros e um Employee Id ainda não utilizado.
3. Salve o cadastro.
4. Pesquise o funcionário pelo ID criado.

**Resultado esperado:** o cadastro é salvo uma única vez; a pesquisa pelo Employee Id da fixture retorna exatamente um funcionário com First Name, Middle Name e Last Name iguais aos cadastrados.

## PIM-003 — Validar campos obrigatórios no cadastro

**Prioridade:** Média

**Pré-condições:** usuário com permissão de criação; fixture inválida da ficha preenchida; campo First Name confirmado como obrigatório.

1. Abra o formulário de inclusão.
2. Deixe First Name vazio, conforme a fixture inválida.
3. Tente salvar.

**Resultado esperado:** o sistema não cria o cadastro e identifica First Name como obrigatório. A busca pelo Employee Id da fixture não retorna funcionário.

## PIM-004 — Impedir ID de funcionário duplicado

**Prioridade:** Alta  
**Pré-condições:** usuário com permissão de criação; fixture válida criada com sucesso e Employee Id registrado.

1. Inicie um novo cadastro.
2. Use a fixture duplicada, mantendo o Employee Id da fixture válida e alterando o nome.
3. Tente salvar.

**Resultado esperado:** o sistema rejeita o cadastro duplicado; a busca pelo Employee Id retorna somente o registro original e seus nomes não foram alterados.

## PIM-005 — Editar dados de funcionário

**Prioridade:** Alta  
**Pré-condições:** usuário com permissão de edição; fixture válida criada em PIM-002.

1. Localize o funcionário pela fixture e abra sua edição.
2. Altere Last Name de `PIM` para `PIM Atualizado`.
3. Salve e reabra o registro.

**Resultado esperado:** Last Name passa a ser exatamente `PIM Atualizado`; Employee Id continua igual ao da fixture e associado ao mesmo registro. Falha ao persistir o nome ou alteração de Employee Id reprova o caso.

## PIM-006 — Buscar funcionário por ID

**Prioridade:** Alta  
**Pré-condições:** existe um funcionário de teste com ID conhecido.

1. Abra a busca/lista de funcionários.
2. Informe o ID completo no campo correspondente e execute a pesquisa.

**Resultado esperado:** o resultado corresponde ao funcionário de teste com aquele ID; nenhum registro diferente é apresentado como correspondência exata.

## PIM-007 — Buscar funcionário por nome

**Prioridade:** Média

**Pré-condições:** fixture válida criada em PIM-002; First Name `QA` não é usado por outro funcionário.

1. Informe o nome no campo de busca correspondente.
2. Execute a pesquisa.

**Resultado esperado:** a pesquisa pelo First Name `QA` retorna exatamente o funcionário da fixture e nenhum outro funcionário.

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

## PIM-011 — Pesquisar com espaços e caracteres especiais

**Prioridade:** Média

**Pré-condições:** usuário autorizado a pesquisar; fixture válida criada em PIM-002; nenhum funcionário usa o Employee Id inexistente abaixo.

1. Pesquise o Employee Id da fixture válida com dois espaços antes e depois do valor, por exemplo `  QA-PIM-<RUN>-001  `.
2. Execute a busca e confirme se o registro da fixture é retornado.
3. Pesquise o Employee Id fictício inexistente ` QA-PIM_!<RUN>-999 `, incluindo pontuação e espaços.
4. Execute a busca.

**Resultado esperado:** a busca remove espaços no início/fim e retorna exatamente o funcionário da fixture no passo 2. No passo 4, não retorna funcionários e continua utilizável; erro de interface ou funcionário incorreto nos resultados reprova o caso.

## PIM-012 — Validar limite de tamanho de campo de texto

**Prioridade:** Média

**Pré-condições:** campo de texto e limite máximo confirmados na ficha; usuário com permissão de criação; fixture exclusiva.

1. No campo escolhido, insira um valor com exatamente o máximo de caracteres confirmado e salve.
2. Em outro cadastro, insira um valor com um caractere a mais e tente salvar.
3. Reabra os registros e confira o valor persistido.

**Resultado esperado:** o valor no limite é aceito e persistido integralmente. O valor com limite + 1 é rejeitado com indicação do campo, ou não pode ser inserido além do limite; truncamento silencioso ou persistência acima do limite reprova o caso. Se o campo ou limite não estiver confirmado, bloqueie o caso.
