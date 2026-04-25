Configuração do PostgreSQL no Spring Boot

Este projeto utiliza Spring Boot com Spring Data JPA para persistência de dados. Para rodar corretamente, é necessário configurar a conexão com o banco de dados PostgreSQL no arquivo application.properties.

Pré-requisitos

PostgreSQL instalado (versão 12 ou superior)

Um banco de dados criado (exemplo: catalogo)

Usuário e senha válidos para acesso ao banco (exemplo: usuário postgres)

Passos de configuração

Criar o banco de dados

CREATE DATABASE catalogo;

Verificar usuário e senha

O usuário padrão do PostgreSQL é postgres.

Defina uma senha segura para este usuário.

Editar o arquivo application.properties Localize o arquivo em src/main/resources/application.properties e configure:

spring.datasource.url=jdbc:postgresql://localhost:5432/catalogo
spring.datasource.username=postgres
spring.datasource.password=suasenha

spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.PostgreSQLDialect

Substitua catalogo pelo nome do seu banco.

Substitua suasenha pela senha definida para o usuário postgres.

Executar o projeto

Inicie o PostgreSQL.

Rode a aplicação com:

mvn spring-boot:run

Verificar conexão

Se configurado corretamente, o Spring Boot criará as tabelas automaticamente no banco.

Logs de inicialização mostrarão a conexão estabelecida com sucesso.

Dicas

Se quiser rodar o projeto sem banco de dados, adicione no application.properties:

spring.autoconfigure.exclude=org.springframework.boot.autoconfigure.jdbc.DataSourceAutoConfiguration,org.springframework.boot.autoconfigure.orm.jpa.HibernateJpaAutoConfiguration

Isso desativa a configuração automática de JPA e JDBC.

Com essa configuração, o projeto estará pronto para rodar com PostgreSQL integrado ao Spring Boot.
