# Normalização para Bancos de Dados Relacionais

## Primeira Forma Normal

Os atributos da relação devem incluir apenas valores atômicos (indivisíveis) e únicos no domínio desse atributo.

A 1FN é inerente ao modelo relacional de bancos de dados.

## Segunda Forma Normal

Toda chave candidata da relação deve determinal de forma total (dependência funcional total) qualquer outro atributo.

Caso não exista chave candidata composta, a relação já se encontra na 2FN.

## Terceira Forma Normal

Nenhum atributo não principal pode determinar outro atributo não principal.

## Forma Normal de Boyce-Codd

Semelhante à 3FN, porém um pouco mais restritiva, determina que nenhum atributo não principal pode determinar qualquer outro atributo, principal ou não.

## Quarta Forma Normal

Referente a verificação da existência de dependências multivaloradas, que costumam levar a redundância de dados.

Uma Dependência Multivalorada ocorre quando, para cada valor de um atributo A, há um conjunto de valores para outros atributos B e C (independentes entre si) que estão associados a A.

Ocorre quando se tem dois ou mais atributos multivalorados independentes no mesmo esquema de relação e acaba levando a repetição de cada valor de um dos atributos com cada valor do outro atributo.

## Quinta Forma Normal

Uma relação R está na Quinta Forma Normal (5FN) se estiver na 4FN e não existir Dependência de Junção.

## Exercícios

1. [Exercício 1](ex1)
1. [Exercício 2](ex2)
1. [Exercício 3](ex3)