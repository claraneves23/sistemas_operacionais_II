
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

# Aula 03

## Explorando o comando `ls`

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














