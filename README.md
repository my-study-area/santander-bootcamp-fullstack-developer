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
### Configuração do ambiente docker
- Clone o projeto:
```bash
git clone https://github.com/my-study-area/santander-bootcamp-fullstack-developer.git
```
- Entre no diretório:
```bash
cd santander-bootcamp-fullstack-developer
```
- Inicialize os container PostgreSQL e PGAdmin4
```bash
docker-compose up -d
```
- Para acessar o PostgreSQL via linha de comando execute:
```bash
docker-compose exec db psql -U user aula
```
- Para acessar o PGAdmin acesse [http://localhost:8080/](http://localhost:8080/) utilizando o seguinte usuário e senha:

|Usuário           |Senha|
|------------------|-----|
|email@email.com   |123  |

- Para desligar os containers execute:
```bash
docker-compose down
```

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

### Como administrar usuários no banco de dados
- Roles, users e grupos de usuários são contas/perfis de atuação de um banco de dados.
- Nas versões anteriores do PostgreSQL 8.1, usuários e roles tinham comportamentos diferentes. Atualmente roles e user são aliases.
- Exemplos de criação de Roles:
```sql
CREATE ROLE administradores
  CREATEDB
  CREATEROLE
  INHERIT
  NOLOGIN
  REPLICATION
  BYPASSRLS
  CONNECTION LIMIT -1;

CREATE ROLE professores
  NOCREATEDB
  NOCREATEROLE
  INHERIT
  NOLOGIN
  NOBYPASSRLS
  CONNECTION LIMIT 10;

CREATE ROLE alunos
  NOCREATEDB
  NOCREATEROLE
  INHERIT
  NOLOGIN
  NOBYPASSRLS
  CONNECTION LIMIT 90;
```
- Associação entre roles:
  - Quando uma role assume permissões de outra role é necessário a opção `INHERIT`.
  - `IN ROLE`: passa a pertencer a role informada
  - `ROLE`: a role informada passa a pertencer a nova role
  - Após a criação da role utilize `GRANT [role a ser concidada] TO [role a assumir as permissões]`
- Exemplo de associação entre roles:
```sql
CREATE ROLE professores
  NOCREATEDB
  NOCREATEROLE
  INHERIT
  NOLOGIN
  NOBYPASSRLS
  CONNECTION LIMIT -1;

-- a role daniel passa a assumir as permissões da role professores
CREATE ROLE daniel LOGIN CONNECTION LIMIT 1 PASSWORD '123' IN ROLE professores;

-- a role professores passa a fazer parte da role daniel
-- assumindo suas permissões
CREATE ROLE daniel LOGIN CONNECTION LIMIT 1 PASSWORD '123' ROLE professores;

CREATE ROLE daniel LOGIN CONNECTION LIMIT 1 PASSWORD '123';
GRANT professores TO daniel;
```
- Desassociar membros entre roles:
  - `REVOKE [role que terá suas permissões revogadas]`
  - Exemplo: `REVOKE professores FROM daniel;`
- Alterando uma role:
  - `ALTER role_specification [WITH] option [ ... ]`
- Excluindo uma role:
  - `DROP ROLE role_specification;`
- `\du`: lista todas as roles do banco de dados
- `SELECT * FROM pg_roles;`: lista todas as roles do banco de dados
- Comando usados na prática:
```sql
CREATE ROLE professores NOCREATEDB NOCREATEROLE INHERIT NOLOGIN NOBYPASSRLS CONNECTION LIMIT 10;

DROP ROLE professoresnocreatedb;

SELECT * FROM pg_roles;

ALTER ROLE professores PASSWORD '123';

CREATE ROLE daniel LOGIN PASSWORD '123';

DROP ROLE daniel;

CREATE ROLE daniel LOGIN PASSWORD '123' IN ROLE professores;

CREATE ROLE daniel2 LOGIN PASSWORD '123' ROLE professores;
```
- Adminstrando acessos (GRANT):
  - são privilégios de acesso aos objetos do banco de dados como: tabela, coluna, sequence, database, domain, function, schema e etc.
  - `revoke`: retira permissões da role. Exemplos revagando todas as permissões:
  ```sql
  REVOKE ALL ON ALL TABLES IN SCHEMA [schema] FROM [role];
  REVOKE ALL ON SCHEMA [schema] FROM [role];
  REVOKE ALL ON DATABASE [database] FROM [role];
  ```
  - Comando utilizados na prática:
  ```sql
  CREATE TABLE teste (nome varchar);

  GRANT ALL ON TABLE teste TO professores;

  CREATE ROLE daniel3 LOGIN PASSWORD '123';

  CREATE ROLE daniel4 INHERIT LOGIN PASSWORD '123' IN ROLE professores;

  REVOKE professores FROM daniel4;
  ```
### Objetos e comandos do banco de dados
- Database:
  - É o banco de dados
  - Grupo de schemas e seus objetos como tabelas, view, funçõrd e etc.
  - Os schemas e objetos de um banco de dados não podem ser compartilhados
  - Bancos de dados compartilham apenas usuários/roles e configurações de cluster PostgreSQL.
- Schemas:
  - É um grupo de objetos, como tabelas, types, views, funções entre outros
  - É possível relacionar objetos entre diversos schemas. Por exemplo: schema public e schema curso podem ter tabelas com o mesmo nome (teste por exemplo) relacionando-se entre si.
- Objetos:
  - São as tabelas, views, funções, types, sequences, entre outros pertencentes aos schemas.
- Melhores práticas:
  - utilizar `IF NOT EXISTS`. Ex: 
    - `CREATE SCHEMA IF NOT EXISTS schema_name [AUTORIZATION role_specification]`
    - `DROP SCHEMA IF EXISTS [nome]`
- Tabelas, colunas e tipos de dados
  - Tabelas são conjuntos de dados dispostos em colunas e linhas referentes a um objetivo comum.
  - Colunas são consideradas como _"compos de tabela"_ ou atributos da tabela.
  - As linhas de uma tabela são chamadas também de tuplas, e é onde estão contidos os valores, os dados.
- [Tipos de dados](https://www.postgresql.org/docs/11/datatype.html):
  - Numeric 
  - Monetary 
  - Character 
  - Binary Data 
  - Date/Time 
  - Boolean 
  - Enumerated 
  - Geometric 
  - Network Address 
  - Bit String 
  - Text Search 
  - UUID 
  - XML 
  - JSON 
  - Arrays
  - Composite 
  - Range 
  - Domain 
  - Object Identifier 
  - pg_lsn 
  - Pseudo-Type
- DML e DDL
  - DML - Data manipulation Language
    - Linguagem de manipulação de dados
    - INSERT, UPDATE, DELETE, SELECT
    - O SELECT pode ser considerado como DML por uns, DQL (Liguagem de consulta de dados)
  - DDL - Data Definition Language
    - Ligaugem de definição de dados
    - CREATE, ALTER, DROP
  - Comando utilizados na prática:
```sql
CREATE DATABASE financas;

CREATE TABLE IF NOT EXISTS banco (
  numero INTEGER NOT NULL,
  nome VARCHAR(50) NOT NULL,
  ativo BOOLEAN NOT NULL DEFAULT TRUE,
  data_criacao TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (numero)
);

CREATE TABLE IF NOT EXISTS agencia (
  banco_numero INTEGER NOT NULL,
  numero INTEGER NOT NULL,
  nome VARCHAR(80) NOT NULL,
  ativo BOOLEAN NOT NULL DEFAULT TRUE,
  data_criacao TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (banco_numero,numero),
  FOREIGN KEY (banco_numero) REFERENCES banco (numero)
);

CREATE TABLE IF NOT EXISTS cliente (
  numero BIGSERIAL PRIMARY KEY,
  nome VARCHAR(120) NOT NULL,
  email VARCHAR(120) NOT NULL,
  ativo BOOLEAN NOT NULL DEFAULT TRUE,
  data_criacao TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE IF NOT EXISTS conta_corrente (
  banco_numero INTEGER NOT NULL,
  agencia_numero INTEGER NOT NULL,
  numero BIGINT NOT NULL,
  digito SMALLINT NOT NULL,
  cliente_numero BIGINT NOT NULL,
  ativo BOOLEAN NOT NULL DEFAULT TRUE,
  data_criacao TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (banco_numero,agencia_numero,numero, digito,cliente_numero),
  FOREIGN KEY (banco_numero, agencia_numero) REFERENCES agencia (banco_numero,numero)
);

CREATE TABLE IF NOT EXISTS tipo_transacao (
  id SMALLSERIAL PRIMARY KEY,
  nome VARCHAR(50) NOT NULL,
  ativo BOOLEAN NOT NULL DEFAULT TRUE,
  data_criacao TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP
);


CREATE TABLE IF NOT EXISTS cliente_transacoes (
  id BIGSERIAL PRIMARY KEY,
  banco_numero INTEGER NOT NULL,
  agencia_numero INTEGER NOT NULL,
  conta_corrente_numero BIGINT NOT NULL,
  conta_corrente_digito SMALLINT NOT NULL,
  cliente_numero BIGINT NOT NULL,
  tipo_transacao_id SMALLINT NOT NULL,
  valor NUMERIC(15,2) NOT NULL,
  data_criacao TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
  FOREIGN KEY (banco_numero, agencia_numero,conta_corrente_numero,conta_corrente_digito,cliente_numero) 
   REFERENCES conta_corrente (banco_numero,agencia_numero,numero, digito,cliente_numero)	
);
```

### Conheça o DML e o Truncate
- `Idempotência`: propriedade que algumas ações/operações possuem possibilitando-as de serem executadas diversas vezes sem alterar o resultado após a aplicação inicial. Ex: o uso de `IF NOT EXISTS` para criar tabelas.
- SELECT - Idempotência
```sql
-- NÃO É BOA PRÁTICA
-- MELHOR USAR LEFT JOIN
SELECT (campos,)
FROM tabela1
WHERE EXISTS (
  SELECT (campo,)
  FROM tabela2
  WHERE campo1 = valor1
  [AND/OR campoN = valorN]
);
```
- Evite o uso de `SELECT *`
- `INSERT` Idempotência
```sql
INSERT INTO agencia (banco_numero, numero, nome) 
VALUES (341,1,'Centro da Cidade');

-- mal uso:
INSERT INTO agencia (banco_numero, numero, nome) 
SELECT 341,1,'Centro da Cidade'
WHERE NOT EXISTS (
  SELECT banco_numero, numero, nome
  FROM agencia
  WHERE banco_numero = 341 AND numero = 1 AND nome = 'Centro da Cidade'
);

-- bom uso:
INSERT INTO agencia (banco_numero, numero, nome) 
VALUES (341,1,'Centro da Cidade')
ON CONFLICT (banco_numero, numero) DO NOTHING;
```

- `TRUNCATE`: limpa uma tabela
```sql
TRUNCATE [ TABLE ] [ ONLY ] name [ * ] [, ... ]
    [ RESTART IDENTITY | CONTINUE IDENTITY ] [ CASCADE | RESTRICT ]
```
- Comandos utilizados na prática:
```sql
CREATE TABLE IF NOT EXISTS teste (
	id SERIAL PRIMARY KEY,
	nome VARCHAR(50) NOT NULL,
	created_at TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP
);

DROP TABLE IF EXISTS teste;

CREATE TABLE IF NOT EXISTS teste (
	cpf VARCHAR(11) NOT NULL,
	nome VARCHAR(50) NOT NULL,
	created_at TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
	PRIMARY KEY (cpf)
);

INSERT INTO teste (cpf, nome, created_at)
VALUES ('12345678901', 'José Maria', '2019-07-01 23:01:00');

INSERT INTO teste (cpf, nome, created_at)
VALUES ('12345678901', 'José Maria', '2019-07-01 23:01:00')
ON CONFLICT (cpf) DO NOTHING;

UPDATE teste SET nome = 'Pedro Silva' WHERE cpf = '12345678901';

SELECT * FROM teste;
```

### Funções agregadas em PostgreSQL
- AVG
- COUNT (opção: HAVING)
- MAX
- MIN
- SUM
- `SELECT column_name, data_type FROM information_schema.columns WHERE table_name = 'banco';`: mostra as colunas e tipos das colunas de uma tabela do banco de dados.
- Comandos utilizados na prática:
```sql
SELECT numero, nome FROM banco;
SELECT banco_numero, numero, nome FROM agencia;
SELECT numero, nome, email FROM cliente;
SELECT banco_numero, agencia_numero, cliente_numero FROM cliente_transacoes;

SELECT * FROM conta_corrente;

SELECT * FROM information_schema.columns WHERE table_name = 'banco';
SELECT column_name, data_type FROM information_schema.columns WHERE table_name = 'banco';

-- AVG
SELECT * FROM cliente_transacoes;
SELECT AVG(valor) FROM cliente_transacoes;

-- COUNT (opção: HAVING)
SELECT COUNT(numero) FROM cliente;

SELECT COUNT(numero), email 
FROM cliente
WHERE email ILIKE '%GMAIL.COM'
GROUP BY email;

SELECT column_name, data_type FROM information_schema.columns WHERE table_name = 'cliente_transacoes';

SELECT COUNT(id), tipo_transacao_id
FROM cliente_transacoes
GROUP BY tipo_transacao_id;

SELECT COUNT(id), tipo_transacao_id
FROM cliente_transacoes
GROUP BY tipo_transacao_id
HAVING COUNT(id) > 150;

-- MAX
SELECT MAX(numero) FROM cliente;
SELECT MAX(valor) FROM cliente_transacoes;

SELECT MAX(valor), tipo_transacao_id
FROM cliente_transacoes
GROUP BY  tipo_transacao_id;

-- MIN
SELECT MIN(numero) FROM cliente;
SELECT MIN(valor) FROM cliente_transacoes;

SELECT MIN(valor), tipo_transacao_id
FROM cliente_transacoes
GROUP BY  tipo_transacao_id;

-- SUM
SELECT SUM(valor) FROM cliente_transacoes;

SELECT SUM(valor) 
FROM cliente_transacoes
GROUP BY tipo_transacao_id
ORDER BY tipo_transacao_id ASC;

SELECT SUM(valor) 
FROM cliente_transacoes
GROUP BY tipo_transacao_id
ORDER BY tipo_transacao_id DESC;
```

### Trabalhando com JOINs
- JOIN (INNER)
- LEFT JOIN (OUTER)
- FULL JOIN (FULL OUTER JOIN)
- CROSS JOIN

- Comandos utilizados na prática:
```sql
SELECT numero, nome FROM banco;
SELECT banco_numero, numero, nome FROM agencia;
SELECT numero, nome FROM cliente;

SELECT banco_numero, agencia_numero, numero, digito, cliente_numero
FROM conta_corrente;

SELECT id, nome FROM tipo_transacao;
SELECT banco_numero, agencia_numero, conta_corrente_numero, conta_corrente_digito, cliente_numero
FROM cliente_transacoes;

SELECT COUNT(1) FROM banco; --151
SELECT COUNT(1) FROM agencia; --296

-- 296
SELECT banco.numero, banco.nome, agencia.numero, agencia.nome
FROM banco
JOIN agencia ON agencia.banco_numero = banco.numero;

-- total de bancos com distinct
SELECT COUNT(distinct banco.numero)
FROM banco
JOIN agencia ON agencia.banco_numero = banco.numero;

-- total de bancos com group by
SELECT banco.numero
FROM banco
JOIN agencia ON agencia.banco_numero = banco.numero
GROUP BY banco.numero;

SELECT banco.numero, banco.nome, agencia.numero, agencia.nome
FROM banco
LEFT JOIN agencia ON agencia.banco_numero = banco.numero;

SELECT banco.numero, banco.nome, agencia.numero, agencia.nome
FROM agencia
RIGHT JOIN banco ON agencia.banco_numero = banco.numero;

SELECT banco.numero, banco.nome, agencia.numero, agencia.nome
FROM agencia
LEFT JOIN banco ON agencia.banco_numero = banco.numero;

SELECT banco.numero, banco.nome, agencia.numero, agencia.nome
FROM banco
FULL JOIN agencia ON agencia.banco_numero = banco.numero;

CREATE TABLE IF NOT EXISTS teste_a (id serial primary key, valor VARCHAR(10));
CREATE TABLE IF NOT EXISTS teste_b (id serial primary key, valor VARCHAR(10));

INSERT INTO teste_a (valor) VALUES ('teste1');
INSERT INTO teste_a (valor) VALUES ('teste2');
INSERT INTO teste_a (valor) VALUES ('teste3');
INSERT INTO teste_a (valor) VALUES ('teste4');
INSERT INTO teste_a (valor) VALUES ('teste5');

INSERT INTO teste_b (valor) VALUES ('testea');
INSERT INTO teste_b (valor) VALUES ('testeb');
INSERT INTO teste_b (valor) VALUES ('testec');
INSERT INTO teste_b (valor) VALUES ('tested');

SELECT tbla.valor, tblb.valor
FROM teste_a tbla
CROSS JOIN teste_b tblb;

DROP TABLE IF EXISTS teste_a;
DROP TABLE IF EXISTS teste_b;

SELECT banco.nome,
     agencia.nome,
     conta_corrente.numero,
     conta_corrente.digito,
     cliente.nome
FROM banco
JOIN agencia ON agencia.banco_numero = banco.numero
JOIN conta_corrente 
  ON conta_corrente.banco_numero = agencia.banco_numero
  AND conta_corrente.agencia_numero = agencia.numero
JOIN cliente
  ON cliente.numero = conta_corrente.cliente_numero;
```

### Otimizando o código com CTE
- `Common Table Expression (CTE)`: Forma auxiliar de organizar "statements", ou seja, blocos de códigos, para consultas muito grandes, gerando tabelas temporárias e criando relacionamentos entre elas. Dentro dos statements podem ter SELECTs, INSERTs, UPDATEs OU DELETEs.
- Comandos utilizados na prática:
```sql
SELECT numero, nome FROM banco;
SELECT banco_numero, numero, nome FROM agencia;

WITH tbl_tmp_banco AS (
  SELECT numero, nome
  FROM banco
)

SELECT numero, nome 
FROM tbl_tmp_banco;

WITH params AS (
  SELECT 213 AS banco_numero
), tbl_tmp_banco AS (
  SELECT numero, nome
  FROM banco
  JOIN params ON params.banco_numero = banco.numero
)

SELECT numero, nome
FROM tbl_tmp_banco;

SELECT banco.numero, banco.nome
FROM banco
JOIN (
  SELECT 213 as banco_numero
) params ON params.banco_numero = banco.numero;

WITH clientes_e_transacoes AS (
  SELECT cliente.nome AS cliente_nome,
     tipo_transacao.nome AS tipo_transacao_nome,
     cliente_transacoes.valor AS tipo_transacao_valor
  FROM cliente_transacoes
  JOIN cliente ON cliente.numero = cliente_transacoes.cliente_numero
  JOIN tipo_transacao ON tipo_transacao.id = cliente_transacoes.tipo_transacao_id
)

SELECT cliente_nome, tipo_transacao_nome, tipo_transacao_valor
FROM clientes_e_transacoes;

WITH clientes_e_transacoes AS (
  SELECT cliente.nome AS cliente_nome,
     tipo_transacao.nome AS tipo_transacao_nome,
     cliente_transacoes.valor AS tipo_transacao_valor
  FROM cliente_transacoes
  JOIN cliente ON cliente.numero = cliente_transacoes.cliente_numero
  JOIN tipo_transacao ON tipo_transacao.id = cliente_transacoes.tipo_transacao_id
  JOIN banco ON banco.numero = cliente_transacoes.banco_numero AND banco.nome ILIKE '%itaú%'
)

SELECT cliente_nome, tipo_transacao_nome, tipo_transacao_valor
FROM clientes_e_transacoes;
```

### Como as views auxiliam no acesso ao banco de dados
- `View` são visões, camadas para as tabelas, "alias" para uma ou mais queries e aceitam comandos de `SELECT`, `INSERT` E `UPDATE`.
- `View` com idempotência:
```sql
CREATE OR REPLACE VIEW vw_bancos AS (
  SELECT numero, nome, ativo
  FROM banco
);

SELECT numero, nome, ativo
FROM vw_bancos;

CREATE OR REPLACE VIEW vw_bancos (banco_numero, banco_nome, banco_ativo) AS (
  SELECT numero, nome, ativo
  FROM banco
);

SELECT banco_numero, banco_nome, banco_ativo
FROM vw_bancos;
```
- `Views` para INSERT, UPDATE E DELETE:
```sql
-- Funcionam apenas para VIEWs com apenas 1 tabela para INSERT, UPDATE E DELETE

CREATE OR REPLACE VIEW vw_bancos AS (
  SELECT numero, nome, ativo
  FROM banco
);

INSERT INTO vw_bancos (numero, nome, ativo) VALUES (100, 'Banco cem', TRUE);

UPDATE vw_bancos set nome = 'Banco 100' WHERE numero = 100;

DELETE FOM vw_bancos WHERE numero = 100;
```
- Comandos utilizados na prática:
```sql
SELECT numero, nome, ativo
FROM banco;

CREATE OR REPLACE VIEW vw_bancos AS (
  SELECT numero, nome, ativo
  FROM banco
);

SELECT numero, nome, ativo
FROM vw_bancos;

CREATE OR REPLACE VIEW vw_bancos2 (banco_numero, banco_nome, banco_ativo) AS (
  SELECT numero, nome, ativo
  FROM banco
);

INSERT INTO vw_bancos2 (banco_numero, banco_nome, banco_ativo)
VALUES (51, 'Banco Boa ideia', TRUE);

SELECT banco_numero, banco_nome, banco_ativo
FROM vw_bancos2 WHERE banco_numero = 51;

UPDATE vw_bancos2 SET banco_ativo = FALSE WHERE banco_numero = 51;

DELETE FROM vw_bancos2 WHERE banco_numero = 51;

CREATE OR REPLACE TEMPORARY VIEW vw_agencia AS (
	SELECT nome FROM agencia
);

SELECT nome FROM vw_agencia;

CREATE OR REPLACE VIEW vw_bancos_com_ativos AS (
  SELECT numero, nome, ativo
  FROM banco
  WHERE ativo = TRUE
) WITH LOCAL CHECK OPTION;

INSERT INTO vw_bancos_com_ativos (numero, nome, ativo)
VALUES (51, 'Banco Boa ideia', FALSE);
-- ERROR:  new row violates check option for view "vw_bancos_com_ativos"
-- DETAIL:  Failing row contains (51, Banco Boa ideia, f, 2021-07-04 18:06:37.006524).
-- SQL state: 44000

CREATE OR REPLACE VIEW vw_bancos_com_a AS (
  SELECT numero, nome, ativo
  FROM vw_bancos_com_ativos
  WHERE nome ILIKE 'a%'
) WITH LOCAL CHECK OPTION;

SELECT nome FROM vw_bancos_com_a;

INSERT INTO vw_bancos_com_a (numero, nome, ativo) VALUES (333, 'Alfa Omega', true);

INSERT INTO vw_bancos_com_a (numero, nome, ativo) VALUES (331, 'Beta Omega', true);
--ERROR:  new row violates check option for view "vw_bancos_com_a"

INSERT INTO vw_bancos_com_a (numero, nome, ativo) VALUES (331, 'Alfa Gama', true);

INSERT INTO vw_bancos_com_a (numero, nome, ativo) VALUES (332, 'Alfa false', false);
--ERROR:  new row violates check option for view "vw_bancos_com_ativos"

--atualiza view removendo restrição da view
CREATE OR REPLACE VIEW vw_bancos_com_ativos AS (
  SELECT numero, nome, ativo
  FROM banco
  WHERE ativo = TRUE
);

INSERT INTO vw_bancos_com_a (numero, nome, ativo) VALUES (332, 'Alfa false', false);

-- atualiza view para restringir em cascata
CREATE OR REPLACE VIEW vw_bancos_com_a AS (
  SELECT numero, nome, ativo
  FROM vw_bancos_com_ativos
  WHERE nome ILIKE 'a%'
) WITH CASCADED CHECK OPTION;

INSERT INTO vw_bancos_com_a (numero, nome, ativo) VALUES (334, 'Alfa False False', false);
-- ERROR:  new row violates check option for view "vw_bancos_com_ativos"

CREATE TABLE IF NOT EXISTS funcionarios (
	id SERIAL,
	nome VARCHAR(50),
	gerente INTEGER,
	PRIMARY KEY (id),
	FOREIGN KEY (gerente) REFERENCES funcionarios(id)
);

INSERT INTO funcionarios (nome, gerente) VALUES ('Anselmo', null);
INSERT INTO funcionarios (nome, gerente) VALUES ('Beatriz', 1);
INSERT INTO funcionarios (nome, gerente) VALUES ('Magno', 1);
INSERT INTO funcionarios (nome, gerente) VALUES ('Cremilda', 2);
INSERT INTO funcionarios (nome, gerente) VALUES ('Wagner', 4);
												
SELECT id, nome, gerente FROM funcionarios;

SELECT id, nome, gerente FROM funcionarios WHERE gerente IS NULL
UNION ALL
SELECT id, nome, gerente FROM funcionarios WHERE id = 999; -- apenas para exemplificar

CREATE OR REPLACE RECURSIVE VIEW vw_func(id, gerente, funcionario) AS (
	SELECT id, gerente, nome
	FROM funcionarios
	WHERE gerente IS NULL
	
	UNION ALL
	
	SELECT funcionarios.id, funcionarios.gerente, funcionarios.nome
	FROM funcionarios
	JOIN vw_func ON vw_func.id = funcionarios.gerente
);

SELECT id, gerente, funcionario
FROM vw_func;

-- Desafio: mostrar o nome do gerente
SELECT vw_func.id, vw_func.funcionario, funcionarios.nome AS gerente_nome
FROM vw_func
INNER JOIN funcionarios ON vw_func.gerente = funcionarios.id
```

### Conheça um dos principais conceitos de banco de dados: transações
- `Transação`: conceito fundamental de todos os sistemas de bancos de dados. Conceito de multiplas etapas/códigos reunidas em apenas 1 transação, onde o resultado precisa ser **tudo ou nada**.

- Comandos utilizados na prática:
```sql
SELECT numero, nome, ativo FROM banco ORDER BY numero;
UPDATE banco SET ativo = false WHERE numero = 0;

BEGIN;
UPDATE banco SET ativo = true WHERE numero = 0;
SELECT numero, nome, ativo FROM banco WHERE numero = 0;
ROLLBACK;

BEGIN;
UPDATE banco SET ativo = true WHERE numero = 0;
COMMIT;
SELECT numero, nome, ativo FROM banco WHERE numero = 0;

SELECT id, gerente, nome
FROM funcionarios;

BEGIN;
UPDATE funcionarios SET gerente = 2 WHERE id = 3;
SAVEPOINT sf_func;
UPDATE funcionarios SET gerente = null;
ROLLBACK TO sf_func;
UPDATE funcionarios SET gerente = 3 WHERE id = 5;
COMMIT;
```

### Conheça as funções que podem ser criadas pelo desenvolvedor
- Funções
  - Definição
    - Conjunto de códigos que são executdos dentro de uma transação com a finalizade de facilitar a programação e obter o reaproveitamento/reutilização de códigos.
    - Existem 4 tipos de funções:
      - query language functions (funções escritas em SQL)
      - procedural language functions (funções escritas, por exemplo, PL/pgSQL ou PL/py)
      - internal functions
      - C-language functions
    - O foco no curso é sobre `USER DEFINED FUNCTIONS`.
  
  - Linguagens
    - SQL
    - **PL/PGSQL**
    - PL/PY
    - PL/PHP
    - PL/RUBY
    - PL/JAVA
    - PL/LUA
  - Idempotência
  ```sql
  CREATE OR REPLACE FUNCTION [nome da função]
  ```
    - Mesmo nome
    - Mesmo tipo de retorno
    - Mesmo número de parâmetros/argumentos
  - `RETURNs`
    - Tipo de retorno (data type)
      - INTEGER
      - CHAR / VARCHAR
      - BOOLEAN
      - ROW
      - TABLE
      - JSON
  - Language
    - SQL
    - PLPGSQL
    - PLJAVA
    - PLPY
  - Segurança
    - Security
      - INVOKER (padrão): executa a função com a permissão do usuário que está executando a função
      - DEFINER: o usuário que está executando a função executa com as permissões do usuário que criou a função.
  - Recursos
    - COST: custo/row em unidades de CPU
    - ROWS: Número estimado de linhas que será analisada pelo planner
  - SQL FUNCTIONS
    - Não é possível utilizar `TRANSAÇÕES`

- Comandos utilizados na prática:
```sql
-- RETURNS NULL ON NULL INPUT
CREATE OR REPLACE FUNCTION func_somar(INTEGER, INTEGER)
RETURNS INTEGER
SECURITY DEFINER
RETURNS NULL ON NULL INPUT
LANGUAGE SQL
AS $$
	SELECT $1 + $2;
$$;

SELECT func_somar(100, 2);
SELECT func_somar(100, null); --retorna null

-- 'CALLED ON NULL INPUT' SEM TRATAMENTO DE NULL
CREATE OR REPLACE FUNCTION func_somar(INTEGER, INTEGER)
RETURNS INTEGER
SECURITY DEFINER
CALLED ON NULL INPUT
LANGUAGE SQL
AS $$
	SELECT $1 + $2;
$$;

SELECT func_somar(100, 2);
SELECT func_somar(100, null); --retorna null

-- 'CALLED ON NULL INPUT' COM TRATAMENTO DE NULL
SELECT COALESCE(null, 'adriano', 'digital'); --adriano
SELECT COALESCE(null, NULL, 'digital', 'adriano'); --digital

CREATE OR REPLACE FUNCTION func_somar(INTEGER, INTEGER)
RETURNS INTEGER
SECURITY DEFINER
CALLED ON NULL INPUT
LANGUAGE SQL
AS $$
	SELECT COALESCE($1,0) + COALESCE($2,0);
$$;

SELECT func_somar(100, 2);
SELECT func_somar(100, null); -- retorna 100

--PLPGSQL
CREATE OR REPLACE FUNCTION bancos_add(p_numero INTEGER, p_nome VARCHAR, p_ativo BOOLEAN)
RETURNS INTEGER
SECURITY INVOKER
LANGUAGE PLPGSQL
CALLED ON NULL INPUT
AS $$
DECLARE variavel_id INTEGER;
BEGIN
	SELECT INTO variavel_id numero
	FROM banco
	WHERE numero = p_numero;
	
	RETURN variavel_id;
END; $$;

SELECT bancos_add(1, 'Banco Novo', FALSE); --1
SELECT bancos_add(5432, 'Banco Novo', FALSE); --NULL

-- Tratamento de erros
CREATE OR REPLACE FUNCTION bancos_add(p_numero INTEGER, p_nome VARCHAR, p_ativo BOOLEAN)
RETURNS INTEGER
SECURITY INVOKER
LANGUAGE PLPGSQL
CALLED ON NULL INPUT
AS $$
DECLARE variavel_id INTEGER;
BEGIN
	IF p_numero IS NULL OR p_nome IS NULL OR p_ativo IS NULL THEN
		RETURN 0;
	END IF;
	SELECT INTO variavel_id numero
	FROM banco
	WHERE numero = p_numero;

	IF variavel_id IS NULL THEN
		INSERT INTO banco(numero, nome, ativo)
		VALUES (p_numero, p_nome, p_ativo);
	ELSE
		RETURN variavel_id;
	END IF;

	SELECT INTO variavel_id numero
	FROM banco
	WHERE numero = p_numero;
	
	RETURN variavel_id;
END; $$;

SELECT bancos_add(5432, 'Banco Novo', FALSE);
SELECT bancos_add(NULL, 'Banco Novo', FALSE);

SELECT * FROM banco WHERE numero = 5432;
```
