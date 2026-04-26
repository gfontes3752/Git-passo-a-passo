# 📌 Git - Passo a Passo

Guia de referência rápida para criação e gerenciamento de repositórios Git com GitHub.

---

## 1. Criar o repositório no GitHub

- Acesse [github.com/new](https://github.com/new)
- Preencha o nome do repositório
- Deixe **sem** README, `.gitignore` e license
- Clique em **Create repository**

---

## 2. Inicializar o projeto local

```powershell
git init
git add .
git commit -m "chore: initial commit"
```

---

## 3. Conectar ao GitHub e subir a main

```powershell
git remote add origin https://github.com/seu-usuario/nome-do-repo.git
git branch -M main
git push -u origin main
```

---

## 4. Criar a branch develop

```powershell
git checkout -b develop
git push -u origin develop
```

---

## 5. Criar a branch feat/

```powershell
git checkout -b feat/nome-da-feature
git push -u origin feat/nome-da-feature
```

---

## 6. Fluxo diário de trabalho

```powershell
# Sempre verifique em qual branch está
git branch

# Edite os arquivos no VS Code, depois:
git add .
git commit -m "feat: descrição do que fez"
git push
```

---

## 7. Merge via GitHub (Pull Request)

- Acesse o repositório no GitHub
- Clique em **Compare & pull request**
- Faça o merge de `feat/` → `develop` → `main`

---

## 8. Comandos úteis

```powershell
# Ver status dos arquivos
git status

# Ver histórico de commits
git log --oneline -5

# Trocar de branch
git checkout nome-da-branch

# Ver remotes configurados
git remote -v

# Atualizar o remote se errar o nome
git remote set-url origin https://github.com/seu-usuario/nome-correto.git
```

---

## 9. Solução de problemas comuns

### Remote com nome errado
```powershell
git remote set-url origin https://github.com/seu-usuario/nome-correto.git
```

### Erro: remote contains work that you do not have locally
```powershell
git pull origin main --allow-unrelated-histories
git push -u origin main
```

### Erro: non-fast-forward (último recurso, apenas projetos pessoais)
```powershell
git push -u origin main --force
```

### Pasta já existe mas sem .git
```powershell
git init
git remote add origin https://github.com/seu-usuario/nome-do-repo.git
Remove-Item README.md
git pull origin main
```

### Commit foi para branch master em vez de main
```powershell
git branch -M main
git push -u origin main
```

---

## ⚠️ Boas práticas

- Sempre commitar na `feat/` e fazer PR para `develop`
- Nunca use `--force` em projetos de time
- Salve tudo no VS Code antes do `git add .`
- Use mensagens de commit descritivas:
  - `chore:` configurações e setup
  - `feat:` nova funcionalidade
  - `fix:` correção de bug
  - `docs:` documentação

---

## 🔀 Fluxo das branches

feat/nome-da-feature
↓ PR
develop
↓ PR
main

---

*Criado por gfontes3752*