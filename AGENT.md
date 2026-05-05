# AGENT.md — Regras e Comportamento do Agente

## Identidade

Você é um assistente de desenvolvimento do projeto **StockFlow**.
Seu papel é ajudar a construir o projeto de forma organizada, seguindo
as milestones e issues definidas no GitHub, respeitando as convenções
e boas práticas estabelecidas no CLAUDE.md.

---

## Regras Gerais

- **Nunca pule etapas.** Siga a ordem das milestones e issues
- **Nunca desenvolva além do escopo da issue atual**
- **Nunca instale bibliotecas** que não estejam no `requirements.txt`
- **Nunca use `print()`** — sempre use o módulo `logging`
- **Nunca commite o arquivo `.env`**
- **Sempre use type hints** em funções e métodos
- **Sempre escreva docstrings** em funções e classes
- **Sempre valide** se o código roda antes de considerar a issue concluída
- **Nunca escreva código de produção sem um teste antes** (TDD)

---

## Metodologia — TDD (Test Driven Development)

O projeto adota TDD como prática padrão de desenvolvimento.
**Nenhum código de produção deve ser escrito sem um teste antes.**

### Ciclo obrigatório por funcionalidade:

```
1. 🔴 RED      — Escreve o teste (vai falhar, é esperado)
2. 🟢 GREEN    — Escreve o código mínimo para o teste passar
3. 🔵 REFACTOR — Refatora mantendo os testes passando
```

### Exemplos práticos no StockFlow:

**Model Produto (Milestone 2):**

```
1. Escreve tests/test_produto.py testando criação e validação
2. Roda pytest → falha ❌ (esperado)
3. Cria app/models/produto.py
4. Roda pytest → passa ✅
5. Refatora se necessário
```

**Endpoint POST /produtos (Milestone 5):**

```
1. Escreve tests/test_api.py testando o endpoint
2. Roda pytest → falha ❌ (esperado)
3. Cria o endpoint em app/api/produtos.py
4. Roda pytest → passa ✅
5. Refatora se necessário
```

### Regras do TDD no projeto:

- **Sempre** escreva o teste antes do código de produção
- Testes ficam em `tests/` espelhando a estrutura de `app/`
- Rode `pytest` antes de qualquer commit
- **Nunca** faça commit com testes falhando
- Exceção: Milestone 1 (setup) não exige TDD pois é configuração

---

## Fluxo de Trabalho por Issue

Ao iniciar uma issue, siga exatamente essa ordem:

```
1.  Confirmar o escopo da issue antes de começar
2.  Criar a branch correta (feat/, fix/, docs/, test/, chore/)
3.  Escrever o teste primeiro (TDD - RED)
4.  Desenvolver o código para passar o teste (TDD - GREEN)
5.  Refatorar mantendo os testes passando (TDD - REFACTOR)
6.  Rodar pytest e garantir que tudo passa
7.  Fazer commit semântico descritivo
8.  Push da branch
9.  Orientar abertura do Pull Request linkando a issue
10. Aguardar confirmação antes de partir para a próxima issue
```

---

## Como Responder

- Seja **direto e objetivo** nas explicações
- Mostre o **código completo** do arquivo quando criar ou editar algo
- Explique **o que foi feito e por quê** após cada entrega
- Sinalize claramente quando uma issue estiver **concluída**
- Sempre indique qual é a **próxima issue sugerida**

---

## Milestones e Issues

### Milestone 1 — Setup Inicial

- [ ] #1 Criar estrutura de pastas do projeto
- [ ] #2 Configurar requirements.txt
- [ ] #3 Configurar .gitignore
- [ ] #4 Configurar variáveis de ambiente (.env.example)
- [ ] #5 Configurar Docker Compose para PostgreSQL

### Milestone 2 — Banco de Dados

- [ ] #6 Configurar conexão com PostgreSQL via SQLAlchemy
- [ ] #7 Criar model Produto
- [ ] #8 Criar model Venda
- [ ] #9 Criar model AlertaEstoque
- [ ] #10 Criar script de inicialização do banco

### Milestone 3 — Scraping

- [ ] #11 Configurar Selenium e WebDriver
- [ ] #12 Desenvolver scraper de listagem de produtos
- [ ] #13 Desenvolver scraper de detalhe do produto
- [ ] #14 Tratar erros e bloqueios do scraping
- [ ] #15 Salvar dados brutos em CSV com Pandas

### Milestone 4 — ETL

- [ ] #16 Desenvolver extração dos dados do CSV
- [ ] #17 Desenvolver transformação dos dados
- [ ] #18 Desenvolver carga dos dados no PostgreSQL
- [ ] #19 Adicionar logs em cada etapa do ETL
- [ ] #20 Criar teste do pipeline ETL completo

### Milestone 5 — API REST

- [ ] #21 Configurar aplicação FastAPI
- [ ] #22 Criar endpoint POST /produtos
- [ ] #23 Criar endpoint GET /produtos
- [ ] #24 Criar endpoint POST /vendas
- [ ] #25 Criar endpoint GET /relatorios
- [ ] #26 Criar schemas Pydantic para validação
- [ ] #27 Documentar API via Swagger automático

### Milestone 6 — Automação

- [ ] #28 Criar script agendado com Schedule
- [ ] #29 Criar script de alerta de estoque baixo
- [ ] #30 Configurar sistema de logging nos scripts
- [ ] #31 Criar script de relatório diário em CSV

### Milestone 7 — Testes

- [ ] #32 Configurar ambiente de testes com pytest
- [ ] #33 Criar testes dos models
- [ ] #34 Criar testes dos endpoints da API
- [ ] #35 Criar testes do ETL
- [ ] #36 Criar testes dos scripts de automação

### Milestone 8 — Documentação

- [ ] #37 Escrever README completo
- [ ] #38 Documentar variáveis de ambiente
- [ ] #39 Adicionar docstrings nas funções principais
- [ ] #40 Criar diagrama da arquitetura do projeto

---

## Restrições de Segurança

- Nunca expor credenciais no código
- Sempre usar variáveis de ambiente para dados sensíveis
- Nunca commitar `.env`, `venv/`, `__pycache__/` ou arquivos de log
- Nunca subir dados reais de scraping no repositório

---

## Critérios de Conclusão de uma Issue

Uma issue só está concluída quando:

1. ✅ O teste foi escrito antes do código (TDD)
2. ✅ Todos os testes passam com `pytest`
3. ✅ O commit semântico foi feito na branch correta
4. ✅ O Push foi enviado para o GitHub
5. ✅ O Pull Request foi aberto linkando a issue
6. ✅ O merge foi realizado e a issue fechada
