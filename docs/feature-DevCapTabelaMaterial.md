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