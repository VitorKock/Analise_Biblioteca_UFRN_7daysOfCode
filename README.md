# desafio_7daysOfCode - Análise de Dados com Phyton
Estudo de análise de dados com Phyton a partir de bibliotecas da universidade UFRN, proposto pelo instrutor Francisco Foz

O arquivo do Jupyter Notebook contém todo o processamento dos dados, construção de gráficos, tabelas e insights observados.

O desafio começa com o fornecimento de dados de empréstimos (data de empréstimo, renovação, devolução, código de barras do exemplar, matrícula do aluno, etc) e de exemplares (código de barras do exemplar, id do exemplar, coleção, biblioteca em que está, localização, etc).

Como os dados de empréstimos vieram em arquivos separados semestralmente do primeiro semestre de 2010 ao segundo semestre de 2020, fiz um "for loop" para todos os .csv de uma pasta e concatenei os arquivos em um dataframe do pandas. 

Fiz a limpeza (removendo duplicados) e uni os dados de empréstimo com os de exemplares em um único arquivo. Também removi a coluna "registro_sistema" (pois não vou utilizar esse endereçamento) e converti a coluna de matrícula para string.

Depois fiz uma lista dos assuntos mais emprestados a partir do número de localização nas bibliotecas (seguindo o CDU - Classificação Decimal Universal, e obtive o seguinte resultado:

![image](https://github.com/user-attachments/assets/059c9110-d72c-417c-a5f2-811727075681)

Depois fiz uma investigação de sazonalidade (empréstimos por mês e hora do dia) e tendência (emprestimos em cada ano), construindo gráficos com Seaborn. As conclusões foram:
## Conclusões Análise Ano
1. Há uma tendência de queda no número de empréstimos desde 2013, possivelmente impulsionada pelo fácil acesso a livros digitais pela internet. 
2. Não é recomendado contratar novos colaboradores, sendo necessário diminuir o quadro ao longo dos anos. Chama a atenção a grande queda em 2019. 2020 não é possível avaliar pois os dados não estão completos e foi ano da pandemia. 
3. É preciso investigar também outras causas que podem estar levando a essa queda, como o interesse por livros, a qualidade do acervo e o número de alunos matriculados.

## Conclusões Análise Mês
1. Os meses em que a frequencia de emprestimos é mais alta são março e agosto (principais), seguidos por fevereiro e abril (evitar liberar colaboradores).
2. Os meses mais tranquilos são janeiro e dezembro (principais, férias de verão), seguidos por junho, julho e novembro (melhores meses para dar férias aos colaboradores e fazer projetos administrativos).

## Conclusões Análise Horário
1. Os horários com mais emprestimos são às 16h e 10h (principais), seguidos por 17h e 18h (ter mais funcionários para atendimento ao público). 
2. Os horários com menos emprestimos são das 7h às 9h, 20h às 22h e 13h (podendo destinar mais funcionários para atividades administrativas e horários de almoço/jantar).

Depois fiz uma análise exploratória das categorias, e os insights obtidos foram:
1. Quase 80% dos empréstimos são feitos pelos alunos de graduação, possivelmente por serem o maior público nas universidades (preicsamos de dados para confirmar se esse perfil se aplica a base). Alunos de pós-graduação e docentes são responsáveis por 14.6% e 3.4% dos empréstimos, será que esse público está sendo contemplado com os recursos necessários para atividades de pesquisa, ou há muita necessidade de livros/artigos que a biblioteca não disponibiliza? Muitos artigos podem ser acessados online em plataformas externas a universidade, por isso é esperado que o público de pós-graduação (mestrado, doutorado e latu sensu) use menos as bibliotecas.
2. Mais de 99% dos empréstimos são de Acervo Circulante, ou seja, livros físicos. Chama a atenção o baixo número de empréstimos de Monografias e Dissertações, e isso ocorre provavelmente porque esse material já está disponível na internet e já é acessado sem empréstimos (seria o caso de incluir na base as consultas a esses materiais para verificar a relevância desses materiais em termos de consulta). Os baixos índices de empréstimo de Obras Raras, Literatura de Cordel e Coleções Mossoroense e Zila Mamede também chamam a atenção, não há interesse por parte da comunidade acadêmica nessas obras? Ações de marketing podem reverter esse quadro.
3. Quase 70% dos empréstimos ocorre na Biblioteca Central Zila Mamede, provavelmente por ser onde estão concentrados o maior número de alunos. Uma métrica relevante seria avaliar o número de empréstimos por aluno em cada câmpus/setor associado a cada biblioteca, mas não temos dados suficientes.
4. Referente às Classificações Decimais Universais (por área científica), 68.8% dos empréstimos ocorre para Ciências Aplicadas (Engenharia, Medicina, Tecnologia da Informação) e 17.8% para Ciências Sociais, o que também corresponde muito ao perfil dos alunos da universidade. Provavelmente há muito mais cursos associados a Ciências Aplicadas dos que os demais. Uma análise mais profunda seria avalir o número de empréstimos pela quantidade de alunos matriculados em cada curso, mas também não temos informações suficientes para apurar essas informações. Entender também porque áreas como linguagem, belas artes e geogriafia estão com números tão baixos comparados aos demais exige um detalhamento do número de alunos matriculados e de formados (talvez há um índice de abandono dos cursos maior que nos demais)

Teste.html é a tabela o último desafio, em que o objetivo é calcular as variações percentuais nos empréstimos e converter em html para ser publicado em um site.

![image](https://github.com/user-attachments/assets/9663bf8e-e32f-4d2e-8f34-827c290e3b24)

