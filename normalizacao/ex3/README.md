# Exercício 3

Considere o esquema abaixo, de um sistema de folha de pagamento de uma empresa. É armazenado, para cada funcionário, seus dados pessoais, o histórico dos seus cargos assumidos na empresa e o histórico de seus pagamentos recebidos. Considere que o funcionário não recebe dois pagamentos na mesma data.

Funcionario (**codFunc**, nomeFunc, dataNascimento, {codCargo, nomeCargo, dataInicioCargo, dataFimCargo, tempoNoCargo}, {dataPagamento, codBanco, codAgencia, nomeBanco, valorPagamento}) 

No esquema, os metacaracteres { e } indicam repetição. Assim, o esquema não está na 1a Forma Normal. Em cada resposta, deixe indicado claramente a chave primária, as chaves secundárias e as chaves estrangeiras de cada tabela, se existirem. 

a) Apresente o esquema relacional normalizado para a 1a Forma Normal, mas não ainda normalizado para a 2a e 3a Formas Normais. 

R:

Funcionario (**codFunc**, nomeFunc, dataNascimento)

CargoFunc (**codFunc**, **codCargo**, **dataInicioCargo**, nomeCargo, dataFimCargo, tempoNoCargo)

* CargoFunc[codFunc] $\rightarrow$ (p) Funcionario[codFunc]

PagamentoFunc (**codFunc**, **dataPagamento**, codBanco, codAgencia, nomeBanco, valorPagamento)   

* PagamentoFunc[codFunc] $\rightarrow$ (p) Funcionario[codFunc]

b) Apresente o esquema relacional normalizado para a 2a Forma Normal, mas não ainda normalizado para a 3a Forma Normal. 

R:

Funcionario (**codFunc**, nomeFunc, dataNascimento)

Cargo (**codCargo**, nomeCargo)

CargoFunc (**codFunc**, **codCargo**, **dataInicioCargo**, dataFimCargo, tempoNoCargo)

* CargoFunc[codFunc] $\rightarrow$ (p) Funcionario[codFunc]

* CargoFunc[codCargo] $\rightarrow$ (p) Cargo[codCargo]

PagamentoFunc (**codFunc**, **dataPagamento**, codBanco, codAgencia, nomeBanco, valorPagamento)   

* PagamentoFunc[codFunc] $\rightarrow$ (p) Funcionario[codFunc]

c) Apresente o esquema relacional normalizado para a 3a Forma Normal.

R:

Funcionario (**codFunc**, nomeFunc, dataNascimento)

Cargo (**codCargo**, nomeCargo)

CargoFunc (**codFunc**, **codCargo**, **dataInicioCargo**, dataFimCargo, tempoNoCargo)

* CargoFunc[codFunc] $\rightarrow$ (p) Funcionario[codFunc]

* CargoFunc[codCargo] $\rightarrow$ (p) Cargo[codCargo]

Banco (**codBanco**, nomeBanco)

PagamentoFunc (**codFunc**, **dataPagamento**, codBanco, codAgencia, valorPagamento)   

* PagamentoFunc[codFunc] $\rightarrow$ (p) Funcionario[codFunc]

* PagamentoFunc[codBanco] $\rightarrow$ (b) Banco[codBanco]
