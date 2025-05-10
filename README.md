
# Sistemas Operacionais II 🐧

Disciplina ministrada pela professora Dorotea Garcia

Lattes:  http://lattes.cnpq.br/8453243844263956
## Aula 01

Sistema Operacional: é um conjunto de programas que faz a ligação entre o usuário e o hardware. Ele recebe os comandos do usuário e faz com que o hardware os execute.

Linux: criado por Linus Torvalds em 1991, é um sistema operacional de código aberto, gratuito e que segue o padrão POSIX, o mesmo usado pelo Unix. Isso facilita a portabilidade para outros sistemas compatíveis. Como é mantido por uma grande comunidade, recebe melhorias constantes em estabilidade e desempenho.

Interpretador de Comandos (Shell): é o programa que recebe os comandos do usuário e os repassa para o sistema operacional. Ele pode rodar comandos digitados na hora (modo interativo) ou ler e executar comandos de um arquivo (modo não interativo). O shell mais usado no Linux é o bash, mas existem outros como sh, csh e tcsh.

Execução de Comandos:

Interativa: o usuário digita os comandos um a um, e o sistema os executa imediatamente.
Não interativa: comandos são escritos em um arquivo (script), e o sistema os executa automaticamente na ordem definida. Isso permite criar rotinas e automações.

- Sistema Operacional: meio de campo entre hardware e usuário.

- Ambiente básico de computação: hardware e software

- Ambiente automobilístico: máquina + combustível + piloto

- Ambiente computacional: hardware + sistema operacional + usuário

Linux: open source, gratuito, compatível com Unix via padrão POSIX, portabilidade para todos os sistemas que atendem o padrão POSIX, constantemente atualizado e optimizado pela comunidade.

Interpretador de Comandos: shell, interpreta os comandos feitos pelo usuário e seus programas ao sistema operacional(o kernel).
(a shell é  intermediário entre o usuário e o kernel). *É a principal ligação entre o usuário, os programas e o kernel.*

*Interpretador de comando mais usado é o bash*

Os comandos podem ser enviados de forma interativa ou não interativa.


* Interativa: comandos digitados e passados pelo interpretador um a um. Computador mais dependente do usuário para executar uma tarefa.

* Não interativa: scripts para o computador executar os comandos na ordem encontrada no arquivo. O computador segue as ordens do script para executar rotinas. O script pode checar qual será o próximo comando dependendo do término do anterior.

## Aula 02
Linux: Tipos de Usuários e Comandos Básicos

## Tipos de Usuário

- **Admin (root)**: Possui plenos poderes dentro do sistema Linux.
- **Grupo**: Usuários que compartilham características em comum.

## Chaves de Acesso

### Administrador (root)
```bash
styx login: root
Password: 123456
```

### Usuário Comum
```bash
styx login: dora
Password: dora
```

## Formação da Chave de Acesso

### Root
```bash
[root@styx root]#
```
- **root**: Nome do usuário.
- **@styx**: Terminal em uso (identificação).
- **root**: Diretório nativo.
- **#**: Prompt do root.

### Usuário Comum
```bash
[dora@styx dora]$
```
- **dora**: Nome do usuário.
- **@styx**: Terminal em uso (identificação).
- **dora**: Diretório nativo.
- **$**: Prompt do usuário comum.

## Estrutura de Diretórios no Linux
```bash
/ (diretório raiz)
│
├── root (diretório nativo do administrador)
│
└── home (diretório nativo do usuário)
    ├── dora
```

## Sair do Ambiente

### Usuário Comum
```bash
logout
exit
CTRL+D
```

### Administrador (root)
```bash
shutdown -h now  # Desliga o ambiente para todos os usuários.
shutdown -h -t 60  # Envia um aviso e desliga em 60 segundos.
halt  # Desliga imediatamente.
shutdown -r -t 60  # Reinicia o sistema em 60 segundos.
reboot  # Reinicia o sistema imediatamente.
```

## Tipos de Arquivos no Linux

- Arquivos que começam com `.` são ocultos.
- **.txt**: Arquivo de texto.
- **.sh**: Script interpretado pelo shell (`/bin/sh`).
- **.log**: Registro de logs de programas.
- **.gz**: Arquivo compactado pelo utilitário gzip.
- **.aspl**: Página de internet em formato hipertexto.

## Comandos Úteis

- **Visualizar o conteúdo do diretório atual:**
  ```bash
  ls
  ```

- **Acessar o diretório home do usuário:**
  ```bash
  cd ~
  ```

- **Acessar o diretório root (somente para administradores):**
  ```bash
  cd /
  ```

## FHS (Hierarquia Padrão do Sistema de Arquivos)

O FHS define a estrutura de diretórios do Linux, garantindo organização e padronização do sistema.

## Aula 03 - Explorando o comando `ls`

- **Atenção** 🚨

*Diretório raiz NÃO É SINÔNIMO de diretório nativo, diretório nativo é de onde o usuário veio e diretório raiz é o diretório que contem todos os diretório, é representado por ´/`* 

<p align="center">
  <img src= "https://github.com/claraneves23/sistemas_operacionais_II/blob/main/Captura%20de%20tela%202025-03-11%20184951.png">
</p>

- 🔵 = diretório
- ⚪ = arquivo
- 🔴 = arquivo compactado
- 🟢 = link

### Comando ls e seus parâmetros
| Comando    |Descrição                    |
|------------|-----------------------------|
| ls ou ls . | exibe o diretório corrente  |
| ls ..      | exibe o conteúdo do diretório anterior|
| ls ~       | visualizar o diretório nativo sem se deslocar do diretório corrente |
| ls -F     | adiciona símbolos ao final dos nomes para indicar o tipo de cada item. **Sem símbolo (arquivo comum), / *barra* (diretório) e @ (link)**|
| ls -a     | vizualizar arquivos ocultos|
| ls -t     | listar arquivos por ordem de data de modificação, Arquivos modificados mais recentemente aparecem primeiro na listagem.|
| ls -1     | lista os arquivos por linha, um em cada linha|
| ls -l     | listar arquivos pelo formato longo|

<p align="center">
<img width="80%" src= "https://github.com/claraneves23/sistemas_operacionais_II/blob/main/Captura%20de%20tela%202025-03-11%20191520.png">
</p>

| Coluna                     | Descrição                                                                                 |
|----------------------------|--------------------------------------------------------------------------------------------|
| Permissões                 | Indica se é um diretório (d), link simbólico (l), e as permissões de leitura, escrita e execução para dono, grupo e outros. |
| Links                     | Quantidade de links (hard links) associados ao arquivo ou diretório.                      |
| Proprietário              | Usuário dono do arquivo (geralmente root em /proc).                                       |
| Grupo                     | Grupo dono do arquivo (também root).                                                      |
| Tamanho                   | Tamanho em bytes (nem sempre útil no /proc por ser virtual).                              |
| Data e Hora               | Última modificação.                                                                        |
| Nome do Arquivo/Diretório | Nome do item listado.                                                                      |

### Criando um arquivo vazio
```
touch <nome_do_arquivo>
```

### Metacaracteres

| Metacaractere | Função                                                                 | Exemplo                           | Resultado do Exemplo                              |
|----------------|------------------------------------------------------------------------|-----------------------------------|----------------------------------------------------|
| `*`            | Substitui qualquer quantidade de caracteres (zero ou mais).           | `arq*`                            | Encontra `arq1`, `arq_backup`, `arquivo.txt` etc. |
| `?`            | Substitui exatamente um único caractere.                              | `arq?.txt`                        | Encontra `arq1.txt`, `arq2.txt` (mas não `arq10.txt`) |
| `[]`           | Define uma lista de caracteres possíveis em uma posição.              | `arq[1-3].txt`                    | Encontra `arq1.txt`, `arq2.txt`, `arq3.txt`        |
| `{}`           | Gera uma sequência de caracteres separados por vírgula.               | `arq{1,2,3}.txt`                  | Expande para `arq1.txt`, `arq2.txt`, `arq3.txt`    |

## Aula 04 - Explorando o comando `cd`

### Comando cd e seus parâmetros
| Comando    |Descrição                    |
|------------|-----------------------------|
| cd  | serve para acessar e mudar de diretório corrente.​  |
| cd /(caminho) |parte do raiz até o último diretório passado como referência.​ |
| cd ..      | visualizar o diretório que está um nível acima. |
| cd ~     | vai para o diretório nativo|
| cd -     | retorna ao último diretório acessado. |

### Estrutura de Diretórios (FHS)

Use o comando tree para visualizar a estrutura de diretórios:

```bash
tree         # Mostra arquivos e pastas
tree -d      # Mostra apenas diretórios

```

### Criação de Diretórios

| Situação | Comando | Resultado |
|---------|---------|-----------|
| Criar um diretório | `mkdir trabalho` | Cria `/home/trabalho` |
| Criar diretórios em árvore | `mkdir -p lista/atividade/tarefa` | Cria todos os diretórios em cadeia |
| Criar múltiplos diretórios no mesmo nível | `mkdir licao1 licao2 licao3` | Cria três diretórios no mesmo nível |

### Remoção de Diretórios

#### Requisitos
- Diretório deve estar vazio	
- Estar um nível acima

| Comando | Função |
|--------|--------|
| `rmdir nome` | Remove diretório vazio |
| `rm nome` | Remove arquivo |
| `rm -rf nome` | Remove diretório com tudo dentro (⚠️ sem confirmação) |

### Comando pwd
Mostra o caminho completo do diretório atual a partir da raiz.

```bash
pwd
# Exemplo de saída:
/home/fatec/CPD

```

## Aula 05 

### Comando cp – Copiar Arquivos

| Parâmetro | Descrição | Exemplo |
|-----------|-----------|---------|
| *(sem parâmetro)* | Copia o arquivo com mesmo nome | `cp /proc/version /home/sistop` |
| `-i` | Interativo – pede confirmação antes de sobrescrever | `cp -i version /home/sistop` |
| `-f` | Força a cópia, mesmo que o arquivo exista | `cp -f version /home/sistop` |
| `-b` | Cria backup do destino, adicionando `~` | `cp -b version /home/sistop` |
| `-r` | Copia diretórios recursivamente | `cp -r pasta1/ /home/sistop` |
| Usar novo nome | Copia e já renomeia o arquivo | `cp version versão` |
| Vários arquivos | Copia múltiplos arquivos ao destino | `cp version versão version~ /home` |

### Comando mv – Mover e/ou Renomear Arquivos

| Exemplo| Descrição | 
|-----------|-----------|
|`mv versao /root`   | Move o arquivo com mesmo nome | 
| `mv version teste` | Renomeia o arquivo no mesmo local |  
| `mv version~ /root/novo`  | Move e renomeia ao mesmo tempo | 

### Comando rm – Apagar Arquivos

| Parâmetro | Descrição | Exemplo |
|-----------|-----------|---------|
| `-i` | Interativo – pede confirmação para cada arquivo | `rm -i teste` |
| `-f` | Força a exclusão sem perguntar | `rm -f v*` |
| `-r` | Apaga diretórios e conteúdos recursivamente | `rm -r pasta1/` |
| `-rf` | Remove diretórios e arquivos de forma forçada | `rm -rf trabalho/` |

### Comando cat – Visualizar Arquivos

| Combinação | Descrição | Exemplo |
|------------|-----------|---------|
| `cat` | Mostra o conteúdo completo de um arquivo | `cat /etc/passwd` |
| `cat arquivo1 arquivo2` | Exibe múltiplos arquivos na sequência | `cat file1 file2` |

## Aula 06 - Comandos úteis

### Comando cal – Exibe o calendário

| Parâmetro | Descrição | Exemplo |
|-----------|-----------|---------|
| *(sem parâmetro)* | Mostra o mês atual | `cal` |
| `<mês> <ano>` | Mostra o mês e ano especificado | `cal 12 2025` |
| `<ano>` | Mostra o calendário do ano inteiro | `cal 2023` |

### Comando date – Exibe ou altera data/hora

| Parâmetro | Descrição | Exemplo |
|-----------|-----------|---------|
| *(sem parâmetro)* | Mostra a data e hora atual | `date` |
| `<MMDDhhmmYYYY>` | Define nova data/hora (root) | `date 082711412019` |
| `hwclock -w` | Sincroniza relógio do sistema com hardware | `date 082711412019 (barra em pé) hwclock -w` |
| `+%d/%m/%Y` | Mostra data formatada | `date "+%d/%m/%Y"` |

### Comando lpr – Envia arquivos para impressão

| Parâmetro | Descrição | Exemplo |
|-----------|-----------|---------|
| `arquivo` | Envia o arquivo para impressora padrão | `lpr /etc/passwd` |
| `cat arquivo | lpr` | Visualiza e imprime arquivo | `cat /etc/passwd | lpr` |
| `-#n` | Imprime várias cópias | `lpr -#3 /etc/passwd` |

### Comando finger – Mostra info de usuários

| Parâmetro | Descrição | Exemplo |
|-----------|-----------|---------|
| `login` | Exibe dados do usuário | `finger root` |
| Vários usuários | Mostra vários perfis | `finger fatec dora` |

### Comando history – Mostra histórico de comandos

| Parâmetro | Descrição | Exemplo |
|-----------|-----------|---------|
| *(sem parâmetro)* | Mostra histórico do terminal | `history` |
| `-c` | Limpa o histórico atual | `history -c` |
| `>> arquivo` | Salva histórico em arquivo | `history >> comandos.txt` |

### Comando uptime – Mostra tempo ligado e carga

| Parâmetro | Descrição | Exemplo |
|-----------|-----------|---------|
| *(sem parâmetro)* | Mostra tempo de atividade do sistema | `uptime` |
| `-V` | Mostra versão do comando | `uptime -V` |

### Comando uname – Informações do sistema
| Parâmetro | Descrição | Exemplo |
|-----------|-----------|---------|
| `-p` | Tipo de processador | `uname -p` |
| `-n` | Nome do host (rede) | `uname -n` |
| `-s` | Nome do SO | `uname -s` |
| `-v` | Versão do kernel | `uname -v` |
| `-a` | Todas as informações | `uname -a` |

### Comando free – Mostra uso de memória

| Campo | Descrição |
|-------|-----------|
| `total` | Memória RAM total disponível |
| `used` | Memória em uso real |
| `free` | Memória completamente livre |
| `shared` | Memória compartilhada entre apps |
| `buffers/cache` | Áreas temporárias para desempenho |
| `swap` | Espaço reservado no disco para memória virtual |

```bash
free -h     # Mostra valores em formato legível

```
### Comando top – Monitor de processos em tempo real

| Campo | Descrição |
|-------|-----------|
| `PID` | ID do processo |
| `USER` | Dono do processo |
| `%CPU` | Uso da CPU |
| `%MEM` | Uso da memória |
| `RES` | Memória usada pelo processo |
| `TIME+` | Tempo total de CPU utilizado |

### Comando vi – Editor de texto

| Comando | Ação | Exemplo |
|---------|------|---------|
| `vi` ou `vi nome` | Abre o vi (arquivo novo ou existente) | `vi texto.txt` |
| `Esc + a` | Entra em modo de inserção | `a` |
| `Esc + x` | Apaga caractere à esquerda |
| `Esc + dd` | Apaga linha atual |
| `Esc + :w nome` | Salva como novo nome | `:w texto2.txt` |
| `Esc + :wq` | Salva e sai |
| `Esc + :q!` | Sai sem salvar |

###  Comando ln – Criar links simbólicos
```bash
ln -s texto1 texto
```
## Aula 07 - Administração de Usuários e Grupos no Linux

### Comando useradd – Criar usuário

| Parâmetro | Descrição | Exemplo |
|-----------|-----------|---------|
| *(sem parâmetro)* | Cria usuário com configurações padrão | `useradd joao` |
| `-d /caminho` | Define diretório home do usuário | `useradd -d /projetos/joao joao` |
| `-m` | Cria o diretório home se não existir | `useradd -m joao` |
| `-s /bin/bash` | Define shell padrão do usuário | `useradd -s /bin/bash joao` |
| `-c "comentário"` | Adiciona descrição sobre o usuário | `useradd -c "Novo funcionário" joao` |
| `-G grupo1,grupo2` | Adiciona a grupos secundários | `useradd -G cpd,financeiro joao` |

```
Arquivos alterados automaticamente:
/etc/passwd, /etc/shadow, /etc/group
```

### Comando passwd – Definir ou alterar senha

| Parâmetro | Descrição | Exemplo |
|-----------|-----------|---------|
| `<usuário>` | Define ou altera a senha | `passwd joao` |
| `-l` | Bloqueia a conta do usuário | `passwd -l joao` |
| `-u` | Desbloqueia a conta do usuário | `passwd -u joao` |

### Comando userdel – Apagar usuário

| Parâmetro | Descrição | Exemplo |
|-----------|-----------|---------|
| `<usuário>` | Remove o usuário (sem deletar home) | `userdel joao` |
| `rm -rf /home/usuario` | Remove o diretório home manualmente | `rm -rf /home/joao` |

```
O usuário não pode estar logado no momento da exclusão.
Para sair: exit, logout ou Ctrl + D.
```

### Comando groupadd – Criar grupo

```bash
groupadd nome_do_grupo
```

### Comando gpasswd – Administrar grupos

| Parâmetro | Descrição | Exemplo |
|-----------|-----------|---------|
| `-a usuário grupo` | Adiciona usuário ao grupo | `gpasswd -a joao cpd` |
| `-d usuário grupo` | Remove usuário do grupo | `gpasswd -d joao cpd` |
| `grupo` | Define senha para grupo | `gpasswd cpd` |
| `-r grupo` | Remove a senha do grupo | `gpasswd -r cpd` |
| `-A user1,user2 grupo` | Define administradores do grupo | `gpasswd -A danilo,daphne cpd` |

### Comando id – Verificar UID, GID e grupos

| Parâmetro | Descrição | Exemplo |
|-----------|-----------|---------|
| *(sem parâmetro)* | Mostra dados do usuário atual | `id` |
| `<usuário>` | Mostra dados do usuário indicado | `id joao` |

### Comando usermod – Modificar usuários

| Parâmetro | Descrição | Exemplo |
|-----------|-----------|---------|
| `-G grupo` | Adiciona grupos secundários | `usermod -G cpd joao` |
| `-g grupo` | Altera grupo primário | `usermod -g vendas joao` |
| `-c "comentário"` | Altera campo de descrição | `usermod -c "TI Pleno" joao` |
| `-d /novo/home -m` | Altera e move diretório home | `usermod -d /dados/joao -m joao` |
| `-s /bin/zsh` | Altera shell padrão | `usermod -s /bin/zsh joao` |
| `-L` | Bloqueia a conta (sem usar `passwd`) | `usermod -L joao` |
| `-U` | Desbloqueia a conta | `usermod -U joao` |

##  Aula 08 - Permissões de Arquivos no Linux

Entendendo as permissões<br>
Cada arquivo ou diretório possui:<br>

- Proprietário (usuário)
- Grupo<br>

Permissões para:

- Usuário (u)

- Grupo (g)

- Outros (o)
  
#### Exemplo do comando ls -l

```bash
ls -l texto.txt

```

Saída:

```bash
-rw-r--r-- 1 joao joao 0 abr 30 14:00 texto.txt

```
#### Explicação dos campos de permissão:

| Posição | Significado | Descrição |
|---------|-------------|-----------|
| 1º caractere | Tipo de arquivo | `-` (arquivo), `d` (diretório), `c`, `b`, `s`, `p` |
| 2-4 | Permissões do usuário | `rwx` (leitura, escrita, execução) |
| 5-7 | Permissões do grupo | `r--` (somente leitura, por exemplo) |
| 8-10 | Permissões de outros | `r--` (idem) |

### Comando chmod – Alterar permissões

### Modo Octal

| Valor | Permissão | Significado |
|-------|-----------|-------------|
| `4` | `r` | Leitura |
| `2` | `w` | Escrita |
| `1` | `x` | Execução |
| `0` | `-` | Sem permissão |

### Modo Simbólico
| Símbolo | Descrição | Exemplo |
|--------|-----------|---------|
| `u` | Usuário | `u-x` → remove execução do usuário |
| `g` | Grupo | `g+x` → adiciona execução ao grupo |
| `o` | Outros | `o+r` → adiciona leitura a outros |
| `a` | Todos (u, g, o) | `a-w` → remove escrita de todos |

| Operador | Função | Exemplo |
|----------|--------|---------|
| `+` | Adiciona permissão | `g+x` |
| `-` | Remove permissão | `u-w` |
| `=` | Define somente a permissão informada | `u=rwx,g=rw,o=x` |

### Comando chown – Alterar dono e grupo

| Sintaxe | Descrição | Exemplo |
|--------|-----------|---------|
| `chown novo_usuario arquivo` | Altera o dono | `chown jonathan relatorio.txt` |
| `chown :novo_grupo arquivo` | Altera apenas o grupo | `chown :cpd relatorio.txt` |
| `chown usuario:grupo arquivo` | Altera dono e grupo | `chown jonathan:cpd relatorio.txt` |

```
Precisa ser root. O novo dono deve estar no grupo, senão ocorre erro.
```

### Comando chgrp – Alterar grupo (sem root)

| Sintaxe | Descrição | Exemplo |
|--------|-----------|---------|
| `chgrp grupo arquivo` | Altera grupo do arquivo | `chgrp cpd script.sh` |

```
O usuário deve fazer parte do grupo.
```

## Aula 09 – Shell Script no Linux

### Introdução

Quem usa Linux conhece bem o prompt de comando como o `bash`. O que muita gente não sabe é que o `sh` ou o `bash` têm uma poderosa linguagem de script embutida. Essa linguagem é amplamente usada para facilitar tarefas administrativas e automatizações.

Patrick Volkerding, criador da distribuição Slackware, usa shell script em toda a instalação e configuração da distro.

Você pode usar scripts para:

- Automatizar tarefas diárias
- Efetuar backups automáticos
- Procurar textos
- Criar formatações
- E muito mais

---

## Interpretadores de Comandos

Interpretadores de comandos (shells) fazem a ponte entre o usuário e o sistema. Usaremos o `bash`, pois é mais completo que o `sh`. Scripts em shell não precisam ser compilados, basta:

1. Criar um arquivo de texto com comandos
2. Iniciar com a linha `#!/bin/bash`
3. Tornar o arquivo executável com `chmod`

---

### Exemplo de Script: "Alo Mundo"

#### Passo a passo:

1. Abra o editor (ex: `vi`)
2. Pressione `Esc + A` para editar
3. Digite `#!/bin/bash`
4. (Boa prática) limpe a tela com `clear`
5. Digite os comandos do script
6. Grave com `:w`, nomeie com `.sh`
7. Saia com `:q!`
8. Torne executável: `chmod +x <nome do script>`
9. Execute: `./<nome do script>`

---

### Comando `echo`

O `echo` exibe strings na saída padrão ou arquivos.

```bash
echo [opções] string
```
| Comando               | Efeito                                      |
|-----------------------|---------------------------------------------|
| `echo`                | Promove salto de linha                     |
| `echo "Alo mundo"`    | Mostra "Alo mundo"                         |
| `echo -e "Alo \bmundo"` | Mostra "Alomundo" (remove espaço)         |
| `echo -e "Alo \nmundo"` | Mostra em linhas separadas                |
| `echo -n "Alo mundo"`  | Mostra "Alo mundo" sem nova linha         |

### Variáveis em Shell Script
Variáveis armazenam dados como texto, números, comandos, etc. No bash, são acessadas com $.

#### 1° Caso – Conteúdo fixo
```bash
nome='Clara'
echo $nome
```
#### 2° Caso – Usando outra variável
```bash
nome="Clara"
dia="10"
mes="Agosto"
echo "$nome faz aniversário em $dia/$mes"
```
#### 3° Caso – Executando comandos
```bash
usuario=`whoami`
caminho=`pwd`
echo "Usuário: $usuario - Caminho: $caminho"
```

### Comando read
Permite entrada de dados do usuário.
```bash
read [parametros] <variável>
```
#### Parâmetros do read
| Parâmetro | Função                                                                 |
|-----------|------------------------------------------------------------------------|
| ` -p`      | Exibe uma mensagem antes da entrada do usuário (prompt).              |
| `-t`      | Define um tempo limite (em segundos) para o usuário digitar algo.     |
| `-s`      | Oculta o que está sendo digitado (ideal para senhas).                 |
| `-n`      | Limita o número de caracteres que podem ser digitados.                |


#### Exemplo de Script
```bash
read -t 5 -p "Login: " login
read -s -p "Senha: " senha
echo
read -n 7 -p "Código (máx. 7 dígitos): " codigo
echo
echo "Login: $login"
echo "Senha: [oculta]"
echo "Código: $codigo"

```

## Aula 10 – Controle de Fluxo com if no Shell Script

### Introdução ao `if`
O if no shell script permite avaliar uma condição e executar um bloco de comandos conforme o resultado (verdadeiro ou falso).

```bash
if [ condição ]; then
  # comandos se a condição for verdadeira
fi
```
####  Exemplo: Verificação de Nome

```bash
#!/bin/bash

# Solicita o nome do usuário
read -p "Digite seu nome: " nome

# Verifica se o nome foi fornecido
if [ -z "$nome" ]; then
  echo "Erro: Nome não fornecido."
elif [ "$nome" == "Dora" ]; then
  echo "Olá, professora!"
else
  echo "Olá, aluno(a)!"
fi
```

### Operadores Numéricos e Lógicos

| Tipo                | Operador | Significado                      |
|---------------------|----------|----------------------------------|
| Comparação Numérica | `-lt`    | Menor que (*Less Than*)          |
| Comparação Numérica | `-gt`    | Maior que (*Greater Than*)       |
| Comparação Numérica | `-le`    | Menor ou igual (*Less or Equal*) |
| Comparação Numérica | `-ge`    | Maior ou igual (*Greater Equal*) |
| Comparação Numérica | `-eq`    | Igual (*Equal*)                  |
| Comparação Numérica | `-ne`    | Diferente (*Not Equal*)          |
| Operador Lógico     | `!`      | NÃO lógico (*NOT*)               |
| Operador Lógico     | `&&`     | E lógico (*AND*)                 |
| Operador Lógico     | `II`     | OU lógico (*OR*)                 |


### Cálculo com bc: Exemplo de IMC
O bash não tem suporte nativo para ponto flutuante, por isso usamos o comando externo bc para fazer divisões decimais.

```bash
#!/bin/bash

# Solicita peso e altura
read -p "Digite o peso (kg): " peso
read -p "Digite a altura (m): " altura

# Cálculo do IMC com duas casas decimais
imc=$(echo "scale=2; $peso/($altura*$altura)" | bc)

echo "Seu IMC é: $imc"

```

| Termo     | Explicação                                                |
| --------- | --------------------------------------------------------- |
| `scale=2` | Define que queremos 2 casas decimais no resultado         |
| `bc`      | Comando de calculadora básica para operações com precisão |

###  Transformando número decimal em inteiro com sed
O sed é um editor de texto que também pode ser usado para remover caracteres, como o ponto decimal.

```bash
numero="3.14"
numero_inteiro=$(echo $numero | sed 's/\.//')

echo $numero_inteiro  # Saída: 314
```
#### O que significa sed 's/\.//'

| Parte do comando | Significado                           |
| ---------------- | ------------------------------------- |
| `s`              | Indica substituição                   |
| `\.`             | Representa o ponto literal            |
| `//`             | Substitui o ponto por "nada" (remove) |

### Testes com Arquivos

| Teste        | Significado                 |
| ------------ | --------------------------- |
| `-e arquivo` | Testa se o arquivo existe   |
| `-f arquivo` | Testa se é um arquivo comum |
| `-d arquivo` | Testa se é um diretório     |

```bash
read -p "Digite o nome do arquivo: " arquivo

if [ -e "$arquivo" ]; then
  echo "O arquivo existe!"
  if [ -f "$arquivo" ]; then
    echo "É um arquivo comum."
  elif [ -d "$arquivo" ]; then
    echo "É um diretório."
  fi
else
  echo "Arquivo não encontrado."
fi

```

### Estrutura `case` – Mais Limpa para Várias Opções

A estrutura case é ideal quando você precisa tomar decisões com várias alternativas:

```bash
read -p "Escolha uma opção (a/b/c): " opcao

case $opcao in
  a) echo "Você escolheu A";;
  b) echo "Você escolheu B";;
  c) echo "Você escolheu C";;
  *) echo "Opção inválida";;
esac
```

















