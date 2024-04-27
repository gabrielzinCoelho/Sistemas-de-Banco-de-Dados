# Sistema de uma Biblioteca

Considere o seguinte diagrama ER. Ele representa o banco de dados de um sistema de empréstimos de livros de uma biblioteca universitária. 

Apresente o esquema relacional correspondente ao seu mapeamento ER-Relacional. 

Deixe indicado claramente a chave primária, as chaves secundárias e as chaves estrangeiras (com suas opções de exclusão) de cada tabela, se existirem.

<p align="center">
    <img src="../readmeImg/01_enunciado.png" width="800px" height="450px">
</p>

## Solução

* Editora (<u>cnpj</u>, nome, endereco, site, e-mail)

* Livro (<u>isbn</u>, titulo, edicao, anoPublicacao, cnpjEditora)
    * Livro[cnpjEditora] $\rightarrow ^{b}$ Editora[cnpj]

* LivroAutor (<u>isbn</u>, <u>autor</u>)
    * LivroAutor[isbn] $\rightarrow ^{p}$ Livro[isbn]

* Exemplar (<u>idExemplar</u>, localizacao, tipoEmprestimo, isbn)
    * Exemplar[isbn] $\rightarrow ^{b}$ Livro[isbn]

* Usuario (<u>numMatricula</u>, nome, endereco)

* UsuarioFone (<u>numMatricula</u>, <u>fone</u>)
    * UsuarioFone[numMatricula] $\rightarrow ^{p}$ Usuario[numMatricula]

* Emprestimo (<u>idExemplar</u>, <u>numMatricula</u>, dataEmp, dataLimDevol, dataRealDevol)
    * Emprestimo[idExemplar] $\rightarrow ^{p}$ Exemplar[idExemplar]
    * Emprestimo[numMatricula] $\rightarrow ^{p}$ Usuario[numMatricula]