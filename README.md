LiterAlura
-----

*Descrição*

Projeto desenvolvido como parte do programa ONE (Oracle Next Education) em parceria com a Alura, com o objetivo de praticar conceitos de Java, Spring Boot, consumo de APIs e persistência de dados em banco relacional.
O LiterAlura é um catálogo de livros que consome dados da API pública Gutendex, permitindo buscar livros por título e armazená-los em um banco de dados. Após o cadastro, é possível realizar consultas diretamente no banco de dados sobre livros e autores.

Este projeto foi desenvolvido como desafio prático dentro da formação ONE - Oracle Next Education, reforçando habilidades essenciais para desenvolvimento backend com Java e Spring.

-------

*Funcionalidades*

Buscar um livro pelo título e salvar informações de livro e autor no banco de dados.

Listar todos os livros cadastrados.

Listar todos os autores cadastrados.

Listar livros por idioma.

Possibilidade de expansão para consultas adicionais de autores por ano.

------

*Tecnologias*

Java 17+

Spring Boot 3+

Spring Data JPA

H2 / MySQL / PostgreSQL (configurável)

Maven

------

*Objetivo do Projeto*

Este projeto foi desenvolvido com foco em praticar:

Consumo de APIs externas

Persistência de dados com JPA

Integração com banco de dados relacional

Estruturação de aplicações backend com Spring Boot

------

*Configuração*

As credenciais não ficam no código. Defina as variáveis de ambiente antes de executar:

DB_URL (opcional, padrão: jdbc:postgresql://localhost:5432/SpringAlura)

DB_USERNAME (obrigatória)

DB_PASSWORD (obrigatória)

Exemplo no PowerShell:

$env:DB_USERNAME="postgres"

$env:DB_PASSWORD="sua-senha"

mvn spring-boot:run

O menu interativo é opcional e fica desativado por padrão para não bloquear testes e execuções em segundo plano. Para habilitá-lo:

mvn spring-boot:run -Dspring-boot.run.arguments=--app.menu.enabled=true

---

Autor: Gilvam Oliveira · [LinkedIn](https://www.linkedin.com/in/gilvam-oliveira/)
