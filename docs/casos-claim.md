# Casos de teste — Claims

## Preparação

Antes da execução, preencha [parâmetros da instância e dados de teste](parametros-instancia.md), incluindo campos obrigatórios, categorias, moeda, limites, precisão decimal, período, transições e contas. Use as fixtures fictícias dessa ficha. Caso um parâmetro necessário esteja vazio, marque o caso dependente como bloqueado.

## CLM-001 — Abrir o formulário de nova solicitação

**Prioridade:** Alta

**Pré-condições:** conta com permissão de criação de Claim; módulo habilitado.

1. Abra Claims e inicie uma nova solicitação.

**Resultado esperado:** o formulário de nova solicitação é exibido; os campos obrigatórios e a categoria selecionada correspondem aos parâmetros preenchidos. Campo obrigatório não documentado bloqueia o caso.

## CLM-002 — Validar salvamento de rascunho incompleto

**Prioridade:** Média

**Pré-condições:** conta solicitante; campos obrigatórios para salvar rascunho identificados na ficha; política de rascunho incompleto preenchida.

1. Abra uma nova solicitação e deixe vazio um campo obrigatório para envio.
2. Tente salvar a solicitação como rascunho.

**Resultado esperado:** o resultado corresponde à política documentada: se salvar rascunho incompleto for permitido, somente um rascunho é criado, com o status registrado na ficha; se for proibido, nada é salvo e o campo pendente é indicado. O rascunho nunca aparece como enviado ou na fila de aprovação. Política não preenchida bloqueia o caso.

## CLM-003 — Salvar solicitação válida

**Prioridade:** Alta  
**Pré-condições:** categoria e regras registradas na ficha; fixture Claim válida; conta solicitante.

1. Preencha os campos exigidos com a fixture válida da ficha.
2. Salve a solicitação sem enviá-la.
3. Abra a lista ou detalhe da solicitação.

**Resultado esperado:** a solicitação é registrada uma única vez, pode ser localizada pelo identificador da fixture e seu status é exatamente o status de rascunho registrado na ficha. Sem suporte a rascunho confirmado, bloqueie o caso.

## CLM-004 — Impedir envio de solicitação incompleta

**Prioridade:** Alta  
**Pré-condições:** conta solicitante; campos obrigatórios para envio identificados na ficha.

1. Inicie uma solicitação e deixe um campo obrigatório vazio.
2. Tente enviá-la.

**Resultado esperado:** a solicitação não é enviada, não aparece na fila de aprovação e o campo obrigatório vazio é identificado. Qualquer avanço de status reprova o caso.

## CLM-005 — Enviar solicitação válida

**Prioridade:** Alta  
**Pré-condições:** solicitação completa que ainda não foi enviada; fluxo de aprovação configurado.

1. Abra a solicitação válida.
2. Execute a ação de envio.
3. Consulte seu detalhe e a lista do solicitante.

**Resultado esperado:** a solicitação aparece uma única vez na lista do solicitante e seu status é exatamente o status após envio registrado na ficha.

## CLM-006 — Validar fronteiras e precisão do valor

**Prioridade:** Média  
**Pré-condições:** moeda, limites inclusivos, precisão máxima e resultados esperados para zero e negativo preenchidos na ficha; fixtures independentes por tentativa.

1. Tente salvar valores de `0` e `-0,01` (ou o menor incremento negativo da moeda); compare cada resultado com a regra documentada.
2. Tente salvar o mínimo e o máximo, que devem ser aceitos porque os limites estão definidos como inclusivos.
3. Tente salvar o mínimo menos um incremento e o máximo mais um incremento; ambos devem ser rejeitados.
4. Tente salvar um valor com uma casa decimal além da precisão máxima documentada (por exemplo, `12,345` quando o máximo é duas casas).

**Resultado esperado:** zero e negativo são aceitos/rejeitados exatamente como registrado na ficha; mínimo e máximo são aceitos; valores imediatamente fora dos limites e valores acima da precisão máxima são rejeitados e não podem ser enviados. Registre cada valor, resultado e mensagem. Parâmetro ausente bloqueia o caso.

## CLM-007 — Validar fronteiras do período de datas

**Prioridade:** Média  
**Pré-condições:** datas inicial/final inclusivas e política para datas fora do período preenchidas na ficha; conta solicitante.

1. Tente registrar uma despesa na data inicial permitida.
2. Tente a data imediatamente anterior à data inicial.
3. Tente registrar uma despesa no último dia permitido.
4. Tente o primeiro dia após a data final permitida.

**Resultado esperado:** datas inicial e final são aceitas; o dia anterior à data inicial e o primeiro dia após a data final são rejeitados, conforme limites inclusivos. Datas inválidas não podem ser enviadas. Registre datas e mensagens; período não preenchido bloqueia o caso.

## CLM-008 — Aprovar uma solicitação enviada

**Prioridade:** Alta  
**Pré-condições:** solicitação enviada e pendente; conta aprovadora autorizada pela configuração.

1. Entre com a conta aprovadora.
2. Localize e abra a solicitação pendente.
3. Aprove a solicitação.
4. Consulte o detalhe como aprovador e como solicitante.

**Resultado esperado:** a aprovação é registrada uma única vez; o status corresponde ao status após aprovação da ficha e fica visível para as contas autorizadas.

## CLM-009 — Rejeitar uma solicitação enviada

**Prioridade:** Alta  
**Pré-condições:** solicitação pendente distinta; conta aprovadora autorizada; motivo obrigatório conhecido, se houver.

1. Entre com a conta aprovadora e abra a solicitação.
2. Rejeite-a e informe o motivo se o formulário exigir.
3. Consulte o detalhe como aprovador e como solicitante.

**Resultado esperado:** a rejeição é registrada uma única vez; o status corresponde ao status após rejeição da ficha e o motivo é salvo quando obrigatório.

## CLM-010 — Negar aprovação por usuário sem permissão

**Prioridade:** Alta  

**Pré-condições:** solicitação pendente; conta marcada **Negado** na linha “Claim — aprovar solicitação pendente” da matriz.

1. Entre com a conta sem permissão.
2. Tente localizar e aprovar a solicitação.

**Resultado esperado:** a conta não consegue aprovar nem alterar a solicitação; o estado e os dados da solicitação permanecem inalterados.

## CLM-011 — Impedir edição após envio

**Prioridade:** Alta

**Pré-condições:** solicitação da fixture pendente para edição, enviada pela conta solicitante; linha “Claim — editar solicitação enviada” marcada **Negado** na matriz.

1. Abra a solicitação enviada como solicitante.
2. Tente alterar descrição, valor ou categoria e salvar.

**Resultado esperado:** a alteração é rejeitada; descrição, valor, categoria e status permanecem inalterados. Qualquer alteração persistida reprova o caso.

## CLM-012 — Cancelar solicitação antes da aprovação

**Prioridade:** Média

**Pré-condições:** solicitação da fixture para cancelamento ainda pendente e não aprovada/rejeitada; política de cancelamento e status resultante preenchidos na ficha.

1. Abra a solicitação pendente como solicitante.
2. Cancele a solicitação e confirme a ação, se solicitado.
3. Consulte o detalhe e a lista do solicitante e a fila do aprovador.

**Resultado esperado:** o comportamento corresponde à política registrada. Se permitido, a solicitação deixa de estar pendente para aprovação e assume o status de cancelamento documentado; se proibido, não é cancelada e seu status/dados permanecem inalterados. Política ou status resultante ausente bloqueia o caso.

## CLM-013 — Impedir ação incompatível com o estado atual

**Prioridade:** Média  
**Pré-condições:** solicitação aprovada ou rejeitada; transições proibidas confirmadas na ficha.

1. Abra uma solicitação aprovada ou rejeitada.
2. Tente repetir a ação já concluída e executar outra transição que a ficha marque como proibida.

**Resultado esperado:** nenhuma transição proibida é concluída, nenhuma aprovação/rejeição duplicada é criada e o status terminal permanece inalterado. Transições não documentadas bloqueiam o caso.
