# santander-bootcamp-fullstack-developer

## Lógica de programação essencial
### Entendendo o que é Lógica

### O que são algoritmos e pseudocódigo
- `Algoritmo` é uma sequência de passos que resolve um problema
- [Jogo de lógica: O aventureiro Minecraft](https://studio.code.org/s/mc/lessons/1/levels/1)
- `Pseudocódigo` é u ma forma genérica de escrever um algoritmo, utilizando uma liguagem simples.
- [Jogo de pseudocódigo: Lobo, ovelha e o repolho](https://www.proprofsgames.com/wolf-sheep-and-cabbage/)
- [Atividade: Jogo Pinguins numa fria](https://rachacuca.com.br/jogos/pinguins-numa-fria/)

### Aprendendo fluxograma, variáveis e constantes
- `Fluxograma` é uma ferramenta utilizada para representar graficamente o algoritmo.
- `Variável` é um espaço na memória do compoutador destinado a um dado que é alterado durante a execução do algoritmo.
- `Constantes` são valores imutáveis e não são alterados durante a vida útil do programa.
- [flowgorithm](http://www.flowgorithm.org/download/)

### Tomadas de decisões e expressões
- Operadores aritméticos: `+ - * / ^ %`
- Exemplos de expressões literais:
```
nome = "José Silva"
nome <- "José Silva"
media = (nota1 + nota2 + nota3) / 3
```
- Exemplos de expressões aritméticas:
```
A = 2
B = A + 3
C = A + B
```
- Operadores relacionais: `> >= < <= == !=`.
- 

### Como utilizar a concatenação
- `Concatenação` é a união de duas strings.

### Aprenda como utilizar uma estrutura de repetição

### O que são linguagens de programação?
- Linguagem de programação é uma escrita forma que especifica um conjunto de instruções e regras usadas para gerar programa.
- Portugol é uma pseudolinguagem que permite ao programador pensar no problema em si e não no equipamento que irá wxecutar o algoritmo.
- [Portigol Studio](https://github.com/UNIVALI-LITE/Portugol-Studio/releases)

### Aprenda a utilizar desvios condicionais e boas práticas em programação
- a palavra reservada `se` no portugal é utilizada para testar uma condição. Ex:
```
se(numero > 5) {

}
```
- a palavra reservada `senao` é utilizada em conjunto com a palavra reservada `se`. E somente é acessada quando a condição é `falsa`. Ex:
```
se(media >= 7) {
  escreva("Aprovado!")
}
senao {
  escreva("Reprovado!")
}
```
- comentário são criados utilizando `//seu comentário`
- a palavra chave `caso` é utilizada para realizar diversas comparações e não permite operadores lógicos. Ex:
```
escolha (menu) {
  caso 1:
    escreva("Opção 1")
    pare

  caso 2:
    escreva("Opção 2")
    pare

  caso 3:
    escreva("Opção 3")
    pare

  caso contrario:
    escreva("Você deve scolher a opção 1, 2 ou 3")
}
```

### Trabalhando com laços de repetição em Portugol
- Na programação `Laço de repetição` é uma estrutura que permite executar mais de uma vez o mesmo comando ou conjunto de comando, de acordo com uma condição ou com um contador. Ex:
```
inteiro contador, limite
contador = 0
limite = 10
faca {
  escreva(contador)
  contador++
} enquanto (contador <= limite)
```

### Aplicação prática com matrizes e vetores
- `Matriz` é uma coleção de variáveis de mesmo tipo, acessíveis com um único nome e armazenados continuamente na memória. Com diversas dimensões (linhas e colunas)
- `Vetor` é uma matriz que possui somente uma dimenção.

## Conceitos e melhores práticas com bancos de dados PostgreSQL

### Fundamentos de banco de dados
- **Modelo Relacional** é um modelo de dados representativo, onde as informações são organizadas em tabelas. A tabela é forma por linhas e colunas, onde as linhas são os dados e as colunas são os atributos.
- **Chave primária** é uma coluna na tabela para identificar um valor único e é usado como índice para relacionar tabelas.
- **Chave estrangeira** é uma coluna utilizada para criar um relacionamento em outras tabelas. Essa coluna possui um identificador (id) para localizar as informações em uma outra tabela.
- PostgreSQL
- [Documentação completa](https://www.postgresql.org/docs/13/)

### O que é o arquivo postgresql.conf
- `postgresql.conf` é o arquivo que possui todas as configurações do banco de dados.
- a view `pg_settings`, acessada por dentro do banco de dados possui as configurações atuais do banco de dados. Alterações no arquivo `postgresql.conf` somente poderão ser acessadas após a reinicialização do servidor. Exemplo de comandos:
```sql
SELECT name, setting FROM pg_settings;
```
- o arquivo `postgresql.conf` está localizado no diretório **PGDATA** que é definido durante a instalação. Na imagem docker **postgres:11** está localizado em `/var/lib/postgresql/data/postgresql.conf`.
- Configurações de conexão:
  - `LISTEN_ADDRESS`: enredeços TCP/IP que o servidor irá escutar/liberar conexões.
  - `PORT`: A porta TCP que o servidor PostgreSQL vai ouvir. O padrão é 5432.
  - `MAX_CONNECTIONS`: número máximo de conexões simultâneas.
  - `SUPERUSER_RESERVED_CONNECTIONS`: número de conexões (slots) reservadas para conexão do banco de dados de super usuários.
- Configurações de autenticação:
  - `AUTHENTICATION_TIMEOUT`: tempo máximo em segundos para cliente conseguir uma conexão com o servidor.
  - `PASSWORD_ENCRYPTION`: algoritmo usado para criptografia das senhas dos usuários do banco de dados.
  - `SSL`: habilita a conexão criptografada por ssl (somente se o PostgreSQL fio compilado com suporte SSL).
- Configurações de memória:
  - `SHARED_BUFFERS`: tamanho da memória compartilhada do servidor PostgreSQL para chache/buffer de tabelas, índices e damais relações.
  - `WORK_MEM`: tamanho de memória para operações de agrupamento e ordenação (**ORDER BY, DISTINCT, MERGE JOINS**)
  - `MAINTENANCW_WORK_MEM`: tamanho da memória para operações como VACUUM, INDEX, ALTER TABLE.
- o arquivo `pg_hba.conf` é responsávelpelo controle de autenticação no servidor PostgreSQL. Na imagem docker **postgres:11** está localizado em `/var/lib/postgresql/data/pg_hba.conf`. Ex:
```
local     database user auth-method    [auth-options]
host      database user address   auth-method  [auth-options]
hostssl     database user address   auth-method  [auth-options]
hostnossl     database user address   auth-method  [auth-options]
host     database user ip-address  IP-mask  auth-method  [auth-options]
hostssl     database user ip-address  IP-mask  auth-method  [auth-options]
hostnossl     database user ip-address  IP-mask  auth-method  [auth-options]
```
- Métodos de autenticação:
  - `TRUST`: conexão sem requisição de senha
  - `REJECT`: rejeita conexões
  - `MD5`: cripstografia md5
  - `PASSWORD`: senha sem criptografia
  - `GSS`: generic security service apllication program interface
  - `SSPI`: security support provider interface (Windows)
  - `KRB5`: Kerberos V5
  - `IDENT`: utiliza o usuário do sistema operacional do cliente via ident server
  - `PEER`: utiliza o usuário do sistema operacional do cliente
  - `LDAP`: ldap server
  - `RADIUS`: radius server
  - `CERT`: autenticação via certificado ssl do cliente
  - `PAM`: pluggable authentication modules. O usuário precisa estar no banco
- o arquivo `pg_ident.conf` é responsavél por mapear os usuários do sistema operacional com os usuários do banco de dados. Ele está localizado no diretório PGDATA. A opção `ident` deve ser utilizada no arquivo `pg_hba.conf`. Exemplo:
```
# MAPNAME       SYSTEM-USERNAME PG-USERNAME
diretoria       daniel          pg_diretoria
comercial       tiburcio        pg_diretoria
comercial       valdeci         pg_comercial
```
- Comandos administrativos:
  - Ubuntu:
    - pg_lsclusters: lista os cluster PostgreSQL
    - pg_createcluster <version> <cluster name>: cria um novo cluster PostgreSQL
    - pg_dropcluster <verions> <cluster>: apaga um cluster PostgreSQL
    - pg_ctlcluster <verison> <cluster> <action>: start, stop, status, restar de clusters PostgreSQL
- `Cluster` é uma coleção de banco de dados que compartilham as mesmas configurações (arquivos de configuração) do PostgreSQL e dos Sistema operacional (porta, listen_address, etc). Ele pode conter um ou mais bancos de dados.
- `Bancos de dados` é um conjunto de schemas com seus objetos/relações (tabelas, funções, views, etc)
- `Schema` é um conjunto de objetos e relações (tabelas, funções, views, etc). Alguns bancos de dados, como o Mysql, interpretam schemas como bancos de dados.

### Conheça a ferramenta PGAdmin
- Verificações para realizar conexão com banco de dados:
  - Liberar acesso ao cluster em `postgresql.conf`
  - Liberar acesso ao cluster para o usuário do banco de dados em `pg_hba.conf`
  - Criar/editar usuários
- Exemplo de conexão com postgresql na linha de comando: `psql -U usuario -h localhost nomeDoBancoDeDados`, onde `usuario` é o usuário, `localhost` é o nome ou ip do servidor e `nomeDoBancoDeDados` é o nome do banco de dados.
- Para adicionar senha no usuário **postgres** padrão faça:
  - conectado no banco de dados execute `ALTER USER postgres PASSWORD '123';`
  - acesse o arquivo `pg_hba.conf` e na seção de conexão local altere o método de autenticação de `PEER` para `MD5`.
  - reinicie o cluster para as alterações terem efeito: `pg_ctlcluster 11 aula reload`
- criando banco de dados no pgadmin:
  - selecione uma banco de dados existente e acesse `Tools > Query Tool` e crie um banco de dado com `CREATE DATABASE auladb;`
  - atualize a visualização dos bancos de dados no menu lateral clicando com o `botão direito do mouse` > `Refresh ...`
  - selecione o banco de dados criado, acesse `Tools > Query Tool` para realizar os comando no banco de dados criado.
