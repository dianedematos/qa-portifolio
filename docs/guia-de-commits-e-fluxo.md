# 🧭 Guia de Commits & Fluxo de Trabalho (Git)

Este guia define **como escrever mensagens de commit**, **como versionar no dia a dia** e **como abrir PRs**.  
Objetivo: manter histórico **claro**, facilitar **code review** e **automação** (changelogs, releases).

---

## 🧩 Padrão: Conventional Commits

**Formato básico**

```
<tipo>(<escopo opcional>): <resumo no imperativo e minúsculas>

<corpo opcional explicando o porquê/como>

<footer opcional com referências, breaking changes, etc.>
```

**Tipos comuns**

- `feat` → nova funcionalidade  
- `fix` → correção de bug  
- `docs` → documentação (README, .md, comentários)  
- `test` → testes (unit, e2e, mocks)  
- `refactor` → refatoração sem mudar comportamento  
- `perf` → melhorias de performance  
- `style` → formatação/estilo (lint, espaços), sem código de lógica  
- `build` → mudanças em build, dependências  
- `ci` → pipelines, GitHub Actions, Jenkins  
- `chore` → tarefas diversas (scripts, limpeza)  
- `revert` → reverte um commit anterior

**Exemplos bons**

```
feat(login): adiciona validação de token no fluxo de autenticação

Permite bloquear sessão expirada e exibir mensagem ao usuário.
Refs #34
```

```
fix(api): corrige status 500 ao atualizar perfil quando telefone é nulo

Ajusta validação de payload e retorna 400 com mensagem clara.
Closes #89
```

```
docs(readme): adiciona seção de execução dos testes e2e
```

```
refactor(cypress): extrai page objects para camada de componentes
```

```
feat!: altera formato de resposta do endpoint /orders

BREAKING CHANGE: o campo `total` agora vem como string formatada.
```

---

## ✅ Checklist do Commit

- [ ] Mensagem segue o padrão `tipo(escopo): resumo`  
- [ ] Explicou **o porquê** no corpo quando necessário  
- [ ] Testes e/ou docs atualizados (se aplicável)  
- [ ] Rodou localmente (lint/testes) antes de commitar/push  

---

## 🔄 Fluxo de Trabalho Diário (Git)

### 1) Atualize sua cópia
```bash
git pull origin main
```

### 2) Crie uma branch
```bash
git checkout -b feat/login-validacao-token
# ou
git checkout -b fix/perfil-telefone-nulo
```

### 3) Trabalhe e versione
```bash
git status
git add .
git commit -m "feat(login): adiciona validação de token no fluxo de login"
```

### 4) Envie a branch
```bash
git push -u origin feat/login-validacao-token
```

### 5) Abra um Pull Request (PR)
- Título do PR ≈ seu commit principal.  
- Descreva **contexto, solução, impacto** e **como testar**.  
- Marque **issue** relacionada (`Closes #ID`).  

### 6) Após aprovação
- Faça **merge** (squash ou merge comum).  
- Delete a branch remota/local se não for mais necessária.  

---

## 🌿 Convenção de Branches (sugestão)

```
feat/<area>-<descricao-curta>
fix/<area>-<descricao-curta>
docs/<topico>
chore/<assunto>
```

**Exemplos**
- `feat/cadastro-validacao-email`  
- `fix/login-redirect-apos-expirar`  
- `docs/guia-contribuicao`  

---

## 📦 Mensagens de Merge (PR)

Prefira **squash merge** (consolida commits pequenos) e defina o título no padrão:

```
feat(login): adiciona validação de token
fix(api): corrige erro 500 no /profile
docs(readme): inclui seção de execução dos testes
```

---

## 🧰 Dicas úteis

**Ver commits prontos para enviar**
```bash
git log --oneline --decorate --graph --all
```

**Ver o que mudou antes do commit**
```bash
git diff
```

**Amendar o último commit (corrigir mensagem/arquivo)**
```bash
git add arquivo-que-faltou
git commit --amend
```

**Reverter um commit**
```bash
git revert <hash>
```

---

## 📝 Mini–Cheat Sheet (4 passos)

```bash
git status
git add .
git commit -m "docs: atualiza guia de commits"
git push
```

---

### 📎 Badge para o README (opcional)
Adicione no seu `README.md`:
```md
<img src="https://img.shields.io/badge/Conventional%20Commits-1.0.0-yellow.svg" />
```
