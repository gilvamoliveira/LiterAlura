# LiterAlura

Catálogo de livros em Java que consulta a API pública [Gutendex](https://gutendex.com/) e grava livros e autores em PostgreSQL. Projeto do desafio final do Oracle Next Education (ONE), com foco em consumo de API, JPA e aplicação de console organizada em camadas.

## Como funciona

A aplicação sobe como um `CommandLineRunner`. Por padrão o menu fica desligado para não travar execuções em segundo plano e testes; com `--app.menu.enabled=true` ele abre no terminal:

```text
1 - Buscar livro pelo título
2 - Listar livros registrados
3 - Listar autores
4 - Listar autores vivos em determinado ano
5 - Listar livros por idioma
0 - Sair
```

Ao buscar por título, a aplicação consulta o Gutendex, converte o JSON em DTOs e salva o primeiro resultado (com o primeiro autor informado pela API).

## Stack

- Java 17
- Spring Boot 3
- Spring Data JPA / Hibernate
- PostgreSQL
- Jackson
- Maven

## Requisitos

- JDK 17
- PostgreSQL com um banco criado (o padrão é `SpringAlura`)

## Configuração

As credenciais vêm de variáveis de ambiente:

| Variável | Obrigatória | Padrão |
| --- | --- | --- |
| `DB_URL` | não | `jdbc:postgresql://localhost:5432/SpringAlura` |
| `DB_USERNAME` | sim | — |
| `DB_PASSWORD` | sim | — |

No PowerShell:

```powershell
$env:DB_USERNAME="postgres"
$env:DB_PASSWORD="sua-senha"
```

## Como executar

```bash
cd SpringAlura
mvn spring-boot:run -Dspring-boot.run.arguments=--app.menu.enabled=true
```

O `spring.jpa.hibernate.ddl-auto=update` cria/atualiza as tabelas na primeira execução. Em produção, o ideal é trocar isso por migrations versionadas.

## Testes

```bash
cd SpringAlura
mvn test
```

Os testes usam H2 em memória (`src/test/resources/application.properties`), então não precisam de PostgreSQL. Hoje a suíte tem apenas o teste de carregamento de contexto; as consultas e a integração com o Gutendex não estão cobertas.

## Estrutura

```text
SpringAlura/src/main/java/com/example/SpringAlura/
├── model/         Livro, Autor
├── dto/           DadosLivro, DadosAutor, DadosResultado
├── repository/    LivroRepository, AutorRepository
├── service/       ConsumoApi, ConverteDados, LivroService
└── principal/     Principal (menu e fluxo do console)
```

## Limitações

- Sem interface web: a saída é o terminal.
- A busca depende da disponibilidade e do formato do Gutendex.
- Buscas repetidas podem duplicar livro e autor: não há verificação de registro existente antes de salvar.
- `ddl-auto=update` em vez de migrations.
- Cobertura de testes restrita ao contexto da aplicação.

## Licença

MIT. Veja [LICENSE](LICENSE).

---

Feito por mim — [LinkedIn](https://www.linkedin.com/in/gilvam-oliveira/)
