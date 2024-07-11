# Exercício 1

Considere o esquema relacional abaixo, de um sistema de pedidos de venda de produtos eletrônicos. A venda é feita por meio de pedidos. Cada pedido é feito por um cliente, vendido por um vendedor em uma determinada data e contém vários itens de produtos.

ItemPedido (**numPedido**, **codProduto**, qtdePedida, dataPedido, codCliente, nomeCliente, codVendedor, nomeVendedor, descricaoProduto, precoVendaProduto)

O esquema já se encontra na 1a Forma Normal. Em cada resposta, deixe indicado claramente a chave primária, as chaves secundárias e as chaves estrangeiras de cada tabela, se existirem.

a) Apresente o esquema relacional normalizado para a 2a Forma Normal, mas não ainda normalizado para a 3a Forma Normal.

R:

Pedido (**numPedido**, dataPedido, codCliente, nomeCliente, codVendedor, nomeVendedor) 

Produto (**codProduto**, descricaoProduto, precoVendaProduto) 

ItemPedido (**numPedido**, **codProduto**, qtdePedida) 

* ItemPedido[numPedido] $\rightarrow$ (p) Pedido[numPedido]

* ItemPedido[codProduto] $\rightarrow$ (p) Produto[codProduto]

b) Apresente o esquema relacional normalizado para a 3a Forma Normal.

R:

Cliente (**codCliente**, nomeCliente)

Vendedor (**codVendedor**, nomeVendedor)

Pedido (**numPedido**, dataPedido, codCliente, codVendedor)

* Pedido[codCliente] $\rightarrow$ (b) Cliente[codCliente]

* Pedido[codVendedor] $\rightarrow$ (b) Vendedor[codVendedor]

Produto (**codProduto**, descricaoProduto, precoVendaProduto)

ItemPedido (**numPedido**, **codProduto**, qtdePedida)

* ItemPedido[numPedido] $\rightarrow$ (p) Pedido[numPedido]

* ItemPedido[codProduto] $\rightarrow$ (p) Produto[codProduto]