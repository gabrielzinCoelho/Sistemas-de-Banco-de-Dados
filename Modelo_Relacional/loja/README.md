# Restrições de Integridade Referencial: Loja de Produtos

Considere o banco de dados de um sistema vendas de produtos de uma loja, representado pelo seguinte esquema relacional:

* Fornecedor (<u>CNPJ</u>, nomeFor, enderecoFor)
* Produto (<u>codProd</u>, descricao, precoVenda, qtdeEstoque, CNPJfor)
* Cliente (<u>codCli</u>, nomeCli, enderecoCli)
* Pedido (<u>numPed</u>, codCli, dataVenda, nomeVendedor)
* ItemPedido (<u>numPed</u>, <u>codProd</u>, qtdeVendida, precoVendido)

Indique as restrições de integridade referencial, com opção de exclusão, mais apropriadas para esse banco de dados. As opções de exclusão são: P – propagação, B – bloqueio e N – substituição por nulos. Justifique sua resposta. Depois, mostre exemplos de dados em cada tabela. 

Dica: faça o diagrama ER correspondente ao esquema relacional para ajudar na escolha das opções de exclusão mais apropriadas. Faça suposições para casos em que não e possível deduzir do esquema relacional. É um método conhecido como engenharia reversa: gerar um diagrama ER a partir do diagrama (ou esquema) relacional.

## Solução

Observe o diagrama ER correspondente ao modelo relacional:

<p align="center">
    <img src="./readmeImg/loja.png" width="800px" height="300px">
</p>

Veja a opção de exclusão mais apropriada definida nos relacionamentos:

* Produto (<u>codProd</u>, descricao, precoVenda, qtdeEstoque, CNPJfor)
    *  Produto[CNPJfor] $\rightarrow ^{b}$ Fornecedor[CNPJfor]
* Pedido (<u>numPed</u>, codCli, dataVenda, nomeVendedor)
    * Pedido[codCli] $\rightarrow ^{b}$ Cliente[codCli]
* ItemPedido (<u>numPed</u>, <u>codProd</u>, qtdeVendida, precoVendido)
    * ItemPedido[numPed] $\rightarrow ^{p}$ Pedido[numPed]
    * ItemPedido[codProd] $\rightarrow ^{p}$ Produto[codProd]

Na tabela "Produto", a opção de exclusão por bloqueio foi utilizada visto que tal atributo não pode assumir valor nulo. Além disso, a opção de propagação também não é apropriada, pois "Produto" é uma entidade independente, e, dessa forma, a entidade "Fornecedor" estaria interferindo diretamente nela.

O mesmo vale para a tabela "Pedido". Na tabela "Pedido", a opção de exclusão por bloqueio também foi utilizada visto que tal atributo, similarmente, não pode assumir valor nulo. Além disso, a opção de propagação também não é apropriada, pois "Pedido" é uma entidade independente, e, dessa forma, a entidade "Cliente" estaria interferindo diretamente nela.

Já no caso da entidade "ItemPedido", temos que considerar o fato da mesma possuir ambas chaves estrangeiras como sua chave primária, caracterizando a mesma como uma entidade fraca. Nesse caso, a deleção de uma tupla que é referenciada por outras na relação "ItemPedido", seja da tabela "Pedido" ou "Produto", deve resultar na deleção em cascata das instâncias relacionadas. Isso, devido ao fato de "ItemPedido" ser uma entidade dependende de "Pedido" e também de "Produto".

