# GitHub e Repositórios Remotos

Este documento explica o que é o GitHub, sua relação com o Git, e como conectar repositórios locais a repositórios remotos usando HTTP e SSH.

---

## 1. O que é GitHub?

### 1.1 GitHub vs Git

**Git** é o sistema de controle de versão - o software que roda na sua máquina e gerencia o histórico de mudanças.

**GitHub** é uma plataforma web que hospeda repositórios Git na nuvem, permitindo:

- Armazenamento remoto de código
- Colaboração entre desenvolvedores
- Compartilhamento de projetos
- Backup automático do código
- Ferramentas adicionais (Issues, Pull Requests, Actions, etc.)

> **Analogia:** Git é como um sistema de arquivos versionado no seu computador. GitHub é como o Google Drive ou Dropbox, mas especializado em código com ferramentas de colaboração.

### 1.2 Alternativas ao GitHub

Outras plataformas similares:

- **GitLab** - Alternativa open-source, pode ser auto-hospedada
- **Bitbucket** - Popular em ambientes corporativos
- **Azure DevOps** - Solução da Microsoft
- **Gitea** - Solução leve e auto-hospedada

---

## 2. Protocolos de Conexão: HTTPS vs SSH

### 2.1 HTTPS (HTTP Secure)

**Vantagens:**

- Mais simples de configurar
- Funciona em qualquer rede (não é bloqueado por firewalls)
- Não requer configuração inicial

**Desvantagens:**

- Solicita usuário e senha a cada operação (pode ser mitigado com credential helper)
- Menos seguro que SSH para uso frequente

**Formato da URL:**

```
https://github.com/usuario/repositorio.git
```

### 2.2 SSH (Secure Shell)

**Vantagens:**

- Mais seguro (usa criptografia de chave pública/privada)
- Não solicita senha após configuração inicial
- Ideal para uso diário

**Desvantagens:**

- Requer configuração de chaves SSH
- Pode ser bloqueado em algumas redes corporativas

**Formato da URL:**

```
git@github.com:usuario/repositorio.git
```

---

## 3. Configurando Conexão HTTPS

### 3.1 Clonar Repositório com HTTPS

```bash
# Clonar repositório público
git clone https://github.com/usuario/repositorio.git

# Entrar na pasta do repositório
cd repositorio
```

### 3.2 Adicionar Remote Existente com HTTPS

```bash
# Se você já tem um repositório local
git remote add origin https://github.com/usuario/repositorio.git

# Verificar se foi adicionado
git remote -v
```

### 3.3 Configurar Credential Helper (Evitar Digite Senha Toda Hora)

**macOS:**

```bash
# Usar Keychain do macOS para armazenar credenciais
git config --global credential.helper osxkeychain
```

**Linux:**

```bash
# Armazenar credenciais em cache por 1 hora
git config --global credential.helper 'cache --timeout=3600'

# Ou armazenar permanentemente (menos seguro)
git config --global credential.helper store
```

**Windows:**

```bash
# Usar Windows Credential Manager
git config --global credential.helper wincred
```

### 3.4 Usar Personal Access Token (Recomendado)

Desde 2021, o GitHub não aceita mais senha comum. Use um **Personal Access Token**:

1. Acesse: `GitHub → Settings → Developer settings → Personal access tokens → Tokens (classic)`
2. Clique em "Generate new token"
3. Selecione os escopos necessários (repo, workflow, etc.)
4. Copie o token gerado (você não verá novamente!)
5. Use o token como senha quando o Git solicitar

```bash
# Exemplo de push
git push origin main

# Quando solicitar:
Username: seu-usuario
Password: ghp_SeuTokenAqui123456789...
```

---

## 4. Configurando Conexão SSH

### 4.1 Gerar Chave SSH

```bash
# Gerar par de chaves SSH (pública e privada)
ssh-keygen -t ed25519 -C "seu.email@exemplo.com"

# Se seu sistema não suporta ed25519, use RSA:
ssh-keygen -t rsa -b 4096 -C "seu.email@exemplo.com"

# Pressione Enter para aceitar o local padrão (~/.ssh/id_ed25519)
# Opcionalmente, defina uma senha para a chave (recomendado)
```

**Arquivos criados:**

- `~/.ssh/id_ed25519` - Chave privada (NUNCA compartilhe!)
- `~/.ssh/id_ed25519.pub` - Chave pública (esta você adiciona ao GitHub)

### 4.2 Adicionar Chave SSH ao ssh-agent

```bash
# Iniciar ssh-agent em background
eval "$(ssh-agent -s)"

# Adicionar chave privada ao ssh-agent
ssh-add ~/.ssh/id_ed25519

# macOS: adicionar chave ao Keychain
ssh-add --apple-use-keychain ~/.ssh/id_ed25519
```

### 4.3 Adicionar Chave Pública ao GitHub

```bash
# Copiar chave pública para clipboard
# macOS:
pbcopy < ~/.ssh/id_ed25519.pub

# Linux:
cat ~/.ssh/id_ed25519.pub
# (copie manualmente a saída)
```

**No GitHub:**

1. Acesse: `GitHub → Settings → SSH and GPG keys`
2. Clique em "New SSH key"
3. Dê um título descritivo (ex: "MacBook Pro")
4. Cole a chave pública no campo "Key"
5. Clique em "Add SSH key"

### 4.4 Testar Conexão SSH

```bash
# Testar conexão com GitHub
ssh -T git@github.com

# Saída esperada:
# Hi usuario! You've successfully authenticated, but GitHub does not provide shell access.
```

### 4.5 Clonar Repositório com SSH

```bash
# Clonar usando SSH
git clone git@github.com:usuario/repositorio.git

# Entrar na pasta
cd repositorio
```

### 4.6 Converter Remote de HTTPS para SSH

```bash
# Ver remote atual
git remote -v

# Trocar de HTTPS para SSH
git remote set-url origin git@github.com:usuario/repositorio.git

# Verificar mudança
git remote -v
```

---

## 5. Comandos Úteis para Repositórios Remotos

### 5.1 Gerenciar Remotes

```bash
# Listar remotes configurados
git remote -v

# Adicionar novo remote
git remote add upstream git@github.com:original/repositorio.git

# Remover remote
git remote remove origin

# Renomear remote
git remote rename origin novo-nome

# Ver informações detalhadas do remote
git remote show origin
```

### 5.2 Sincronizar com Remote

```bash
# Baixar mudanças sem fazer merge
git fetch origin

# Baixar mudanças de todos os remotes
git fetch --all

# Baixar e fazer merge automaticamente
git pull origin main

# Enviar commits locais
git push origin main

# Enviar todas as branches
git push --all origin

# Enviar tags
git push --tags
```

### 5.3 Trabalhar com Múltiplos Remotes

```bash
# Cenário: Fork de projeto open-source

# Seu fork (onde você tem permissão de escrita)
git remote add origin git@github.com:seu-usuario/projeto.git

# Repositório original (upstream)
git remote add upstream git@github.com:usuario-original/projeto.git

# Atualizar do upstream
git fetch upstream
git merge upstream/main

# Enviar suas mudanças para seu fork
git push origin main
```

---

## 6. Fluxo Prático Completo

### 6.1 Criar Novo Repositório no GitHub e Conectar

```bash
# 1. Criar repositório no GitHub via interface web

# 2. No seu computador, criar pasta do projeto
mkdir meu-projeto
cd meu-projeto

# 3. Inicializar Git
git init

# 4. Criar arquivo inicial
echo "# Meu Projeto" > README.md

# 5. Fazer primeiro commit
git add README.md
git commit -m "Initial commit"

# 6. Adicionar remote (escolha HTTPS ou SSH)
# HTTPS:
git remote add origin https://github.com/usuario/meu-projeto.git
# OU SSH:
git remote add origin git@github.com:usuario/meu-projeto.git

# 7. Renomear branch para main (se necessário)
git branch -M main

# 8. Enviar para GitHub
git push -u origin main
```

### 6.2 Clonar Repositório Existente e Trabalhar

```bash
# 1. Clonar repositório
git clone git@github.com:usuario/projeto.git
cd projeto

# 2. Criar branch para nova feature
git checkout -b minha-feature

# 3. Fazer mudanças
# ... editar arquivos ...

# 4. Adicionar e commitar
git add .
git commit -m "Adicionar nova funcionalidade"

# 5. Enviar branch para remote
git push origin minha-feature

# 6. Criar Pull Request no GitHub via interface web

# 7. Após merge, atualizar main local
git checkout main
git pull origin main

# 8. Deletar branch local
git branch -d minha-feature
```

---

## 7. Boas Práticas

### 7.1 Segurança

- **Nunca** compartilhe sua chave SSH privada
- Use senha forte para proteger suas chaves SSH
- Revogue tokens e chaves que não usa mais
- Use tokens com escopo mínimo necessário
- Ative autenticação de dois fatores (2FA) no GitHub

### 7.2 Organização

- Use nomes descritivos para remotes (`origin`, `upstream`, `production`)
- Mantenha branches locais sincronizadas com o remote
- Delete branches remotas após merge
- Configure `.gitignore` antes do primeiro commit

### 7.3 Comandos Úteis para Diagnóstico

```bash
# Verificar status de tracking das branches
git branch -vv

# Ver diferenças entre local e remote
git diff origin/main

# Ver commits que serão enviados
git log origin/main..HEAD

# Ver commits que serão baixados
git log HEAD..origin/main

# Verificar configuração do Git
git config --list --show-origin
```

---

## 8. Solução de Problemas Comuns

### 8.1 Erro: Permission Denied (SSH)

```bash
# Verificar se chave SSH está no agent
ssh-add -l

# Se não estiver, adicionar
ssh-add ~/.ssh/id_ed25519

# Testar conexão
ssh -T git@github.com
```

### 8.2 Erro: Authentication Failed (HTTPS)

```bash
# Limpar credenciais salvas
git credential-cache exit
git credential reject

# Tentar novamente - solicitará credenciais
git push origin main
```

### 8.3 Divergência entre Local e Remote

```bash
# Se remote tem commits que você não tem
git pull --rebase origin main

# Ou fazer merge manual
git fetch origin
git merge origin/main
```

### 8.4 Forçar Push (Cuidado!)

```bash
# Apenas use se tem certeza absoluta
# Sobrescreve histórico no remote
git push --force origin main

# Versão mais segura (falha se remote mudou)
git push --force-with-lease origin main
```

---

## Conclusão

A conexão entre Git local e GitHub (ou outra plataforma) é essencial para colaboração e backup de código. Escolha entre HTTPS (mais simples) ou SSH (mais seguro e conveniente) baseado nas suas necessidades e ambiente de trabalho.

**Recomendação:** Para uso diário, configure SSH. Para scripts e CI/CD, use HTTPS com tokens.

**Documentos relacionados:**

- **[Controle de Versão com Git](./git-controle-versao.md)** - Conceitos fundamentais do Git
- **[Interfaces de Usuário e Terminal](./interfaces-terminal.md)** - Comandos básicos do terminal
