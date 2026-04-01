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

---

# Parte 3 — Front-end – Exibição e Manipulação de Dados

## Objetivo

Criar uma tela no front-end que exiba a tabela de materiais e permita interações de filtro e criação de novos registros, utilizando a Model para manipulação dos dados.

---

## 1. Criar o projeto Fiori

### Step — Point and Click no BAS

1. Clique em **File → New Project from Template**
2. Selecione **SAP Fiori generator**
3. Selecione **Basic**
4. Em **Data Source and Service Selection** configure:
   - **Data Source:** `Use a Local CAP Project`
   - **CAP Project:** `CAP_TabelaDeMateriais`
   - **OData Service:** `MateriaisService (Node.js)`
5. Em **Entity Selection** coloque:
   - **View Name:** `List`
6. Em **Project Attributes** coloque:
   - **Module Name:** `tabelademateriaismname`
   - **Application Title:** `Tabela de Materiais`
   - **Description:** `Tabela de Materiais ANA PAULA COSTA AGUIAR`
7. Clique em **Finish**

### Step — Commit

```bash
git add .
git commit -m "[PARTE 3] feat: create Fiori project tabelademateriaismname"
```

### Step — Rodar projeto

```bash
cd CAP_TabelaDeMateriais
cds watch
```

**Resultado no terminal:**
```bash
[cds] - serving MateriaisService { at: [ '/odata/v4/materiais' ] }
[cds] - server listening on { url: 'http://localhost:4004' }
[cds] - server v9.8.4 launched in 1923 ms
```

> 💡 Abra o browser em `http://localhost:4004` e clique em `/tabelademateriaismname/index.html` em **Web Applications**.

---

## 2. Editar o List.view.xml

### Step — Localizar o arquivo

```
CAP_TabelaDeMateriais → app → tabelademateriaismname → webapp → view → List.view.xml
```

### Step — Substituir o conteúdo pelo código abaixo

```xml
<mvc:View controllerName="tabelademateriaismname.controller.List"
    xmlns:mvc="sap.ui.core.mvc"
    xmlns="sap.m">
    <Page title="Tabela de Materiais">
        <content>
            <VBox>
                <HBox>
                    <Input id="inputQuantidade" placeholder="Digite a quantidade" />
                    <Button text="Filtrar" press="onFiltrar" />
                </HBox>
                <Table items="{tableMaterial>/tableMaterial}">
                    <columns>
                        <Column><Text text="ID" /></Column>
                        <Column><Text text="NumMat" /></Column>
                        <Column><Text text="Nome" /></Column>
                        <Column><Text text="Descr" /></Column>
                    </columns>
                    <items>
                        <ColumnListItem>
                            <cells>
                                <Text text="{tableMaterial>ID}" />
                                <Text text="{tableMaterial>NumMat}" />
                                <Text text="{tableMaterial>Nome}" />
                                <Text text="{tableMaterial>Descr}" />
                            </cells>
                        </ColumnListItem>
                    </items>
                </Table>
            </VBox>
        </content>
    </Page>
</mvc:View>
```

Salve com `Ctrl + S`.

### Step — Commit

```bash
git add .
git commit -m "[PARTE 3] feat: update List.view.xml with SAP Table, Input and Filter button"
```

---

## 3. Editar o List.controller.js

### Step — Localizar o arquivo

```
CAP_TabelaDeMateriais → app → tabelademateriaismname → webapp → controller → List.controller.js
```

### Step — Substituir o conteúdo pelo código abaixo

```js
sap.ui.define([
    "sap/ui/core/mvc/Controller",
    "sap/m/MessageToast"
], (Controller, MessageToast) => {
    "use strict";
    return Controller.extend("tabelademateriaismname.controller.List", {
        onInit: function () {
            this.oRouter = sap.ui.core.UIComponent.getRouterFor(this);
            this.oRouter
                .getTarget("TargetList")
                .attachDisplay(this.handleRouteMatched, this);
        },
        handleRouteMatched: function () {
            this.createModel();
            this.carregarDados();
        },
        createModel: function () {
            this.getView().setModel(
                new sap.ui.model.json.JSONModel({
                    tableMaterial: []
                }),
                "tableMaterial"
            );
        },
        carregarDados: async function () {
            const response = await fetch("/odata/v4/materiais/Material");
            const data = await response.json();
            this.getView().getModel("tableMaterial").setProperty("/tableMaterial", data.value);
        },
        onFiltrar: async function () {
            const quantidade = this.getView().byId("inputQuantidade").getValue();
            if (!quantidade) {
                MessageToast.show("Digite uma quantidade!");
                return;
            }
            const response = await fetch(`/odata/v4/materiais/filtroMateriais(quantidade=${quantidade})`);
            const data = await response.json();
            this.getView().getModel("tableMaterial").setProperty("/tableMaterial", data.value);
        }
    });
});
```

Salve com `Ctrl + S`.

### Step — Commit

```bash
git add .
git commit -m "[PARTE 3] feat: update List.controller.js with Model and filtroMateriais"
```

---

## 4. Testar a aplicação

### Step — Rodar projeto

```bash
cd CAP_TabelaDeMateriais
cds watch
```

> 💡 Abra o browser em `http://localhost:4004` e clique em `/tabelademateriaismname/index.html` em **Web Applications**.

**Verifique:**
```
✅ Tabela com os 10 materiais exibida
✅ Campo Input para quantidade
✅ Botão Filtrar
✅ Colunas ID, NumMat, Nome, Descr
```

> 💡 Teste o filtro digitando `3` no campo e clicando em **Filtrar** — deve retornar apenas 3 materiais!

---

## 5. [DESAFIO] Editar o List.view.xml

### Step — Localizar o arquivo

```
CAP_TabelaDeMateriais → app → tabelademateriaismname → webapp → view → List.view.xml
```

### Step — Substituir o conteúdo pelo código abaixo

```xml
<mvc:View controllerName="tabelademateriaismname.controller.List"
    xmlns:core="sap.ui.core"
    xmlns:mvc="sap.ui.core.mvc"
    xmlns="sap.m">
    <Page id="page" title="{i18n>title}" class="sapUiContentPadding">
        <Input id="inputQuantidade" placeholder="Digite a quantidade" width="200px"/>
        <Button text="Filtrar" press="onFiltrar"/>
        <Table id="tabelaMateriais" items="{tableMaterial>/tableMaterial}">
            <headerToolbar>
                <Toolbar>
                    <Title text="Materiais"/>
                    <ToolbarSpacer/>
                    <Button text="Criar" press="onAbrirCriar"/>
                </Toolbar>
            </headerToolbar>
            <columns>
                <Column><Text text="ID"/></Column>
                <Column><Text text="NumMat"/></Column>
                <Column><Text text="Nome"/></Column>
                <Column><Text text="Descr"/></Column>
            </columns>
            <items>
                <ColumnListItem>
                    <cells>
                        <Text text="{tableMaterial>ID}"/>
                        <Text text="{tableMaterial>NumMat}"/>
                        <Text text="{tableMaterial>Nome}"/>
                        <Text text="{tableMaterial>Descr}"/>
                    </cells>
                </ColumnListItem>
            </items>
        </Table>
        <Dialog id="dialogCriar" title="Criar Material">
            <content>
                <Input id="inputNumMat" placeholder="NumMat" width="100%"/>
                <Input id="inputNome" placeholder="Nome" width="100%"/>
                <Input id="inputDescr" placeholder="Descr" width="100%"/>
            </content>
            <beginButton>
                <Button text="Confirmar" press="onConfirmarCriar"/>
            </beginButton>
            <endButton>
                <Button text="Cancelar" press="onFecharCriar"/>
            </endButton>
        </Dialog>
    </Page>
</mvc:View>
```

Salve com `Ctrl + S`.

### Step — Commit

```bash
git add .
git commit -m "[PARTE 3] feat: update List.view.xml with create button and dialog popup"
```

---

## 6. [DESAFIO] Adicionar action adicionarMaterial no service.cds

### Step — Localizar o arquivo

```
CAP_TabelaDeMateriais → srv → service.cds
```

### Step — Substituir o conteúdo pelo código abaixo

```cds
using materiais from '../db/schema';
service MateriaisService {
    entity Material as projection on materiais.Material;
    function filtroMateriais(quantidade : Integer) returns array of Material;
    action adicionarMaterial(NumMat: Integer, Nome: String, Descr: String) returns { sucesso: Boolean; mensagem: String; };
}
```

Salve com `Ctrl + S`.

### Step — Commit

```bash
git add .
git commit -m "[PARTE 3] feat: add adicionarMaterial action in service.cds"
```

---

## 7. [DESAFIO] Atualizar o service.js com a action adicionarMaterial

### Step — Localizar o arquivo

```
CAP_TabelaDeMateriais → srv → service.js
```

### Step — Substituir o conteúdo pelo código abaixo

```js
const cds = require('@sap/cds')
module.exports = cds.service.impl(async function () {
    this.on('filtroMateriais', async (req) => {
        const { quantidade } = req.data;
        const materiais = await SELECT.from('MateriaisService.Material');
        return materiais.slice(0, quantidade);
    })

    this.on('adicionarMaterial', async (req) => {
        const { NumMat, Nome, Descr } = req.data;
        const existe = await SELECT.one.from('MateriaisService.Material').where({ NumMat });
        if (existe) {
            return { sucesso: false, mensagem: `Material com NumMat ${NumMat} já cadastrado!` };
        }
        const ultimo = await SELECT.one.from('MateriaisService.Material').orderBy({ ID: 'desc' });
        const novoID = ultimo ? ultimo.ID + 1 : 1;
        await INSERT.into('MateriaisService.Material').entries({ ID: novoID, NumMat, Nome, Descr });
        return { sucesso: true, mensagem: `Material ${Nome} adicionado com sucesso!` };
    })
})
```

Salve com `Ctrl + S`.

### Step — Commit

```bash
git add .
git commit -m "[PARTE 3] feat: add adicionarMaterial action in service.js"
```

---

## 8. [DESAFIO] Atualizar o List.controller.js com as funções do pop-up

### Step — Localizar o arquivo

```
CAP_TabelaDeMateriais → app → tabelademateriaismname → webapp → controller → List.controller.js
```

### Step — Substituir o conteúdo pelo código abaixo

```js
sap.ui.define([
    "sap/ui/core/mvc/Controller",
    "sap/m/MessageToast",
    "sap/m/MessageBox"
], (Controller, MessageToast, MessageBox) => {
    "use strict";
    return Controller.extend("tabelademateriaismname.controller.List", {
        onInit: function () {
            this.oRouter = sap.ui.core.UIComponent.getRouterFor(this);
            this.oRouter
                .getTarget("TargetList")
                .attachDisplay(this.handleRouteMatched, this);
        },
        handleRouteMatched: function () {
            this.createModel();
            this.carregarDados();
        },
        createModel: function () {
            this.getView().setModel(
                new sap.ui.model.json.JSONModel({
                    tableMaterial: []
                }),
                "tableMaterial"
            );
        },
        carregarDados: async function () {
            const response = await fetch("/odata/v4/materiais/Material");
            const data = await response.json();
            this.getView().getModel("tableMaterial").setProperty("/tableMaterial", data.value);
        },
        onFiltrar: async function () {
            const quantidade = this.getView().byId("inputQuantidade").getValue();
            if (!quantidade) {
                MessageToast.show("Digite uma quantidade!");
                return;
            }
            const response = await fetch(`/odata/v4/materiais/filtroMateriais(quantidade=${quantidade})`);
            const data = await response.json();
            this.getView().getModel("tableMaterial").setProperty("/tableMaterial", data.value);
        },
        onAbrirCriar: function () {
            this.byId("dialogCriar").open();
        },
        onFecharCriar: function () {
            this.byId("dialogCriar").close();
        },
        onConfirmarCriar: async function () {
            const NumMat = this.byId("inputNumMat").getValue();
            const Nome = this.byId("inputNome").getValue();
            const Descr = this.byId("inputDescr").getValue();
            if (!NumMat || !Nome || !Descr) {
                MessageBox.error("Todos os campos são obrigatórios!");
                return;
            }
            const response = await fetch("/odata/v4/materiais/adicionarMaterial", {
                method: "POST",
                headers: { "Content-Type": "application/json" },
                body: JSON.stringify({ ID: 0, NumMat: parseInt(NumMat), Nome, Descr })
            });
            const data = await response.json();
            if (data.sucesso) {
                MessageBox.success(data.mensagem);
                this.byId("inputNumMat").setValue("");
                this.byId("inputNome").setValue("");
                this.byId("inputDescr").setValue("");
                this.byId("dialogCriar").close();
                this.carregarDados();
            } else {
                MessageBox.error(data.mensagem);
            }
        }
    });
});
```

Salve com `Ctrl + S`.

### Step — Commit

```bash
git add .
git commit -m "[PARTE 3] feat: update List.controller.js with create button, popup and field validation"
```

---

## 9. Testar o Desafio

### Step — Rodar projeto

```bash
cd CAP_TabelaDeMateriais
cds watch
```

**Teste criando os materiais abaixo:**

| NumMat | Nome | Descr |
|---|---|---|
| 3011 | Perfurador | Perfurador de papel 2 furos |
| 3012 | Apontador | Apontador escolar simples |
| 3013 | Fita Adesiva | Fita adesiva transparente 45mm |
| 3014 | Caderno | Caderno universitário 200 folhas |

**Verifique:**
```
✅ Botão Criar aparece no cabeçalho da tabela
✅ Pop-up abre ao clicar em Criar
✅ Validação de campos obrigatórios funcionando
✅ Material adicionado com sucesso na tabela
✅ Campos limpos após criar
✅ Mensagem de erro ao tentar cadastrar NumMat duplicado
```

---

## 10. Commit e Push final

Pare o servidor com `Ctrl + C` e rode:

```bash
cd ..
git add .
git commit -m "[PARTE 3] docs: update docs/parte3-frontend with all instructions"
git push origin feature/DevCapTabelaMaterial
```

---

## 11. Pull Request & Merge — feature/DevCapTabelaMaterial → Development

### Step — No GitHub, clique em "Compare & pull request"

- **base:** `Development`
- **compare:** `feature/DevCapTabelaMaterial`

### Step — Adicione título e descrição

**Título:**
```
[PARTE 3] feat: front-end Fiori com tabela Material, filtro e desafio criar material
```

**Descrição:**
```
### Front-end Fiori
- Criação do projeto Fiori tabelademateriaismname via Template Wizard
- Configuração do List.view.xml com SAP Table, Input e botão Filtrar
- Configuração do List.controller.js com Model e carregamento de dados

### Funcionalidades
- Tabela exibindo os 10 materiais
- Dados carregados via Model na inicialização da tela
- Botão Filtrar integrado com a função filtroMateriais
- Campo Input para informar a quantidade do filtro

### Desafio
- Botão Criar no cabeçalho da tabela
- Pop-up com inputs NumMat, Nome e Descr
- Validação de campos obrigatórios
- Action adicionarMaterial implementada no backend
- Validação de NumMat duplicado
- Limpeza dos campos após criar
- Mensagem de sucesso ou erro via MessageBox
```

- Clique em **Create pull request**

### Step — Revisão e Merge

```
## Revisão - Ana Paula Costa Aguiar

> ⚠️ Simulação de revisão — em um projeto real, essa etapa seria feita por um tech lead ou desenvolvedor senior.

✅ Projeto Fiori tabelademateriaismname criado via Template Wizard
✅ SAP Table implementada corretamente (não foi usada List conforme orientado)
✅ Dados carregados via Model na inicialização da tela
✅ Entidade tableMaterial definida na Model
✅ Botão Filtrar integrado com a função filtroMateriais
✅ Campo Input para informar a quantidade do filtro
✅ Tabela atualizada automaticamente após o filtro
✅ [DESAFIO] Botão Criar no cabeçalho da tabela implementado
✅ [DESAFIO] Pop-up com validação de campos obrigatórios
✅ [DESAFIO] Action adicionarMaterial implementada no backend
✅ [DESAFIO] Validação de NumMat duplicado funcionando
✅ [DESAFIO] Campos limpos após criação bem-sucedida
✅ Commits padronizados seguindo o padrão [PARTE 3] tipo: descrição

PR aprovado. Pode realizar o merge.
```

- Clique em **Comment**
- Clique em **Merge pull request**
- Clique em **Confirm merge** ✅

---
