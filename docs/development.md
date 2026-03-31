# Parte 1 — Git e Desenvolvimento de Repositório

---

## 6. Criar Branch Development

> 💡 **Boa prática:** Crie sempre o branch no GitHub primeiro e depois puxe com `git pull`. É mais fácil do que criar localmente e publicar depois.

### Step — No GitHub

1. No repositório, clique em **main** > **View all branches** > **New branch**.
2. Crie a branch `Development` a partir de `main`.

### Step — No BAS

```bash
git pull
git checkout Development
```

**Resultado no terminal:**
```bash
user: TabelaDeMateriais-AnaPaulaCostaAguiar $ git pull
From https://github.com/anapcaguiar/TabelaDeMateriais-AnaPaulaCostaAguiar
 * [new branch]      Development -> origin/Development
Already up to date.
user: TabelaDeMateriais-AnaPaulaCostaAguiar $ git checkout Development
branch 'Development' set up to track 'origin/Development'.
Switched to a new branch 'Development'
```

### Step — Commit

```bash
git add .
git commit -m "[PARTE 1] chore: pull Development branch from GitHub"
```

---

## 7. Criar arquivo docs/development.md

### Step — Criar o arquivo

```bash
touch docs/development.md
```

### Step — Editar o development.md

Abra o `docs/development.md` no Explorer do BAS e adicione o conteúdo desejado.

### Step — Commit e Push

```bash
git add .
git commit -m "[PARTE 1] docs: create and update docs/development with instructions"
git push
```