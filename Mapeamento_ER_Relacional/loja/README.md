# Loja de Produtos

Considere o seguinte diagrama ER. Ele representa o banco de dados de um sistema de compras e vendas de uma loja de produtos de informática. 

Apresente o esquema relacional correspondente ao seu mapeamento ERRelacional. 

Deixe indicado claramente a chave primária, as chaves secundárias e as chaves estrangeiras (com suas opções de exclusão) de cada tabela, se existirem.

<p align="center">
    <img src="../readmeImg/03_enunciado.png" width="900px" height="500px">
</p>

## Solução

* Vendedor (<ins>numRegistro</ins>, nome, dataAdmissao)

* Cliente (<ins>cpf</ins>, nome, logradouro, numero, complemento, bairro, cidade, estado, cep)

* FoneCliente (<ins>cpf</ins>, <ins>fone</ins>)
    * FoneCliente[cpf] $\rightarrow ^{p}$ Cliente[cpf]

* PedidoVenda (<ins>numPedido</ins>, numVendedor, cpfCliente, dataPedido, situacao)
    * PedidoVenda[numVendedor] $\rightarrow ^{b}$ Vendedor[numRegistro]
    * PedidoVenda[cpfCliente] $\rightarrow ^{b}$ Cliente[cpf]

* Produto (<ins>codProduto</ins>, descricao, precoVenda, quantidadeEstoque)

* ProdutoVenda (<ins>codProduto</ins>, <ins>numPedido</ins>, precoVendido, quantidade)
    * ProdutoVenda[codProduto] $\rightarrow ^{p}$ Produto[codProduto]
    * ProdutoVenda[numPedido] $\rightarrow ^{p}$ PedidoVenda[numPedido]

* Fornecedor (<ins>cnpj</ins>, nomeFantasia, razaoSocial, logradouro, numero, complemento, bairro, cidade, estado, cep)

* FoneFornecedor (<ins>cnpj</ins>, <ins>fone</ins>)
    * FoneFornecedor[cnpj] $\rightarrow ^{p}$ Fornecedor[cnpj]

* ProdutoFornecedor (<ins>codProduto</ins>, <ins>cnpjFornecedor</ins>, dataCotacao, precoCotado, dataValidade, prazoEntrega)
    * ProdutoFornecedor[codProduto] $\rightarrow ^{p}$ Produto[codProduto]
    * ProdutoFornecedor[cnpjFornecedor] $\rightarrow ^{p}$ Fornecedor[cnpj]

* PedidoCompra (<ins>numPedido</ins>, cnpfFornecedor, dataPedido, situacao)
    * PedidoCompra[cnpjFornecedor] $\rightarrow ^{b}$ Fornecedor[cnpj]

* ProdutoCompra (<ins>codProduto</ins>, <ins>numPedido</ins>, precoComprado, quantidade)
    * ProdutoCompra[codProduto] $\rightarrow ^{p}$ Produto[codProduto]
    * ProdutoCompra[numPedido] $\rightarrow ^{p}$ PedidoCompra[numPedido]

