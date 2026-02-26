<div align="center">

<img src="https://cdn-icons-png.flaticon.com/512/4494/4494748.png" alt="Git Logo" width="110" />

# 🌿 Curso Git — Repositório de Estudos

**Repositório de prática e aprendizado do sistema de controle de versões Git,**
**documentando os principais comandos, fluxos de trabalho e conceitos essenciais.**

<br>

![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white)
![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)
![Markdown](https://img.shields.io/badge/Markdown-000000?style=for-the-badge&logo=markdown&logoColor=white)
![Status](https://img.shields.io/badge/Status-Em%20Aprendizado-blue?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-blue?style=for-the-badge)

</div>

---

## 📚 Tabela de Conteúdos

> Navegue rapidamente pelas seções do repositório.

| # | Seção |
|:-:|:------|
| 1 | [📖 Sobre o Repositório](#-sobre-o-repositório) |
| 2 | [🎯 Conceitos Abordados](#-conceitos-abordados) |
| 3 | [📋 Comandos Essenciais](#-comandos-essenciais) |
| 4 | [🌿 Fluxo de Branches](#-fluxo-de-branches) |
| 5 | [🔄 Fluxos de Trabalho (Workflows)](#-fluxos-de-trabalho-workflows) |
| 6 | [🚀 Como Clonar e Usar](#-como-clonar-e-usar) |
| 7 | [🤝 Como Contribuir](#-como-contribuir) |
| 8 | [👨‍💻 Autor](#-autor) |
| 9 | [📄 Licença](#-licença) |

---

## 📖 Sobre o Repositório

> Este repositório foi criado durante os estudos de **Git e controle de versão**, com o objetivo de documentar, praticar e consolidar os principais conceitos e comandos da ferramenta mais utilizada no desenvolvimento de software moderno.

O Git é um **sistema de controle de versão distribuído** criado por Linus Torvalds em 2005. Ele permite rastrear alterações no código, colaborar em equipe e manter um histórico completo de todas as modificações de um projeto.

---

## 🎯 Conceitos Abordados

| Ícone | Conceito | Descrição |
|:-----:|:---------|:----------|
| 📦 | **Repositório** | Local onde o Git armazena o histórico completo do projeto (local e remoto). |
| 📸 | **Commit** | Snapshot do estado dos arquivos em um determinado momento. |
| 🌿 | **Branch** | Ramificação independente do projeto para desenvolvimento paralelo. |
| 🔀 | **Merge** | Integração de duas branches, unindo os históricos de commits. |
| 🔁 | **Rebase** | Reescrita do histórico de commits para uma linha linear. |
| 📤 | **Push / Pull** | Envio e recebimento de alterações entre repositório local e remoto. |
| 🏷️ | **Tags** | Marcadores imutáveis para versões específicas (ex: `v1.0.0`). |
| 🧺 | **Stash** | Armazenamento temporário de alterações não commitadas. |
| ↩️ | **Revert / Reset** | Desfazer commits de forma segura ou reescrever o histórico. |
| 🔍 | **Log / Diff** | Visualização do histórico e diferenças entre versões. |

---

## 📋 Comandos Essenciais

### ⚙️ Configuração Inicial

```bash
# Configurar identidade global
git config --global user.name "Victor H. J. Santiago"
git config --global user.email "seu@email.com"

# Verificar configurações
git config --list

# Definir editor padrão (VS Code)
git config --global core.editor "code --wait"
```

---

### 📁 Repositório

```bash
# Inicializar repositório local
git init

# Clonar repositório remoto
git clone https://github.com/VictorHJesusSantiago/curso_git.git

# Verificar estado dos arquivos
git status

# Ver histórico de commits
git log
git log --oneline --graph --all   # Visualização compacta com grafo
```

---

### 📸 Commits

```bash
# Adicionar arquivos à staging area
git add arquivo.txt           # Arquivo específico
git add .                     # Todos os arquivos alterados

# Criar commit
git commit -m "feat: descrição clara da mudança"

# Alterar o último commit (antes do push)
git commit --amend -m "mensagem corrigida"

# Desfazer último commit (mantendo as alterações)
git reset --soft HEAD~1

# Desfazer último commit (descartando as alterações)
git reset --hard HEAD~1
```

---

### 🌿 Branches

```bash
# Listar branches
git branch                    # Locais
git branch -a                 # Todas (local + remoto)

# Criar e trocar de branch
git checkout -b minha-feature
git switch -c minha-feature   # Forma moderna

# Trocar de branch
git checkout main
git switch main

# Deletar branch
git branch -d minha-feature   # Seguro (só deleta se já foi merged)
git branch -D minha-feature   # Forçado
```

---

### 🔀 Merge e Rebase

```bash
# Merge (mantém histórico completo)
git checkout main
git merge minha-feature

# Rebase (histórico linear)
git checkout minha-feature
git rebase main

# Abortar merge/rebase em conflito
git merge --abort
git rebase --abort
```

---

### 🌐 Remoto (Remote)

```bash
# Adicionar repositório remoto
git remote add origin https://github.com/VictorHJesusSantiago/curso_git.git

# Verificar remotos configurados
git remote -v

# Enviar commits para o remoto
git push origin main
git push -u origin main       # Define upstream padrão

# Receber atualizações do remoto
git pull origin main
git fetch origin              # Baixa sem fazer merge automático
```

---

### 🧺 Stash

```bash
# Guardar alterações temporariamente
git stash

# Listar stashes salvos
git stash list

# Recuperar o último stash
git stash pop

# Recuperar stash específico
git stash apply stash@{0}

# Deletar stash
git stash drop stash@{0}
```

---

### 🏷️ Tags

```bash
# Criar tag leve
git tag v1.0.0

# Criar tag anotada (recomendado)
git tag -a v1.0.0 -m "Versão 1.0.0 — Release inicial"

# Listar tags
git tag

# Enviar tags para o remoto
git push origin v1.0.0
git push origin --tags        # Envia todas as tags
```

---

## 🌿 Fluxo de Branches

> Modelo de branches utilizado para organizar o desenvolvimento.

```
main (produção — estável)
│
├── develop (integração — em desenvolvimento)
│   │
│   ├── feature/nova-funcionalidade
│   ├── feature/outra-funcionalidade
│   └── fix/correcao-de-bug
│
├── hotfix/correcao-critica (direto da main)
│
└── release/v1.0.0 (preparação de versão)
```

| Branch | Finalidade |
|:-------|:-----------|
| `main` | Código em produção — sempre estável. |
| `develop` | Branch de integração — recebe as features prontas. |
| `feature/*` | Novas funcionalidades — criadas a partir de `develop`. |
| `fix/*` | Correções de bugs não críticos. |
| `hotfix/*` | Correções urgentes diretamente na `main`. |
| `release/*` | Preparação de uma nova versão para produção. |

---

## 🔄 Fluxos de Trabalho (Workflows)

### 📌 Padrão de Mensagens de Commit (Conventional Commits)

```
<tipo>(<escopo>): <descrição curta>

[corpo opcional]

[rodapé opcional]
```

| Tipo | Quando Usar |
|:-----|:------------|
| `feat` | Nova funcionalidade adicionada. |
| `fix` | Correção de um bug. |
| `docs` | Alterações apenas na documentação. |
| `style` | Formatação, ponto e vírgula ausente, etc. (sem mudança de lógica). |
| `refactor` | Refatoração de código sem correção de bug ou nova feature. |
| `test` | Adição ou correção de testes. |
| `chore` | Tarefas de build, CI, dependências, etc. |

**Exemplos:**
```bash
git commit -m "feat: adiciona tela de login com validação"
git commit -m "fix: corrige cálculo de total no carrinho"
git commit -m "docs: atualiza README com instruções de instalação"
git commit -m "refactor: extrai lógica de autenticação para service"
```

---

## 🚀 Como Clonar e Usar

### 📋 Pré-requisitos

| Requisito | Detalhe |
|:----------|:--------|
| **Git** | Versão **2.x ou superior** instalada e configurada. |
| **Terminal** | Bash, Zsh, PowerShell ou qualquer terminal de sua preferência. |

---

### 🔧 Passo a Passo

**1. Clone o repositório:**

```bash
git clone https://github.com/VictorHJesusSantiago/curso_git.git
cd curso_git
```

**2. Verifique o histórico de commits para acompanhar o aprendizado:**

```bash
git log --oneline --graph --all
```

**3. Explore as branches criadas durante o curso:**

```bash
git branch -a
```

---

## 🤝 Como Contribuir

> Contribuições são muito bem-vindas! Siga as etapas abaixo para colaborar de forma organizada.

| Passo | Ação | Comando |
|:-----:|:-----|:--------|
| 1️⃣ | **Fork** | Crie um fork do repositório para a sua conta. | — |
| 2️⃣ | **Branch** | Crie sua feature branch a partir da `main`. | `git checkout -b feature/NovaFeature` |
| 3️⃣ | **Commit** | Salve as alterações com mensagem clara e semântica. | `git commit -m 'feat: Adiciona NovaFeature'` |
| 4️⃣ | **Push** | Envie a branch para o repositório remoto. | `git push origin feature/NovaFeature` |
| 5️⃣ | **Pull Request** | Abra um PR detalhando as mudanças realizadas. | — |

<div align="center">

<br>

**Se este repositório foi útil para os seus estudos, deixe uma estrela ⭐️!**

</div>

---

## 👨‍💻 Autor

<div align="center">

<br>

**Victor H. J. Santiago**

<br>

[![GitHub](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/VictorHJesusSantiago)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/victor-henrique-de-jesus-santiago/)

</div>

---

## 📄 Licença

<div align="center">

Este projeto está distribuído sob a **Licença MIT**.
Consulte o arquivo [`LICENSE`](./LICENSE) no repositório para mais informações.

![License](https://img.shields.io/badge/License-MIT-blue?style=for-the-badge)

</div>

---

<div align="center">

*Feito com 🌿 e Git por **Victor H. J. Santiago***

</div>
