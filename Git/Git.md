## Comandos Git e suas Funções

### **Configuração**

```sh
git config --global user.name "Seu Nome"  # Define o nome de usuário global
git config --global user.email "seu@email.com"  # Define o email global
git config --global core.editor "vim"  # Define o editor padrão
git config --global alias.<atalho> "<comando>"  # Cria atalhos para comandos Git
git config --global credential.helper store  # Salva credenciais do Git permanentemente
git config --global diff.tool vimdiff  # Define uma ferramenta de comparação de diferenças
git config --global merge.tool vimdiff  # Define uma ferramenta para resolver merges
git config --list  # Lista todas as configurações do Git
git config --global push.default simple  # Define o comportamento padrão do push
git config --global pull.rebase true  # Define pull para usar rebase por padrão

```

### **Inicialização e Clonagem**

```sh
git init  # Inicializa um repositório Git no diretório atual
git clone <URL_DO_REPOSITORIO>  # Clona um repositório remoto
git clone --depth=1 <URL>  # Clona apenas o último commit (shallow clone)
```

### **Status e Informações**

```sh
git status  # Mostra o status dos arquivos no repositório
git log  # Exibe o histórico de commits
git log --oneline  # Exibe o histórico de commits de forma resumida
git log --graph --decorate --oneline --all  # Exibe log em formato gráfico
git show <commit>  # Exibe detalhes de um commit específico
git diff  # Mostra diferenças entre arquivos não commitados
git diff --staged  # Mostra diferenças entre arquivos commitados
git log --since="1 week ago"  # Mostra commits da última semana
git log --author="Nome"  # Mostra commits de um autor específico
git log --grep="Palavra-chave"  # Filtra commits por mensagem
git diff HEAD~1 HEAD  # Compara o último commit com o penúltimo
git diff <branch1> <branch2>  # Compara duas branches
git log --pretty=format:"%h - %an, %ar : %s"  # Formato personalizado do log
git log --stat  # Mostra estatísticas de arquivos alterados nos commits
git show-branch  # Mostra histórico de várias branches
git whatchanged  # Mostra as mudanças no repositório (obsoleto, mas útil em alguns casos)

```

### **Adição e Remoção de Arquivos**

```sh
git add <arquivo>  # Adiciona um arquivo específico à área de staging
git add .  # Adiciona todos os arquivos modificados e novos ao staging
git rm <arquivo>  # Remove um arquivo do repositório e do diretório local
git mv <arquivo> <novo_nome>  # Renomeia/move um arquivo
```

### **Commits**

```sh
git commit -m "Mensagem do commit"  # Realiza um commit com mensagem
git commit --amend -m "Nova mensagem"  # Altera o último commit
git commit --amend --no-edit  # Modifica o último commit sem alterar a mensagem
git rebase -i HEAD~3  # Reescreve os últimos 3 commits interativamente
git cherry-pick -n <commit>  # Aplica um commit sem criar um novo commit automaticamente
git commit --squash <commit>  # Junta mudanças de um commit anterior no atua
git commit --date="YYYY-MM-DD HH:MM:SS" -m "Commit com data específica"  # Commit com data manual
git commit -v  # Commit mostrando diff no editor
git cherry -v master  # Lista commits que ainda não foram mesclados
git pull  # Atualiza o repositório local com as mudanças do repositório remoto
git pull --rebase  # Atualiza o repositório local aplicando rebase ao invés de merge
git fetch origin <branch>  # Busca alterações remotas sem aplicar ao repositório local
```

### **Branches**

```sh
git branch  # Lista todas as branches locais
git branch <nome_da_branch>  # Cria uma nova branch
git checkout <nome_da_branch>  # Muda para uma branch existente
git checkout -b <nome_da_branch>  # Cria e muda para uma nova branch
git branch -d <nome_da_branch>  # Deleta uma branch local
git branch -D <nome_da_branch>  # Força a deleção de uma branch local
git merge <branch>  # Mescla uma branch na atual
git rebase <branch>  # Reaplica commits em cima de outra branch
git branch --merged  # Lista branches já mescladas na branch atual
git branch --no-merged  # Lista branches ainda não mescladas
git push origin --all  # Envia todas as branches locais para o repositório remoto
git fetch --prune  # Atualiza o repositório e remove branches remotas deletadas
git worktree add ../novo-trabalho <branch>  # Cria um diretório separado para uma branch
git checkout -  # Alterna entre a branch atual e a anterior
git switch <branch>  # Alternativa moderna ao checkout
git switch -c <branch>  # Cria e muda para uma nova branch
```

### **Sincronização com Repositório Remoto**

```sh
git remote add origin <URL>  # Adiciona um repositório remoto
git remote -v  # Lista os repositórios remotos
git fetch  # Baixa os dados do repositório remoto sem mesclar
git pull origin <branch>  # Atualiza a branch local com as mudanças do remoto
git push origin <branch>  # Envia commits para o repositório remoto
git push -u origin <branch>  # Define upstream e envia commits para o remoto
git push --force  # Força a atualização do repositório remoto
git fetch --all  # Baixa todas as branches remotas sem mesclar
git pull --rebase  # Atualiza a branch local com rebase
git push --delete origin <branch>  # Deleta uma branch remota
```

### **Reset e Revert**

```sh
git reset --hard <commit>  # Reseta o repositório para um commit específico
git reset --soft <commit>  # Mantém mudanças no staging após reset
git reset --mixed <commit>  # Mantém mudanças no diretório de trabalho
git revert <commit>  # Cria um commit que reverte um commit específico
git revert -n <commit>  # Prepara a reversão de um commit sem confirmar automaticamente
git checkout --ours <arquivo>  # Mantém sua versão do arquivo durante conflitos de merge
git checkout --theirs <arquivo>  # Mantém a versão do remoto durante conflitos de merge
git fsck --full  # Verifica a integridade do repositório Git
git gc --prune=now  # Limpa e otimiza o repositório Git
git reset --soft HEAD~1 # Resetar commit, mantendo alterações no staging area
git reset --mixed HEAD~1 # Resetar commit, movendo alterações para arquivos não rastreados
git reset --hard HEAD~1 # Resetar commit e perder alterações definitivamente
git reset HEAD <arquivo>  # Remove arquivo do staging sem perder alterações
git reflog expire --expire=now --all && git gc --prune=now  # Força a limpeza do histórico
```

### **Stash (Guardar mudanças temporariamente)**

```sh
git stash  # Guarda temporariamente mudanças não commitadas
git stash list  # Lista os stashes armazenados
git stash pop  # Aplica e remove o stash mais recente
git stash apply  # Aplica o stash sem removê-lo da lista
git stash drop  # Deleta um stash específico
```

### **Tags**

- Tag em Git é um objeto que referencia um commit específico no histórico de um projeto.

```sh
git tag <nome_da_tag>  # Cria uma tag
git tag -a <nome_da_tag> -m "Mensagem da tag"  # Cria uma tag anotada
git show <nome_da_tag>  # Mostra detalhes de uma tag
git push origin <nome_da_tag>  # Envia uma tag para o repositório remoto
git push --tags  # Envia todas as tags para o remoto
git tag -d <nome_da_tag>  # Deleta uma tag local
git push origin --delete <nome_da_tag>  # Remove uma tag do remoto
```

### **Submódulos**

- É uma referência a outro repositório em um determinado instante no tempo.

```sh
git submodule add <URL> <pasta>  # Adiciona um submódulo ao repositório
git submodule update --init --recursive  # Inicializa e atualiza submódulos
git submodule foreach git pull origin main  # Atualiza todos os submódulos
```

### **Outros Comandos Úteis**

- Git Worktree é um recurso do Git que permite criar vários diretórios de trabalho a partir do mesmo repositório.

```sh
git clean -df  # Remove arquivos não rastreados
git blame <arquivo>  # Mostra quem modificou cada linha de um arquivo
git shortlog -s -n  # Mostra contribuições de cada autor
git cherry-pick <commit>  # Aplica um commit específico em outra branch
git bisect start  # Inicia uma busca binária por um commit com erro
git reflog  # Exibe histórico de ações locais do repositório
git push --follow-tags  # Envia commits e tags associadas automaticamente
git bisect run <script>  # Automatiza a busca binária por um commit com erro
git checkout -- <arquivo>  # Restaura um arquivo para seu estado mais recente no repositório
git worktree list  # Lista os worktrees existentes
git worktree prune  # Remove worktrees órfãos
```

### **6. Resolvendo Problemas Comuns**

#### Merge Conflict

```sh
# Identificar conflitos
git status

# Editar arquivos conflitantes manualmente

# Marcar os conflitos como resolvidos
git add <arquivo-conflito>

# Criar um novo commit após resolver
git commit -m "Resolvendo conflito de merge"
```

#### Resetar Último Commit

```sh
# Resetar commit, mantendo alterações no staging area
git reset --soft HEAD~1

# Resetar commit, movendo alterações para arquivos não rastreados
git reset --mixed HEAD~1

# Resetar commit e perder alterações definitivamente
git reset --hard HEAD~1

# Reseta o repositório para um commit específico
git reset --hard <commit>

# Mantém mudanças no staging após reset
git reset --soft <commit>

# Mantém mudanças no diretório de trabalho
git reset --mixed <commit>

# Cria um commit que reverte um commit específico
git revert <commit>
```

#### Corrupção do .git

```sh
# Verificar se o repositório está corrompido
git fsck --full

# Se houver corrupção, listar histórico de referências
git reflog

# Tentar recuperar um commit perdido (se necessário)
git reset --hard <commit-id>

# Se necessário, rebaixar a versão do repositório para o último estado funcional
git checkout -b recovery-branch <commit-id>

# Caso o repositório estiver muito corrompido:

# Clone novamente o repositório:
git clone <nome do repositório>
```

#### Recuperar Arquivos Excluídos

```sh
# Recuperar arquivo deletado antes do commit
git checkout -- <arquivo>

# Recuperar arquivo deletado após commit
git checkout HEAD~1 -- <arquivo>
```

#### Voltar para um Commit Anterior

```sh
# Criar uma nova branch baseada em um commit antigo
git checkout -b <nova-branch> <id-do-commit>

# Resetar branch atual para um commit específico
git reset --hard <id-do-commit>
```

#### Branch Errada

```sh
# Mover o commit atual para outra branch
git branch <nova-branch>
git reset --hard HEAD~1
git checkout <nova-branch>
git commit -m "Movendo commit para a branch correta"
```

#### Esqueci de Adicionar um Arquivo no Último Commit

```sh
# Adicionar o arquivo e modificar o último commit sem mudar o histórico
git add <arquivo>
git commit --amend --no-edit
```

#### Branch Remota Deletada Ainda Aparece

```sh
# Atualizar a lista de branches remotas
git remote prune origin
```

#### Refazer o Último Commit

```sh
# Alterar mensagem do último commit sem mudar o conteúdo
git commit --amend -m "Nova mensagem de commit"
```

#### Desfazer um Commit Empurrado para o Remoto

```sh
# Criar um commit que reverte um commit específico
git revert <id-do-commit>

# Se ainda não foi puxado por ninguém e deseja remover definitivamente
git reset --hard <id-anterior>
git push origin +HEAD --force
```

#### Reaplicar Commits de Outra Branch

```sh
# Cherry-pick para aplicar um commit específico na branch atual
git cherry-pick <id-do-commit>
```

#### Atualizar uma Branch Local com a Última Versão do Remoto

```sh
# Se não houver commits locais
git fetch origin
git reset --hard origin/<branch>

# Se houver commits locais, mesclar com o remoto
git pull origin <branch>
```
