# O que é React?

- É uma biblioteca front-end para construção de interfaces
- Utilizado para construir Single-Page Applications
  - As páginas não são rotas do backend, elas ficam no front-end.
- O ecossistema React é um framework
- Tudo fica dentro do Javascript
- React / ReactJS / React Native
  - React é a biblioteca do React, React Core
  - ReactJS é a junção de React e React DOM, é o React para browser
  - O React Native é o React para aplicações mobile.

# Vantagens do React

- Organização do código
  - Componentização
    - Dividir um monolito em vários componentes que possuem funcionalidades específicas
    - Isolar a lógica de um componente sem que ela interfica na aplicação ao todo
    - Conjunto de lógica, estruturação e estilização que juntos formam um componente que pode ser isolado da aplicação e não interferir no funcionamento dela.
- Divisão de responsabilidades
  - Regras de negócios ficam com o back-end
  - O front-end fica com a responsabilidade de mostrar os dados.
- Uma API, múltiplos clientes
  - Podemos servir os dados para aplicações mobile e web.
- Programação Declarativa vs Programação Imperativa
  - Programação Imperativa
    - O desenvolvedor descreve para o computador cada passo que é necessário.
  - Programação Declarativa
    - O desenvolvedor passa qual o resultado quer e a máquina retorna o esperado.

# JSX

- Permite escrever HTML dentro do Javascript
- Com React podemos criar nossos próprios elementos HTML
- As funções do Javascript podem retornar HTML

# Babel / Webpack

- O browser não entende todo esse código
- O Babel converte o código JS de uma forma que o browser entenda.
- O Webpack possui várias funções
  - Criação do bundle, arquivo com todo código da aplicação
  - Ensinar ao JS como importar arquivos CSS, imagens e etc...
  - Live reload com Webpack Dev Server

# Dependências utilizadas

- react
- react-dom
- @babel/core
- @babel/preset-env
- @babel/preset-react
- @babel/cli
- @babel/plugin-transform-runtime
- babel-loader
- webpack
- webpack-cli
- webpack-dev-server
- style-loader
- css-loader
- file-loader
- axios

# Configuração do Babel e Webpack

O babel server para transpilar (converter) o código de JS Moderno para o JS que o browser entende.
Já o Webpack faz a conversão para tipos de arquivo .js .css .png que estão embutidos no código Javascript
através de Loaders.

1. Inicializar projeto node
   1. `yarn init -y`
2. Adicionar pacotes react e react-dom
   1. `yarn add react react-dom`
3. Criar uma pasta `public` na raíz e dentro dele o arquivo `index.html`

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>ReactJS</title>
  </head>
  <body>
    <div id="app"></div>

    <script src="bundle.js"></script>
  </body>
</html>
```

4. Criar o arquivo `script.js` dentro da pasta `public`
5. Adicionar as dependências:
   1. `yarn add @babel/core @babel/preset-env @babel/preset-react webpack webpack-cli`
6. Criar o arquivo `babel.config.js` na raíz do projeto

```js
module.exports = {
  presets: ["@babel/preset-env", "@babel/preset-react"],
};
```

7. Criar pasta `src` e arquivo `index.js`
8. Adicionar a dependência
   1. `yarn add @babel/cli`
9. Para rodar o código usar
   1. `yarn babel src/index.js --out-file public/bundle.js`

## Agora o Babel já está configurado. Vamos configurar o webpack?

10. Instalar a dependência
    1.  `yarn add babel-loader style-loader css-loader file-loader @babel/plugin-transform-runtime`
11. Criar o arquivo `webpack.config.js` na raíz do projeto

```js
const path = require("path");
module.exports = {
  entry: path.resolve(__dirname, "src", "index.js"),
  output: {
    path: path.resolve(__dirname, "public"),
    filename: "bundle.js",
  },
  devServer: {
    contentBase: path.resolve(__dirname, "public"),
  },
  module: {
    rules: [
      {
        test: /\.js$/,
        exclude: /node_modules/,
        use: [
          {
            loader: "babel-loader",
          },
        ],
      },
      {
        test: /\.css$/,
        exclude: /node_modules/,
        use: [
          {
            loader: "style-loader",
          },
          {
            loader: "css-loader",
          },
        ],
      },
      {
        test: /.*\.gif|png|jpe?g$/i,
        use: [
          {
            loader: "file-loader",
          },
        ],
      },
    ],
  },
};
```

12. Para converter usar:

    1.  `yarn webpack --mode development`

13. Instalar o servidor de desenvolvimento do webpack
    1.  `yarn add webpack-dev-server -D`
14. Dentro do `webpack.config.js` adicionar a propriedade:

```js
devServer: {
  contentBase: path.resolve(__dirname, "public");
}
```

15. Para executar o dev-server

    1.  `yarn webpack-dev-server --mode development`

16. Incluir a linha de código abaixo no arquivo `package.json` para executar o servidor com o yarn

```json
"scripts": {
  "dev:server": "webpack-dev-server --mode development"
},
```

17. Arquivo `src/index.js`

```js
import React from "react";
import { render } from "react-dom";

render(<h1>Hello GoStack!</h1>, document.getElementById("app"));
```

# Componentização

- São conjuntos isolados de lógica, JS, visualização, HTML e possível estilização, CSS.
- Um componente dentro do React é uma função que retorna HTML.
- Todo componente no React deve começar com letra maiúscula e ter a importação do pacote `React`

## Exemplo:

```js
import React from "react";

function App() {
  return <h1>Hello World</h1>;
}

export default App;
```

- Devemos importar o nosso novo componente no `index.js`

```js
import React from "react";
import { render } from "react-dom";

import App from "./App";

render(<App />, document.getElementById("app"));
```

## Fragment?

É um elemento sem tag dentro. É um container sem valor semântico.

```js
<>

<>
```

# Propriedades

- É um informação passada de um componente pai para um componente filho.

Exemplo

```js
// title é passado como propriedade para o componente Header
<Header title="Homepage">
```

# Estado e imutabilidade

- O estado é configurado dentro de um componente.
- Estado são as propriedades de um classe que devem ser armazenadas para renderizamos o componente corretamente.

Exemplo

```js
// Definindo o estado da variável projects, a função que o alterará é setProjects
const [projects, setProjects] = useState([
  "Desenvolvimento de app",
  "Front-end web",
]);
```

```js
// Alterando o valor de projects. No react utilizamos o conceito de imutabilidade
// ou seja, ele nunca deve ser alterado diretamente e sim sobreposto.
function handleAddProject() {
  setProjects([...projects, `Novo projeto ${Date.now()}`]);
  console.log(projects);
}
```

# Conectar o front-end com o back-end feito em node

1. Adicionar a biblioteca `axios`
   1. `yarn add axios`
2. Criar o diretórios `src/services`
3. Criar um arquivo `api.js` dentro de `services`

- **useEffect**
  - Utilizamos para disparar funções sempre que tivermos alguma informação alterada ou quando quisermos disparar uma função quando um elemento acaba de ser renderizado em tela.

```js
// Primeiro parâmetro => Qual função eu desejo disparar
// Segundo parâmetro => Quando eu quero disparar uma função
useEffect(() => {}, []);
```
