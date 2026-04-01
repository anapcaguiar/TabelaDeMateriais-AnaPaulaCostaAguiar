# Parte 1 — Git e Desenvolvimento de Repositório

---

## 7. Criar Branch Development

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

## 8. Criar arquivo docs/development.md

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

---

## 9. Compare, Pull Request & Merge — Development → main

### Step — No GitHub, clique em "Compare & pull request"

- **base:** `main`
- **compare:** `Development`

### Step — Adicione título e descrição

**Título:**
```
[PARTE 1] chore: create Development branch and documentation
```

**Descrição:**
```
### GitHub
- Criação da branch Development a partir da main

### SAP BAS
- git pull e git checkout Development
- Criação do arquivo docs/development.md
- Documentação dos passos realizados
```

- Clique em **Create pull request**

### Step — Commit e Push
```bash
git add .
git commit -m "[PARTE 1] docs: update docs/development with PR and merge steps"
git push
```

### Step — Revisão e Merge

- Adicione o comentário de revisão:
```
## Revisão - Ana Paula Costa Aguiar

> ⚠️ Simulação de revisão — em um projeto real, essa etapa seria feita por um tech lead ou desenvolvedor senior.

✅ Branch Development criada corretamente a partir da main
✅ Documentação dos passos realizada no docs/development.md
✅ Commits padronizados seguindo o padrão [PARTE 1] tipo: descrição

PR aprovado. Pode realizar o merge.
```

- Clique em **Comment**
- Clique em **Merge pull request**
- Clique em **Confirm merge** ✅