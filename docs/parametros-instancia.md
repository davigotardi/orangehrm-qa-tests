# Parâmetros da instância e dados de teste

Preencha esta ficha antes da rodada e registre a versão/data da configuração. Não deduza valores a partir do comportamento observado durante o teste. Campo obrigatório sem confirmação torna bloqueados os casos que dependem dele.

## Identificação da execução

| Parâmetro | Valor confirmado |
|---|---|
| URL e ambiente (teste/homologação) | |
| Versão/build | |
| Data da confirmação | |
| Navegador e versão | |
| Identificador único da rodada (`RUN`) | |
| Contas de teste (apelidos, nunca senhas) | |

## PIM: campos e regras

Registre os campos obrigatórios e o limite máximo aceito, em caracteres, para cada campo exercitado. Confirme se o limite conta espaços. Se a instância não informar limite, marque os casos de fronteira como bloqueados.

| Campo | Obrigatório? (sim/não) | Máximo de caracteres | Espaços contam? | Confirmado por/data |
|---|---|---:|---|---|
| First Name | | | | |
| Middle Name | | | | |
| Last Name | | | | |
| Employee Id | | | | |
| Outro campo exercitado (especificar) | | | | |

## ACC: matriz de permissões

Registre as contas de teste e preencha cada célula relevante com **Permitido**, **Negado** ou **N/A**. Em linhas de escopo, use registros de teste distintos para o próprio usuário, subordinado e usuário fora do escopo. Célula vazia ou regra não confirmada bloqueia o caso correspondente.

| Perfil | Conta de teste (apelido; sem senha) |
|---|---|
| Admin | |
| Supervisor | |
| ESS | |

| Módulo / recurso e ação | Admin | Supervisor | ESS |
|---|---|---|---|
| PIM — consultar lista de funcionários | | | |
| PIM — criar funcionário | | | |
| PIM — editar funcionário | | | |
| PIM — consultar dados próprios | | | |
| PIM — consultar dados de subordinado | | | |
| PIM — consultar dados fora do escopo | | | |
| PIM — editar dados próprios | | | |
| PIM — editar dados de subordinado | | | |
| PIM — editar dados fora do escopo | | | |
| Claim — consultar solicitação própria | | | |
| Claim — consultar solicitação de outra pessoa | | | |
| Claim — criar solicitação própria | | | |
| Claim — editar rascunho próprio | | | |
| Claim — editar solicitação enviada | | | |
| Claim — enviar solicitação própria | | | |
| Claim — cancelar solicitação própria pendente | | | |
| Claim — aprovar solicitação pendente | | | |
| Claim — rejeitar solicitação pendente | | | |
| Outros módulos/ações (especificar) | | | |

## Claim: campos, valores e datas

Confirme o módulo habilitado e preencha as regras exatamente como configuradas. Informe a moeda e a precisão decimal antes de testar valores. Os limites de valor são inclusivos para CLM-006; qualquer regra diferente deve ser anotada em “Regra/observações” e refletida nos dados de fronteira antes da execução.

| Parâmetro | Valor confirmado |
|---|---|
| Módulo Claim habilitado? | |
| Categoria de teste permitida | |
| Moeda e separador decimal exibido | |
| Valor mínimo permitido (inclusivo) | |
| Valor máximo permitido (inclusivo) | |
| Casas decimais máximas | |
| Regra para valor zero | |
| Regra para valor negativo | |
| Data inicial permitida (inclusiva) | |
| Data final permitida (inclusiva) | |
| Regra para datas fora do período | |
| Campos obrigatórios para salvar rascunho | |
| Campos obrigatórios para enviar | |
| Salvar rascunho incompleto é permitido? | |
| Status de rascunho | |
| Status após envio | |
| Status após aprovação | |
| Status após rejeição | |
| Status após cancelamento | |
| Aprovação exige motivo? | |
| Cancelamento antes da aprovação é permitido? | |
| Fluxo de aprovação/contas de teste | |
| Regra/observações adicionais | |

Para as fronteiras de valor, use o incremento mínimo da moeda na precisão confirmada (por exemplo, 0,01 quando há duas casas decimais). Para a precisão, teste um valor com uma casa decimal a mais que o limite configurado; com limite de duas casas, `12,345` é um exemplo rejeitável. Registre previamente o valor esperado para zero e negativos conforme a regra confirmada.

## Claim: transições de status

Preencha as transições aplicáveis antes de executar CLM-002 a CLM-013. Marque **Permitido** ou **Negado** e informe o status resultante esperado para transições permitidas.

| Status atual | Ação | Ator | Permitido/Negado | Status resultante esperado |
|---|---|---|---|---|
| Rascunho | Editar | Solicitante | | |
| Rascunho | Enviar | Solicitante | | |
| Rascunho | Cancelar | Solicitante | | |
| Enviada/pendente | Editar | Solicitante | **Negado (CLM-011)** | Sem alteração |
| Enviada/pendente | Cancelar | Solicitante | | |
| Enviada/pendente | Aprovar | Aprovador autorizado | | |
| Enviada/pendente | Rejeitar | Aprovador autorizado | | |
| Aprovada | Aprovar ou rejeitar novamente | Aprovador | **Negado (CLM-013)** | Sem alteração |
| Rejeitada | Aprovar ou rejeitar novamente | Aprovador | **Negado (CLM-013)** | Sem alteração |

## Fixtures de teste PIM

Use somente dados fictícios. Antes da rodada, substitua `<RUN>` pelo identificador único definido acima e confirme que o ID não existe na instância. Use caracteres permitidos e respeite os limites preenchidos na tabela PIM.

| Fixture | First Name | Middle Name | Last Name | Employee Id | Uso |
|---|---|---|---|---|---|
| Válido | QA | Teste | PIM | `QA-PIM-<RUN>-001` | Criar e localizar em PIM-002 |
| Inválido | *(vazio)* | Teste | PIM | `QA-PIM-<RUN>-002` | Campo obrigatório vazio em PIM-003 |
| Duplicado | QA | Outro | PIM | `QA-PIM-<RUN>-001` | Reutilizar o ID válido com outro nome em PIM-004 |

Se Employee Id aceitar somente dígitos, use IDs numéricos exclusivos no formato aprovado pela instância e anote-os aqui antes da execução. Para demais casos, registre o ID da fixture utilizada sem incluir dados pessoais.

## Fixtures de teste Claim

Use despesas fictícias e sem anexos que contenham informação pessoal. Registre um identificador por fixture e não reutilize uma solicitação já aprovada/rejeitada para um caso que exija estado pendente.

| Fixture | Categoria | Data | Valor | Descrição/identificador | Caso |
|---|---|---|---:|---|---|
| Válida para rascunho/envio | | Dentro do período permitido | Dentro dos limites | `QA-CLM-<RUN>-001` | CLM-003, CLM-005 |
| Pendente para aprovação | | Dentro do período permitido | Dentro dos limites | `QA-CLM-<RUN>-002` | CLM-008 a CLM-010 |
| Pendente para edição após envio | | Dentro do período permitido | Dentro dos limites | `QA-CLM-<RUN>-003` | CLM-011 |
| Pendente para cancelamento | | Dentro do período permitido | Dentro dos limites | `QA-CLM-<RUN>-004` | CLM-012 |

Preencha dados de fronteira para CLM-006 e CLM-007 antes da execução:

| Verificação | Valor de teste | Esperado (aceito/rejeitado) |
|---|---:|---|
| Zero | `0` | |
| Negativo | `-0,01` ou menor incremento da moeda | |
| Mínimo permitido | | Aceito se o limite for inclusivo |
| Um incremento abaixo do mínimo | | Rejeitado se o limite for inclusivo |
| Máximo permitido | | Aceito se o limite for inclusivo |
| Um incremento acima do máximo | | Rejeitado se o limite for inclusivo |
| Precisão: uma casa acima do máximo configurado | | |
| Data inicial permitida | | Aceita se inclusiva |
| Dia anterior à data inicial | | Rejeitada se o limite for inclusivo |
| Data final permitida (último dia) | | Aceita se inclusiva |
| Dia posterior à data final (primeiro proibido) | | Rejeitada se o limite for inclusivo |
