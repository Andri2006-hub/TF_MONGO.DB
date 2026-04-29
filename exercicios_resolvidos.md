# Exercícios Resolvidos: MongoDB com mongosh

## Roteiro Passo a Passo

### 1. Conectar ao MongoDB
Abra o `mongosh` e use o banco de dados `loja_virtual`:
```js
use loja_virtual
```

### 2. Criar a coleção e inserir documentos
Insira o smartphone com `insertOne()`:
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

Insira mais produtos com `insertMany()`:
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
  },
  {
    nome: "Tenis Runner Pro",
    categoria: "Calcados",
    preco: 299.90,
    tamanho: 42,
    cor: "Branco",
    marca: "Olympikus"
  }
])
```

## Exercícios Resolvidos

### Exercício 2: Consultas e Filtros
- Todos os produtos:
```js
db.produtos.find().pretty()
```
- Produtos com preço superior a 100:
```js
db.produtos.find({ preco: { $gt: 100 } }).pretty()
```
- Produtos da categoria `Eletronicos`:
```js
db.produtos.find({ categoria: "Eletronicos" }).pretty()
```
- Apenas `nome` e `preco`:
```js
db.produtos.find({}, { nome: 1, preco: 1, _id: 0 }).pretty()
```

### Exercício 3: Atualização Dinâmica
- Atualizar preço de produto específico:
```js
db.produtos.updateOne(
  { nome: "Smartphone Galaxy A15" },
  { $set: { preco: 1199.90 } }
)
```
- Adicionar campo `estoque` a todos os produtos:
```js
db.produtos.updateMany({}, { $set: { estoque: 50 } })
```
- Marcar `promocao: true` para `Roupas`:
```js
db.produtos.updateMany(
  { categoria: "Roupas" },
  { $set: { promocao: true } }
)
```

### Exercício 4: Exclusão de Dados
- Remover um produto específico:
```js
db.produtos.deleteOne({ nome: "Tenis Runner Pro" })
```
- Remover todos os produtos de uma categoria:
```js
db.produtos.deleteMany({ categoria: "Livros" })
```

## Observações Úteis
- A coleção `produtos` aceita documentos com campos diferentes.
- Use `find().pretty()` para ver melhor os documentos.
- Incrementar o catálogo com outras categorias é uma boa prática para mostrar flexibilidade.
