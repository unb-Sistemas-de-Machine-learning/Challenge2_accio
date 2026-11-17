# api

Camada de **API** do projeto. O app e os agentes chamam **os mesmos serviços** daqui.

## O que vai ficar aqui
- **Contrato OpenAPI** (definido *antes* de implementar, issue S1-04). Quem não roda tudo usa respostas simuladas conforme esse contrato.
- **Serviço de despensa:** consultar e atualizar itens.
- **Serviço de ingestão de notas:** rascunho, detecção de nota repetida e correções do usuário.
- **Endpoint do OCR:** recebe a imagem e devolve o JSON da nota (modelo vem de `src/ocr`).
- **Endpoint de chat:** entrada para o supervisor de `src/agents`.
- **Esquema do banco** e migrações (PostgreSQL).

## Ferramentas
- Python e **FastAPI** (gera a documentação OpenAPI automaticamente).
- **Pydantic** para validar entradas e saídas.
- **PostgreSQL** (um único, com pgvector).
- **pytest** para testes.

## Frente
API e Integração (Ângelo). Consumidores: app (Rodrigo) e agentes (Pedro).

## Regras
- Mudou o contrato? Avise o app e os agentes antes do merge.
- Nunca colocar chaves de API no código. Use variáveis de ambiente.
