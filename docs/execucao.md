# Guia de execução dos testes

## Identificação dos casos

Os casos usam um identificador estável por suíte:

- `PIM`: cadastro, edição e pesquisa de funcionários.
- `ACC`: navegação e permissões.
- `CLM`: solicitações de reembolso (Claim).

Prioridades indicam impacto no objetivo funcional: **Alta** cobre fluxos essenciais; **Média** cobre validações e variações importantes; **Baixa** cobre conveniência e recuperação. Prioridade não substitui a decisão de execução do responsável pelo teste.

## Preparação

1. Registre URL, data/hora, versão/build (se disponível), navegador e perfil utilizado.
2. Confirme que a instância está disponível e que as credenciais de teste estão válidas. Não registre senhas nem use dados pessoais.
3. Preencha [parâmetros da instância e dados de teste](parametros-instancia.md), incluindo a matriz ACC, campos/regras de Claim e fixtures. Não comece casos dependentes de parâmetros em branco ou não confirmados: marque-os como bloqueados.
4. Prepare contas dedicadas de teste, sem reutilizar IDs ou nomes existentes. Use o identificador único da rodada para gerar os IDs das fixtures.
5. Registre os dados de teste usados de forma não sensível para que a execução possa ser repetida.

Não altere dados de produção. Na demo pública, considere que dados e configuração podem ser redefinidos ou modificados por terceiros.

## Execução e resultado

Execute os passos na ordem. Marque cada caso como:

- **Aprovado**: todos os resultados esperados observáveis foram atendidos.
- **Reprovado**: ao menos um resultado esperado não foi atendido; registre o resultado observado e os passos para reproduzir.
- **Bloqueado**: pré-condição indisponível, configuração não confirmada ou ambiente impede a execução. Explique o impedimento; não conte como aprovado.
- **Não executado**: ainda não iniciado.

Para cada execução, registre:

| Campo | Valor |
|---|---|
| ID do caso | |
| Resultado | |
| Executado por / data | |
| Ambiente / perfil | |
| Dados de teste (sem segredos) | |
| Resultado observado | |
| Evidência (referência/link) | |
| Defeito ou motivo do bloqueio | |

Em reprovações, preserve evidências sem expor senhas ou dados pessoais. Registre o texto exato de mensagens, limites e regras observadas quando forem relevantes.

## Regras da instância

Os resultados esperados que dependem da instalação devem ser preenchidos e aprovados em [parâmetros da instância e dados de teste](parametros-instancia.md) antes da rodada. Registre ali a matriz de acesso, categorias, moeda, precisão, limites, datas permitidas, campos obrigatórios e transições de status. Não transforme comportamento descoberto durante o teste em requisito retroativo; se um parâmetro estiver ausente, marque o caso dependente como bloqueado.

## Critério de saída

Como critério inicial, todos os casos de prioridade Alta que sejam executáveis devem estar aprovados, e toda reprovação ou bloqueio deve ter evidência e justificativa. O responsável pela execução pode ajustar o critério antes da rodada, documentando a decisão.
