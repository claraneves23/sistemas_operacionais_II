
# Sistemas Operacionais II 🐧

Disciplina ministrada pela professora Dorotea Garcia

Lattes:  http://lattes.cnpq.br/8453243844263956
## Aula 01

### Conceitos Fundamentais de Sistemas Operacionais e Linux

#### Sistema Operacional

O **sistema operacional (SO)** é um conjunto de programas que atua como intermediário entre o usuário e o hardware. Sua função principal é receber comandos do usuário e garantir que o hardware os execute corretamente.

- **Função principal:** Meio de campo entre hardware e usuário.
- **Exemplo de ambiente computacional:**  
  - Hardware + Sistema Operacional + Usuário

#### Linux

O **Linux** é um sistema operacional de código aberto criado por **Linus Torvalds** em **1991**. É gratuito e compatível com o padrão **POSIX**, o mesmo adotado pelo Unix, o que facilita sua **portabilidade** para sistemas compatíveis.

- **Características do Linux:**
  - Open source (código aberto)
  - Gratuito
  - Compatível com Unix (via POSIX)
  - Portável para qualquer sistema compatível com POSIX
  - Mantido por uma comunidade ativa
  - Frequentemente atualizado, com foco em **estabilidade**, **desempenho** e **segurança**

#### Interpretador de Comandos (Shell)

O **shell** é o programa responsável por interpretar comandos fornecidos pelo usuário ou por outros programas, e repassá-los ao sistema operacional (mais especificamente ao **kernel**).

> O shell é a principal ligação entre o usuário, os programas e o kernel.

- **Modos de operação:**
  - **Interativo:** o usuário digita comandos um a um, e o sistema os executa imediatamente.
  - **Não interativo:** comandos são escritos em um **arquivo script**, permitindo execução automática e criação de **rotinas** ou **automações**.

- **Shells comuns no Linux:**
  - `bash` (mais utilizado)
  - `sh`
  - `csh`
  - `tcsh`


## Aula 02
Linux: Tipos de Usuários e Comandos Básicos

### Tipos de Usuário

- **Admin (root)**: Possui plenos poderes dentro do sistema Linux.
- **Grupo**: Usuários que compartilham características em comum.

### Chaves de Acesso

#### Administrador (root)
```bash
styx login: root
Password: 123456
```

#### Usuário Comum
```bash
styx login: dora
Password: dora
```

### Formação da Chave de Acesso

#### Root
```bash
[root@styx root]#
```
- **root**: Nome do usuário.
- **@styx**: Terminal em uso (identificação).
- **root**: Diretório nativo.
- **#**: Prompt do root.

#### Usuário Comum
```bash
[dora@styx dora]$
```
- **dora**: Nome do usuário.
- **@styx**: Terminal em uso (identificação).
- **dora**: Diretório nativo.
- **$**: Prompt do usuário comum.

### Estrutura de Diretórios no Linux
```bash
/ (diretório raiz)
│
├── root (diretório nativo do administrador)
│
└── home (diretório nativo do usuário)
    ├── dora
```

### Sair do Ambiente

#### Usuário Comum
```bash
logout
exit
CTRL+D
```

#### Administrador (root)
```bash
shutdown -h now  # Desliga o ambiente para todos os usuários.
shutdown -h -t 60  # Envia um aviso e desliga em 60 segundos.
halt  # Desliga imediatamente.
shutdown -r -t 60  # Reinicia o sistema em 60 segundos.
reboot  # Reinicia o sistema imediatamente.
```

### Tipos de Arquivos no Linux

- Arquivos que começam com `.` são ocultos.
- **.txt**: Arquivo de texto.
- **.sh**: Script interpretado pelo shell (`/bin/sh`).
- **.log**: Registro de logs de programas.
- **.gz**: Arquivo compactado pelo utilitário gzip.
- **.aspl**: Página de internet em formato hipertexto.

### Comandos Úteis

- **Visualizar o conteúdo do diretório atual:**
  ```bash
  ls
  ```

- **Acessar o diretório nativo:**
  ```bash
  cd ~
  ```

- **Acessar o diretório root (somente para administradores):**
  ```bash
  cd /
  ```

### FHS (Hierarquia Padrão do Sistema de Arquivos)

O FHS define a estrutura de diretórios do Linux, garantindo organização e padronização do sistema.

## Aula 03

### Explorando o comando `ls`

- **Atenção** 🚨

*Diretório raíz NÃO É SINÔNIMO de diretório nativo, diretório nativo é de onde o usuário veio e diretório raiz é o diretório que contem todos os diretórios, é representado por ´/`* 

### Identificando o conteúdo pelas cores padrão do LINUX

- 🔵 : diretório
- ⚪ : arquivos
- 🔴 : arquivo compactado
- 🟢(verde água) : link
  
<p align="center">
  <img src= "https://github.com/claraneves23/sistemas_operacionais_II/blob/main/Captura%20de%20tela%202025-03-11%20184951.png">
</p>

*dica: o comando `clear`limpa a tela.*

### Ls e a utilização de parâmetros

- `ls` ou `ls .`: para exibir o diretório corrente.
- `ls ..`: listar o conteúdo do diretório anterior.
- `ls ~`: ver o diretório nativo sem se deslocar do diretório corrente.
- `ls -l`: listar os arquivos pelo formato longo
- `ls -l | more`: vizualizar o formato longo sem o scroll
  
  *dica: para interromper use `ctrl +c`*
  
- `ls -a`: exibir arquivos ocultos.
- `ls -F`: exibição dos items com símbolos
  ```
  -- arquivos simples (sem símbolo)
  -- diretórios (com /)
  -- arquivos linkados (com @)
  ```
- `ls -t`: listar arquivos por ordem de data de modificação. Arquivos modificados recentemente são exibidos primeiro.
- `ls -1`: fazer com que os arquivos do diretório sejam listados por linha, um em cada linha.

### Interpretando as informações sobre arquivos em LINUX
<p align="center">
  <img src= "https://github.com/claraneves23/sistemas_operacionais_II/blob/main/Captura%20de%20tela%202025-03-11%20191520.png">
</p>

- 1° coluna: nível de permissão de quem possi acesso ao item da linha, sendo o primeiro caractere referente ao formato(arquivo, diretório, link e etc), e os outros nove (3 grupos de 3) referentes, em ordem esquerda-direita, ao usuário, o grupo do usuário e outros. Sendo o caractere "r" a permissão de leitura, o "w" de escrita e o "x" de execução.
  
- 2° coluna: quantidade de usuários que possuem acesso.

- 3° coluna: usuário que gerou o arquivo/diretório.

- 4° coluna: grupo que usa o arquivo/diretório.

 - 5° coluna: tamanho em bytes do arquivo.

 - 6° coluna: data de criação do arquivo.

 - 7° coluna: horário de criação do arquivo.

 - 8° coluna: nome do arquivo

### Criar arquivo vazio

` touch <nome_do_arquivo>`

### Metacaracteres
- `*`: usado para substituir um conjunto de caracteres.
```
[root@styx home]# ls texto**
texto123 texto2 texto34 textoabc texton

[root@styx home]# ls *texto
13texto  1texto atexto
```
- `?`: usado para substituir um único caracter.
```
[root@styx home]# ls texto?
texton

[root@styx home]# ls *texto???
texto123 textoabc
```
- `[]`: usados para gerar uma lista de caracteres.
```
[root@styx home]# ls [1a3]texto
1texto atexto

[root@styx home]# ls texto[123n]
texto2  texton
```
- `{}`: usados para gerar uma sequência de caracteres separados por vírgula.
```
[root@styx home]# ls {1,a,b,13}texto
ls: btexto: arquivo ou diretório não encontrado
13texto 1texto atexto

[root@styx home]# ls texto{1,2,n,124,abc}
ls: texto1: arquivo ou diretório não encontrado
ls: texto124: arquivo ou diretório não encontrado
texto2 textoabc texton
```

## Aula 04

### Explorando os diretórios no Linux

- cd: serve para acessar e e mudar de diretório corrente.
- cd ..: volta para o diretório pai.
- cd~: volta para o diretório nativo.
- cd-: volta para o diretório corrente que estava antes.

Então pensemos num cenário, imagine que você gostaria de ir para o diretório home, estando no diretório root, como devemos proceder:​
```
[root@styx root]# cd /home
[root@styx home]# 
```
```
/ (diretório raiz)
│
├── root 
│
└── home 
```
Logo, é possível entender que:
- cd /(caminho): parte do raíz até o último diretório passado como referência.

Para acessar um diretório que está hierarquicamente exatamente um nível abaixo ao seu podemos:
- 1° modo: usando o conceito anterior indo da raíz até o destino desejado, temos:
```
[root@styx home]# cd /home/fatec
[root@styx fatec]#

```
- 2° modo: podemos usar o nome do diretório que está a um nível abaixo:
```
[root@styx home]# cd fatec
[root@styx fatec]#
```
```bash
/ (diretório raiz)
│
└── home 
    ├── fatec
```
Já para um arquivo que não está exatamente abaixo:
```bash
/ (diretório raiz)
│
└── home 
    ├── fatec
         ├── CPD
```
- 1° modo:
```
[root@styx home]# cd /home/fatec/CPD
[root@styx CPD]#
```
- 2° modo:
 ```
[root@styx home]# cd fatec/CPD
[root@styx CPD]#
```
- cd..: para ir para o diretório que está um nível acima do seu.
- cd~: para ir para o diretório nativo.
- cd-: retorna para o último diretório acessado.
  
#### Atenção 🚨
- Manipular arquivos somente no home.
  
#### Comando Tree

- tree: auxilia na vizualização da estrutura FHS.
```
[root@styx fatec]# tree
.
|-- CPD
|-- lab2
|-- prova
|-- teste
'-- ver -> prova
1 directory, 4 files
[root@styx fatec]# 
```
- tree -d: para visualizar apenas os diretórios da árvore.

#### Criar diretórios
- mkdir <nome_do_diretorio>: cria um diretório.
- mkdir -p <dir_1>/<dir_2>/<dir_3>: cria uma estrutura em árvore
```
[root@styx home]# mkdir -p lista/atividade/tarefa

/ (diretório raiz)
│
└── home 
    ├── lista
         ├── atividade
                ├── tarefa
```
Para criar diretórios todos no mesmo nível:
- mkdir dir_1 dir_2 dir_3
- mkdir dir_{1,2,3}

#### Apagar um diretório

Para apagar um diretório é necessário obedecer duas condições iniciais:
- O diretório que será apagado deve estar vazio.
- Para apagar o diretório é necessário que esteja pelo menos um nível acima.

Para apagar diretórios:
- rmdir dir_1 dir_2 dir_3
- rmdir dir_{1,2,3}

Para apagar a estrutura:
- rmdir -p <dir_1>/<dir_2>/<dir_3>

**Atenção** 🚨

Para apagar um diretório de forma forçada (não importa se não está vazio):
- rm -rf <dir_1>

### PWD
O comando `pwd` mostra o caminho do diretório que você se encontra até a raíz.
```
[root@styx tarefa]# pwd
/home/lista/atividade/tarefa
[root@styx tarefa]#
```
## Aula 05
### Comandos de Manipulação de Arquivos no Linux

#### **Copiando Arquivos**
- **Sintaxe:** `[ prompt ]# cp <origem> <destino>`
- Exemplo: Copiar `version` de `/proc` para `/home/sistop`
- Diferentes variações do comando podem ser utilizadas.
- O comando `cp` também permite copiar e renomear simultaneamente.

##### **Cópia com Segurança**
- Exibir aviso antes de sobrescrever: `cp -i`
- Copiar mantendo backup do arquivo existente: `cp -b`

##### **Copiando Múltiplos Arquivos**
- Copiar vários arquivos para um único destino.
- Utilizar metacaracteres para selecionar arquivos.

---

#### **Movendo e Renomeando Arquivos**
- **Sintaxe:** `[ prompt ]# mv <origem> <destino>`
- O comando `mv` permite:
  - Mover arquivos entre diretórios.
  - Renomear arquivos.
  - Mover e renomear simultaneamente.

**Exemplos:**
1. Mover `versao` para o diretório root: `mv versao /root/`
2. Renomear `version` para `teste`: `mv version teste`
3. Mover e renomear `version~` para `/root/novo`: `mv version~ /root/novo`

---

#### **Removendo Arquivos**
- **Sintaxe:** `[ prompt ]# rm [parâmetros] <arquivo>`
- Exemplo: Remover `teste` com confirmação: `rm -i teste`
- Remover arquivos específicos:
  - Excluir todos com "tex" no nome e os que começam com "v": `rm *tex* v*`
  
#### **Parâmetros Importantes**
- `-i` → Confirmação antes de apagar.
- `-r` → Remover diretórios recursivamente.
- `-f` → Forçar remoção sem confirmação.

---

#### **Visualizando Arquivos**
- **Sintaxe:** `[ prompt ]# cat <caminho/arquivo>`
- Exemplo: Ver o conteúdo de `passwd`: `cat /etc/passwd`
- Para arquivos grandes, usar `cat | more` para navegação controlada.

**Exemplo de uso do pipe (`|`)**  
Exibir `group` com paginação:  
```bash
cat /etc/group | more
```
## Aula 07  
Comandos Úteis e Gerenciamento no Linux  

### Comandos Básicos  

#### Calendário e Data/Hora  

| Comando | Descrição | Exemplo |  
|---------|-----------|---------|  
| `cal`   | Exibe calendário do mês corrente | `cal` |  
| `cal MM AAAA` | Mostra calendário de um mês/ano específico | `cal 08 2023` |  
| `date`  | Exibe data e hora atuais | `date` |  
| `date MMDDhhmmAAAA` | Atualiza data/hora (root) | `date 082711412023` |  
| `hwclock -w` | Sincroniza hardware clock | `hwclock -w` |  

**Exemplo de formatação de data:**  
```  
date "+%d/%m/%Y %H:%M"   Saída: 27/08/2023 11:41  
```

#### Impressão e Informações do Sistema

| Comando      | Função                          | Exemplo                     |
|--------------|---------------------------------|-----------------------------|
| `lpr`        | Envia arquivo para impressora   | `lpr /etc/passwd`           |
| `lpr -#3`    | Imprime 3 cópias                | `lpr -#3 arquivo.txt`       |
| `finger`     | Exibe info de usuários          | `finger root`               |
| `history`    | Lista comandos executados       | `history`                   |
| `history -c` | Limpa histórico                 | `history -c`                |
| `uptime`     | Tempo de atividade do sistema   | `uptime`                    |

**Saída do `uptime`:
```
20:02:38 up 58 min, 2 users, load average: 0.00, 0.00, 0.00
```

## Monitoramento do Sistema

### Memória e Processos

| Comando | Descrição                          |
|---------|-----------------------------------|
| `free`  | Exibe uso de memória RAM e swap   |
| `top`   | Monitora processos em tempo real  |

### Editor de Texto vi

| Comando           | Ação                          |
|-------------------|-------------------------------|
| `vi arquivo.txt`  | Abre/cria arquivo no vi       |
| `Esc + a`         | Entra no modo INSERT          |
| `Esc + dd`        | Deleta linha inteira          |
| `Esc + :wq`       | Salva e sai                   |
| `Esc + :q!`       | Sai sem salvar                |

### Links Simbólicos

| Comando  | Função                     | Exemplo                                |
|----------|----------------------------|----------------------------------------|
| `ln -s`  | Cria link simbólico        | `ln -s /caminho/origem /caminho/link` |

