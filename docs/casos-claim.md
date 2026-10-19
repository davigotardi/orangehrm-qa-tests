# Casos de teste — Claims

## Preparação

Confirme que Claims está habilitado e registre categoria, moeda, limites, regras de data, status e aprovadores definidos na instância. Prepare uma conta solicitante e contas aprovadoras com permissões confirmadas, além de despesas fictícias. Se uma regra ou transição não estiver configurada/documentada, marque o caso correspondente como bloqueado.

## CLM-001 — Abrir o formulário de nova solicitação

**Prioridade:** Alta  
**Pré-condições:** conta com permissão de criação de Claim; módulo habilitado.

1. Abra Claims e inicie uma nova solicitação.

**Resultado esperado:** o formulário é exibido e apresenta os campos e ações disponíveis para a configuração da instância.

## CLM-002 — Validar campos obrigatórios

**Prioridade:** Média  
**Pré-condições:** conta solicitante; campos obrigatórios identificados.

1. Abra uma nova solicitação.
2. Deixe vazio um campo obrigatório.
3. Tente salvar ou enviar.

**Resultado esperado:** a solicitação incompleta não é salva/enviada como válida e o sistema indica o que precisa ser preenchido.

## CLM-003 — Salvar solicitação válida

**Prioridade:** Alta  
**Pré-condições:** categoria e regras conhecidas; dados de despesa fictícios válidos; conta solicitante.

1. Preencha os campos exigidos com dados válidos para a configuração.
2. Salve a solicitação sem enviá-la, se a opção de rascunho estiver disponível.
3. Abra a lista ou detalhe da solicitação.

**Resultado esperado:** a solicitação é registrada uma única vez e pode ser localizada. O status exibido corresponde ao estado de rascunho definido pela instalação.

## CLM-004 — Impedir envio de solicitação incompleta

**Prioridade:** Alta  
**Pré-condições:** conta solicitante; campos obrigatórios identificados.

1. Inicie uma solicitação e deixe um campo obrigatório vazio.
2. Tente enviá-la.

**Resultado esperado:** a solicitação não avança para o fluxo de aprovação e o sistema informa os dados pendentes.

## CLM-005 — Enviar solicitação válida

**Prioridade:** Alta  
**Pré-condições:** solicitação completa que ainda não foi enviada; fluxo de aprovação configurado.

1. Abra a solicitação válida.
2. Execute a ação de envio.
3. Consulte seu detalhe e a lista do solicitante.

**Resultado esperado:** a solicitação é enviada uma única vez e passa ao estado de submissão configurado; o solicitante consegue consultar o resultado/status.

## CLM-006 — Validar valor conforme as regras configuradas

**Prioridade:** Média  
**Pré-condições:** limites, moeda, precisão decimal e regras para valores não positivos documentados.

1. Tente inserir um valor dentro dos limites configurados.
2. Tente inserir valores de teste fora de cada limite relevante, sem enviar despesas reais.

**Resultado esperado:** valores válidos são aceitos; valores explicitamente proibidos são rejeitados ou sinalizados conforme a regra documentada. Registre a precisão e a mensagem observadas.

## CLM-007 — Validar datas conforme o período permitido

**Prioridade:** Média  
**Pré-condições:** período e regras de data permitidos documentados.

1. Tente registrar uma despesa dentro do período permitido.
2. Tente uma data anterior ou posterior ao período, conforme aplicável.

**Resultado esperado:** o sistema aceita ou rejeita cada data de acordo com as regras documentadas e identifica a correção necessária quando a data não é permitida.

## CLM-008 — Aprovar uma solicitação enviada

**Prioridade:** Alta  
**Pré-condições:** solicitação enviada e pendente; conta aprovadora autorizada pela configuração.

1. Entre com a conta aprovadora.
2. Localize e abra a solicitação pendente.
3. Aprove a solicitação.
4. Consulte o detalhe como aprovador e como solicitante.

**Resultado esperado:** a aprovação é registrada uma única vez, o status avança conforme o fluxo configurado e o resultado fica visível para os usuários autorizados.

## CLM-009 — Rejeitar uma solicitação enviada

**Prioridade:** Alta  
**Pré-condições:** solicitação pendente distinta; conta aprovadora autorizada; motivo obrigatório conhecido, se houver.

1. Entre com a conta aprovadora e abra a solicitação.
2. Rejeite-a e informe o motivo se o formulário exigir.
3. Consulte o detalhe como aprovador e como solicitante.

**Resultado esperado:** a rejeição é registrada uma única vez, o status corresponde ao fluxo configurado e o motivo é preservado quando informado/obrigatório.

## CLM-010 — Negar aprovação por usuário sem permissão

**Prioridade:** Alta  
**Pré-condições:** solicitação pendente; conta explicitamente não autorizada a aprovar; matriz confirmada.

1. Entre com a conta sem permissão.
2. Tente localizar e aprovar a solicitação.

**Resultado esperado:** a conta não consegue aprovar nem alterar a solicitação; o estado e os dados da solicitação permanecem inalterados.

## CLM-011 — Impedir ação incompatível com o estado atual

**Prioridade:** Média  
**Pré-condições:** solicitação em estado final ou outro estado para o qual a matriz de transições não permita a ação.

1. Abra a solicitação.
2. Tente repetir a ação já concluída ou executar uma transição proibida segundo a configuração.

**Resultado esperado:** o sistema não cria uma transição duplicada nem altera o estado de forma incompatível; ações disponíveis correspondem às transições configuradas.
