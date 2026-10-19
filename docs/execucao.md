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
3. Prepare funcionários e contas dedicados a teste, sem reutilizar IDs ou nomes que possam pertencer a outros usuários.
4. Para `ACC`, obtenha a matriz de permissões esperada para Admin, Supervisor e ESS. As permissões podem variar entre instalações.
5. Para `CLM`, confirme que o módulo está habilitado e registre as categorias, moeda, regras de valor/data, fluxo de aprovação e contas aprovadoras configuradas.
6. Registre os dados de teste usados de forma não sensível para que a execução possa ser repetida.

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

## Regras configuráveis

Casos de permissão dependem da matriz de acesso aprovada para a instalação. Casos de Claim dependem de regras como categorias, moeda, limites, período permitido e cadeia de aprovação. Se uma regra não estiver documentada ou não puder ser confirmada, marque o caso como bloqueado em vez de inferir um resultado esperado.

## Critério de saída

Como critério inicial, todos os casos de prioridade Alta que sejam executáveis devem estar aprovados, e toda reprovação ou bloqueio deve ter evidência e justificativa. O responsável pela execução pode ajustar o critério antes da rodada, documentando a decisão.
