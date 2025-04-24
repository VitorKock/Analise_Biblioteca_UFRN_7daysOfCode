# Análise de Dados da Biblioteca da UFRN - desafio_7daysOfCode
Estudo de análise de dados com Phyton a partir de bibliotecas da universidade UFRN, proposto pelo instrutor Francisco Foz.

O arquivo do Jupyter Notebook contém todo o processamento dos dados, construção de gráficos, tabelas e insights observados.

Linguagem Principal: Phyton
Bibliotecas Utilizadas: Pandas(Tabelas e limpeza de dados), os (Operacional System), Seaborn e Plotly (Gráficos).

O desafio começa com o fornecimento de dados de empréstimos (data de empréstimo, renovação, devolução, código de barras do exemplar, matrícula do aluno, etc) e de exemplares (código de barras do exemplar, id do exemplar, coleção, biblioteca em que está, localização, etc).

Como os dados de empréstimos vieram em arquivos separados semestralmente do primeiro semestre de 2010 ao segundo semestre de 2020, fiz um "for loop" para todos os .csv de uma pasta e concatenei os arquivos em um dataframe do pandas. 

Fiz a limpeza (removendo duplicados) e uni os dados de empréstimo com os de exemplares em um único arquivo. Também removi a coluna "registro_sistema" (pois não vou utilizar esse endereçamento) e converti a coluna de matrícula para string.

Depois fiz uma lista dos assuntos mais emprestados a partir do número de localização nas bibliotecas (seguindo o CDU - Classificação Decimal Universal, e obtive o seguinte resultado:

![image](https://github.com/user-attachments/assets/059c9110-d72c-417c-a5f2-811727075681)

Depois fiz uma investigação de sazonalidade (empréstimos por mês e hora do dia) e tendência (emprestimos em cada ano), construindo gráficos com Seaborn. Seguem os resultados:

## Análise Ano
![emprestimos_ano](https://github.com/user-attachments/assets/edcc7ce6-31aa-4386-9a5a-3d12cb03c8c2)

1. Há uma tendência de queda no número de empréstimos desde 2013, possivelmente impulsionada pelo fácil acesso a livros digitais pela internet. 
2. Não é recomendado contratar novos colaboradores, sendo necessário diminuir o quadro ao longo dos anos. Chama a atenção a grande queda em 2019. 2020 não é possível avaliar pois os dados não estão completos e foi ano da pandemia. 
3. É preciso investigar também outras causas que podem estar levando a essa queda, como o interesse por livros, a qualidade do acervo e o número de alunos matriculados.

## Análise Mês
![emprestimos_mes_sazonalidade](https://github.com/user-attachments/assets/039456eb-45fb-4738-a63f-2104ffe18777)

1. Os meses em que a frequencia de emprestimos é mais alta são março e agosto (principais), seguidos por fevereiro e abril (evitar liberar colaboradores).
2. Os meses mais tranquilos são janeiro e dezembro (principais, férias de verão), seguidos por junho, julho e novembro (melhores meses para dar férias aos colaboradores e fazer projetos administrativos).

## Análise Horário
![emprestimos_horario_sazonalidade](https://github.com/user-attachments/assets/d32c03d0-2e13-45b6-8603-6ae4b73b2531)

1. Os horários com mais emprestimos são às 16h e 10h (principais), seguidos por 17h e 18h (ter mais funcionários para atendimento ao público). 
2. Os horários com menos emprestimos são das 7h às 9h, 20h às 22h e 13h (podendo destinar mais funcionários para atividades administrativas e horários de almoço/jantar).
## Análise Exploratória Categorias
![image](https://github.com/user-attachments/assets/65c3f03d-a6e7-4f30-974e-6937d7749a8a)
![image](https://github.com/user-attachments/assets/a8569b84-46a3-48dc-b5bb-1350ac77f668)

Depois fiz uma análise exploratória das categorias, e os insights obtidos foram:
1. Quase 80% dos empréstimos são feitos pelos alunos de graduação, possivelmente por serem o maior público nas universidades (preicsamos de dados para confirmar se esse perfil se aplica a base). Alunos de pós-graduação e docentes são responsáveis por 14.6% e 3.4% dos empréstimos, será que esse público está sendo contemplado com os recursos necessários para atividades de pesquisa, ou há muita necessidade de livros/artigos que a biblioteca não disponibiliza? Muitos artigos podem ser acessados online em plataformas externas a universidade, por isso é esperado que o público de pós-graduação (mestrado, doutorado e latu sensu) use menos as bibliotecas.
2. Mais de 99% dos empréstimos são de Acervo Circulante, ou seja, livros físicos. Chama a atenção o baixo número de empréstimos de Monografias e Dissertações, e isso ocorre provavelmente porque esse material já está disponível na internet e já é acessado sem empréstimos (seria o caso de incluir na base as consultas a esses materiais para verificar a relevância desses materiais em termos de consulta). Os baixos índices de empréstimo de Obras Raras, Literatura de Cordel e Coleções Mossoroense e Zila Mamede também chamam a atenção, não há interesse por parte da comunidade acadêmica nessas obras? Ações de marketing podem reverter esse quadro.
3. Quase 70% dos empréstimos ocorre na Biblioteca Central Zila Mamede, provavelmente por ser onde estão concentrados o maior número de alunos. Uma métrica relevante seria avaliar o número de empréstimos por aluno em cada câmpus/setor associado a cada biblioteca, mas não temos dados suficientes.
4. Referente às Classificações Decimais Universais (por área científica), 68.8% dos empréstimos ocorre para Ciências Aplicadas (Engenharia, Medicina, Tecnologia da Informação) e 17.8% para Ciências Sociais, o que também corresponde muito ao perfil dos alunos da universidade. Provavelmente há muito mais cursos associados a Ciências Aplicadas dos que os demais. Uma análise mais profunda seria avalir o número de empréstimos pela quantidade de alunos matriculados em cada curso, mas também não temos informações suficientes para apurar essas informações. Entender também porque áreas como linguagem, belas artes e geogriafia estão com números tão baixos comparados aos demais exige um detalhamento do número de alunos matriculados e de formados (talvez há um índice de abandono dos cursos maior que nos demais)

Na sequência foi feita uma avaliação de distribuição de empréstimos por ano para os alunos de graduação e pós graduação, com Boxplot. Os resultados foram:

## Graduação
![boxplot_graduacao](https://github.com/user-attachments/assets/1a55f59f-0901-44e9-bda2-d3ca82820d8f)
- 2011 foi um dos anos com maior variação na quantidade de empréstimos, com 25% dos menores valores entre 809 e 9809.
- Os 2 menores valores para cada ano são de janeiro e dezembro (meses de fechamento e férias), em 2014 e 2017 foram detectados como outliers no Boxplot. 
- 2020 só tem dados de empréstimos até março, como janeiro são férias de graduação é esperado que as quantidades seja mais baixa. Como a pandemia da COVID-19 começou no final de fevereiro, é esperado que o número de empréstimos em fevereiro e março tenha sido menor que nos anos anteriores (se o calendário de graduação iniciou no final de fevereiro).
- Na maioria dos anos a mediana está mais próxima ao quartil 3 do que o quartil 1, ou seja, há mais meses com menos empréstimos do que a média do maiores (provavelmente por conta dos meses de janeiro e dezembro estarem inclusos no gráfico). A exceção é o ano de 2014, que foi um ano de redução significativa na quantidade de empréstimos em relação aos anos anteriores. Seria interessante entender o que causou essa queda.
- Em 2017 houve um aumento no número de empréstimos que seria interessante investigar o que ajudou a reverter a tendência de queda desde 2014.

## Pós-Graduação
![boxplot_posgraduacao](https://github.com/user-attachments/assets/f87f7cf5-25e2-4ca4-a812-f97772e47104)
- Quantidade de empréstimos ao longo do ano bem distribuída (mediana quase equidistante do quartil 1 e 3)
- Aumento da quantidade de empréstimos de 2010 a 2013, estagnação/leve redução até 2017 e redução brusca de 2018 em diante (o que será que aconteceu?)
- Em 2020 tivemos menos empréstimos mensais pelo mesmo motivo apontado para a graduação, somente dados até março, com fevereiro e março ruins por conta da pandemia e calendário possivelmente tardio.

Depois fiz uma análise de empréstimos por curso fazendo uma tabela resumo/dinâmica (Pivot Table)
Para isso foi fornecido tabelas em Excel e JSON (obtidos no sistema da universidade) com matrícula e curso dos alunos de graduação e pós-graduação. Foi feito o tratamento e filtragem das informações de interesse para chegar na tabela dinâmica (tanto para graduação quanto pós graduação).

Graduação de 2015 a 2020:
![image](https://github.com/user-attachments/assets/de5926ec-5d66-437d-88a4-2a4449edd4cc)

Pós-Graduação de 2017 a 2022 (sem dados de 2021):
![image](https://github.com/user-attachments/assets/1ebea963-d048-416c-9df3-c14556ae5374)

Ao final foram calculados os percentuais de variação do número de empréstimos por ano para os valores da tabela dinâmica por curso para os alunos de pós-graduação, sendo fornecido o número de empréstimos por curso em 2022 (foi necessário incluir na tabela dinâmica). Então a tabela foi formatada em HTML e CSS para ser incluída no site da universidade, como parte de uma campanha de marketing da Biblioteca. O resultado é apresentado abaixo:

![image](https://github.com/user-attachments/assets/9663bf8e-e32f-4d2e-8f34-827c290e3b24)

Vemos que de 2017 a 2019 as quedas foram no número de empréstimos foram expressivas, e a previsão é de aumento no número de empréstimos em 2022 em relação a 2019 para os cursos de Administração, Bioinformática e Ciências Odontológicas, principalmente, enquanto a queda persistiu em Ciências da Saúde e Engenharia Civil.

Obs: Na época em que o desafio foi criado, os dados de 2022 eram uma previsão. Como já estamos em 2025, considerei que a previsão se concretizou e essa análise foi feita agora para a universidade.
