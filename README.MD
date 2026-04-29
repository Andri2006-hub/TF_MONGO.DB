# Proposta de Aula Prática: MongoDB com mongosh

## Objetivo
Compreender a flexibilidade do modelo de documentos e praticar operações CRUD essenciais utilizando o `mongosh`.

## Cenário
Vamos construir um sistema simplificado de Catálogo de E-commerce, onde os alunos experimentarão a criação de produtos com atributos variados, aproveitando o esquema flexível do MongoDB.

## Catálogo de Dados de Referência
Coleção: `produtos`

Cada documento representa um produto da loja virtual. Apesar de pertencerem à mesma coleção, os documentos podem ter campos diferentes de acordo com a categoria.

Exemplo 1: Smartphone
```json
{
  nome: "Smartphone Galaxy A15",
  categoria: "Eletronicos",
  preco: 1299.90,
  marca: "Samsung",
  armazenamento: "128GB",
  cor: "Azul"
}
```

Exemplo 2: Livro
```json
{
  nome: "MongoDB na Pratica",
  categoria: "Livros",
  preco: 79.90,
  autor: "Joao Silva",
  editora: "Tech Books",
  paginas: 320
}
```

Exemplo 3: Camisa
```json
{
  nome: "Camiseta Basica",
  categoria: "Roupas",
  preco: 49.90,
  tamanho: "M",
  cor: "Preta",
  material: "Algodao"
}
```

Exemplo 4: Caderno
```json
{
  nome: "Notebook Ultra X",
  categoria: "Eletronicos",
  preco: 3899.90,
  marca: "Lenovo",
  memoria_ram: "16GB",
  processador: "Intel i7"
}
```

Exemplo 5: Tênis
```json
{
  nome: "Tenis Runner Pro",
  categoria: "Calcados",
  preco: 299.90,
  tamanho: 42,
  cor: "Branco",
  marca: "Olympikus"
}
```

## Observação sobre o modelo
No MongoDB, documentos da mesma coleção não precisam ter exatamente os mesmos campos. Essa flexibilidade permite que produtos de diferentes categorias sejam armazenados juntos sem a obrigação de um esquema fixo.

## Parte 1: Exercícios Práticos

### Exercício 1: Criação e Coleções (O "C" do CRUD)
1. Conecte ao MongoDB com `mongosh`.
2. Crie um banco de dados chamado `loja_virtual`:
   ```js
   use loja_virtual
   ```
3. Crie uma coleção `produtos` e insira um produto simples usando `insertOne()`:
   ```js
   db.produtos.insertOne({
     nome: "Smartphone Galaxy A15",
     categoria: "Eletronicos",
     preco: 1299.90,
     marca: "Samsung",
     armazenamento: "128GB",
     cor: "Azul"
   })
   ```
4. Insira pelo menos dois outros produtos de categorias diferentes usando `insertMany()`:
   ```js
   db.produtos.insertMany([
     {
       nome: "MongoDB na Pratica",
       categoria: "Livros",
       preco: 79.90,
       autor: "Joao Silva",
       editora: "Tech Books",
       paginas: 320
     },
     {
       nome: "Camiseta Basica",
       categoria: "Roupas",
       preco: 49.90,
       tamanho: "M",
       cor: "Preta",
       material: "Algodao"
     }
   ])
   ```

### Exercício 2: Consultas e Filtros (O "R" do CRUD)
1. Liste todos os produtos da coleção:
   ```js
   db.produtos.find().pretty()
   ```
2. Busque apenas produtos onde o preço seja superior a 100:
   ```js
   db.produtos.find({ preco: { $gt: 100 } }).pretty()
   ```
3. Liste apenas os produtos da categoria `Eletronicos`:
   ```js
   db.produtos.find({ categoria: "Eletronicos" }).pretty()
   ```
4. Realize uma busca que retorne apenas o `nome` e o `preco` dos produtos:
   ```js
   db.produtos.find({}, { nome: 1, preco: 1, _id: 0 }).pretty()
   ```

### Exercício 3: Atualização Dinâmica (O "U" do CRUD)
1. Atualize o preço de um produto específico usando o operador `$set`:
   ```js
   db.produtos.updateOne(
     { nome: "Smartphone Galaxy A15" },
     { $set: { preco: 1199.90 } }
   )
   ```
2. Adicione um novo campo chamado `estoque` para todos os produtos com `updateMany()`:
   ```js
   db.produtos.updateMany({}, { $set: { estoque: 50 } })
   ```
3. Marque os produtos da categoria `Roupas` com o campo `promocao: true`:
   ```js
   db.produtos.updateMany(
     { categoria: "Roupas" },
     { $set: { promocao: true } }
   )
   ```

### Exercício 4: Exclusão de Dados (O "D" do CRUD)
1. Remova um produto específico usando `deleteOne()`:
   ```js
   db.produtos.deleteOne({ nome: "Tenis Runner Pro" })
   ```
2. Remova todos os produtos de uma categoria usando `deleteMany()`:
   ```js
   db.produtos.deleteMany({ categoria: "Livros" })
   ```

---

## Dicas para a turma
- Explique que no MongoDB não há necessidade de esquema fixo.
- Mostre como cada documento pode ter campos diferentes.
- Encoraje os alunos a inserir produtos adicionais com estruturas variadas.
