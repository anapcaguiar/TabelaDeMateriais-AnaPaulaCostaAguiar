# Parte 1 — Git e Desenvolvimento de Repositório

## Objetivo

Trabalhar com Git, criando um repositório, branches, commits e pull requests no ambiente SAP Business Application Studio (BAS).

---

## 1. Criar Repositório no GitHub

**Nome do repositório:** `TabelaDeMateriais-AnaPaulaCostaAguiar`

### Passos

1. Acesse [github.com](https://github.com) e clique em **New repository**.
2. Dê o nome ao repositório: `TabelaDeMateriais-AnaPaulaCostaAguiar`.
3. Defina como **Public**.
4. Habilite **Add a README file**.
5. Clique em **Create repository**.

> 💡 **Boa prática:** O `.gitignore` não precisa ser configurado aqui — o BTP já gera um automaticamente. Ele ignora a pasta `node_modules`, que é muito pesada.

---

## 2. Acessar e Iniciar o SAP BAS

1. Acesse o [SAP BTP Trial](https://cockpit.hanatrial.ondemand.com/trial/#/home/trial) e faça login.
2. Vá em **Services > Instances and Subscriptions**.
3. Clique no link do **SAP Business Application Studio**.
4. Localize o Dev Space `BTP_TCS`.
5. Se o status estiver `STOPPED`, clique em ▶ para iniciar.
6. Aguarde o status mudar para `RUNNING`.
7. Clique no nome do Dev Space para abrir o ambiente.

> 💡 **Boa prática:** O Dev Space para automaticamente após 30 dias sem uso no trial.

---

## 3. Clonar o Repositório no BAS

### Step — Clonar

```bash
git clone https://github.com/anapcaguiar/TabelaDeMateriais-AnaPaulaCostaAguiar.git
```

**Resultado no terminal:**
```bash
user: projects $ git clone https://github.com/anapcaguiar/TabelaDeMateriais-AnaPaulaCostaAguiar.git
Cloning into 'TabelaDeMateriais-AnaPaulaCostaAguiar'...
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
Receiving objects: 100% (3/3), done.
```

### Step — Abrir repositório no terminal

```bash
cd TabelaDeMateriais-AnaPaulaCostaAguiar
```

> 💡 **Boa prática:** Prefira sempre salvar em `/projects` para visualizar todos os projetos ao mesmo tempo no Explorer.

### Step — Commit

```bash
git add .
git commit -m "[PARTE 1] chore: Clone repository to BAS"
```

**Resultado no terminal:**
```bash
user: TabelaDeMateriais-AnaPaulaCostaAguiar $ git add .
user: TabelaDeMateriais-AnaPaulaCostaAguiar $ git commit -m "[PARTE 1] chore: Clone repository to BAS"
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
```

> 💡 O `nothing to commit` é esperado! O clone já trouxe tudo sincronizado do GitHub.

### Step — Push

```bash
git push
```

**Resultado no terminal:**
```bash
user: TabelaDeMateriais-AnaPaulaCostaAguiar $ git push
Everything up-to-date
```

> 💡 O `Everything up-to-date` confirma que o repositório local e o GitHub estão sincronizados.

---

## 4. Atualizar README

### Step — Editar o README.md

Abra o `README.md` no Explorer do BAS e adicione o conteúdo desejado.

### Step — Commit e Push

```bash
git add .
git commit -m "[PARTE 1] docs: update README with instructions"
git push origin main
```

---

## 5. Criar Pasta docs/

### Step — Criar pasta e arquivo de documentação

```bash
mkdir docs
touch docs/main.md
```

> 💡 **Boa prática:** O GitHub não aceita pasta vazia — por isso criamos o `main.md` dentro da pasta ao mesmo tempo.

### Step — Commit e Push

```bash
git add .
git commit -m "[PARTE 1] docs: create documentation folder and file"
git push origin main
```

---

## 6. Atualizar docs/main.md

### Step — Editar o main.md

Abra o `docs/main.md` no Explorer do BAS e adicione o conteúdo desejado.

### Step — Commit e Push

```bash
git add .
git commit -m "[PARTE 1] docs: update docs/main with instructions"
git push origin main
```