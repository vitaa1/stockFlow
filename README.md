# StockFlow

Sistema de gestão de estoque para loja de informática com scraping, ETL e API REST.

## Stack

- **Python 3.11+**
- **FastAPI** — API REST
- **SQLAlchemy** — ORM
- **PostgreSQL** — banco de dados (via Docker)
- **Pandas** — processamento de dados (ETL)
- **Selenium** — scraping
- **Schedule** — agendamento de tarefas
- **pytest** — testes

## Início rápido

### 1. Clonar e configurar variáveis de ambiente

```bash
cp .env.example .env
# Edite .env se quiser alterar usuário/senha/porta do PostgreSQL
```

### 2. Subir o banco de dados

```bash
docker compose up -d
```

### 3. Criar e ativar o ambiente virtual

```bash
python -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

## Estrutura do projeto

```
StockFlow/
├── app/
│   ├── api/        # Routers e endpoints FastAPI
│   ├── models/     # Modelos SQLAlchemy (tabelas)
│   ├── schemas/    # Schemas Pydantic (request/response)
│   └── core/       # Configurações, banco, segurança
├── scripts/        # Scripts de scraping e ETL
├── tests/          # Testes automatizados
└── docs/           # Documentação adicional
```
