
Exercício Prático: Modelagem e Consultas em MongoDB
Este exercício visa consolidar os conceitos de modelagem NoSQL (Incorporação vs. Referência) e o uso do Framework de Agregação.

Parte 1: Modelagem de Dados
Imagine que você está desenvolvendo um sistema para uma Plataforma de Cursos Online .

Incorporação (Incorporação): Crie um documento para um curso que já contenha uma matriz de "módulos" (com nome e carga horária) dentro dele.

Pergunta: Por que, neste caso, colocar os módulos dentro do documento do curso (incorporar) é melhor para o desempenho de leitura?
Referência: Crie dois documentos separados: um para um Instrutor e outro para um Curso , conectando o curso ao instrutor através de um identificador ( instrutor_id).

Pergunta: Em que situação seria preferível referenciar o instrutor em vez de copiar os dados dele dentro de cada curso que ele ministra?
Parte 2: Consultas e Filtros
Utilize uma coleção clientese os operadores JSON para responder às seguintes questões:

Filtro de Existência: Escreva o comando find()para encontrar todos os clientes que possuem o campo emailpreenchido (utilize o operador $exists).
Filtro de Comparação: Escreva uma consulta para encontrar clientes com idademaior ou igual a 21 anos (utilize o operador $gte).
Filtro Complexo: Como você busca clientes que moram na cidade "São Paulo" E têm idade inferior a 30 anos ( $lt)?
Parte 3: Estrutura de Agregação (Relatórios)
Considere uma coleção chamada vendascom a seguinte estrutura de exemplo: { produto: "Webcam", categoria: "Periféricos", quantidade: 3, preco_unitario: 200.00, status: "concluída" }

Crie um pipeline de agregação para gerar um relatório que:

Filtre apenas as vendas com o status: "concluída".
Agrupe os dados por categoria.
Calcule a soma total da quantidadevendida por categoria.
