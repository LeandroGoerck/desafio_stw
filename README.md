# Desafio-STW
Criar o frontend e o backend para criação e edição de listas de receitas

---

# Descritivo do desafio
A produção de uma fábrica de farinhas trabalha diariamente com diversos tipos de receitas.
Essas receitas possuem um conjunto de ingredientes que devem ser consumidos na ordem em que foram salvos.
Atualmente as receitas já estão organizadas em planilhas do Excel e são impressas sempre que uma receita é finalizada.
O desafio é implementar uma aplicação web para cadastro de receitas para eliminar a impressão em papel e facilitar o gerenciamento das mesmas.


Com as seguintes funcionalidades:
1. Receitas
  - [x] Listar receitas
  - [x] Listar uma determinada receita com seus respectivos ingredientes
  - [x] Adicionar uma nova receita com seus respectivos ingredientes
  - [x] Atualizar uma receita com seus respectivos ingredientes
  - [x] Excluir uma receita

2. Ingredientes
  - [x] Listar os ingredientes
  - [x] Adicionar um novo ingrediente
  - [x] Atualizar um ingrediente
  - [x] Excluir um ingrediente

---

# Sumário

- [Status](#status)
- [Licença](#licença)
- [Habilidades desenvolvidas](#habilidades-desenvolvidas)
- [Tecnologias utilizadas](#tecnologias-utilizadas)
- [Organização e Estruturação do Projeto](#organização-e-estruturação-do-projeto)
- [Organização e Estruturação do Banco de Dados](#organização-e-estruturação-do-banco-de-dados)  
- [Pré-requisitos](#pré-requisitos)
  - [Ferramentas necessárias](#ferramentas-necessárias)
  - [Rodando no servidor local](#rodando-no-servidor-local)
- [Orientações detalhadas de como utilizar a página WEB](#orientações-detalhadas-de-como-utilizar-a-página-WEB)
- [Orientações detalhadas de como utilizar a API](#orientações-detalhadas-de-como-utilizar-a-API)
  - [Ingredients](#ingredients)
    - [Ingredients create](#ingredients-create)
    - [Ingredients getAll](#ingredients-getall)
    - [Ingredients getById](#ingredients-getbyid)
    - [Ingredients updateById](#ingredients-updatebyid)
    - [Ingredients deleteById](#ingredients-deletebyid)
  - [Recipes](#recipes)
    - [Recipes create](#recipes-create)
    - [Recipes getAll](#recipes-getall)
    - [Recipes getById](#recipes-getbyid)
    - [Recipes updateById](#recipes-updatebyid)
    - [Recipes deleteById](#recipes-deletebyid)
    - [RecipesIngredient](#recipes-ingredient)
    - [RecipesIngredient addIngredient](#recipes-ingredient-addingredient)
    - [RecipesIngredient removeIngredient](#recipes-ingredient-removeingredient)
    - [RecipesIngredient updateIngredientById](#recipes-ingredient-updateingredientbyId)
    - [RecipesIngredient swapIngredients](#recipes-ingredient-swapingredients)
    - [RecipesCreate createOrUpdate](#recipes-create-createorupdate)

- [Contribuição](#contribuição)
- [Agradecimentos](#agradecimentos)
- [Autor](#autor)



  ---

# Status

Este projeto está em desenvolvimento.

---

# Licença

Este projeto está sob a licença [MIT](https://pt.wikipedia.org/wiki/Licen%C3%A7a_MIT).
---

# Habilidades desenvolvidas

- Criação do backend com express e typescript
- Teste das rotas utilizando Postman
- Integração com mysql utilizando Prisma ORM
- Desenvolvimento de telas com React, javascript e hooks
- Criação, leitura, edição e exclusão (CRUD) de ingredientes
- CRUD de receitas com ingredientes cadastrados

---

# Tecnologias utilizadas

- [Node.js](https://nodejs.org/en/)
- [Express.js](https://expressjs.com/pt-br/)
- [Typescript](https://www.typescriptlang.org/)
- [dotenv](https://www.npmjs.com/package/dotenv)
- [React](https://create-react-app.dev/docs/getting-started)
- [Tailwindcss](https://tailwindcss.com/docs/guides/create-react-app)
- [Postman](https://www.postman.com/)

---

# Organização e Estruturação do Projeto

O projeto está organizado e estruturado da seguinte maneira:
```
├── backend
│   ├── example.env
│   ├── package.json
│   ├── package-lock.json
│   ├── prisma
│   │   ├── migrations
│   │   │   ├── 20220819014704_1
│   │   │   │   └── migration.sql
│   │   │   └── migration_lock.toml
│   │   ├── schema.prisma
│   │   └── seed.ts
│   ├── src
│   │   ├── app.ts
│   │   ├── controllers
│   │   │   ├── ingredientsController.ts
│   │   │   └── recipesController.ts
│   │   ├── database
│   │   │   └── prismaClient.ts
│   │   ├── interfaces
│   │   │   ├── IAddIngredient.ts
│   │   │   ├── ICreateOrUpdateRecipe.ts
│   │   │   ├── ICreateRecipe.ts
│   │   │   ├── IIngredient.ts
│   │   │   ├── IRecipe.ts
│   │   │   └── ISwapIngredient.ts
│   │   ├── middlewares
│   │   │   └── errorMiddleware.ts
│   │   ├── routes
│   │   │   ├── ingredientsRoutes.ts
│   │   │   └── recipesRoutes.ts
│   │   ├── server.ts
│   │   └── services
│   │       ├── customError.ts
│   │       ├── errors.ts
│   │       ├── ingredientsService.ts
│   │       └── recipesService.ts
│   └── tsconfig.json
├── frontend
│   ├── package.json
│   ├── package-lock.json
│   ├── postcss.config.js
│   ├── public
│   │   ├── favicon.ico
│   │   ├── index.html
│   │   ├── manifest.json
│   │   ├── robots.txt
│   │   └── stw.svg
│   ├── README.md
│   ├── src
│   │   ├── App.css
│   │   ├── App.js
│   │   ├── App.test.js
│   │   ├── components
│   │   │   ├── AddIngredientToRecipeForm2.jsx
│   │   │   ├── AddIngredientToRecipeForm.jsx
│   │   │   ├── CodeAndDescriptionForm.jsx
│   │   │   ├── IngredientSelect.jsx
│   │   │   ├── IngredientsTable.jsx
│   │   │   ├── NavBar.jsx
│   │   │   ├── RecipesForm.jsx
│   │   │   ├── RecipesTable.jsx
│   │   │   ├── RecipeWithIngredientsTable2.jsx
│   │   │   └── RecipeWithIngredientsTable.jsx
│   │   ├── context
│   │   │   ├── GlobalContext.js
│   │   │   └── GlobalProvider.jsx
│   │   ├── helpers
│   │   │   └── request.js
│   │   ├── index.css
│   │   ├── index.js
│   │   ├── logo.svg
│   │   ├── pages
│   │   │   ├── Ingredients.jsx
│   │   │   ├── RecipeCreate.jsx
│   │   │   ├── RecipeDetails.jsx
│   │   │   └── Recipes.jsx
│   │   ├── reportWebVitals.js
│   │   ├── routes
│   │   │   └── index.js
│   │   └── setupTests.js
│   └── tailwind.config.js
├── imagens
│   └── planejamento_banco.png
├── package-lock.json
├── README.md
```
---
## Organização e Estruturação do Banco de Dados  
O banco de dados utilizado está ilustrado na figura abaixo:
  ![Planejamento do Banco](./imagens/planejamento_banco.png)

---
# Pré-requisitos

## Ferramentas necessárias

Para rodar o projeto, você vai precisar instalar as seguintes ferramentas:
 - [Git](https://git-scm.com);
 - [Node.js >= 14.17](https://nodejs.org/en/);
 - Um editor para trabalhar com o código como [VSCode](https://code.visualstudio.com/) ou outro de sua preferência;

 ## Rodando no servidor local

 - Clone do Projeto e instale as dependências

    - Clone este repositório
    ```bash
    git clone git@github.com:LeandroGoerck/desafio-stw.git
    ```

    - Acesse a pasta do projeto no terminal/cmd
    ```bash
    cd desafio-stw
    ```

    - Instale as dependências do backend e do frontend
    ```bash
    cd backend/ && npm install && cd ../frontend && npm install
    ```
    - Configure as variaveis de ambiente
    No ubuntu
 - Renomeie o arquivo `example.env` para `.env` ou crie um novo arquivo chamado `.env` na raiz do projeto de backend com as seguintes configurações:
    - DATABASE_URL="mysql://root:1234@localhost:3306/banco_receitas"
  
    Se você estiver usando WSL, digite o comando:
    ```bash
    set DATABASE_URL="mysql://root:1234@localhost:3306/banco_receitas"
    ```  
    - Suba uma instância do banco de dados mysql:
    Utilizando um container docker:
    ```bash
    docker run -p 3306:3306 --name mysql_80 -e MYSQL_ROOT_PASSWORD=1234 -d mysql:8 mysqld --default-authentication-plugin=mysql_native_password
    ```

    - Rode as migrations do prisma para criar as tabelas:
    ```bash
    npx prisma migrate dev --name init
    ```

 - Inicie o sistema:

    - Inicie o backend
    ```bash
    cd backend && npm start
    ```
    - Inicie o frontend
    ```bash
    cd frontend && npm start
    ```
    Abra em qualquer navegador http://localhost:3000/

---
# Orientações detalhadas de como utilizar a página WEB

A ser implementado.

---
# Orientações detalhadas de como utilizar a API
A ser implementado.
  ### Ingredients
    - [Ingredients create](#ingredients-create)
    - [Ingredients getAll](#ingredients-getall)
    - [Ingredients getById](#ingredients-getbyid)
    - [Ingredients updateById](#ingredients-updatebyid)
    - [Ingredients deleteById](#ingredients-deletebyid)
  ### Recipes
    - [Recipes create](#recipes-create)
    - [Recipes getAll](#recipes-getall)
    - [Recipes getById](#recipes-getbyid)
    - [Recipes updateById](#recipes-updatebyid)
    - [Recipes deleteById](#recipes-deletebyid)
    - [RecipesIngredient](#recipes-ingredient)
    - [RecipesIngredient addIngredient](#recipes-ingredient-addingredient)
    - [RecipesIngredient removeIngredient](#recipes-ingredient-removeingredient)
    - [RecipesIngredient updateIngredientById](#recipes-ingredient-updateingredientbyId)
    - [RecipesIngredient swapIngredients](#recipes-ingredient-swapingredients)
    - [RecipesCreate createOrUpdate](#recipes-create-createorupdate)

## Contribuição
## Agradecimentos
## Autor