![image](https://github.com/user-attachments/assets/5280ac7e-122a-4e33-9948-7d8bb2282bd0)
# Gerenciamento de Séries

Este é um projeto de gerenciamento de séries, desenvolvido com o objetivo de aplicar conceitos avançados de Java, Spring Boot e JPA, além de explorar integrações externas. O projeto permite gerenciar informações sobre séries, suas temporadas e episódios, além de gerar insights utilizando a API do ChatGPT.

## 📋 Funcionalidades

- **CRUD de Séries**: Cadastro, edição, listagem e remoção de séries.
- **Relacionamentos JPA**:
  - Série ↔ Temporadas ↔ Episódios.
- **Consultas Avançadas**:
  - Geração de consultas derivadas.
  - Consultas personalizadas utilizando JPQL.
- **Persistência de Dados**: Banco de dados PostgreSQL para armazenar informações das séries e seus relacionamentos.
- **Integração com ChatGPT**: Geração de insights, resumos e recomendações automáticas para séries cadastradas.

## 🛠️ Tecnologias Utilizadas

- **Java 17**: Linguagem de programação principal.
- **Spring Boot 3**: Framework para desenvolvimento da aplicação.
  - Spring Data JPA: Mapeamento objeto-relacional e gerenciamento dos dados.
  - Spring Web: Para criação de endpoints RESTful.
  - Spring DevTools: Para facilitar o desenvolvimento.
- **PostgreSQL**: Banco de dados relacional.
- **API do ChatGPT**: Integração para análises automáticas.
- **Maven**: Gerenciamento de dependências.

```

## 🔧 Configuração e Execução

### Pré-requisitos

- **Java 17+** instalado.
- **PostgreSQL** configurado.
- **Docker** (opcional, mas recomendado para facilitar a execução).

### Passos para Executar

1. Clone o repositório:
   ```bash
   git clone https://github.com/seu-usuario/gerenciamento-series.git
   cd gerenciamento-series
   ```

2. Configure o banco de dados no arquivo `application.properties`:
   ```properties
   spring.datasource.url=jdbc:postgresql://localhost:5432/seriesdb
   spring.datasource.username=seu_usuario
   spring.datasource.password=sua_senha
   spring.jpa.hibernate.ddl-auto=update
   ```

3. Compile e execute o projeto:
   ```bash
   ./mvnw spring-boot:run
   ```

4. (Opcional) Execute o projeto com Docker:
   ```bash
   docker-compose up
   ```

5. Acesse a aplicação:
   - API REST: `http://localhost:8080/api/v1/series`
   - Documentação Swagger (se configurada): `http://localhost:8080/swagger-ui.html`

## 🫠 Exemplos de Consultas

### Consultas Derivadas
- Encontre todas as séries com determinada palavra no título:
  ```java
  Optional<Serie> findByTituloContainingIgnoreCase(String nomeSerie);
  ```

### Consultas JPQL
- Encontre episódios de uma temporada específica:
  ```java
    @Query("SELECT e FROM Serie s JOIN s.episodios e WHERE s.id = :id AND e.temporada = :numero")
    List<Episodio> obterEpisodiosPorTemporada(Long id, Long numero);
  ```

## 🌐 Integração com ChatGPT

A integração com o ChatGPT é feita utilizando a API oficial da OpenAI. Após cadastrar uma série, é possível gerar descrições automáticas e insights sobre ela. Certifique-se de configurar sua chave de API no arquivo `application.properties`:
```properties
chatgpt.api.key=your_openai_api_key
```

## 🚀 Melhorias Futuras

- Interface gráfica utilizando React ou Angular.
- Geração de relatórios em PDF.
- Integração com outras APIs de recomendação de séries.

## 📄 Licença

Este projeto está sob a licença MIT. Consulte o arquivo `LICENSE` para mais detalhes.

