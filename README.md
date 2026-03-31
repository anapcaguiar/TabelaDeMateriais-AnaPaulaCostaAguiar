# Desenvolvimento com BTP, GIT e CAP

## Objetivo

Avaliar os conhecimentos adquiridos durante as aulas de BTP, GIT e desenvolvimento CAP.

---

## Parte 1 — Git e Desenvolvimento de Repositório

**Objetivo:** Trabalhar com Git, criando um repositório, branches, commits e pull requests.

### Instruções

**1. Criar um novo repositório Git:**
- Nome do repositório: `TabelaDeMateriais(SEU-NOME)`
- Criar a branch `Development`
- Criar a branch `feature/DevCapTabelaMaterial`

**2. Objetivos da Atividade:**
- Trabalhar com o Git: criar o repositório, realizar clone no ambiente de desenvolvimento
- Criar e alternar entre branches
- Fazer commits e push periódicos
- Ao finalizar o desenvolvimento, criar uma pull request da branch `feature/DevCapTabelaMaterial` para a branch `Development`

---

## Parte 2 — Projeto CAP – Tabela de Materiais

**Objetivo:** Criar um projeto CAP, definir uma estrutura de tabela e implementar funcionalidades para manipulação de dados.

### Instruções

**3.** Criar um projeto CAP do zero, conforme mostrado nas aulas.

**4. Criar a tabela de materiais com a seguinte estrutura:**

| Campo | Tipo |
|---|---|
| Key ID | Int |
| Key NumMat | Int |
| Nome | String |
| Descr | String |

**5.** Criar um serviço para expor a tabela de materiais.

**6.** Gerar um arquivo CSV dentro da pasta `data`, contendo 10 registros de materiais, que serão utilizados para rodar o projeto localmente.

**7.** Criar uma função (`filtroMateriais`) que receba um número (quantidade) e retorne a quantidade correspondente de materiais da tabela.

> 💡 Exemplo: se a quantidade for `3` e a tabela contiver `10` materiais, a função deve retornar `3` materiais (aleatórios ou sequenciais).

**8. 🏆 Desafio: Criar uma action para adicionar novos materiais na tabela.**
- Campos obrigatórios: `ID`, `NumMat`, `Nome`, `Descr`
- Validar se o material já foi cadastrado, verificando o campo `NumMat`
- O campo `ID` deve ser sequencial (próximo ID = último ID + 1)
- Retornar uma mensagem de sucesso ou erro da operação realizada

---

## Parte 3 — Front-end – Exibição e Manipulação de Dados

**Objetivo:** Criar uma tela no front-end que exiba a tabela de materiais e permita interações de filtro e criação de novos registros, utilizando a Model para manipulação dos dados.

> A tela deve conter: um campo Input, um botão Filtro e uma tabela para mostrar os dados.

### Instruções

**9.** Exibir a tabela de materiais na tela inicial do aplicativo utilizando uma **SAP Table** (não usar list, conforme as aulas).

**10. Usar a Model para manipulação dos dados:**
- Os dados devem ser carregados inicialmente pela controller para a Model
- Dentro do `onInit` da controller, crie a rota que chamará o handler
- Crie um handler com duas funções:
  - Uma para cadastrar a Model na página
  - Uma para carregar dados da tabela na Model
- Na Model, defina a entidade `tableMaterial` que representará os dados da tabela de materiais
- Adicione dados predefinidos na tabela para que ela seja populada na primeira execução

**11. Adicionar a funcionalidade de filtro:**
- A função `filtroMateriais` será utilizada para carregar dados na Model e chamada pelo botão Filtro, tendo o campo Input
- Quando o botão for clicado, substituirá os dados na Model com a quantidade de registros solicitados no Input
- A tabela na tela será atualizada automaticamente com os dados filtrados

**12. 🏆 Desafio: Criar um botão "Criar" no cabeçalho da tabela.**
- O botão deve abrir um pop-up com três inputs: `ID`, `Nome` e `Descr`
- Validar se os campos estão preenchidos corretamente antes de enviar para a action
- Se os campos estiverem corretos, enviar os dados para a action e exibir uma mensagem de sucesso ou erro usando `message.box`