# Gestor de Despensa

App mobile em que o usuário fotografa a notinha do supermercado, um modelo de OCR treinado pelo grupo lê os itens e a despensa é atualizada. Um chat com agentes sugere receitas com o que há em casa e dá orientação de qualidade de vida (calorias, gordura, açúcar, tipo de refeição, tempo de preparo).

Projeto da disciplina Tópicos Especiais em Engenharia de Software (UnB), Challenge 2, tema qualidade de vida. **Entrega final: 07/12/2026.**

> O app apoia a decisão do usuário. Ele **não** é aconselhamento nutricional nem garantia de segurança alimentar.

## Perfis
- **Prático:** foco em tempo e ingredientes, esconde números.
- **Nutrição:** mostra e filtra por calorias, gordura e açúcar.

## Arquitetura (5 camadas)

| Camada | Tecnologia | Pasta |
|---|---|---|
| App | React Native com Expo | [src/app](src/app) |
| API | FastAPI, contrato OpenAPI | [src/api](src/api) |
| OCR | Donut com LoRA (imagem para JSON) | [src/ocr](src/ocr) |
| Agentes | LangGraph (supervisor, Inventário e Receitas) | [src/agents](src/agents) |
| Dados | PostgreSQL com pgvector, busca híbrida e re-rank | [src/rag](src/rag) |
| Orquestração | Apache Airflow (4 DAGs) | [src/airflow](src/airflow) |
| Infra | Docker, GitHub Actions, AWS | [src/infra](src/infra) |

A decisão de cada camada, os riscos e as métricas ficam no documento técnico (Docs), que é a fonte da verdade. Não há relatório separado.

## Estrutura do repositório

```
.
├── src/
│   ├── api/       serviços FastAPI e contrato OpenAPI
│   ├── agents/    supervisor e agentes (LangGraph)
│   ├── ocr/       gerador de notas sintéticas, treino e avaliação do OCR
│   ├── rag/       embeddings, índices, busca híbrida (RRF) e re-rank
│   ├── airflow/   DAGs e funções das tarefas
│   ├── app/       app mobile (Expo)
│   └── infra/     Docker Compose, Dockerfiles, CI/CD, AWS
├── docs/          glossário e documentação de apoio
├── CLAUDE.md      instruções do assistente de programação em par
└── README.md
```

Cada pasta de `src/` tem seu próprio README com o que ela contém, as ferramentas e quem cuida dela.

## Como rodar

> O ambiente completo com Docker Compose é a issue S1-02. Até lá, cada pasta explica o que dá para rodar sozinha. Este trecho será atualizado quando o Compose existir.

Pré-requisitos previstos: Docker e Docker Compose, Python 3.11 ou superior, Node.js (LTS) e uma conta no Expo.

Quando o ambiente existir, o fluxo será:
1. Copiar `.env.example` para `.env` e preencher as variáveis (nunca versionar o `.env`).
2. Subir os serviços com Docker Compose (comando definido em `src/infra`).
3. Abrir o app com o Expo e apontar para a API local.

Quem não consegue rodar tudo na própria máquina usa respostas simuladas conforme o contrato OpenAPI.

## Equipe e frentes

| Frente | Responsáveis (GitHub) |
|---|---|
| OCR | Matheus (`matheus-06`) e Ângelo |
| Multiagente | Pedro (`pedrossantoss`) e Ângelo |
| Engenharia de Dados | Yan (`yanrdgs-dev`) |
| App | Rodrigo (`Rodrigoatila09`) |
| DevOps, integração, arquitetura | Ângelo |

## Fluxo de código

1. **Uma issue, uma branch.** Nome da branch começa com o código da issue, por exemplo `s2-03-primeiro-finetuning`.
2. **Nada direto na `main`.** Todo código entra por pull request.
3. **Pull request** com descrição contendo `Closes #n` (n é o número da issue) e **uma aprovação** de um colega.
4. Veja "Depende de" na issue antes de começar. Se algo bloqueia, avise o grupo.
5. **Código congelado em 05/12.**

Commits curtos e no imperativo, por exemplo `Adiciona gerador de notas sintéticas`.

## Regras de segurança

- **Segredos** (chaves de API, credenciais) só em variáveis de ambiente e GitHub Secrets. Nunca no Git.
- **Notas fiscais reais** (imagens e rótulos) nunca vão para o Git nem para conversas. Ficam fora do repositório, com dados pessoais borrados.
- **Dataset sintético e pesos do OCR** ficam fora do Git, versionados em outro lugar (issue S2-02).

## Sprints

| Sprint | Período |
|---|---|
| S1 | 16 a 22/11 |
| S2 | 23 a 29/11 |
| S3 | 30/11 a 06/12 |

As aulas de segunda e quarta (14h às 16h) funcionam como checkpoints.
