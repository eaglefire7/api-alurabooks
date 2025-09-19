### DevOps Security

## 📖 Descrição do Projeto

Este projeto serve como um laboratório prático para os conceitos do curso **"DevOps: trabalhando com tráfego seguro em comunicações web"**. Mais do que uma simples API para um e-commerce, esta aplicação foi utilizada para explorar, diagnosticar e implementar as melhores práticas de segurança e comunicação na web moderna.

O foco principal foi analisar o fluxo de dados entre cliente e servidor, compreendendo as vulnerabilidades do HTTP e implementando uma comunicação segura com HTTPS, validando cada etapa com ferramentas profissionais.

## 🔬 Laboratório DevSecOps: Análise de Tráfego e Segurança

Esta seção detalha a lógica e os principais pontos de aprendizado obtidos durante o desenvolvimento, alinhados com as boas práticas de **DevOps**.

### 1. Análise de Requisições com Postman

O **Postman** foi utilizado como cliente para simular requisições e testar os endpoints da API, permitindo uma análise detalhada das particularidades dos métodos HTTP:

* **`GET`**: Usado para consultar dados, como a lista de livros. Foi observado como os parâmetros (ex: filtros de categoria) são enviados de forma visível na URL (`/livros?categoria=1`), o que é inadequado para dados sensíveis.
* **`POST`**: Implementado no endpoint de login (`/public/login`), demonstrou como enviar dados (email e senha) de forma mais discreta, no corpo (body) da requisição, uma prática essencial para o envio de informações sigilosas.

### 2. Monitoramento e Diagnóstico com Wireshark

O **Wireshark** funcionou como um "raio-x" da nossa rede, permitindo o monitoramento de todo o tráfego. O diagnóstico de segurança foi feito comparando duas capturas:
* **Tráfego HTTP**: Foi possível visualizar todas as informações das requisições, incluindo cabeçalhos e dados do corpo, em texto plano. Isso provou a total falta de confidencialidade do protocolo.
* **Tráfego HTTPS**: Ao ativar o servidor seguro, a captura no Wireshark mostrou que, após o handshake TLS, os dados da aplicação (`Application Data`) estavam **completamente ilegíveis e criptografados**. Foi a prova visual de que os dados sensíveis estavam protegidos.

### 3. Segurança de Dados Sensíveis com HTTPS

A transição de HTTP para HTTPS foi o ponto central do projeto. Utilizando o módulo `https` do Node.js com certificados **SSL/TLS**, a API passou a garantir:
* **Confidencialidade:** A criptografia impede que ataques de interceptação (Man-in-the-Middle) consigam ler os dados.
* **Integridade:** Assegura que os dados enviados não foram alterados no caminho.

### 4. Camada de Transporte e Boas Práticas DevOps

Para esta API, a camada de transporte escolhida foi o **TCP**, dada sua natureza confiável que garante a entrega ordenada dos pacotes, um requisito essencial para a integridade de requisições web e respostas de API. A utilização de ferramentas como Postman e Wireshark desde o início do ciclo de desenvolvimento para validar a segurança é uma **boa prática de DevSecOps**, antecipando problemas e garantindo que a segurança seja parte integral da aplicação ("Shift-left security").

## 🚀 Tecnologias Utilizadas

* **Node.js / Express.js**: Construção do servidor e gerenciamento das rotas.
* **JSON Server**: Prototipação rápida da API.
* **HTTPS/SSL**: Implementação da camada de segurança.
* **Postman**: Teste e validação dos endpoints.
* **Wireshark**: Análise e monitoramento do tráfego de rede.
* **Git & GitHub**: Versionamento de código.

## 🔧 Instalação e Execução

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

    * **Modo de Desenvolvimento (HTTP):**
        ```bash
        npm start
        ```
        *(Servidor em `http://localhost:3000`)*

    * **Modo Seguro (HTTPS):**
        ```bash
        npm run start-auth
        ```
        *(Servidor em `https://localhost:8000`)*

## 🔗 Endpoints da API

* `GET /livros`
* `GET /livros?categoria={id}`
* `GET /autores`
* `POST /public/login` (Apenas no modo HTTPS)
