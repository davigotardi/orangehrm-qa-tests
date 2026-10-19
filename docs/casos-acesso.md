# Casos de teste — Navegação e permissões

## Preparação da matriz

Antes da execução, obtenha do responsável pela instância a matriz autorizada para cada conta de Admin, Supervisor e ESS. Registre, por módulo e ação, se a conta pode visualizar, criar, editar, excluir, enviar ou aprovar. Não presuma que nomes de perfil impliquem permissões idênticas em todas as instalações.

Use contas de teste separadas. Para cada caso, configure a pré-condição com uma ação explicitamente permitida ou negada na matriz; se não houver expectativa confirmada, marque o caso como bloqueado.

## ACC-001 — Acessar uma ação permitida

**Prioridade:** Alta  
**Pré-condições:** conta de teste; ação explicitamente permitida na matriz.

1. Entre com a conta.
2. Abra o módulo e execute a ação permitida em um registro de teste.

**Resultado esperado:** a ação está disponível e pode ser concluída conforme a permissão documentada.

## ACC-002 — Negar uma ação não permitida

**Prioridade:** Alta  
**Pré-condições:** conta de teste; ação explicitamente negada na matriz.

1. Entre com a conta.
2. Verifique se a ação está indisponível na interface.
3. Se houver uma URL direta conhecida para a ação, tente acessá-la sem executar alterações.

**Resultado esperado:** a ação não pode ser concluída. O sistema oculta ou desabilita a ação, redireciona ou apresenta uma resposta de acesso negado, conforme o padrão da instalação; não deve expor dados nem efetivar alterações.

## ACC-003 — Verificar permissões do Admin

**Prioridade:** Alta  
**Pré-condições:** conta Admin de teste e matriz de permissões confirmada.

1. Entre como Admin.
2. Verifique uma ação permitida e uma ação negada na matriz.

**Resultado esperado:** o resultado corresponde à matriz configurada; não se presume acesso irrestrito a todos os módulos.

## ACC-004 — Verificar permissões do Supervisor

**Prioridade:** Alta  
**Pré-condições:** conta Supervisor de teste e matriz confirmada; registro de teste pertinente ao escopo do supervisor.

1. Entre como Supervisor.
2. Consulte ou altere o registro conforme a permissão esperada.
3. Tente acessar um registro fora do escopo, se a matriz documentar essa restrição.

**Resultado esperado:** ações e registros acessíveis correspondem à matriz e ao escopo documentado; acesso fora do escopo não revela dados nem permite alterações.

## ACC-005 — Verificar permissões do ESS

**Prioridade:** Alta  
**Pré-condições:** conta ESS de teste e matriz confirmada; dados próprios e de outro usuário de teste.

1. Entre como ESS.
2. Acesse as funções permitidas para a conta.
3. Tente consultar ou alterar dados de outro usuário apenas se a matriz negar esse acesso.

**Resultado esperado:** a conta consegue usar as funções autorizadas e não acessa dados ou ações explicitamente proibidos.

## ACC-006 — Navegar entre módulos disponíveis

**Prioridade:** Média  
**Pré-condições:** conta com acesso a pelo menos dois módulos.

1. Abra cada módulo autorizado pelo menu.
2. Retorne à página anterior ou use a navegação interna.

**Resultado esperado:** as telas corretas são abertas e a navegação não apresenta erro nem mostra ações incompatíveis com a matriz.

## ACC-007 — Bloquear acesso direto após logout

**Prioridade:** Alta  
**Pré-condições:** conta autenticada e URL de uma tela restrita conhecida.

1. Registre a URL da tela (sem parâmetros que contenham dados sensíveis).
2. Encerre a sessão pelo mecanismo de logout.
3. Tente abrir a URL registrada em uma nova navegação.

**Resultado esperado:** o conteúdo restrito não é exibido; a aplicação solicita autenticação ou apresenta a resposta prevista para sessão encerrada.

## ACC-008 — Não restaurar sessão protegida pelo botão Voltar

**Prioridade:** Média  
**Pré-condições:** conta autenticada e tela restrita visitada.

1. Encerre a sessão.
2. Use o botão Voltar do navegador para retornar à tela protegida.
3. Atualize a página, se o navegador oferecer essa opção.

**Resultado esperado:** dados protegidos não ficam disponíveis após o logout; a aplicação exige autenticação válida antes de exibi-los.
