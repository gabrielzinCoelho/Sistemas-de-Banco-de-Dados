# Mapeamento ER-Relacional

O obejtivo do Mapeamento ER-Relacional é projetar um esquema de banco de dados relacional tomando como base a descrição de um modelo ER.

### Entidade Fraca

Incluir como chave estrangeira todas os atributos que compõe as chaves primárias das entidades fortes.

A chave primária passa a ser a combinação das chaves primárias das entidades fortes e da chave parcial, se houver.

### Atributo Multivalorado

Necessário criar uma tabela, a qual possui como chave primária a combinação da chave estrangeira referente a entidade que possui o respectivo atributo e a coluna que descreve o atributo.

### Relacionamento Binário 1:1

* Chave Estrangeira (adição de coluna)

    * Uma das relações passa a ter uma chave estrangeira que referencia a outra relação. Além disso, os atributos do relacionamento também são adicionados a tabela que possui a chave estrangeira.

    * Preferível adicionar a chave estrangeira na tabela que possua participação total no relacionamento.

    * A chave estrangeira também deve ser chave secundária. Isso garante a cardinalidade máxima de 1 no relacionamento.

* Fusão de Tabelas

    * Quando ambas entidades possuem participação total no relacionamento é viável mesclar ambas relações em apenas uma.

    * A chave primária de uma das relações passa a ser a chave primária da nova relação criada, e a chave primária da outra passa é utilizada como chave secundária.

* Tabela própria

    * Apropriada quando a participação é parcial em ambos lados do relacionamento. Isso devido ao fato de evitar a presença de campos nulos, visto que apenas tuplas que participam do relacionamento são mapeadas na tabela.

    * A chave primária da nova relação será uma das duas chaves estrangeiras, e a outra chave estrangeira será uma chave secundária.

### Relacionamento Binário 1:N

* Chave estrangeira do lado N

    * É adicionado à relação que representa o tipo entidade participante do lado N do relacionamento a chave primária da outra relação, como chave estrangeira. 

* Tabela própria

    * Apropriada quando há participação parcial do lado N, visto que evita presença de campos nulos excessivos.

    * Criada uma tabela nova para representar o relacionamento, a qual possui como estrangeiras as chaves primárias de ambas relações. A chave primária da nova tabela será a chave primária da relação do lado N.

### Relacionamento Binário N:N

Criação de tabela própria, para representar o relacionamento. Possui como chaves estrangeiras as chaves primárias de ambas relações e a chave primária da nova tabela é a combinação de suas chaves estrangeiras.

### Relacionamento N-ário

Criação de tabela própria, para representar o relacionamento, que possui como chave primária apenas as chaves estrangeiras das relações com partipação N no relacionamento.

### Herança

* Múltiplas relações: superclasse e subclasse

    * Criar uma tabela para superclasse e para cada superclasse.

    * Adicionar como chave primárica de cada subclasse a chave estrangeira da superclasse.

    * Um atributo de tipo, indicando a subclasse à qual cada tupla pertence, pode ser adicionado na superclasse.

    * Mapeamento mais genérico de herança, que funciona para todos casos, mas não restringe tipo de participação (total ou parcial) ou subclasses disjuntas/sobrepostas.

* Múltiplas relações: apenas subclasse

    * Criar apenas as tabelas referentes às subclasses.

    * Funciona apenas nos casos de participação total na herança.

    * Nos casos de subclasses sobrepostas, deve ser evitada, visto que resulta em redundância de dados.

* Relação única com atributo de tipo

    * Criar apenas uma tabela, que inclui os atributos da superclasse e de todas subclasses. Além disso, há um atributo de tipo para informar a subclasse à qual cada tupla pertence.

    * Válido apenas para herança com subclasses disjuntas.

    * A quantidade de atributos específicos presentes nas subclasses refletem no número de campos nulos existentes.

* Relação única com atributos de múltiplos tipos

    * Criar apenas uma tabela, que inclui os atributos da superclasse e de todas subclasses. Além disso, para cada subclasse, há um atributo booleano para informar se a tupla pertence a mesma.

    * Apesar de funcionar para herança disjunta, é mais indicada para casos de herança com sobreposição de subclasses.

### União

Criar uma tabela com os atributos específicos da categoria e adicionar um identificador como chave primária.

Após isso, basta adicionar, para cada superclasse, como chave estrangeira a chave primária da categoria (subclasse). 

## Exercícios