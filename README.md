# desafio_7daysOfCode - Análise de Dados com Phyton
Estudo de análise de dados com Phyton a partir de bibliotecas da universidade UFRN, proposto pelo instrutor Francisco Foz

O arquivo do Jupyter Notebook contém todo o processamento dos dados, construção de gráficos, tabelas e insights observados.

O desafio começa com o fornecimento de dados de empréstimos (data de empréstimo, renovação, devolução, código de barras do exemplar, matrícula do aluno, etc) e de exemplares (código de barras do exemplar, id do exemplar, coleção, biblioteca em que está, localização, etc).

Como os dados de empréstimos vieram em arquivos separados semestralmente do primeiro semestre de 2010 ao segundo semestre de 2020, fiz um "for loop" para todos os .csv de uma pasta e concatenei os arquivos em um dataframe do pandas. 

Fiz a limpeza (removendo duplicados) e uni os dados de empréstimo com os de exemplares em um único arquivo. Também removi a coluna "registro_sistema" (pois não vou utilizar esse endereçamento) e converti a coluna de matrícula para string.

Depois fiz uma lista dos assuntos mais emprestados a partir do número de localização nas bibliotecas (seguindo o CDU - Classificação Decimal Universal, e obtive o seguinte resultado:
CDU
Ciências aplicadas.                1425473
Ciências sociais.                   369536
Matemática e ciências naturais.      68744
Generalidades.                       62521
Religião.                            62295
Filosofia e psicologia.              60563
Geografia. Biografia. História.       7989
Belas artes.                          7911
Linguagem. Língua. Linguística.       7490
Name: count, dtype: int64

Teste.html é a tabela o último desafio, em que o objetivo é calcular as variações percentuais nos empréstimos e converter em html para ser publicado em um site.

![image](https://github.com/user-attachments/assets/9663bf8e-e32f-4d2e-8f34-827c290e3b24)

