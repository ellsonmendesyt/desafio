# Back-end

Sua tarefa é construir uma API e banco de dados para uma aplicação simples que gerencia ferramentas com seus respectivos nomes, links, descrições e tags.

A aplicação pode ser construída utilizando qualquer linguagem, banco de dados, frameworks, libraries e ferramentas de sua preferência (Ex: Node + Express + Mongoose + MongoDB, PHP + Lumen + RedBean + PostgreSQL, etc). Apesar disso, a stack mais comum aqui é **Node.js**, seguida por **PHP**, e seria ótimo escolher uma das duas.

A API deverá ser documentada utilizando o [Stoplight](https://stoplight.io/), [API Blueprint](https://apiblueprint.org/) ou [Swagger](https://swagger.io/docs/specification/basic-structure/).

## O que será avaliado

Queremos avaliar sua capacidade de desenvolver e documentar um back-end para uma aplicação. Serão avaliados:

- Código bem escrito e limpo;
- Organização estrutural do projeto
- Quais ferramentas foram usadas, como e por quê, além do seu conhecimento das mesmas;
- Seu conhecimento em banco de dados, requisições HTTP, APIs REST, etc;
- Sua capacidade de se comprometer com o que foi fornecido;
- Sua capacidade de documentação da sua parte da aplicação.

## O mínimo necessário

- Uma aplicação contendo uma API real simples, sem autenticação, que atenda os requisitos descritos abaixo, fazendo requisições à um banco de dados para persistência;
- README.md contendo informações básicas do projeto e como executá-lo;
- Documentação da aplicação utilizando uma das ferramentas indicadas: [Stoplight](https://stoplight.io/), [API Blueprint](https://apiblueprint.org/) ou [Swagger](https://swagger.io/docs/specification/basic-structure/).

## Bônus

Os seguintes itens não são obrigatórios, mas darão mais valor ao seu trabalho (os em negrito são mais significativos para nós)

- Uso de ferramentas externas que facilitem o seu trabalho;
- Cuidados especiais com otimização, padrões, entre outros;
- Migrations ou script para configuração do banco de dados utilizado;
- **Testes**;
- **Disponibilização de um endpoint GraphQL**;
- **Conteinerização da aplicação**;
- **Autenticação e autorização** (**OAuth, JWT**);

# Requisitos

## 1) A API deve responder na porta 3000

## 2) Deve haver uma rota para listar todas as ferramentas cadastradas

`GET /tools`

Resposta:

```jsx
[
    {
        id: 1,
        title: "Notion",
        link: "https://notion.so",
        description: "All in one tool to organize teams and ideas. Write, plan, collaborate, and get organized. ",
        tags: [
            "organization",
            "planning",
            "collaboration",
            "writing",
            "calendar"
        ]
    },
    {
        id: 2,
        title: "json-server",
        link: "https://github.com/typicode/json-server",
        description: "Fake REST API based on a json schema. Useful for mocking and creating APIs for front-end devs to consume in coding challenges.",
        tags: [
            "api",
            "json",
            "schema",
            "node",
            "github",
            "rest"
        ]
    },
    {
        id: 3,
        title: "fastify",
        link: "https://www.fastify.io/",
        description: "Extremely fast and simple, low-overhead web framework for NodeJS. Supports HTTP2.",
        tags: [
            "web",
            "framework",
            "node",
            "http2",
            "https",
            "localhost"
        ]
    }
]
```

## 3) Deve ser possível filtrar ferramentas utilizando uma busca por tag

`GET /tools?tag=node`   (*node* é a tag sendo buscada neste exemplo)

Resposta:

```jsx
[
    {
        id: 2,
        title: "json-server",
        link: "https://github.com/typicode/json-server",
        description: "Fake REST API based on a json schema. Useful for mocking and creating APIs for front-end devs to consume in coding challenges.",
        tags: [
            "api",
            "json",
            "schema",
            "node",
            "github",
            "rest"
        ]
    },
    {
        id: 3,
        title: "fastify",
        link: "https://www.fastify.io/",
        description: "Extremely fast and simple, low-overhead web framework for NodeJS. Supports HTTP2.",
        tags: [
            "web",
            "framework",
            "node",
            "http2",
            "https",
            "localhost"
        ]
    }
]
```

## 4) Deve haver uma rota para cadastrar uma nova ferramenta

O corpo da requisição deve conter as informações da ferramenta a ser cadastrada, sem o ID (gerado automaticamente pelo servidor). A resposta, em caso de sucesso, deve ser o mesmo objeto, com seu novo ID gerado.

`POST /tools
Content-Type: application/json`

```jsx
{
    "title": "hotel",
    "link": "https://github.com/typicode/hotel",
    "description": "Local app manager. Start apps within your browser, developer tool with local .localhost domain and https out of the box.",
    "tags":["node", "organizing", "webapps", "domain", "developer", "https", "proxy"]
}
```

Resposta:

`Status: 201 Created`

`Content-Type: application/json`

```jsx
{
    "title": "hotel",
    "link": "https://github.com/typicode/hotel",
    "description": "Local app manager. Start apps within your browser, developer tool with local .localhost domain and https out of the box.",
    "tags":["node", "organizing", "webapps", "domain", "developer", "https", "proxy"],
    "id":5
}
```

## 5) O usuário deve poder remover uma ferramenta por ID

`DELETE /tools/:id`

Resposta:

`Status: 200 OK`

```jsx
{}
```


# Critérios de Aceitação

- A API deve ser real e escrita por você. Ferramentas que criam APIs automaticamente (Loopback, json-server, etc) não são aceitas;
- Todos os requisitos acima devem ser cumpridos, seguindo o padrão de rotas estabelecido;
- Deve haver um documento de Stoplight, API Blueprint ou OpenAPI (antigo Swagger) descrevendo sua API;
- Se você julgar necessário, adequado ou quiser deixar a aplicação mais completa (bônus!) você pode adicionar outras rotas, métodos, meios de autenticação com usuários, etc.

Ao término do desafio, você deve enviar o link do seu repositório [GitHub](https://github.com/) no formulário de resposta.
