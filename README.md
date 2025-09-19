# API do Projeto Alurabooks

![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)

## 📖 Descrição do Projeto

Esta é a API backend para o projeto **Alurabooks**, uma plataforma de e-commerce de livros. O projeto foi desenvolvido como parte dos estudos sobre desenvolvimento web, focando em conceitos de comunicação cliente-servidor, protocolos HTTP/HTTPS, segurança e diagnóstico de rede.

A API é responsável por servir os dados de livros, categorias, autores e pedidos, além de simular um endpoint de autenticação.

## ✨ Principais Pontos e Lógica Utilizada

* **Comunicação Segura:** Implementação de um servidor **HTTPS** utilizando certificados SSL/TLS locais (`server.key` e `server.crt`) para garantir que os dados trafeguem de forma criptografada, protegendo contra ataques de interceptação.
* **Servidor Duplo:** O projeto pode ser executado em dois modos:
    1.  Um servidor de desenvolvimento simples com `json-server` (HTTP na porta 3000).
    2.  Um servidor robusto com `Node.js` e `Express` (HTTPS na porta 8000), que representa um ambiente mais próximo da produção.
* **Endpoints RESTful:** A API segue princípios REST para a consulta de recursos, como a listagem e filtragem de livros.
* **Diagnóstico e Verificação:** O desenvolvimento incluiu o uso de ferramentas como **Postman** para testar os endpoints e **Wireshark** para analisar o tráfego de rede e confirmar a eficácia da criptografia HTTPS.

## 🚀 Tecnologias Utilizadas

* **Node.js:** Ambiente de execução do JavaScript no lado do servidor.
* **Express.js:** Framework para a construção da API e gerenciamento das rotas.
* **JSON Server:** Ferramenta para prototipação rápida de APIs a partir de um arquivo JSON.
* **HTTPS/SSL:** Módulo `https` do Node.js para criação do servidor seguro.
* **Git & GitHub:** Para versionamento de código e portfólio.

## 🔧 Instalação e Execução

Siga os passos abaixo para executar o projeto localmente.

**Pré-requisitos:**
* [Node.js](https://nodejs.org/en/) (que já inclui o npm)
* [Git](https://git-scm.com/)

**Passos:**

1.  **Clone o repositório:**
    ```bash
    git clone [https://github.com/eaglefire7/api-alurabooks.git](https://github.com/eaglefire7/api-alurabooks.git)
    ```

2.  **Navegue até a pasta do projeto:**
    ```bash
    cd api-alurabooks
    ```

3.  **Instale as dependências:**
    ```bash
    npm install
    ```

4.  **Inicie o servidor (escolha uma das opções):**

    * **Opção A: Modo de Desenvolvimento Simples (HTTP)**
        ```bash
        npm start
        ```
        *(O servidor estará disponível em `http://localhost:3000`)*

    * **Opção B: Modo Seguro com Autenticação (HTTPS)**
        ```bash
        npm run start-auth
        ```
        *(O servidor estará disponível em `https://localhost:8000`)*


## 🔗 Endpoints da API

Abaixo estão os principais endpoints disponíveis.

#### Livros
* `GET /livros` - Retorna uma lista de todos os livros.
* `GET /livros/{id}` - Retorna os detalhes de um livro específico.
* `GET /livros?categoria={id_categoria}` - Retorna todos os livros de uma categoria específica.
    * *Exemplo:* `http://localhost:3000/livros?categoria=1`

#### Outros Recursos
* `GET /autores` - Retorna uma lista de todos os autores.
* `GET /categorias` - Retorna uma lista de todas as categorias.
* `GET /pedidos` - Retorna uma lista de todos os pedidos.

#### Autenticação (Apenas no modo HTTPS)
* `POST /public/login` - Endpoint para autenticação de usuários.
    * **Corpo da requisição (JSON):**
        ```json
        {
          "email": "seu-email@exemplo.com",
          "senha": "sua-senha"
        }
        ```

## 📄 Licença

Este projeto está sob a licença MIT.