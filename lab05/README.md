# Modelo para Apresentação do Lab05 - Marcadores e Taxonomia em Cypher

Estrutura de pastas:

~~~
├── README.md  <- arquivo apresentando a tarefa
~~~

# Aluno
* 213259: Arthur Cemin Baia

## Tarefa de Cypher sobre Marcadores e Taxonomia

## Tarefa 1

Escreva em Cypher uma consulta que retorne os marcadores da categoria `Serviços`, sem considerar as categorias subordinadas.

### Resolução
~~~cypher
MATCH (:Categoria {id: 'Serviços'})--(m:Marcador)
RETURN m
~~~

## Tarefa 2

Escreva em Cypher uma consulta que retorne os marcadores da categoria `Serviços`, considerando as categorias subordinadas.

### Resolução
~~~cypher
MATCH (C:Categoria {id:'Serviços'})<-[:Superior*]-(c1:Categoria)<-[:Pertence]-(m:Marcador) 
match (C1:Categoria {id: 'Serviços'})<-[:Pertence]-(m1:Marcador) 
RETURN m,m1
~~~
