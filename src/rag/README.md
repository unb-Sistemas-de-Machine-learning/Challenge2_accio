# rag

Camada de **dados de receitas e busca**: onde as receitas são carregadas, enriquecidas e buscadas.

## O que vai ficar aqui
- **Carga do RecipeNLG Lite** no PostgreSQL (issue S1-06).
- **Padronização de ingredientes.**
- **Enriquecimento nutricional** com a **TBCA (USP)**; plano B: TACO (Unicamp). Ingredientes em inglês são mapeados uma vez para o nome da TBCA, com cache. Sem correspondência confiável, o LLM estima e o valor fica marcado como **estimativa**.
- **Classificação** de culinária, categoria da refeição e tempo de preparo.
- **Embeddings e índices.**
- **Busca híbrida** com **Reciprocal Rank Fusion (RRF)** e **re-rank**.
- Conjunto de avaliação da busca.

## Busca
1. Lexical: `tsvector` e `pg_trgm`.
2. Vetorial: `pgvector`.
3. Fusão das listas com RRF.
4. Re-rank com **cross-encoder** (MiniLM): cerca de 20 candidatos para 5.

Tudo em **um único PostgreSQL**.

## Ferramentas
- PostgreSQL com pgvector, tsvector e pg_trgm.
- Modelo de embeddings e cross-encoder MiniLM (sentence-transformers).
- pandas para exploração dos dados.
- pytest.

## Métricas
**Recall@k** e **MRR**, comparando vetorial puro, híbrido e híbrido com re-rank.

## Licença e limitação
O RecipeNLG Lite é em inglês e tem licença **só não comercial**. Isso é registrado como limitação no Docs.

## Frente
Engenharia de Dados (Yan). As funções daqui são chamadas pelas DAGs de `src/airflow`.
