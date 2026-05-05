# StockFlow — Contexto do Projeto

## Descrição

Sistema de gestão de estoque para loja de informática com pipeline ETL completo:
scraping de produtos via Selenium, transformação com Pandas, carga no PostgreSQL
e exposição via API REST com FastAPI. Inclui automação com scripts agendados.

---

## Stack

- **Linguagem:** Python 3.11+
- **API REST:** FastAPI
- **ORM:** SQLAlchemy
- **Banco de dados:** PostgreSQL (via Docker)
- **ETL / Dados:** Pandas
- **Scraping:** Selenium + WebDriver
- **Agendamento:** Schedule
- **Testes:** pytest
- **Ambiente:** python-dotenv
- **Logs:** Logging (nunca usar print)
- **Containerização:** Docker + Docker Compose

---

## Estrutura de Pastas

```
StockFlow/
├── app/
│   ├── api/          # endpoints FastAPI
│   ├── models/       # models SQLAlchemy
│   ├── schemas/      # schemas Pydantic
│   └── core/         # configurações, banco, logger
├── scripts/          # automações e tarefas agendadas
├── tests/            # testes com pytest
├── docs/             # documentação
├── .env.example      # variáveis de ambiente (modelo)
├── .env              # variáveis reais (nunca commitar)
├── .gitignore
├── docker-compose.yml
├── requirements.txt
└── README.md
```

---

## Comandos Úteis

```bash
# Ativar ambiente virtual
source venv/bin/activate

# Instalar dependências
pip install -r requirements.txt

# Subir banco PostgreSQL
docker compose up -d

# Rodar a API
uvicorn app.main:app --reload

# Rodar testes
pytest tests/

# Rodar script de automação
python scripts/scheduler.py
```

---

## Variáveis de Ambiente

Copie o `.env.example` para `.env` e preencha os valores:

```
DB_HOST=localhost
DB_PORT=5432
DB_NAME=stockflow
DB_USER=postgres
DB_PASSWORD=postgres
DATABASE_URL=postgresql://postgres:postgres@localhost:5432/stockflow
```

---

## Convenções de Código

### Branches

```
feat/nome-da-feature
fix/nome-do-bug
docs/nome-da-doc
test/nome-do-teste
chore/nome-da-tarefa
```

### Commits semânticos

```
feat: descrição da funcionalidade
fix: descrição da correção
docs: descrição da documentação
test: descrição do teste
chore: descrição da tarefa de setup
refactor: descrição da refatoração
```

### Código

- Sempre usar **type hints** nas funções
- Sempre usar **docstrings** nas funções e classes
- Usar **logging** no lugar de print
- Variáveis e funções em **snake_case**
- Classes em **PascalCase**
- Nunca commitar o arquivo `.env`

---

## Milestones do Projeto

| #   | Milestone      | Status          |
| --- | -------------- | --------------- |
| 1   | Setup Inicial  | 🔄 Em andamento |
| 2   | Banco de Dados | ⏳ Pendente     |
| 3   | Scraping       | ⏳ Pendente     |
| 4   | ETL            | ⏳ Pendente     |
| 5   | API REST       | ⏳ Pendente     |
| 6   | Automação      | ⏳ Pendente     |
| 7   | Testes         | ⏳ Pendente     |
| 8   | Documentação   | ⏳ Pendente     |

---

## Observações Importantes

- O arquivo `.env` **nunca** deve ser commitado
- Toda nova dependência deve ser adicionada ao `requirements.txt`
- Sempre rodar os testes antes de abrir um Pull Request
- Cada issue deve ter sua própria branch e Pull Request
