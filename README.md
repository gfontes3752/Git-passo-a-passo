# 📌 Git — Passo a Passo

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

> ⚠️ Se a branch já existe no GitHub e você está em uma máquina nova, use:
> ```powershell
> git checkout feat/nome-da-feature
> git push --set-upstream origin feat/nome-da-feature
> ```

---

## 6. Fluxo diário de trabalho

```powershell
# Sempre verifique em qual branch está
git branch

# Se estiver na branch errada, mude antes de editar qualquer arquivo
git checkout nome-da-branch-correta

# Edite os arquivos no VS Code, depois:
git add .
git commit -m "feat: descrição do que fez"
git push
```

> ⚠️ **Atenção:** sempre confirme a branch antes de começar a editar.
> Commitar na branch errada pode causar problemas no histórico do projeto.

---

## 7. Merge via GitHub (Pull Request)

- Acesse o repositório no GitHub
- Clique em **Compare & pull request**
- Faça o merge de `feat/` → `develop` → `main`
- O Railway detecta o push na `main` e faz deploy automático

---

## 8. Descobrir onde você parou

Use estes comandos para saber qual branch foi mexida por último e se já foi mergeada.

```powershell
# Ver todas as branches ordenadas pela data do último commit (mais recente primeiro)
git branch -a --sort=-committerdate

# Ver apenas branches locais ordenadas por data
git branch --sort=-committerdate

# Ver branches já mergeadas na develop
git branch --merged develop

# Ver branches já mergeadas na main
git branch --merged main

# Ver últimos commits da branch atual
git log --oneline -5
```

> 💡 **Dica:** Se a branch aparece em `git branch --merged main`, ela já foi mergeada.
> Se não aparece, ainda está pendente de PR.

---

## 9. Comandos úteis

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

# Baixar atualizações sem fazer merge
git fetch origin

# Ver diferença entre branch local e remota
git diff main origin/main
```

---

## 10. Solução de problemas comuns

### Branch sem upstream (erro ao fazer push)
```powershell
git push --set-upstream origin feat/nome-da-feature
```

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

## 11. Atualizando o projeto em notebooks diferentes

Quando trabalhar em uma máquina diferente, sempre sincronize o projeto antes de começar a editar.

### Se o projeto ainda não existe na máquina

```powershell
cd C:\sua-pasta
git clone https://github.com/seu-usuario/nome-do-repo.git
cd nome-do-repo
```

### Se o projeto já existe na máquina

```powershell
# Acesse a pasta do projeto
cd C:\sua-pasta\nome-do-repo

# Veja qual branch foi mexida por último
git branch --sort=-committerdate

# Troque para a branch feat/ que deseja atualizar
git checkout feat/nome-da-feature

# Baixe as últimas atualizações
git pull origin feat/nome-da-feature
```

### Confirme que está atualizado

```powershell
git log --oneline -5
```

> ⚠️ **Atenção:** sempre execute o `git pull` antes de começar a editar
> em uma máquina diferente. Isso evita conflitos com o trabalho feito em outra máquina.

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
  - `wip:` trabalho em progresso (não finalizado)

---

## 🔀 Fluxo das branches

```
feat/nome-da-feature
        ↓ PR
    develop
        ↓ PR
      main  ←  Railway faz deploy automático aqui
```

---

*Criado por gfontes3752*
