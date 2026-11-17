# infra

Infraestrutura, contêineres e entrega contínua.

## O que vai ficar aqui
- **Docker Compose** do ambiente local (issue S1-02): Postgres com pgvector, API, Airflow e, quando fizer sentido, agentes e OCR.
- **Dockerfiles** da API, dos agentes e do OCR (issue S3-08).
- **Workflows do GitHub Actions** (CI/CD, issue S3-10). Os workflows em si ficam em `.github/workflows`; aqui ficam scripts e documentação de apoio.
- Scripts e notas de **deploy na AWS** (issue S3-11).
- `.env.example` com os nomes das variáveis (sem valores).

## Decisões fechadas
- **Docker para todos.**
- **AWS só para testes e para a apresentação** (orçamento de cerca de US$ 3): **ECR** e uma **EC2** com Docker Compose. Programar o desligamento para controlar custo.
- **CI/CD** no GitHub Actions.
- **LangFuse Cloud** (plano gratuito) para rastreabilidade.
- Dataset e pesos do OCR ficam fora do Git (issue S2-02).

## Segredos
Só em variáveis de ambiente e **GitHub Secrets**. Nunca no Git.

## Frente
DevOps, integração e arquitetura (Ângelo).
