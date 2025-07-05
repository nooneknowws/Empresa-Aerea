# Empresa Aerea: Sistema de Gerenciamento de Companhia Aérea

---

Este projeto, "Empresa Aerea", é um sistema web de gerenciamento de companhia aérea desenvolvido como trabalho acadêmico para a disciplina **"Desenvolvimento de Aplicações Corporativas - DAC"** do curso de TADS na Universidade Federal do Paraná.

### Visão Geral do Projeto

O sistema foi projetado para simular as operações de uma companhia aérea, fornecendo funcionalidades para gerenciar **voos**, **reservas** e, potencialmente, outros aspectos relacionados. Ele é construído com uma arquitetura moderna, separando o backend e o frontend em serviços distintos.

### Tecnologias Utilizadas

O projeto utiliza um conjunto robusto de tecnologias para entregar uma experiência abrangente e interativa:

**Backend:**
* **Spring Framework:** O backend é desenvolvido em **Java** com o framework **Spring**, seguindo uma arquitetura de microsserviços para escalabilidade e fácil manutenção.
    * Java (52,2% do código)

**Frontend:**
* **Angular:** A interface do usuário é construída com **Angular**, proporcionando uma aplicação web dinâmica e responsiva.
    * TypeScript (25,4% do código)
    * HTML (15,5% do código)
    * JavaScript (4,4% do código)
    * CSS (2,0% do código)

**Containerização:**
* **Dockerfile (0,5% do código):** A inclusão de um Dockerfile sugere que a aplicação é conteinerizada, facilitando a implantação consistente em diferentes ambientes.

### Padrões de Projeto

O backend da aplicação emprega diversos padrões de projeto para garantir a robustez, escalabilidade e manutenibilidade do sistema:

* **CQRS (Command Query Responsibility Segregation) no Microsserviço de Reserva:** Este padrão é aplicado no microsserviço de reserva para separar as operações de leitura (Queries) das operações de escrita (Commands). Isso permite otimizar cada lado independentemente, melhorando a performance e a escalabilidade, especialmente em sistemas com alta demanda de leituras ou escritas.

* **Saga Orquestrada para Comunicação com RabbitMQ:** Para gerenciar transações distribuídas entre os microsserviços, o projeto utiliza o padrão Saga, especificamente a abordagem orquestrada. O **RabbitMQ** é empregado como *broker* de mensagens, garantindo a comunicação assíncrona e confiável entre os serviços, o que é crucial para manter a consistência dos dados em um ambiente distribuído.

* **API Composition no Gateway:** O padrão API Composition é implementado no Gateway da aplicação. Isso significa que o Gateway agrega e compõe respostas de múltiplos microsserviços para atender a uma única requisição do cliente, simplificando a interação do frontend com o backend complexo.

* **DTOs (Data Transfer Objects):** DTOs são amplamente utilizados para transferir dados entre as camadas da aplicação (por exemplo, entre o frontend e o backend, ou entre diferentes microsserviços). Eles ajudam a encapsular e formatar os dados de forma eficiente, reduzindo a sobrecarga de comunicação e melhorando a segurança ao expor apenas os dados necessários.

### Estrutura do Projeto

O projeto segue uma arquitetura desacoplada:

* **Backend (Microsserviços - Spring):** Lida com a lógica de negócios, processamento de dados e *endpoints* da API.
* **Frontend (Angular):** Fornece a interface do usuário e interage com os serviços de backend.

---

### Como Executar

Para colocar o projeto em funcionamento, siga as instruções abaixo para o backend e o frontend:

#### Backend

Certifique-se de ter o **Docker** e o **Docker Compose** instalados em sua máquina.

1.  Navegue até a pasta raiz do backend do projeto no seu terminal.
2.  Execute o seguinte comando para construir e iniciar os serviços Docker:

    ```bash
    docker-compose up --build
    ```

Este comando irá construir as imagens Docker necessárias (caso ainda não existam) e iniciar todos os contêineres definidos no arquivo `docker-compose.yml`, incluindo os microsserviços e as dependências como o RabbitMQ.

#### Frontend

1.  Certifique-se de ter o **Node.js** e o **Angular CLI** instalados globalmente.
2.  Navegue até a pasta raiz do frontend do projeto no seu terminal.
3.  Instale as dependências do projeto com o comando:

    ```bash
    npm install
    ```

4.  Após a instalação das dependências, inicie o servidor de desenvolvimento do Angular com:

    ```bash
    ng serve
    ```

    Isso geralmente iniciará o frontend em `http://localhost:4200`.

---
