
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

Diretório raiz NÃO É SINÔNIMO de diretório nativo, diretório nativo é de onde o usuário veio e diretório raiz é o diretório que contem todos os diretório, é representado por ´/` 
 

















