# Parte 1 — Git e Desenvolvimento de Repositório

---

## 10. Criar Branch feature/DevCapTabelaMaterial

> 💡 **Boa prática:** Crie sempre o branch no GitHub primeiro e depois puxe com `git pull`. É mais fácil do que criar localmente e publicar depois.

### Step — No GitHub

1. No repositório, clique em **main** > **View all branches** > **New branch**.
2. Crie a branch `feature/DevCapTabelaMaterial` a partir de `Development`.

### Step — No BAS

```bash
git pull
git checkout feature/DevCapTabelaMaterial
```

**Resultado no terminal:**
```bash
user: TabelaDeMateriais-AnaPaulaCostaAguiar $ git checkout feature/DevCapTabelaMaterial
branch 'feature/DevCapTabelaMaterial' set up to track 'origin/feature/DevCapTabelaMaterial'.
Switched to a new branch 'feature/DevCapTabelaMaterial'
```

### Step — Commit

```bash
git add .
git commit -m "[PARTE 1] chore: pull feature/DevCapTabelaMaterial branch from GitHub"
```

---

## 11. Criar arquivo docs/feature-DevCapTabelaMaterial.md

### Step — Criar o arquivo

```bash
touch docs/feature-DevCapTabelaMaterial.md
```

### Step — Editar o arquivo

Abra o `docs/feature-DevCapTabelaMaterial.md` no Explorer do BAS e adicione o conteúdo desejado.

### Step — Commit e Push

```bash
git add .
git commit -m "[PARTE 1] docs: create and update docs/feature-DevCapTabelaMaterial with instructions"
git push
```

---

## 12. Compare, Pull Request & Merge — feature/DevCapTabelaMaterial → Development

### Step — No GitHub, clique em "Compare & pull request"

- **base:** `Development`
- **compare:** `feature/DevCapTabelaMaterial`

### Step — Adicione título e descrição

**Título:**
```
[PARTE 1] chore: create feature/DevCapTabelaMaterial branch and documentation
```

**Descrição:**
```
### GitHub
- Criação da branch feature/DevCapTabelaMaterial a partir da Development

### SAP BAS
- git pull e git checkout feature/DevCapTabelaMaterial
- Criação do arquivo docs/feature-DevCapTabelaMaterial.md
- Documentação dos passos realizados
```

- Clique em **Create pull request**

### Step — Commit e Push

```bash
git add .
git commit -m "[PARTE 1] docs: update docs/feature-DevCapTabelaMaterial with PR and merge steps"
git push
```

### Step — Revisão e Merge

- Adicione o comentário de revisão:

```
## Revisão - Ana Paula Costa Aguiar

> ⚠️ Simulação de revisão — em um projeto real, essa etapa seria feita por um tech lead ou desenvolvedor senior.

✅ Branch feature/DevCapTabelaMaterial criada corretamente a partir da Development
✅ Documentação dos passos realizada no docs/feature-DevCapTabelaMaterial.md
✅ Commits padronizados seguindo o padrão [PARTE 1] tipo: descrição

PR aprovado. Pode realizar o merge.
```

- Clique em **Comment**
- Clique em **Merge pull request**
- Clique em **Confirm merge** ✅

# Parte 2 — Projeto CAP – Tabela de Materiais

## Objetivo

Criar um projeto CAP, definir uma estrutura de tabela e implementar funcionalidades para manipulação de dados.

---

## 1. Confirmar branch e localização

```bash
git branch
git checkout feature/DevCapTabelaMaterial
pwd
```

---

## 2. Criar o projeto CAP

```bash
cds init CAP_TabelaDeMateriais
```

### Step — Commit

```bash
git add .
git commit -m "[PARTE 2] feat: create CAP project"
```

### Step — Entrar na pasta do projeto

```bash
cd CAP_TabelaDeMateriais
```

### Step — Instalar dependências

```bash
npm install
```

### Step — Commit

```bash
git add .
git commit -m "[PARTE 2] feat: install dependencies"
```

---

## 3. Criar o schema.cds

### Step — Criar arquivo

```bash
touch db/schema.cds
```

### Step — Adicionar código ao arquivo

```cds
namespace materiais;
entity Material {
    key ID     : Integer;
    key NumMat : Integer;
    Nome       : String;
    Descr      : String;
}
```

Salve com `Ctrl + S`.

### Step — Commit

```bash
git add .
git commit -m "[PARTE 2] feat: create schema.cds with Material entity"
```

---

## 4. Criar o service.cds

### Step — Criar arquivo

```bash
touch srv/service.cds
```

### Step — Adicionar código ao arquivo

```cds
using materiais from '../db/schema';
service MateriaisService {
    entity Material as projection on materiais.Material;
}
```

Salve com `Ctrl + S`.

### Step — Commit

```bash
git add .
git commit -m "[PARTE 2] feat: create service.cds with MateriaisService"
```

---

## 5. Testar o projeto

### Step — Rodar projeto

```bash
cds watch
```

> 💡 A tabela está vazia ainda porque não criamos o CSV. Pare o servidor com `Ctrl + C` para continuar.

---

## 6. Criar o CSV com 10 registros

### Step — Parar servidor

Pare o servidor com `Ctrl + C`.

### Step — Criar pasta

```bash
mkdir db/data
```

### Step — Commit

```bash
git add .
git commit -m "[PARTE 2] feat: create data folder"
```

### Step — Criar arquivo

```bash
touch db/data/materiais-Material.csv
```

### Step — Adicionar informações ao arquivo

```csv
ID,NumMat,Nome,Descr
1,3001,Caneta,Caneta esferográfica azul
2,3002,Lapis,Lápis grafite nº 2
3,3003,Borracha,Borracha branca macia
4,3004,Regua,Régua plástica 30cm
5,3005,Tesoura,Tesoura inox multiuso
6,3006,Grampeador,Grampeador de mesa 26/6
7,3007,Clips,Clips metálico nº 2 caixa 50un
8,3008,Pasta,Pasta arquivo com elástico
9,3009,Bloco,Bloco de notas adesivo amarelo
10,3010,Corretivo,Corretivo líquido branco 18ml
```

Salve com `Ctrl + S`.

### Step — Commit

```bash
git add .
git commit -m "[PARTE 2] feat: create CSV with 10 material records"
```

### Step — Rodar projeto

```bash
cds watch
```

> 💡 Marque o **Pretty-print** no canto superior esquerdo para visualizar melhor os dados!

---

## 7. Criar a função filtroMateriais

### Step — Parar servidor

Pare o servidor com `Ctrl + C`.

### Step — Atualizar arquivo srv/service.cds

```cds
using materiais from '../db/schema';
service MateriaisService {
    entity Material as projection on materiais.Material;
    function filtroMateriais(quantidade : Integer) returns array of Material;
}
```

Salve com `Ctrl + S`.

### Step — Commit

```bash
git add .
git commit -m "[PARTE 2] feat: add filtroMateriais function in srv/service.cds"
```

### Step — Criar arquivo srv/service.js

```bash
touch srv/service.js
```

### Step — Adicionar código ao arquivo

```js
const cds = require('@sap/cds')
module.exports = cds.service.impl(async function () {
    this.on('filtroMateriais', async (req) => {
        const { quantidade } = req.data;
        const materiais = await SELECT.from('MateriaisService.Material');
        return materiais.slice(0, quantidade);
    })
})
```

Salve com `Ctrl + S`.

### Step — Commit

```bash
git add .
git commit -m "[PARTE 2] feat: create srv/service.js with filtroMateriais implementation"
```

### Step — Rodar projeto e testar

```bash
cds watch
```

Acesse no browser:
```
/odata/v4/materiais/filtroMateriais(quantidade=3)
```

> 💡 Deve retornar apenas 3 materiais!

---

## 8. Atualizar docs/feature-DevCapTabelaMaterial.md

### Step — Voltar para a pasta raiz

```bash
cd ..
```

### Step — Atualizar o arquivo

Abra o `docs/feature-DevCapTabelaMaterial.md` no Explorer do BAS e adicione o conteúdo desejado.

### Step — Commit e Push

```bash
git add .
git commit -m "[PARTE 2] docs: update docs/feature-DevCapTabelaMaterial with instructions"
git push
```

---

## 9. Compare, Pull Request & Merge — feature/DevCapTabelaMaterial → Development

### Step — No GitHub, clique em "Compare & pull request"

- **base:** `Development`
- **compare:** `feature/DevCapTabelaMaterial`

### Step — Adicione título e descrição

**Título:**
```
[PARTE 2] feat: create CAP project with Material table, CSV and filtroMateriais function
```

**Descrição:**
```
### GitHub
- Criação da branch feature/DevCapTabelaMaterial a partir da Development

### SAP BAS
- Criação do projeto CAP_TabelaDeMateriais
- Criação do schema.cds com a entidade Material
- Criação do service.cds com MateriaisService
- Criação do CSV com 10 registros
- Criação da função filtroMateriais
- Documentação dos passos realizados
```

- Clique em **Create pull request**

### Step — Revisão e Merge

- Adicione o comentário de revisão:

```
## Revisão - Ana Paula Costa Aguiar

> ⚠️ Simulação de revisão — em um projeto real, essa etapa seria feita por um tech lead ou desenvolvedor senior.

✅ Projeto CAP criado corretamente com a entidade Material
✅ CSV com 10 registros criado na pasta db/data
✅ Função filtroMateriais implementada e testada
✅ Documentação dos passos realizada no docs/feature-DevCapTabelaMaterial.md
✅ Commits padronizados seguindo o padrão [PARTE 2] tipo: descrição

PR aprovado. Pode realizar o merge.
```

- Clique em **Comment**
- Clique em **Merge pull request**
- Clique em **Confirm merge** ✅
