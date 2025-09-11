# 🛠️ Web Services com Spring Boot e JPA/Hibernate  

Este projeto implementa uma aplicação **Java Spring Boot** para estudo e prática de **APIs RESTful**, utilizando **JPA/Hibernate** para persistência de dados. Foi desenvolvido com foco em **boas práticas de arquitetura**, organização em camadas e tratamento adequado de exceções.  

## 🚀 Objetivos do Projeto  
- Criar e estruturar uma aplicação Java com **Spring Boot**.  
- Implementar o **modelo de domínio** e relacionamentos entre entidades.  
- Estruturar as camadas: **resource, service e repository**.  
- Configurar banco de dados de teste em memória (**H2**).  
- Implementar operações **CRUD (Create, Retrieve, Update, Delete)**.  
- Tratar exceções personalizadas.  

---

## 🏗️ Arquitetura do Projeto  
O projeto segue uma arquitetura em **camadas**:  

- **Resource (Controller):** expõe endpoints REST.  
- **Service:** contém a lógica de negócios.  
- **Repository:** abstrai o acesso ao banco de dados usando **Spring Data JPA**.  

📌 Principais entidades e relacionamentos:  
- **User**  
- **Order** (com status e relacionamento com User)  
- **Category**  
- **Product** (com associação many-to-many com Category)  
- **OrderItem** (relacionamento many-to-many com atributos extras)  
- **Payment** (associação one-to-one com Order)  

---

## ⚙️ Tecnologias Utilizadas  
- **Java 17**  
- **Spring Boot**  
  - Spring Web  
  - Spring Data JPA  
- **Hibernate**  
- **Banco de dados H2** (para testes em memória)  
- **Maven** (gerenciamento de dependências)  
- **Docker** (melhoria adicionada por mim ao projeto)  

---

## 🗂️ Estrutura de Pastas  
```
src/
 └── main/
      ├── java/com/example/project
      │    ├── entities        # Modelo de domínio
      │    ├── repositories    # Interfaces JPA
      │    ├── services        # Regras de negócio
      │    └── resources       # Controladores REST
      └── resources/
           ├── application.properties
           └── application-test.properties
```  

---

## 🔗 Endpoints Exemplos  
### Usuários  
- `GET /users` → lista todos os usuários  
- `GET /users/{id}` → busca usuário por ID  
- `POST /users` → insere novo usuário  
- `PUT /users/{id}` → atualiza usuário existente  
- `DELETE /users/{id}` → remove usuário  

### Pedidos (Orders)  
- `GET /orders` → lista todos os pedidos  
- `GET /orders/{id}` → busca pedido por ID  

---

## 🛠️ Como Executar Localmente  
### Pré-requisitos  
- **Java 17+**  
- **Maven** instalado  

### Passos  
1. Clone o repositório:  
   ```bash
   git clone https://github.com/seu-usuario/seu-repo.git
   cd seu-repo
   ```  

2. Compile e rode o projeto:  
   ```bash
   mvn spring-boot:run
   ```  

3. Acesse no navegador:  
   ```
   http://localhost:8080/users
   ```  

4. Para acessar o console do **H2 Database**:  
   ```
   http://localhost:8080/h2-console
   ```
   - JDBC URL: `jdbc:h2:mem:testdb`  
   - User: `sa`  
   - Password: *(vazio)*  

---

## 🐳 Executando com Docker (Melhoria Pessoal 🚀)  
Como melhoria própria do projeto, adicionei um **Dockerfile** para facilitar a execução da aplicação sem necessidade de instalar dependências locais.  

### Passos  
1. Construa a imagem Docker:  
   ```bash
   docker build -t springboot-jpa-app .
   ```  

2. Rode o container:  
   ```bash
   docker run -p 8080:8080 springboot-jpa-app
   ```  

3. Acesse a aplicação em:  
   ```
   http://localhost:8080/users
   ```  

---

## 🛡️ Tratamento de Exceções  
O projeto possui tratamento customizado para:  
- **ResourceNotFoundException** → quando o recurso não é encontrado.  
- **DatabaseException** → erros de integridade ou exclusão.  

As respostas seguem um padrão JSON com timestamp, status e mensagem de erro.  

---

## 📚 Meus Aprendizados e Contribuições Pessoais  
Durante o desenvolvimento deste projeto pude:  
- Aprofundar meus conhecimentos em **modelagem de entidades complexas**, incluindo relacionamentos `OneToMany`, `ManyToMany` e `OneToOne`.  
- Praticar a criação de uma **arquitetura em camadas bem definida**, separando responsabilidades de controllers, serviços e repositórios.  
- Entender como funciona a configuração de diferentes **profiles** (test, dev, prod) e a importância dessa abordagem em ambientes reais.  
- Implementar **tratamento de exceções personalizado**, garantindo respostas consistentes para a API.  
- Consolidar minha prática no uso do **Spring Data JPA** e **Hibernate** para persistência de dados.  
- Trabalhar com **banco de dados em memória (H2)**, facilitando testes rápidos sem necessidade de configuração externa.  
- **Adicionar suporte a Docker**, permitindo que o projeto seja iniciado facilmente em qualquer ambiente sem configuração adicional. 🚀  

Esses pontos foram fundamentais para consolidar minha base em **Spring Boot e APIs RESTful**, além de me preparar para projetos mais robustos em ambiente profissional.  

---

## 👨‍💻 Autor  
Projeto desenvolvido como exercício de aprendizado com base no curso de **Java Spring Boot com JPA/Hibernate** do professor Nelio Alves.  
Adaptações e melhorias feitas por Sérgio Botelho.  
