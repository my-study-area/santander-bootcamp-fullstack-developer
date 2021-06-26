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
