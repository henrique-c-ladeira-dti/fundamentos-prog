# Controle de Versão com Git

Este documento apresenta os conceitos fundamentais do Git, o sistema de controle de versão mais utilizado no desenvolvimento de software, explicando como funciona e como usar na prática.

---

## Parte I: O que é Controle de Versão

### 1.1 Por que Precisamos de Controle de Versão?

Imagine que você está escrevendo um texto importante e quer manter diferentes versões:

```
texto_v1.doc
texto_v2.doc
texto_v2_corrigido.doc
texto_v2_corrigido_final.doc
texto_v2_corrigido_final_agora_vai.doc
```

**Problemas desta abordagem:**

- Difícil saber qual é a versão mais recente
- Impossível ver exatamente o que mudou entre versões
- Colaboração com outras pessoas se torna caótica
- Perda de espaço em disco
- Risco de sobrescrever trabalho importante

### 1.2 O que é um Sistema de Controle de Versão

Um **sistema de controle de versão** é uma ferramenta que:

- **Registra mudanças** em arquivos ao longo do tempo
- **Permite reverter** para versões anteriores
- **Facilita colaboração** entre múltiplas pessoas
- **Mantém histórico completo** de todas as alterações
- **Identifica conflitos** quando pessoas editam o mesmo arquivo

---

## Parte II: Git - Conceitos Fundamentais

### 2.1 Como o Git Funciona

#### **Repositório (Repository)**

- "Pasta especial" que contém seu projeto e todo o histórico
- Pasta `.git` escondida guarda todas as informações de versões

#### **Commit**

- "Fotografia" do estado do projeto em um momento específico
- Cada commit tem um identificador único (hash)
- Contém: autor, data, mensagem e mudanças feitas

#### **Branch (Ramificação)**

- Linha independente de desenvolvimento
- Permite trabalhar em funcionalidades sem afetar o código principal
- Branch padrão geralmente se chama `main` ou `master`

#### **Working Directory, Staging Area e Repository**

```
Working Directory  →  Staging Area  →  Repository
(seus arquivos)       (preparação)     (histórico)
       |                    |               |
   git add            git commit        git log
```

### 2.2 Estados dos Arquivos no Git

| Estado        | Descrição                          | Localização       |
| ------------- | ---------------------------------- | ----------------- |
| **Untracked** | Arquivo novo, Git não conhece      | Working Directory |
| **Modified**  | Arquivo alterado mas não preparado | Working Directory |
| **Staged**    | Arquivo preparado para commit      | Staging Area      |
| **Committed** | Arquivo salvo no histórico         | Repository        |

---

## Parte III: Comandos Básicos

### 3.1 Configuração Inicial

```bash
# Configurar nome e email (obrigatório)
git config --global user.name "Seu Nome"
git config --global user.email "seu.email@exemplo.com"

# Ver configurações atuais
git config --list

# Configurar editor padrão
git config --global core.editor nano
```

#### 3.1.1 Personalização Avançada do .gitconfig

O arquivo `.gitconfig` é onde o Git armazena todas as suas configurações. Você pode editá-lo diretamente ou usar comandos `git config`.

**Localização do arquivo:**

- **Global:** `~/.gitconfig` (configurações para todos os repositórios)
- **Local:** `.git/config` (específico do repositório atual)

##### **Aliases - Atalhos Personalizados**

```bash
# Criar aliases úteis
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.unstage 'reset HEAD --'

# Aliases mais elaborados
git config --global alias.lg "log --oneline --graph --all"
git config --global alias.last 'log -1 HEAD'
git config --global alias.visual '!gitk'
```

**Exemplo de uso:**

```bash
# Em vez de: git status
git st

# Em vez de: git log --oneline --graph --all
git lg
```

##### **Configurações de Comportamento**

```bash
# Configurar comportamento do push
git config --global push.default simple

# Habilitar cores no terminal
git config --global color.ui auto

# Configurar merge tool
git config --global merge.tool vimdiff

# Configurar diff tool
git config --global diff.tool vimdiff

# Auto-correção de comandos digitados errado
git config --global help.autocorrect 1

# Habilitar rebase automático no pull
git config --global pull.rebase true
```

##### **Exemplo de arquivo .gitconfig completo**

```ini
[user]
    name = Seu Nome
    email = seu.email@exemplo.com

[core]
    editor = nano
    autocrlf = input
    safecrlf = true

[color]
    ui = auto

[alias]
    st = status
    co = checkout
    br = branch
    ci = commit
    df = diff
    lg = log --oneline --graph --all
    unstage = reset HEAD --
    last = log -1 HEAD
    amend = commit --amend
    undo = reset --soft HEAD~1

[push]
    default = simple

[pull]
    rebase = true

[merge]
    tool = vimdiff

[diff]
    tool = vimdiff

[help]
    autocorrect = 1
```

##### **Configurações por Repositório**

Você também pode ter configurações específicas para cada projeto:

```bash
# Dentro de um repositório específico
cd meu-projeto

# Configurar email diferente para este projeto
git config user.email "trabalho@empresa.com"

# Esta configuração fica em .git/config (local)
```

##### **Dicas de Personalização**

**🔧 Aliases Úteis para Produtividade:**

```bash
# Commit com mensagem rápida
git config --global alias.cm "commit -m"

# Add e commit juntos
git config --global alias.ac "!git add -A && git commit -m"

# Push para origin da branch atual
git config --global alias.ps "push origin HEAD"

# Pull com rebase
git config --global alias.pr "pull --rebase"

# Desfazer último commit mantendo mudanças
git config --global alias.undo "reset --soft HEAD~1"
```

**🎨 Personalizar Saída de Log:**

```bash
# Log bonito com gráfico
git config --global alias.tree "log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"

# Ver contribuições por autor
git config --global alias.contributors "shortlog --summary --numbered"
```

### 3.2 Criando e Clonando Repositórios

```bash
# Criar novo repositório na pasta atual
git init

# Clonar repositório existente
git clone https://github.com/usuario/projeto.git

# Clonar para pasta específica
git clone https://github.com/usuario/projeto.git minha-pasta
```

### 3.3 Comandos de Status e Informação

```bash
# Ver status atual dos arquivos
git status

# Ver diferenças nos arquivos modificados
git diff

# Ver diferenças dos arquivos na staging area
git diff --staged

# Ver histórico de commits
git log

# Ver histórico resumido
git log --oneline
```

### 3.4 Adicionando e Commitando

```bash
# Adicionar arquivo específico à staging area
git add arquivo.txt

# Adicionar todos os arquivos modificados
git add .

# Adicionar apenas arquivos .js
git add *.js

# Fazer commit com mensagem
git commit -m "Adicionar nova funcionalidade"

# Adicionar e commitar em um comando (apenas arquivos já rastreados)
git commit -am "Corrigir bug na validação"
```

### 3.5 Trabalhando com Branches

```bash
# Listar branches
git branch

# Criar nova branch
git branch nova-funcionalidade

# Trocar para outra branch
git checkout nova-funcionalidade

# Criar e trocar para nova branch
git checkout -b outra-funcionalidade

# Voltar para branch principal
git checkout main

# Deletar branch (após fazer merge)
git branch -d funcionalidade-concluida
```

---

## Parte IV: Colaboração e Repositórios Remotos

### 4.1 Conceitos de Remote

#### **Origin**

- Nome padrão para o repositório remoto principal
- Geralmente no GitHub, GitLab ou similar

#### **Push e Pull**

- **Push:** Enviar seus commits para o repositório remoto
- **Pull:** Baixar e integrar mudanças do repositório remoto

### 4.2 Comandos de Repositório Remoto

```bash
# Ver repositórios remotos configurados
git remote -v

# Adicionar repositório remoto
git remote add origin https://github.com/usuario/projeto.git

# Enviar commits para o remoto
git push origin main

# Baixar e integrar mudanças do remoto
git pull origin main

# Apenas baixar mudanças (sem integrar)
git fetch origin
```

### 4.3 Fluxo Básico de Trabalho

```bash
# 1. Baixar última versão
git pull origin main

# 2. Criar branch para nova funcionalidade
git checkout -b minha-funcionalidade

# 3. Fazer modificações nos arquivos
# ... editar arquivos ...

# 4. Adicionar mudanças
git add .

# 5. Fazer commit
git commit -m "Implementar minha funcionalidade"

# 6. Enviar branch para o remoto
git push origin minha-funcionalidade

# 7. Criar Pull Request/Merge Request no GitHub/GitLab
# 8. Após aprovação, fazer merge e voltar para main
git checkout main
git pull origin main
git branch -d minha-funcionalidade
```

---

## Parte V: Resolvendo Problemas Comuns

### 5.1 Desfazendo Mudanças

```bash
# Desfazer mudanças não commitadas em um arquivo
git checkout -- arquivo.txt

# Remover arquivo da staging area
git reset arquivo.txt

# Desfazer último commit (mantendo mudanças)
git reset --soft HEAD~1

# Desfazer último commit (perdendo mudanças)
git reset --hard HEAD~1

# Reverter commit específico (cria novo commit)
git revert abc123
```

### 5.2 Trabalhando com .gitignore

Arquivo `.gitignore` especifica quais arquivos/pastas o Git deve ignorar:

```bash
# Exemplo de .gitignore

# Arquivos de sistema
.DS_Store
Thumbs.db

# Dependências
node_modules/
vendor/

# Arquivos de configuração local
.env
config.local.js

# Arquivos de build
dist/
build/
*.log

# Arquivos temporários
tmp/
*.tmp
*~
```

### 5.3 Resolvendo Conflitos

Quando duas pessoas editam o mesmo arquivo:

```bash
# Durante git pull ou git merge, pode aparecer conflito
Auto-merging arquivo.txt
CONFLICT (content): Merge conflict in arquivo.txt
Automatic merge failed; fix conflicts and then commit the result.
```

**Como resolver:**

1. **Abrir arquivo com conflito:**

```
<<<<<<< HEAD
Sua versão do código
=======
Versão que está vindo do remoto
>>>>>>> branch-name
```

2. **Editar manualmente** para resolver o conflito
3. **Adicionar arquivo resolvido:** `git add arquivo.txt`
4. **Fazer commit:** `git commit -m "Resolver conflito em arquivo.txt"`

---

## Parte VI: Boas Práticas

### 6.1 Mensagens de Commit

#### **Boas mensagens:**

```bash
git commit -m "Adicionar validação de email no formulário"
git commit -m "Corrigir bug de divisão por zero"
git commit -m "Refatorar função de cálculo de impostos"
```

#### **Mensagens ruins:**

```bash
git commit -m "fix"
git commit -m "mudanças"
git commit -m "atualizei uns negócios"
```

#### **Padrão recomendado:**

```
Tipo: Descrição curta (máximo 50 caracteres)

Explicação mais detalhada se necessário (máximo 72 caracteres por linha).
Explicar o que foi feito e por quê, não como.

- Item 1 da mudança
- Item 2 da mudança
```

### 6.2 Quando Fazer Commit

#### **Faça commit quando:**

- Completar uma pequena funcionalidade
- Corrigir um bug específico
- Refatorar uma parte do código
- Adicionar testes

#### **Não faça commit quando:**

- Código não compila/não funciona
- Mudanças muito grandes misturadas
- Arquivos temporários ou de configuração pessoal

### 6.3 Organização de Branches

#### **Estratégia simples:**

```
main           # Código em produção
develop        # Desenvolvimento ativo
feature/login  # Nova funcionalidade
hotfix/bug123  # Correção urgente
```

#### **Nomenclatura:**

- `feature/` para novas funcionalidades
- `bugfix/` para correções
- `hotfix/` para correções urgentes
- `refactor/` para refatorações

---

## Parte VII: Comandos de Referência Rápida

### 7.1 Comandos Essenciais

```bash
# Status e informações
git status                    # Ver estado atual
git log --oneline            # Histórico resumido
git diff                     # Ver mudanças

# Trabalhando com mudanças
git add .                    # Adicionar tudo
git commit -m "mensagem"     # Fazer commit
git push origin main         # Enviar para remoto
git pull origin main         # Baixar do remoto

# Branches
git branch                   # Listar branches
git checkout -b nova-branch  # Criar e trocar
git merge outra-branch       # Fazer merge

# Desfazer
git checkout -- arquivo     # Desfazer mudanças
git reset HEAD arquivo      # Remover da staging
```

### 7.2 Aliases Úteis

Adicione ao seu `.gitconfig` ou use `git config --global`:

```bash
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.unstage 'reset HEAD --'
git config --global alias.last 'log -1 HEAD'
git config --global alias.visual '!gitk'
```

Uso:

```bash
git st        # em vez de git status
git co main   # em vez de git checkout main
git ci -m     # em vez de git commit -m
```

---

## Parte VIII: Integrações e Ferramentas

### 8.1 GitHub/GitLab

#### **Pull Requests / Merge Requests**

- Proposta para integrar mudanças
- Permite revisão de código
- Discussão sobre as mudanças
- Testes automatizados

#### **Issues**

- Rastreamento de bugs
- Solicitações de funcionalidades
- Documentação de problemas

### 8.2 Ferramentas Visuais

#### **Linha de comando melhorada:**

```bash
# Ver histórico gráfico
git log --graph --oneline --all

# Status colorido
git config --global color.ui auto
```

#### **Editores com integração Git:**

- VS Code (extensão GitLens)
- Sublime Text
- Atom
- Vim/Neovim

---

## Conclusão

O Git é uma ferramenta fundamental no desenvolvimento moderno. Este documento cobriu:

1. **Conceitos básicos** → Por que usar controle de versão
2. **Comandos essenciais** → Para uso diário
3. **Colaboração** → Trabalhando em equipe
4. **Resolução de problemas** → Situações comuns
5. **Boas práticas** → Como usar de forma eficiente

> **Próximo passo:** Pratique criando um repositório local, fazendo alguns commits e enviando para o GitHub!

**Documentos relacionados:**

- **[Interfaces de Usuário e Terminal](./interfaces-terminal.md)** - Comandos de terminal
- **[Fundamentos de Eletrônica e Programação](./introducao.md)** - Conceitos de programação
