# Exercício 2

Considere o esquema abaixo, de um sistema acadêmico de uma faculdade. É armazenado, para cada aluno, o seu histórico escolar contendo as disciplinas cursadas em cada semestre, com suas respectivas notas e frequências obtidas. Considere que, em cada semestre, é oferecida somente uma turma de cada disciplina, e que ela é ministrada por um único professor. 

Aluno (**numMatricula**, nomeAluno, codCurso, nomeCurso, {codDisciplina, nomeDisciplina, cargaHorariaDisc, anoSemestreCursada, codProfessorDisciplina, nomeProfessor, notaDisciplina, frequenciaDisciplina}) 

No esquema, os metacaracteres { e } indicam repetição. Assim, o esquema não está na 1a Forma Normal. Em cada resposta, deixe indicado claramente a chave primária, as chaves secundárias e as chaves estrangeiras de cada tabela, se existirem.

a) Apresente o esquema relacional normalizado para a 1a Forma Normal, mas não ainda normalizado para a 2a e 3a Formas Normais.

R:

Aluno (**numMatricula**, nomeAluno, codCurso, nomeCurso)

Historico (**codDisciplina**, **anoSemestreCursada**, **numMatricula**, nomeDisciplina, cargaHorariaDisc, codProfessorDisciplina, nomeProfessor, notaDisciplina, frequenciaDisciplina)

Historico[numMatricula] $\rightarrow$ (p) Aluno[numMatricula]


b) Apresente o esquema relacional normalizado para a 2a Forma Normal, mas não ainda normalizado para a 3a Forma Normal.

R:

Aluno (**numMatricula**, nomeAluno, codCurso, nomeCurso)

Disciplina (**codDisciplina**, nomeDisciplina, cargaHorariaDisc)

Turma (**codDisciplina**, **anoSemestreCursada**, codProfessorDisciplina, nomeProfessor)

* Turma[codDisciplina] $\rightarrow$ (p) Disciplina[codDisciplina]

Historico (**codDisciplina**, **anoSemestreCursada**, **numMatricula**, notaDisciplina, frequenciaDisciplina)

* Historico[numMatricula] $\rightarrow$ (p) Aluno[numMatricula]

* Historico[codDisciplina, anoSemestreCursada] $\rightarrow$ (p) Turma [codDisciplina, anoSemestreCursada]


c) Apresente o esquema relacional normalizado para a 3a Forma Normal.

R:

Aluno (**numMatricula**, nomeAluno, codCurso)

* Aluno[codCurso] $\rightarrow$ (b) Curso[codCurso]

Curso (**codCurso**, nomeCurso)

Disciplina (**codDisciplina**, nomeDisciplina, cargaHorariaDisc)

Professor (**codProfessor**, nomeProfessor)

Turma (**codDisciplina**, **anoSemestreCursada**, codProfessorDisciplina)

* Turma[codDisciplina] $\rightarrow$ (p) Disciplina[codDisciplina]

* Turma[codProfessorDisciplina] $\rightarrow$ (b) Professor[codProfessor] 

Historico (**codDisciplina**, **anoSemestreCursada**, **numMatricula**, notaDisciplina, frequenciaDisciplina)

* Historico[numMatricula] $\rightarrow$ (p) Aluno[numMatricula]

* Historico[codDisciplina, anoSemestreCursada] $\rightarrow$ (p) Turma [codDisciplina, anoSemestreCursada]
