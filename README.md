# Api Votação

## Descrição

A **API de Votação** é um sistema desenvolvido com Spring Boot e Maven, projetado para permitir que associados votem em pautas. O projeto gerencia sessões de votação, registros de associados, criação de pautas e cálculo de resultados. Ele oferece endpoints para a interação com o sistema de votação, garantindo a integridade e a funcionalidade das votações.

## Tecnologias

- **Java** (Spring Boot)
- **Maven** (Gerenciamento de dependências)
- **SQL** (Banco de dados)

## Instalação

1. Clone o repositório:
    ```bash
    git clone https://github.com/leozeraxp/apivotacao.git
    cd api-votacao
    ```

2. Instale as dependências do projeto usando Maven:
    ```bash
    mvn install
    ```

3. **Configuração do Banco de Dados:**

    Você precisará de um banco de dados SQL. O projeto foi desenvolvido para funcionar com um banco de dados relacional, como MySQL ou PostgreSQL.

    - Crie um banco de dados no seu ambiente SQL.
    - No arquivo `application.properties` ou `application.yml`, configure a URL do banco de dados, usuário e senha. Exemplo para MySQL:

      ```properties
      spring.datasource.url=jdbc:mysql://localhost:3306/api_votacao
      spring.datasource.username=seu_usuario
      spring.datasource.password=sua_senha
      spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
      spring.jpa.hibernate.ddl-auto=update
      spring.jpa.database-platform=org.hibernate.dialect.MySQL8Dialect
      ```

4. Execute o aplicativo:
    ```bash
    mvn spring-boot:run
    ```

A API estará disponível na URL base `http://localhost/api/`.

## Endpoints

### 1. Registrar Associado

**POST**: `/api/associado`

Exemplo de Payload:
```json
{
  "nome": "Jose Moreira",
  "cpf": "36341686099"
}
```

### 2 . Criar Pauta
**POST**: /api/pauta

Exemplo de Payload:

```json
{
  "descricao": "Teste"
}
```

### 3. Criar Sessão de Votação
**POST**: /api/sessao

Exemplo de Payload:

```json
{
  "pauta": {
    "id": "1"
  },
  "fim": "2024-12-05T16:30:00"
}
```

### 4. Registrar Voto
**POST**: /api/voto/votar

Exemplo de Payload:

```json
{
  "associado": {
    "id": "1"
  },
  "sessao": {
    "id": "1"
  },
  "opcaoVoto": "NAO"
}
```

### 5. Calcular Resultado
**POST**: /api/resultado/calcular/{idSessao}

Exemplo:

**POST**: /api/resultado/calcular/2


### 6. Obter Resultado
**GET**: /api/resultado/{idSessao}

Exemplo:

**GET**: /api/resultado/1

### Executando Testes

## Como Executar os Testes

Este projeto utiliza o **JUnit** para garantir que todas as funcionalidades estão funcionando corretamente. Para garantir a qualidade do código, executamos testes de unidade e de integração para validar o comportamento esperado. Aqui estão os passos para executar os testes de forma local.

### Pré-requisitos

Certifique-se de ter as seguintes ferramentas instaladas:

- **Java 8 ou superior**: O projeto requer o JDK 8 ou versões posteriores.
- **Maven**: O Maven é utilizado para gerenciamento de dependências e execução dos testes. Caso não tenha o Maven instalado, consulte a [documentação do Maven](https://maven.apache.org/install.html) para instruções de instalação.

### Executando Todos os Testes

Para rodar todos os testes de unidade e integração do projeto, basta executar o seguinte comando Maven na raiz do projeto:

```bash
mvn clean test
```

## Autor
Leonardo Alves Gonçalves https://github.com/leozeraxp
