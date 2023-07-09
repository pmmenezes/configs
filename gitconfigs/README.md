# Condigurações de ambiente pessoal

### Múltiplas contas GIT 

1. Gere suas chaves sssh
```bash
ssh-keygen -t rsa -f ".ssh/id_rsa_pessoal" -C "pessoal@meuemail.pessoal.com.br"

ssh-keygen -t rsa -f ".ssh/id_rsa_work" -C "work@meuemail.work.com.br"

ssh-keygen -t rsa -f ".ssh/id_rsa_azdev01" -C "azdev01@email.com.br"

ssh-keygen -t rsa -f ".ssh/id_rsa_azdev02" -C "azdev02@email.com.br"


```
2. Redistre as chaves vomSSH agent

```bash
eval $(ssh-agent)
ssh-add ~/.ssh/id_rsa_pessoal
ssh-add ~/.ssh/id_rsa_work
ssh-add ~/.ssh/id_rsa_azdev01
ssh-add ~/.ssh/id_rsa_azdev02
```
3. Crie o arquivo de configuração ssh

```bash
cat >> ~/.ssh/config << EOF
    # Configuação padrão - perfil pessoal
    Host github.com
        HostName github.com
        User git
        IdentityFile ~/.ssh/id_rsa_pessoal

    # GitHub Work - Perfil profissional
        Host github.com-worker
        HostName github.com
        User git
        IdentityFile ~/.ssh/id_rsa_work

    # Exemplo de configuração Azure devops caso mais de uma conta
        Host azrepo01
        HostName ssh.dev.azure.com
        IdentityFile ~/.ssh/id_rsa_azrepo01
        IdentitiesOnly yes
        
        Host azrepo02
        HostName ssh.dev.azure.com
        IdentityFile ~/.ssh/id_rsa_azrepo02
        IdentitiesOnly yes
EOF
```
4. Crei os diretórios para os repositórios

```bash
 mkdir pessoal work azrepo1 azrepo2
 
```
5. Crie uma configuração global para o git

```bash
cat >> ~/.gitconfig << EOF
[user]
  name = SEU NOME 
[init]
  defaultBranch = main

[includeIf "gitdir:~/pessoal"]
  path = .gitconfig-pessoal
[includeIf "gitdir:~/work"]
  path = .gitconfig-work
[includeIf "gitdir:~/azrepo1"]
  path = .gitconfig-azrepo1
[includeIf "gitdir:~/azrepo2"]
  path = .gitconfig-azrepo2
EOF
```
6. Crie os gitconfigs para cada repo
```bash 
touch  ~/.gitconfig-{pessoal,work,azrepo{1,2}}
```
Exemplo de configuração gitconfig individuais

- .gitconfig-pessoal
```bash
[user]
  email = pessoal@meuemail.pessoal.com.br"
```
- .gitconfig-work

```bash
[user]
  email = "work@meuemail.work.com.br"
```
- .gitconfig-azrepo1
- 
```bash
[user]
  email = "azdev01@email.com.br"
```
- .gitconfig-azrepo2

```bash
[user]
  email = "azdev01@email.com.br"
```

