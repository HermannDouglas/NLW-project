# Gerenciamento de Eventos

Este projeto é uma API desenvolvida em Python utilizando o framework Flask. A aplicação permite criar e gerenciar eventos, inscritos e links de eventos. 

## Estrutura do Projeto

- `case.py`: Contém uma classe de exemplo com métodos `__enter__` e `__exit__`.
- `init/schema.sql`: Script SQL para criação das tabelas `Eventos`, `Inscritos` e `Eventos_link`.
- `requirements.txt`: Lista de dependências do projeto.
- `run.py`: Arquivo principal para iniciar o servidor Flask.
- `schema.db`: Banco de dados SQLite.
- `src/`: Diretório principal contendo o código-fonte da aplicação.

### Diretórios e Arquivos Importantes

- `src/controllers/`: Contém os controladores que gerenciam a lógica de criação de eventos, links de eventos e inscritos.
    - `events/`: Controladores relacionados a eventos.
    - `events_link/`: Controladores relacionados a links de eventos.
    - `subscribers/`: Controladores relacionados a inscritos.
- `src/http_types/`: Define os tipos de requisição e resposta HTTP.
    - `http_request.py`: Define a classe `HttpRequest`.
    - `http_response.py`: Define a classe `HttpResponse`.
- `src/main/`: Contém a configuração do servidor e as rotas da aplicação.
    - `routes/`: Define as rotas para eventos, links de eventos e inscritos.
    - `server/`: Configuração do servidor Flask.
- `src/model/`: Contém a configuração do banco de dados e as entidades.
    - `configs/`: Configurações do banco de dados.
    - `entities/`: Define as entidades `Eventos`, `Inscritos` e `Eventos_link`.
    - `repositories/`: Define os repositórios para acesso ao banco de dados.
- `src/validators/`: Contém validadores para as requisições HTTP.

## Instalação

1. Clone o repositório:
    ```sh
    git clone https://github.com/HermannDouglas/NLW-project
    ```
2. Navegue até o diretório do projeto:
    ```sh
    cd NLW-project
    ```
3. Crie um ambiente virtual:
    ```sh
    python -m venv venv
    ```
4. Ative o ambiente virtual:
    - No Windows:
        ```sh
        venv\Scripts\activate
        ```
    - No macOS/Linux:
        ```sh
        source venv/bin/activate
        ```
5. Instale as dependências:
    ```sh
    pip install -r requirements.txt
    ```

## Uso

1. Inicie o servidor Flask:
    ```sh
    python run.py
    ```
2. Acesse a aplicação em `http://localhost:3000`.

## Endpoints

### Criar Evento

- **URL**: `/event`
- **Método**: `POST`
- **Corpo da Requisição**:
    ```json
    {
        "data": {
            "name": "Nome do Evento"
        }
    }
    ```

### Criar Link de Evento

- **URL**: `/events_link`
- **Método**: `POST`
- **Corpo da Requisição**:
    ```json
    {
        "data": {
            "event_id": 1,
            "subscriber_id": 1
        }
    }
    ```

### Criar Inscrito

- **URL**: `/subscriber`
- **Método**: `POST`
- **Corpo da Requisição**:
    ```json
    {
        "data": {
            "name": "Nome do Inscrito",
            "email": "email@exemplo.com",
            "evento_id": 1
        }
    }
    ```

### Consultar Inscritos por Link

- **URL**: `/subscriber/link/<link>/event/<event_id>`
- **Método**: `GET`

### Consultar Ranking de Evento

- **URL**: `/subscriber/ranking/event/<event_id>`
- **Método**: `GET`

