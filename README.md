# Testes de QA — OrangeHRM

Repositório de documentação e preparação de testes funcionais para o OrangeHRM. Os casos de teste seguem o formato usado no projeto Sauce Demo e cobrem cadastro e busca de funcionários, navegação, permissões e o fluxo de solicitações de reembolso (Claim).

> **Status:** em desenvolvimento

## Escopo

### Incluído

- PIM: cadastro, edição e validação de funcionários.
- Busca de funcionários por nome, ID e filtros combinados.
- Navegação entre telas e tentativa de acesso direto a páginas restritas.
- Verificação de permissões para Admin, Supervisor e ESS.
- Claims: criação, envio, aprovação, rejeição e validação de regras de valor, data e transição de status.

### Fora do escopo atual

- Fluxo de compra ou pagamento: o OrangeHRM não é um sistema de e-commerce.
- Testes de carga, desempenho, segurança especializada e compatibilidade ampla entre navegadores.
- Automatização dos casos e integração contínua, até que essas partes sejam adicionadas ao projeto.

O módulo Claim é usado como cenário de aprovação de negócio, em substituição ao fluxo de compra. Sua disponibilidade e suas regras dependem da configuração da instância.

## Estrutura

- [`docs/execucao.md`](docs/execucao.md): preparação, dados de teste, registro de resultados e critério de saída.
- [`docs/casos-pim.md`](docs/casos-pim.md): cadastro, edição, busca e filtros de funcionários.
- [`docs/casos-acesso.md`](docs/casos-acesso.md): navegação e verificação de acesso por perfil.
- [`docs/casos-claim.md`](docs/casos-claim.md): criação, envio e aprovação/rejeição de solicitações de reembolso.

## Ambiente de teste

É possível começar pela demo pública:

- URL: <https://opensource-demo.orangehrmlive.com/>
- Credenciais divulgadas para a demo: `Admin` / `admin123`

A demo pode ser resetada ou alterada sem aviso. Confirme se a URL e as credenciais continuam válidas antes de executar os testes e não use dados pessoais ou informações confidenciais. Para resultados repetíveis, prefira uma instância própria com dados de teste controlados.

Para os casos de permissão, prepare contas com os perfis Admin, Supervisor e ESS. Para os casos de Claim, confirme que o módulo está habilitado e configure previamente categorias, moeda, período permitido e aprovador. A interface e as permissões podem variar entre versões e instalações.

## Execução manual

1. Leia as pré-condições do caso e prepare os dados necessários na instância.
2. Execute os passos na ordem indicada.
3. Compare o comportamento observado com o resultado esperado.
4. Registre o resultado como aprovado, reprovado ou bloqueado. Anote ambiente, versão, evidências e, em caso de reprovação, os passos para reproduzir e o resultado observado.
5. Para mensagens, limites de campos e regras que dependem da configuração, registre o texto ou valor efetivamente observado; não presuma um comportamento específico da demo.

**Critério de saída proposto:** todos os casos de prioridade Alta executáveis passam, e toda falha ou bloqueio fica documentado com evidência e justificativa. Ajuste esse critério conforme o objetivo da execução.

# orangehrm-qa-tests
